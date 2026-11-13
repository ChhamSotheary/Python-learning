# មេរៀន ២១៖ Testing, Debugging និង Logging

## Unit tests
~~~python
def add_tax(amount, rate):
    return amount * (1 + rate)

def test_add_tax():
    assert add_tax(100, 0.1) == 110
~~~
Test បញ្ជាក់ behavior ដែលរំពឹង; unit test តូច និងឯករាជ្យ។ Built-in unittest មិនត្រូវការ dependency; pytest ជា third-party ដែលមាន fixtures/parametrization ងាយស្រួល។ ជ្រើសមួយ និងកត់ version ក្នុង project។

## Test boundaries
សាក normal case, edge case, invalid input និង exception។ Test business logic ជា pure function ងាយជាង test function ដែលអាន network/database/file ជាមួយគ្នា។ Integration tests ពិនិត្យ component ច្រើនធ្វើការជាមួយគ្នា។

## Debugging
Traceback ជួយរក call path; print សមសម្រាប់សាកល្បងលឿន តែ debugger/IDE អនុញ្ញាត breakpoints, inspect variables និង step execution។ បង្កើត minimal reproduction មុនដោះស្រាយ bug។

## Logging
~~~python
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)
logger.info("បានដំណើរការ task %s", task_id)
~~~
Logging មាន levels DEBUG, INFO, WARNING, ERROR, CRITICAL។ កុំ log password, token, personal data ឬ secret; កំណត់ handler/format/level សម្រាប់ app ត្រឹមត្រូវ។ Library គួរប្រើ logger ហើយកុំ configure global logging របស់ app។

## អនុវត្ត
សរសេរ tests សម្រាប់ calculator/task functions; test invalid inputs; បន្ថែម logging តែ task ID មិនមែន secret។

## សំណួរ
1. Unit test ពិនិត្យអ្វី?
2. តើគួរ log password ដើម្បី debug ទេ?
3. Logger ក្នុង library គួរ configure root logger ទេ?

**ចម្លើយ**៖ behavior តូចមួយដោយឯករាជ្យ; មិនគួរ; ជាទូទៅទុក app configure logging និង library ប្រើ logger ឈ្មោះ module។
