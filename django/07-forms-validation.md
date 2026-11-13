# មេរៀន ៧៖ Forms និង Validation

## Form ជួយអ្វី?
Django Form បង្កើត fields, parse input, validate និងបង្ហាញ errors។ ModelForm map fields ទៅ model និងអាច save object បាន។ Form validation គឺសម្រាប់ usability/data integrity; authorization ត្រូវពិនិត្យផ្សេងទៀត។

~~~python
from django import forms

class CourseForm(forms.Form):
    title = forms.CharField(max_length=200)
    level = forms.ChoiceField(choices=[
        ("beginner", "Beginner"),
        ("advanced", "Advanced"),
    ])
~~~

## GET និង POST
GET បង្ហាញទំព័រ/form; POST បញ្ជូន data ដែលអាចផ្លាស់ប្តូរ state។ ប្រើ request.method និង bind form ទៅ POST:
~~~python
def create_course(request):
    if request.method == "POST":
        form = CourseForm(request.POST)
        if form.is_valid():
            # save/use cleaned_data
            ...
    else:
        form = CourseForm()
    return render(request, "courses/form.html", {"form": form})
~~~
is_valid() run validation; cleaned_data មាន values បន្ទាប់ពី parse/validate; កុំយក request.POST ត្រង់ៗទៅ persist ដោយមិន validate។

## ModelForm និង errors
ModelForm អនុញ្ញាតកំណត់ Meta.model និង fields allowlist។ កុំប្រើ fields="__all__" ដោយមិនគិត; fields ដែលមិនគួរអ្នកប្រើកែ អាចក្លាយជា mass-assignment issue។ បង្ហាញ field errors និង non-field errors ក្នុង template។

## CSRF និង templates
ក្នុង form POST ទៅ view ដែល protected ដាក់ {% csrf_token %}។ CSRF token ជួយការពារ forged requests; កុំបិទ CSRF middleware ដើម្បីធ្វើឱ្យ form ដំណើរការ។

## អនុវត្ត
បង្កើត CourseForm/ModelForm, validate title និង level, បង្ហាញ field errors, រក្សាទិន្នន័យតែពេល valid និង test invalid POST។

## សំណួរ
1. cleaned_data មានអ្វី?
2. ហេតុអ្វី ModelForm fields គួរ allowlist?
3. CSRF token ជំនួស authorization ដែរឬទេ?

**ចម្លើយ**៖ values ដែលបាន validate/convert; កុំឱ្យអ្នកប្រើកែ fields ដែលមិនគួរអាចកែ; មិនមែនទេ—permission ត្រូវពិនិត្យដោយឡែក។
