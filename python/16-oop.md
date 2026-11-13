# មេរៀន ១៦៖ Object-Oriented Programming

## Class និង instance
Class ជា blueprint/type; object/instance ជាតម្លៃដែលបង្កើតពី class។ Attributes រក្សា state; methods កំណត់ behavior។
~~~python
class Student:
    def __init__(self, name, score=0):
        self.name = name
        self.score = score

    def passed(self):
        return self.score >= 50

student = Student("សុភា", 82)
print(student.name, student.passed())
~~~
__init__ រៀបចំ instance បន្ទាប់ពីបង្កើត; self សំដៅ instance បច្ចុប្បន្ន។ Method ហៅដោយ instance ហើយ Python បញ្ជូន self ដោយស្វ័យប្រវត្តិ។

## Encapsulation និង invariants
Python ប្រើ convention underscore ដូច _score ដើម្បីបង្ហាញ implementation detail; វាមិនមែន privacy hard barrier ទេ។ Class គួររក្សា invariant ដូច score នៅ 0–100។ អាចប្រើ property ដើម្បី validate តែបើចាំបាច់; កុំបង្កើត getters/setters សម្រាប់រាល់ attribute ដោយមិនមាន logic។

## Class vs instance attributes
Class attribute ចែករួមរវាង instances; instance attribute ជាក់លាក់មួយ object។ កុំដាក់ mutable list/dict ជា class attribute ប្រសិនបើមិនចង់ឱ្យ instances ចែក state ដូចគ្នា។

## អនុវត្ត
បង្កើត Book class មាន title/author និង method summary(); បង្កើត object 2 ហើយពិនិត្យថា state មិនច្របូកគ្នា។

## សំណួរ
1. Class និង instance ខុសគ្នាដូចម្តេច?
2. self ជា keyword ពិសេសដែរឬទេ?
3. ហេតុអ្វី mutable class attribute មានគ្រោះថ្នាក់?

**ចម្លើយ**៖ class ជាប្រភេទ/គំរូ, instance ជា object ជាក់លាក់; self ជា convention parameter name មិនមែន keyword; list/dict អាចត្រូវបាន shared ដោយ instances ទាំងអស់។
