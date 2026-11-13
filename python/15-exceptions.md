# មេរៀន ១៥៖ Exceptions និង Error Handling

## Syntax error និង runtime exception
SyntaxError បង្ហាញថា code មិនអាច parse; exception កើតពេល runtime ដូច ValueError, TypeError, KeyError, FileNotFoundError។ អាន traceback ពីចុងឡើងលើ: បន្ទាត់ចុងក្រោយមានប្រភេទ error និង message; frames បង្ហាញ call path។

## try / except / else / finally
~~~python
try:
    quantity = int(raw)
except ValueError:
    print("សូមបញ្ចូលលេខគត់។")
else:
    print(f"ចំនួន: {quantity}")
finally:
    print("បញ្ចប់ការបញ្ចូល")
~~~
ដាក់តែកូដដែលអាចបង្ក error ក្នុង try; ចាប់ exception ជាក់លាក់ មិនប្រើ except: ធំទូលាយ។ else រត់បើគ្មាន error; finally រត់សម្រាប់ cleanup មិនថាជោគជ័យឬអត់។

## Raise exception ផ្ទាល់ខ្លួន
~~~python
def set_age(age):
    if age < 0:
        raise ValueError("អាយុមិនអាចអវិជ្ជមាន")
    return age
~~~
ប្រើ exception type ដែលសម; message ជួយអ្នកកែ input។ កុំប្រើ exception ជា flow control ធម្មតា បើ condition អាចពិនិត្យធម្មតាបាន។

## Exception chaining
~~~python
try:
    value = int(raw)
except ValueError as exc:
    raise ValueError("អាយុត្រូវជាលេខ") from exc
~~~
from exc រក្សាមូលហេតុដើមសម្រាប់ debugging។ កុំលាក់ error ដោយ pass លុះត្រាតែការមិនធ្វើអ្វីជាចេតនា និងមានការកត់ត្រា។

## អនុវត្ត
អានលេខពី user, បម្លែង, reject តម្លៃអវិជ្ជមាន, និងសរសេរ helper ដែលបោះ ValueError។ សាក input ត្រឹមត្រូវ, ទទេ និងអក្សរ។

## សំណួរ
1. ហេតុអ្វីចាប់ exception ជាក់លាក់?
2. else នៅ try block រត់ពេលណា?
3. finally សមសម្រាប់អ្វី?

**ចម្លើយ**៖ កុំលាក់ bug/interrupts ដែលមិនរំពឹង; ពេល try ជោគជ័យ; cleanup resource ឬ action ដែលត្រូវធ្វើជានិច្ច។
