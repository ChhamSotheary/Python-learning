# មេរៀន ១៣៖ Modules, Packages និង Imports

## Module
Module ជា Python file ដែលមាន definitions; import វា ដើម្បីប្រើ code ដែលរៀបចំរួច។ ឧទាហរណ៍ math, pathlib, json ជា standard library modules។
~~~python
import math
print(math.sqrt(25))

from pathlib import Path
print(Path.cwd())
~~~
ប្រើ import module ជាទូទៅ ដើម្បីឱ្យប្រភពឈ្មោះច្បាស់។ from module import name អាចងាយអាន ប៉ុន្តែកុំប្រើ import * ព្រោះបង្ក name collisions។

## Main guard
~~~python
def main():
    print("កម្មវិធីចាប់ផ្តើម")

if __name__ == "__main__":
    main()
~~~
ពេល file រត់ផ្ទាល់ __name__ ជា "__main__"; ពេល import វាជា module name។ Guard ធ្វើឱ្យ code startup មិនរត់ពេលគេ import module។

## Packages និង project structure
Package រៀប modules ក្នុងថត; package regular ជាទូទៅមាន __init__.py (namespace packages មាន exception)។
~~~text
myapp/
├── __init__.py
├── cli.py
└── helpers.py
~~~
ប្រើ absolute imports ឬ relative imports តាម convention មួយ; កុំដាក់ file ឈ្មោះដូច library ដូច json.py ដែលអាច shadow module។

## Import search path និង circular imports
Python ស្វែងរក module តាម sys.path; current project, environment និង standard library អាចប៉ះឈ្មោះ។ កំហុស import ម្តងម្កាលមកពីឈ្មោះ file ជាន់គ្នា។ Circular import កើតពេល modules import គ្នាទៅវិញទៅមក; កាត់ dependency ដោយដាក់ common logic ក្នុង module ផ្សេង ឬរៀប direction dependencies។

## អនុវត្ត
បង្កើត package school_tools មាន functions.py និង cli.py; ប្រើ main guard; រត់ cli និង import function ក្នុង Python prompt។

## សំណួរ
1. Module ខុសពី package ដូចម្តេច?
2. Main guard ការពារអ្វី?
3. ហេតុអ្វី import * គួរជៀសវាង?

**ចម្លើយ**៖ Module ជា file; package ជាការរៀប modules ក្នុង namespace/ថត; ការពារ startup code រត់ពេល import; import * បង្កឈ្មោះមិនច្បាស់ និង collisions។
