# មេរៀន ៩៖ Dictionaries និង Sets

## Dictionary
dict ផ្គូផ្គង key ទៅ value; key ត្រូវ hashable ហើយ unique:
~~~python
student = {"name": "សុភា", "score": 90}
student["score"] = 94
student["class"] = "Python"
print(student.get("email", "មិនបានកំណត់"))
~~~
ការចូល student["missing"] បង្ក KeyError; get() អនុញ្ញាត default។ Keys ស្របសម្រាប់ lookup; កុំសន្មតថា dict ជាអ object មាន schema តឹងរ៉ឹង បើ input មកពីប្រភពខាងក្រៅ—ត្រូវ validate។

## Iterate dict
~~~python
for key, value in student.items():
    print(key, value)
~~~
keys(), values(), items() ជួយអាន។ dict insertion-ordered ក្នុង Python ថ្មី ប៉ុន្តែកុំប្រើ order ជំនួស model ច្បាស់ប្រសិនបើ semantics សំខាន់។

## Sets
set ជា collection នៃតម្លៃ unique មិនរក្សាលំដាប់សម្រាប់ការប្រើទូទៅ:
~~~python
tags = {"python", "web", "python"}
tags.add("django")
print("web" in tags)
~~~
ប្រតិបត្តិការសំខាន់៖ union A | B, intersection A & B, difference A - B។ ប្រើ set សម្រាប់ deduplicate ឬ membership test; កុំប្រើពេល order/duplicates មានន័យ។

## Mutable keys
list/dict មិនអាចជា dict key/set member ព្រោះវា mutable និងមិន hashable។ tuple ដែលមានតែ values hashable អាចប្រើជាគន្លឹះបាន។

## អនុវត្ត
បង្កើត inventory dict item→quantity; បន្ថែម/កែ stock; រក missing item ដោយ get; គណនា tags រួម/ខុសគ្នារវាង users។

## សំណួរ
1. get() មានអត្ថប្រយោជន៍អ្វី?
2. Set រក្សា duplicate ដែរឬទេ?
3. ហេតុអ្វី list មិនអាចជាឃ្លឹះ dict?

**ចម្លើយ**៖ ផ្តល់ fallback ជំនួស KeyError; ទេ; list mutable ដូច្នេះមិន hashable។
