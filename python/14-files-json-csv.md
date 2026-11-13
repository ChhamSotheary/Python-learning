# មេរៀន ១៤៖ Files, pathlib, JSON និង CSV

## File I/O ជាមួយ context manager
~~~python
from pathlib import Path

path = Path("notes.txt")
path.write_text("សួស្តី\n", encoding="utf-8")
text = path.read_text(encoding="utf-8")
print(text)
~~~
pathlib ផ្តល់ object សម្រាប់ paths លើ OS ផ្សេងៗ។ read_text/write_text សមសម្រាប់ file តូច; សម្រាប់ streams ធំប្រើ open() និង iterate line by line។ Context manager with បិទ file resource ដោយសុវត្ថិភាព។

~~~python
with Path("notes.txt").open(encoding="utf-8") as file:
    for line in file:
        print(line.rstrip())
~~~

## JSON
~~~python
import json

data = {"name": "ដារ៉ា", "score": 90}
Path("data.json").write_text(
    json.dumps(data, ensure_ascii=False, indent=2),
    encoding="utf-8",
)
loaded = json.loads(Path("data.json").read_text(encoding="utf-8"))
~~~
JSON គាំទ្រ object/array/string/number/boolean/null; Python map ទៅ dict/list/str/int,float/bool,None។ JSON មិនគាំទ្រ arbitrary class objects ដោយផ្ទាល់។ បើ file invalid, JSONDecodeError។ មិន eval JSON ឬ input ទេ។

## CSV
~~~python
import csv

with open("scores.csv", newline="", encoding="utf-8") as file:
    for row in csv.DictReader(file):
        print(row["name"], row["score"])
~~~
ប្រើ csv module ជំនួស split(",") ព្រោះ CSV អាចមាន quoted commas និង escaping។ តម្លៃ CSV ជាអត្ថបទ; បំលែង type និង validate ជាដំណាក់កាល។

## Paths និង trust boundary
កុំសន្មត path ពី user មានសុវត្ថិភាព; ប្រយ័ត្ន path traversal។ សម្រាប់ file upload ឬ path ពី network ត្រូវកំណត់ថតអនុញ្ញាត, normalize/validate និងកំណត់ទំហំ។

## អនុវត្ត
រក្សា contacts list ក្នុង JSON; read ត្រឡប់វិញ; export names ទៅ CSV; ចាប់ JSONDecodeError និងបង្ហាញសារអាចយល់។

## សំណួរ
1. ហេតុអ្វីប្រើ with?
2. ហេតុអ្វី csv.DictReader ល្អជាង split(",")?
3. តើ JSON រក្សា Python object ណាក៏បានដែរឬទេ?

**ចម្លើយ**៖ បិទ resource សូម្បីពេល error; គាំទ្រ quoting/escaping និង header; មិនបានទេ, មានតែ types ដែល JSON គាំទ្រ ឬ serialization ផ្ទាល់ខ្លួន។
