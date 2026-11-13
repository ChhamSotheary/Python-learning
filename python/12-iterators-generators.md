# មេរៀន ១២៖ Comprehensions, Iterators និង Generators

## Comprehension
បង្កើត collection ពី iterable ដោយ expression ច្បាស់:
~~~python
squares = [n * n for n in range(1, 6)]
evens = [n for n in range(10) if n % 2 == 0]
lookup = {word: len(word) for word in ["python", "django"]}
unique_lengths = {len(word) for word in ["one", "two", "three"]}
~~~
List comprehension បង្កើត list ទាំងមូល; dict/set comprehensions សម្រាប់ mapping/unique values។ កុំដាក់ loop ជាច្រើនស្រទាប់ ឬ logic វែងក្នុង comprehension—ប្រើ for loop ដើម្បីអានងាយ។

## Iterable និង iterator
Iterable អាចផ្តល់ item ម្តងៗ; iterator រក្សាទីតាំងបច្ចុប្បន្ន ហើយទទួល item តាម next()។ for loop គ្រប់គ្រង iteration protocol ដោយស្វ័យប្រវត្តិ។ Iterator ជាទូទៅ exhausted ក្រោយប្រើអស់; បើចង់ iterate ម្តងទៀត បង្កើត iterator ថ្មីពី iterable។

## Generator
~~~python
def count_up_to(limit):
    number = 1
    while number <= limit:
        yield number
        number += 1

for value in count_up_to(3):
    print(value)
~~~
yield ផ្អាក function ហើយបញ្ជូនតម្លៃមួយ; ពេល next iteration វាបន្តពីទីតាំងដើម។ Generator សន្សំ memory សម្រាប់ stream ធំ ព្រោះមិនបង្កើត list ទាំងមូល។ តែវា one-pass និងមិនមាន random indexing ដូច list។

## Generator expression
~~~python
total = sum(n * n for n in range(1_000_000))
~~~
នេះផលិតតម្លៃតាមតម្រូវការ។ កុំធ្វើ code ឱ្យ lazy បើវាធ្វើឱ្យ logic ពិបាកយល់; ជ្រើសសមាមាត្ររវាង memory និងភាពច្បាស់។

## អនុវត្ត
បម្លែង list លេខទៅ list squares ដោយ comprehension; សរសេរ generator អាន records មួយៗ និងរាប់ពិន្ទុដោយ sum ដោយមិនបង្កើត intermediate list។

## សំណួរ
1. List comprehension និង generator ខុសគ្នាត្រង់ memory?
2. តើ yield ធ្វើអ្វី?
3. Iterator ដែល exhausted អាចចាប់ផ្តើមវិញដោយខ្លួនឯងទេ?

**ចម្លើយ**៖ list រក្សាតម្លៃទាំងអស់, generator ផលិតតាមតម្រូវការ; yield ផ្អាក/បញ្ជូនតម្លៃ; ជាទូទៅត្រូវបង្កើត iterator ថ្មីពី iterable។
