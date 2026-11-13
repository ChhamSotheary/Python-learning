# មេរៀន ២៖ Variables, Names និង Data Types

## គោលដៅ
ដាក់តម្លៃក្នុងឈ្មោះ, យល់ type មូលដ្ឋាន និងបំលែងទិន្នន័យដោយចេតនា។

## Names និង assignment
~~~python
name = "សុភា"
age = 20
height_m = 1.62
is_student = True
~~~
សញ្ញា = ក្នុង assignment មានន័យថាចងឈ្មោះទៅវត្ថុ/តម្លៃ មិនមែនសមីការស្មើគ្នាទេ។ Python ជា dynamically typed: type របស់ object ដឹងនៅ runtime ហើយឈ្មោះអាចចងទៅ object type ផ្សេង ប៉ុន្តែកុំប្ដូរបែបមិនមានហេតុផល។

~~~python
print(type(name))  # str
print(type(age))   # int
~~~

## Types សំខាន់
- int: ចំនួនគត់ ដូច 20
- float: ចំនួនមានទសភាគ ដូច 1.62
- str: អត្ថបទក្នុង quote
- bool: True ឬ False
- NoneType: តម្លៃគ្មាន/មិនទាន់មាន ដែលសរសេរ None

## Naming convention
ប្រើ lowercase_with_underscores សម្រាប់ variables/functions។ ឈ្មោះត្រូវចាប់ផ្តើមដោយអក្សរ ឬ underscore មិនមែនលេខ; case-sensitive; កុំប្រើ Python keywords ដូច if/class ជាឈ្មោះ។ ជ្រើសឈ្មោះពិពណ៌នាដូច total_price ជាង x នៅក្នុង logic សំខាន់។

## Conversion និង type errors
~~~python
age_text = "20"
age = int(age_text)
price = float("2.50")
label = str(age)
~~~
ការបំលែងអាចបរាជ័យ៖ int("hello") បង្ក ValueError។ input() ត្រឡប់ string ជានិច្ច; កុំរំពឹងថាវាក្លាយជា number ដោយស្វ័យប្រវត្តិ។

## Mutable vs immutable បើកចំហ
int, float, bool, str ជា immutable; list/dict អាចកែបាន។ ឈ្មោះជាឯកសារយោងទៅ object; នេះនឹងសំខាន់ពេលបញ្ជូន object ទៅ function (មេរៀន 11)។

## អនុវត្ត
បង្កើត variables សម្រាប់ឈ្មោះ, អាយុ, តម្លៃសៀវភៅ និងស្ថានភាពបានបង់។ បោះពុម្ព type។ បំលែង age string ទៅ int ហើយគណនាអាយុឆ្នាំក្រោយ។

## លំហាត់
1. តើ type របស់ "42" ជាអ្វី?
2. តើ input() ត្រឡប់ type អ្វី?
3. តើឈ្មោះ total-price ត្រឹមត្រូវជាឈ្មោះ variable ដែរឬទេ?

**ចម្លើយ**៖ "42" ជា str; input() ត្រឡប់ str; total-price មិនត្រឹមត្រូវសម្រាប់ variable ព្រោះ hyphen ត្រូវបានយល់ជាដក។
