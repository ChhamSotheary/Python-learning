# មេរៀន ៥៖ Input និង Output

## គោលដៅ
ទទួល input ពី user, បម្លែង/validate និងបង្ហាញលទ្ធផលដោយច្បាស់។

## print()
~~~python
name = "មាលា"
score = 88
print("ឈ្មោះ:", name, "ពិន្ទុ:", score)
print(f"{name} ទទួលបាន {score} ពិន្ទុ")
~~~
print() បង្ហាញតម្លៃទៅ stdout; អាចកំណត់ sep/end សម្រាប់ separator និងការបញ្ចប់បន្ទាត់។ Output មិនមែន log សម្រាប់ production ទេ—ប្រើ logging នៅកម្មវិធីពិត។

## input() ត្រឡប់ string
~~~python
name = input("បញ្ចូលឈ្មោះ៖ ").strip()
age_text = input("បញ្ចូលអាយុ៖ ")
age = int(age_text)
print(f"សួស្តី {name}; ឆ្នាំក្រោយអ្នកមានអាយុ {age + 1}")
~~~
បើ age_text មិនមែនលេខ int() បង្ក ValueError។ កុំទុកកម្មវិធី crash ដោយមិនមានសារជួយ user។

~~~python
raw = input("ចំនួន៖ ").strip()
try:
    amount = int(raw)
except ValueError:
    print("សូមបញ្ចូលចំនួនគត់។")
else:
    print(f"អ្នកបញ្ចូល {amount}")
~~~
យើងនឹងរៀន exceptions ពេញលេញនៅមេរៀន 15។ កុំប្រើ eval(input()) ដើម្បីបម្លែងលេខ—វាអាចប្រតិបត្តិកូដដែលមិនទុកចិត្ត។

## អនុវត្ត
បង្កើតកម្មវិធីសួរឈ្មោះ, អាយុ និងពិន្ទុ; strip whitespace; បម្លែងអាយុ/ពិន្ទុ; បង្ហាញសារសង្ខេប។ បើបញ្ចូលខុស បង្ហាញសារ error ដែលមានប្រយោជន៍។

## សំណួរ
1. input() ត្រឡប់ type អ្វី?
2. ហេតុអ្វីមិនប្រើ eval() លើ user input?
3. try/except ជួយអ្វី?

**ចម្លើយ**៖ str; eval អាចរត់ code មិនទុកចិត្ត; ចាប់ error ដែលរំពឹងទុក និងបង្ហាញវិធីកែ។
