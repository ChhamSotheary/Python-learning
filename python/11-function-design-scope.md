# មេរៀន ១១៖ Function Design, Scope និង Arguments

## Positional និង keyword arguments
~~~python
def create_user(name, *, active=True, role="student"):
    return {"name": name, "active": active, "role": role}

user = create_user("Dara", role="teacher")
~~~
សញ្ញា * បង្ខំ arguments ខាងក្រោយឱ្យប្រើ keyword; វាធ្វើឱ្យ call ច្បាស់ និងអនុញ្ញាតបន្ថែម parameter ដោយមិនបំបែក positional call ចាស់។ Python ក៏គាំទ្រ positional-only separator / និង keyword-only separator * ក្នុង signatures ស្មុគស្មាញ។

## *args និង **kwargs
~~~python
def total(*numbers):
    return sum(numbers)

def show_options(**options):
    for key, value in options.items():
        print(key, value)
~~~
*args ប្រមូល positional arguments ជា tuple; **kwargs ប្រមូល keyword arguments ជា dict។ ប្រើពេល API មានហេតុផល flexible; កុំប្រើវាទូទៅពេក ព្រោះបាត់ភាពច្បាស់ និង type checking។

## Scope និង LEGB
ឈ្មោះក្នុង function local; បន្ទាប់មក Python រក enclosing, global, builtins (LEGB)។ ការអាន global អាចធ្វើបាន ប៉ុន្តែការកែ global state ធ្វើឱ្យ test/debug ពិបាក។ បញ្ជូន input ជា parameter និង return result ជំនួសការពឹងលើ global variable។

## Mutable arguments និង default pitfall
~~~python
def add_item(item, items=None):
    if items is None:
        items = []
    items.append(item)
    return items
~~~
កុំសរសេរ items=[] ជា default; list នោះ shared រវាង calls។ បើ function កែ list ដែល caller បញ្ជូន អ្នក caller នឹងឃើញ mutation; បញ្ជាក់ behavior នេះ ឬ copy ប្រសិនបើត្រូវការ។

## អនុវត្ត
សរសេរ function summary(items, *, include_average=True) ដែល return dict សម្រាប់ min/max/average។ កុំ print ក្នុង function; caller ជាអ្នកសម្រេចបង្ហាញ។

## សំណួរ
1. តើ **kwargs ប្រមូលអ្វី?
2. តើ mutable default bug កើតដោយសារអ្វី?
3. ហេតុអ្វី global state ធ្វើឱ្យ test ពិបាក?

**ចម្លើយ**៖ keyword arguments ជា dict; default object បង្កើតតែម្តង និងប្រើឡើងវិញ; tests ពឹង state រួម និងអាចប៉ះគ្នា។
