# មេរៀន ៧៖ Loops និង Control Flow

## គោលដៅ
ធ្វើការដដែលលើ sequence ដោយ for, while, range, break និង continue។

## for និង range
~~~python
names = ["សុភា", "ដារ៉ា", "មាលា"]
for name in names:
    print(f"សួស្តី {name}")
for number in range(1, 6):
    print(number)
~~~
for ឆ្លងកាត់ iterable ម្តងមួយ។ range(stop) ចាប់ពី 0 មិនរួម stop; range(start, stop, step) អាចកំណត់ចាប់ផ្តើមនិងជំហាន។ ប្រសិនបើត្រូវការ index និង value ប្រើ enumerate()។

## while
~~~python
attempts = 0
while attempts < 3:
    print("សាកម្តងទៀត")
    attempts += 1
~~~
while បន្តរហូត condition false។ ត្រូវប្រាកដថាមានអ្វីមួយផ្លាស់ប្តូរ condition; បើមិនដូច្នោះអាច infinite loop។

## break, continue និង loop else
break បញ្ឈប់ loop ទាំងមូល; continue រំលងទៅ iteration បន្ទាប់។ Loop else រត់ពេល loop បញ្ចប់ដោយមិន break; មានប្រយោជន៍សម្រាប់ search តែអ្នកថ្មីអាចជ្រើស flag/return សាមញ្ញជាង។

## កុំកែ list ពេលកំពុង iterate ដោយគ្មានផែនការ
បើចង់លុប items សូមបង្កើត filtered list:
~~~python
active = [user for user in users if user["active"]]
~~~
ការកែ collection ខណៈឆ្លងកាត់វា អាចរំលង element ឬបង្កលទ្ធផលចម្លែក។

## អនុវត្ត
បោះពុម្ពលេខ 1–20 ដែលចែកដាច់នឹង 3; គណនាផលបូកក្នុង list; បង្កើត guessing loop មានកំណត់ចំនួនសាកល្បង។

## សំណួរ
1. range(2, 7) មានតម្លៃអ្វីខ្លះ?
2. តើ while អាចក្លាយជា infinite loop ដោយរបៀបណា?
3. break និង continue ខុសគ្នាដូចម្តេច?

**ចម្លើយ**៖ 2–6; condition មិនដែលក្លាយជា false; break ចេញពី loop, continue រំលងតែ iteration បច្ចុប្បន្ន។
