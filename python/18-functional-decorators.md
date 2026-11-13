# មេរៀន ១៨៖ Functional Patterns និង Decorators

## First-class functions
Function ជា object អាចផ្ទុកក្នុង variable, បញ្ជូនទៅ function ផ្សេង និង return វិញ:
~~~python
def apply(value, operation):
    return operation(value)

print(apply(5, lambda n: n * 2))
~~~
lambda សមសម្រាប់ expression តូចមួយ; បើ logic ធំ ប្រើ def ដែលមានឈ្មោះច្បាស់។

## Pure functions និង side effects
Pure function ឱ្យ output ដូចគ្នាសម្រាប់ input ដូចគ្នា និងមិនកែ external state។ វាងាយ test/reason ប៉ុន្តែកម្មវិធីទាំងមូលត្រូវមាន side effects ដូច file/network; ផ្ដុំ side effects នៅព្រំដែន ហើយរក្សា core logic សាមញ្ញ។

## Decorator
Decorator ទទួល function ហើយ return function ថ្មី:
~~~python
from functools import wraps

def announce(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print("ចាប់ផ្តើម")
        return func(*args, **kwargs)
    return wrapper

@announce
def greet(name):
    return f"សួស្តី {name}"
~~~
@announce ស្មើនឹង greet = announce(greet)។ wraps រក្សា metadata ដូច __name__/docstring។ Decorator ប្រើសម្រាប់ cross-cutting behavior ដូច logging/cache/auth boundary ក្នុង app; កុំដាក់ business logic សំខាន់ក្នុង wrapper ដែលលាក់ flow។

## Closures
Nested function អាចចងឈ្មោះពី enclosing scope; នេះហៅ closure។ ប្រើពេលបង្កើត function ជាមួយ config បាន ប៉ុន្តែ class ឬ callable object អាចអានងាយជាងសម្រាប់ state ស្មុគស្មាញ។

## អនុវត្ត
សរសេរ decorator ដែលវាស់ពេលដំណើរការ និង return ដដែល; ប្រើ functools.wraps; test function ដែលមាន positional/keyword arguments និង exception។

## សំណួរ
1. Decorator syntax បម្លែងអ្វី?
2. wraps ជួយអ្វី?
3. ហេតុអ្វី pure function ងាយ test?

**ចម្លើយ**៖ function ត្រូវបាន wrap/rebind ជា function ថ្មី; រក្សា metadata; គ្មាន side effects លាក់ និង output អាស្រ័យតែ input។
