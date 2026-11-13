# មេរៀន ៤៖ Numbers និង Operators

## គោលដៅ
គណនាលេខ, ប្រៀបធៀបតម្លៃ, ប្រើ boolean operators និងយល់លំដាប់ប្រតិបត្តិការ។

## Arithmetic
~~~python
print(7 + 2)   # បូក
print(7 - 2)   # ដក
print(7 * 2)   # គុណ
print(7 / 2)   # ចែក -> float
print(7 // 2)  # floor division
print(7 % 2)   # remainder
print(2 ** 3)  # power
~~~
// ជា floor division; សម្រាប់ចំនួនអវិជ្ជមាន វាបង្គត់ទៅក្រោម មិនមែន truncate ទៅសូន្យ។ % ជា remainder តាម semantics Python។

## Comparison និង booleans
~~~python
age = 20
print(age >= 18)
print(age == 20)
print(age != 10)
print(age >= 18 and age < 65)
~~~
ប្រើ == សម្រាប់ប្រៀបធៀបតម្លៃ; = សម្រាប់ assignment។ Boolean operators and, or, not បង្កើត logic។ ជៀសវាងប្រៀបធៀប float ដោយ == បើជាលទ្ធផលគណនា precision-sensitive។

## Numeric precision
Float រក្សាតម្លៃប្រព័ន្ធ binary ដូច្នេះ 0.1 + 0.2 អាចមិនស្មើ 0.3 ពិតៗ។ សម្រាប់លុយប្រើ decimal.Decimal ឬរក្សាទុកជាចំនួនសេន int; កុំប្រើ float ជា currency ដោយមិនគិត precision។

~~~python
from decimal import Decimal
total = Decimal("0.10") + Decimal("0.20")
print(total)
~~~

## Operator precedence
សញ្ញាវង់ក្រចកធ្វើឱ្យ logic ច្បាស់៖
~~~python
discounted = price * (1 - discount_rate)
~~~
កុំចាំ precedence ស្មុគស្មាញទាំងអស់; ប្រើ parentheses និងដាក់ calculation ជា variables មានឈ្មោះ។

## អនុវត្ត
គណនា subtotal, tax និង total សម្រាប់ cart តូច។ ប្រើ Decimal សម្រាប់តម្លៃលុយ; ប្រៀបធៀបថ្លៃដឹកជញ្ជូននឹង threshold។

## លំហាត់
1. តើ 9 // 4 និង 9 % 4 បានប៉ុន្មាន?
2. តើ == និង = ខុសគ្នាដូចម្តេច?
3. ហេតុអ្វី Decimal("0.10") ត្រឹមត្រូវជាង Decimal(0.10)?

**ចម្លើយ**៖ 2 និង 1; == ប្រៀបធៀប, = ចងតម្លៃ; string រក្សាតម្លៃទសភាគដែលចង់បានដោយមិនយក floating approximation មកមុន។
