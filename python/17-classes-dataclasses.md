# មេរៀន ១៧៖ Dataclasses, Inheritance និង Composition

## Dataclasses
Dataclass បង្កើត methods boilerplate ដូច __init__, __repr__, equality តាម fields:
~~~python
from dataclasses import dataclass

@dataclass
class Product:
    name: str
    price: int
    in_stock: bool = True
~~~
សមសម្រាប់ data containers; បន្ថែម validation ឬ behavior តាមតម្រូវការ។ បើ field ជា mutable ប្រើ field(default_factory=list) មិនសរសេរ default=[]។

## Inheritance
~~~python
class Person:
    def __init__(self, name):
        self.name = name

class Teacher(Person):
    def teach(self):
        return f"{self.name} កំពុងបង្រៀន"
~~~
Inheritance បង្ហាញ is-a relationship និង reuse behavior។ ប្រើ super() សម្រាប់ហៅ behavior parent; multiple inheritance មាន MRO complexity។ កុំបង្ក class hierarchy ជ្រៅពេក។

## Composition
Composition មាន object មួយប្រើ object ផ្សេងជាផ្នែក (has-a)។ ជាញឹកញាប់ងាយកែជាង inheritance:
~~~python
class Cart:
    def __init__(self, items):
        self.items = list(items)

    def total(self):
        return sum(item.price for item in self.items)
~~~
ជ្រើស composition ប្រសិនបើអាចប្ដូរផ្នែក/behavior បានដោយមិនបង្ខំ type hierarchy។

## Protocols និង duck typing
Python អនុញ្ញាត object ផ្សេងៗប្រើបានដូចគ្នា បើពួកវាមាន methods ដែលត្រូវការ។ Type Protocol (typing.Protocol) អាចពណ៌នាកិច្ចសន្យានេះដោយមិនបង្ខំ inheritance។ ជ្រើស interface តូច និងឯកសារច្បាស់។

## អនុវត្ត
កំណត់ dataclass Product; បង្ក Cart ដែលទទួល products; បន្ថែម method total។ សាក data validation និងសរសេរ test សាមញ្ញ។

## សំណួរ
1. Dataclass ជួយអ្វី?
2. Inheritance សមពេលណា?
3. Composition មានន័យអ្វី?

**ចម្លើយ**៖ កាត់ boilerplate data class; is-a relationship ពិត; object មួយមាន/ប្រើ object ផ្សេងជាផ្នែក។
