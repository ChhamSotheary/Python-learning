# មេរៀន ៣៖ Strings និង Text

## គោលដៅ
បង្កើតអត្ថបទ, ជ្រើស/កាត់ផ្នែក, format string និងគ្រប់គ្រង Unicode។

## String និង indexing
~~~python
text = "Python"
print(text[0])    # P
print(text[-1])   # n
print(text[1:4])  # yth
~~~
String ជាលំដាប់ character និង immutable: មិនអាចសរសេរ text[0]="J" បាន។ Slice ចាប់ពី start រហូតដល់ stop ដោយមិនរួម stop; step អាចបន្ថែមដូច text[::2]។

## Methods
~~~python
name = "  Dara  "
clean = name.strip()
print(clean.lower())
print(clean.upper())
print("a,b,c".split(","))
print("-".join(["2026", "11", "13"]))
~~~
Methods ដូច strip/lower/replace/split បង្កើត string ថ្មី; string ដើមមិនផ្លាស់ប្តូរ។ join ជា method របស់ separator string។

## Formatting ដោយ f-string
~~~python
name = "ដារ៉ា"
score = 95
print(f"{name} ទទួលបាន {score} ពិន្ទុ")
print(f"ពិន្ទុ៖ {score:.1f}")
~~~
f-string អនុញ្ញាត expression ក្នុង braces; សម្រាប់តម្លៃពី user កុំដាក់ដោយ raw string formatting ជំនួស parameterized SQL/HTML escaping ត្រឹមត្រូវ។

## Unicode និងអក្សរខ្មែរ
Python string ជា Unicode; អក្សរខ្មែរអាចមាន combining marks ដូច្នេះចំនួន code points មិនតែងស្មើចំនួនតួដែលមើលឃើញ។ ប្រើ encoding UTF-8 សម្រាប់ file; Python 3 ជាទូទៅគាំទ្រ UTF-8 ប៉ុន្តែ file I/O គួរកំណត់ encoding="utf-8" ដោយច្បាស់។

## អនុវត្ត
យកឈ្មោះដែលមាន whitespace, សម្អាតដោយ strip, បង្ហាញ uppercase/lowercase, បំបែកពាក្យ និងបង្កើតប្រយោគដោយ f-string។

## សំណួរ
1. Slice text[1:4] យក index ណាខ្លះ?
2. តើ string អាចកែ character តាម index បានទេ?
3. ហេតុអ្វី join ប្រើជា separator?

**ចម្លើយ**៖ index 1,2,3; string immutable; separator.join(items) ភ្ជាប់ items ដោយ separator ដែលកំណត់។
