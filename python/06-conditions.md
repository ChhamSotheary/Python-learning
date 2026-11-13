# មេរៀន ៦៖ Conditions និង Boolean Logic

## គោលដៅ
ឱ្យកម្មវិធីសម្រេចតាមលក្ខខណ្ឌដោយ if/elif/else និងសរសេរ Boolean expression ឱ្យអានងាយ។

## if / elif / else
~~~python
score = 82
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
else:
    grade = "ត្រូវហាត់បន្ថែម"
print(grade)
~~~
Python ពិនិត្យលក្ខខណ្ឌពីលើចុះក្រោម ហើយរត់ block ដំបូងដែល True។ Indentation កំណត់ថាបន្ទាត់ណាជាផ្នែក block។ លំដាប់ range មានសារៈសំខាន់; ដាក់កម្រិតធំពីលើតូច។

## Comparison និង and/or/not
~~~python
if age >= 18 and has_id:
    print("អាចបន្ត")
if is_admin or is_owner:
    print("អនុញ្ញាតក្នុង app")
if not is_active:
    print("គណនីមិនសកម្ម")
~~~
and ត្រូវទាំងពីរ; or ត្រូវយ៉ាងតិចមួយ; not បញ្ច្រាស boolean។ ប្រើ parentheses សម្រាប់ expression ដែលមានលក្ខខណ្ឌច្រើន ដើម្បីឱ្យអ្នកអានយល់។

## Truthiness
តម្លៃដូច 0, "", [], {}, None ជាទូទៅ false ក្នុង condition; តម្លៃផ្សេងភាគច្រើន true។ ប្រើ truthiness តែពេល semantics សម; ប្រសិនបើចង់បញ្ជាក់ None សូមប្រើ **is None** មិនមែន == None។

~~~python
items = []
if not items:
    print("បញ្ជីទទេ")
~~~

## អនុវត្ត
បង្កើតលទ្ធផល grade ពីពិន្ទុ 0–100។ ប្រសិនបើក្រៅ range បង្ហាញ invalid។ បន្ថែម logic eligibility ដែលត្រូវមាន age និង consent។

## សំណួរ
1. តើ elif មានប្រយោជន៍អ្វី?
2. ហេតុអ្វីលំដាប់ grade threshold សំខាន់?
3. តើតម្លៃ None ពិនិត្យដោយរបៀបណា?

**ចម្លើយ**៖ ពិនិត្យលក្ខខណ្ឌជំនួសជាលំដាប់; បើ threshold តូចនៅមុន វាចាប់តម្លៃដែលគួរចូលកម្រិតខ្ពស់; ប្រើ is None។
