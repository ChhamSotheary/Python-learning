# មេរៀន ១០៖ Functions មូលដ្ឋាន

## គោលដៅ
ដាក់ logic ដែលប្រើឡើងវិញក្នុង function, ទទួល arguments និងបញ្ជូនលទ្ធផលដោយ return។

~~~python
def greet(name):
    """ត្រឡប់សារស្វាគមន៍។"""
    return f"សួស្តី {name}"

message = greet("សុភា")
print(message)
~~~
def បង្កើត function; name ជា parameter; "សុភា" ជា argument; return បញ្ជូនលទ្ធផលទៅ caller និងបញ្ចប់ function។ បើគ្មាន return ច្បាស់លាស់ function ត្រឡប់ None។

## Parameters និង defaults
~~~python
def calculate_total(price, quantity=1):
    return price * quantity

print(calculate_total(5, 3))
print(calculate_total(5))
~~~
Default parameters អនុញ្ញាត argument មិនចាំបាច់។ កុំប្រើ mutable object ជា default ដូច list/dict ព្រោះ default object ត្រូវបានបង្កើតតែម្តង និងអាចរក្សា state ចន្លោះ calls។

## Function ស្អាត
Function គួរមានការងារមួយច្បាស់, ឈ្មោះជាកិរិយាសព្ទ, input/output ងាយយល់។ បំបែក computation ចេញពី input/output ដើម្បី test ងាយ។ Docstring ពិពណ៌នាកិច្ចសន្យា/side effects មិនមែនអត្ថបទដដែលនឹង code។

## អនុវត្ត
សរសេរ function convert_celsius_to_fahrenheit, function is_even, និង function calculate_total មាន optional tax rate។ សាក values ផ្សេងៗ។

## សំណួរ
1. Parameter ខុសពី argument ដូចម្តេច?
2. Function គ្មាន return ត្រឡប់អ្វី?
3. ហេតុអ្វី function មួយគួរមានគោលបំណងច្បាស់?

**ចម្លើយ**៖ parameter ជាឈ្មោះក្នុង definition; argument ជាតម្លៃពេលហៅ; None; ងាយអាន, test, reuse និងកែ។
