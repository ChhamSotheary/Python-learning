# មេរៀន ១៩៖ Context Managers និង Resource Handling

## គោលដៅ
គ្រប់គ្រង resource ដែលត្រូវបិទ/សម្អាតជានិច្ច ដោយ with statement និង contextlib។

## with statement
~~~python
with open("data.txt", encoding="utf-8") as file:
    content = file.read()
~~~
ពេលចេញពី block, file ត្រូវបិទ ទោះកើត exception ក៏ដោយ។ នេះហេតុផលដែល with ល្អជាង open/read/close ដោយដៃ។

Context manager គាំទ្រ protocol __enter__/__exit__; enter ផ្តល់ object ក្នុង as; exit cleanup និងអាចសម្រេចថា exception ត្រូវបានលាក់ឬបន្ត។ ជាទូទៅកុំលាក់ exceptions ដោយចៃដន្យ។

## contextlib.contextmanager
~~~python
from contextlib import contextmanager

@contextmanager
def temporary_message(message):
    print("START:", message)
    try:
        yield
    finally:
        print("END:", message)

with temporary_message("កិច្ចការ"):
    print("កំពុងធ្វើ")
~~~
កូដមុន yield រៀបចំ resource; finally សម្អាតជានិច្ច។ ប្រើ context manager សម្រាប់ lock, temp directory និង resource lifecycle; កុំប្រើសម្រាប់ logic ដែលមិនត្រូវ cleanup។

## អនុវត្ត
ប្រើ tempfile.TemporaryDirectory ក្នុង with ដើម្បីបង្កើត file បណ្ដោះអាសន្ន; ផ្ទៀងផ្ទាត់ថាថតត្រូវបានសម្អាតក្រោយ block។

## សំណួរ
1. with ការពារបញ្ហាអ្វី?
2. cleanup ដាក់នៅកន្លែងណាក្នុង generator context manager?
3. តើ __exit__ ត្រូវលាក់ exception ជានិច្ចទេ?

**ចម្លើយ**៖ resource មិនបាន close ពេល error; finally; ទេ, ជាទូទៅ exception គួរបន្តឡើងទៅ caller។
