# មេរៀន ១៖ ដំឡើង Python និងសរសេរកម្មវិធីដំបូង

## គោលដៅ
ស្គាល់ Python interpreter, រត់ interactive prompt និង script file; អាន syntax error មូលដ្ឋាន។

## Interpreter និង script
Interpreter អាន/ប្រតិបត្តិ Python code។ Interactive prompt អនុញ្ញាតវាយបញ្ជាមួយៗ; script ជា file អក្សរ plain text មាន extension .py។ បង្កើត hello.py៖
~~~python
print("សួស្តី Python")
print(2 + 3)
~~~
រត់តាម terminal:
~~~bash
python hello.py
~~~
Windows អាចប្រើ:
~~~bash
py hello.py
~~~
បើ command មិនស្គាល់ ពិនិត្យថា Python បានដំឡើង និង PATH ត្រឹមត្រូវឬអត់។ កុំវាយ command terminal ក្នុង Python prompt ដែលមាន >>>។

## Comments និង indentation
~~~python
# នេះជាការពន្យល់សម្រាប់អ្នកអានកូដ
name = "សុភា"
print(name)
~~~
Comment ចាប់ពី # ដល់ចុងបន្ទាត់។ Python ប្រើ indentation បង្កើត block; នៅមេរៀននេះប្រើ 4 spaces ក្នុង block និងកុំលាយ tab/spaces។

## អ្វីកើតឡើងពេល run?
Python អាន source code, parse syntax, បង្កើត bytecode/ប្រតិបត្តិតាម interpreter។ អ្នកសរសេរភាគច្រើនមិនត្រូវគ្រប់គ្រង internals នេះទេ ប៉ុន្តែត្រូវយល់ថា syntax error បង្ហាញទីតាំងដែល parser មិនអាចបន្តបាន។

## កំហុសមូលដ្ឋាន
- បិទ string quote មិនគ្រប់: SyntaxError។
- សរសេរ print មិនត្រឹមត្រូវ: ពិនិត្យ colon/parentheses តាម context។
- ឯកសារមិនបាន save: រត់ code ចាស់។
- ឈ្មោះ file ជា python.py អាចប៉ះ module import; ជ្រើសឈ្មោះដែលមិនជាន់ standard library។

## អនុវត្ត
1. បង្កើត hello.py។
2. បោះពុម្ពឈ្មោះ និងគោលដៅរៀនរបស់អ្នក។
3. បន្ថែម comment មួយ។
4. បង្កើត syntax error ដោយចេតនា រួចអាន error message និងកែវា។

## សំណួរពិនិត្យ
1. Interpreter ខុសពី script file ដូចម្តេច?
2. Comment មានឥទ្ធិពលលើការប្រតិបត្តិដែរឬទេ?
3. ហេតុអ្វី indentation សំខាន់ក្នុង Python?

**ចម្លើយ**៖ Interpreter ជាកម្មវិធីរត់ code; script ជា file code; comment មិនត្រូវបានប្រតិបត្តិ; indentation កំណត់ block code។
