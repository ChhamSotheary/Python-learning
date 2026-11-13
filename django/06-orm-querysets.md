# មេរៀន ៦៖ ORM, QuerySets និង Relationships

## QuerySet
ORM បម្លែង Python expression ទៅ database query។ QuerySet lazy: វាមិន query រហូតដល់ត្រូវ evaluate (iteration, list, bool, slicing ជាក់លាក់)។
~~~python
published = Course.objects.filter(published=True).order_by("-created_at")
for course in published:
    print(course.title)
~~~
filter ជ្រើស records; exclude ដក; get រំពឹង record តែមួយ ហើយបោះ DoesNotExist/MultipleObjectsReturned បើខុស; first អាច return None។ កុំទាញ row ទាំងអស់ដោយមិនចាំបាច់។

## Relationships
~~~python
class Lesson(models.Model):
    course = models.ForeignKey(Course, on_delete=models.CASCADE, related_name="lessons")
    title = models.CharField(max_length=200)
~~~
ForeignKey many-to-one; ManyToManyField many-to-many; OneToOneField one-to-one។ on_delete បញ្ជាក់ behavior ពេល parent លុប (CASCADE, PROTECT, SET_NULL ជាដើម); ជ្រើសតាម business rule មិនមែនចម្លង CASCADE ទាំងអស់។

## N+1 queries
ការចូល related objects ក្នុង loop អាចបង្ក query មួយក្នុងមួយ row។ select_related សម្រាប់ ForeignKey/OneToOne joins; prefetch_related សម្រាប់ ManyToMany/reverse relations:
~~~python
courses = Course.objects.prefetch_related("lessons")
~~~
ប្រើ Django Debug Toolbar ឬ query logging ក្នុង dev ដើម្បីវាស់; កុំ optimize ដោយស្មាន។

## Aggregation និង transactions
annotate បន្ថែម computed value ក្នុង query; aggregate return summary។ transaction.atomic() ធ្វើការផ្លាស់ប្តូរច្រើនជា transaction all-or-nothing។ Parameterize ORM filters; កុំបង្ក raw SQL ដោយ string interpolation។

## អនុវត្ត
បន្ថែម Lesson ForeignKey, migrate, បង្ក queries filter/order, រាប់ lessons per course ដោយ annotate និងប្រៀបធៀប query count មុន/ក្រោយ prefetch_related។

## សំណួរ
1. QuerySet lazy មានន័យអ្វី?
2. select_related សមសម្រាប់ relationship ណា?
3. N+1 query ជាបញ្ហាអ្វី?

**ចម្លើយ**៖ query រត់ពេល evaluate; ForeignKey/OneToOne; query ច្រើនពេក ពេល loop ទាញ related row ដាច់ៗ។
