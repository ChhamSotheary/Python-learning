# មេរៀន ៨៖ Lists និង Tuples

## Lists
List ជា sequence មានលំដាប់ និង mutable។ Index ចាប់ពី 0:
~~~python
scores = [80, 95, 72]
scores.append(88)
scores[0] = 82
print(scores[1])
print(scores[1:])
~~~
append បន្ថែមចុង; extend បន្ថែម iterable; insert ដាក់តាម index; remove លុបតម្លៃដំបូងដែល match; pop យក/លុប item តាមទីតាំង។ ពិនិត្យ list មុន indexing ដើម្បីកុំឱ្យ IndexError។

## Sorting និង copy
~~~python
scores.sort()
sorted_scores = sorted(scores, reverse=True)
copy_scores = scores.copy()
~~~
sort() កែ list ដើមហើយត្រឡប់ None; sorted() បង្កើត list ថ្មី។ ការ copy list nested គឺ shallow copy; nested mutable objects នៅតែអាច shared។

## Tuples
Tuple ជា sequence immutable:
~~~python
point = (10, 20)
x, y = point
single = (5,)  # comma ចាំបាច់
~~~
ប្រើ tuple សម្រាប់ fixed record តូច ឬ value ដែលមិនគួរផ្លាស់។ Tuple មិនធានា object ខាងក្នុង immutable ទាំងអស់ទេ; tuple អាចមាន list ដែលកែបាន។

## List vs tuple
ជ្រើស list បើ collection ត្រូវបន្ថែម/កែ; tuple បើ structure មានចំនួន fields ថេរ។ កុំប្រើ tuple ជា list តែដោយសារគេចូលចិត្តវា—ជ្រើសតាមអត្ថន័យ។

## អនុវត្ត
រក min/max/average នៃ scores; បង្កើត tuple coordinate ហើយ unpack; ប្រៀបធៀប sort() ជាមួយ sorted()។

## សំណួរ
1. តើ list mutable ដែរឬទេ?
2. ហេតុអ្វី tuple មួយតម្លៃត្រូវមាន comma?
3. sort() ត្រឡប់ list ថ្មីទេ?

**ចម្លើយ**៖ បាទ; (5,) បំបែកវាពី expression ក្នុង parentheses; ទេ វាកែ list ដើម និងត្រឡប់ None។
