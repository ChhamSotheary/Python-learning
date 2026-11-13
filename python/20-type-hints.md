# មេរៀន ២០៖ Type Hints និង Static Checking

## Type hints ជាអ្វី?
Type hint ពិពណ៌នាប្រភេទដែល code រំពឹង; Python runtime ជាទូទៅមិនបង្ខំ type ដោយស្វ័យប្រវត្តិទេ។ វាជួយអ្នកអាន, IDE និង static checker រកកំហុសមុន run។

~~~python
def total(prices: list[float]) -> float:
    return sum(prices)
~~~
Parameter prices ជា list នៃ float; return ជា float។ Python 3.10+ ប្រើ union operator:
~~~python
def find_name(user_id: int) -> str | None:
    ...
~~~

## Generic types និង aliases
ប្រើ list[str], dict[str,int], tuple[int,int], set[str] ដើម្បីបង្ហាញ contents។ Type alias ធ្វើឱ្យ signature អានងាយ; typing.TypeAlias ឬ syntax ថ្មីអាស្រ័យ Python version។ កុំបន្ថែម typing ស្មុគស្មាញជាង code ត្រូវការ។

## Protocols និង TypedDict
TypedDict ពិពណ៌នា dict ដែលមាន keys កំណត់; Protocol ពិពណ៌នាកិច្ចសន្យា methods ដោយ structural typing។ សម្រាប់ model data ស្មុគស្មាញ ប្រហែល dataclass ឬ class ច្បាស់ល្អជាង dictionary។

## Static checker
ប្រើ checker ដូច mypy ឬ pyright ក្នុង project; កំណត់ config/version និងរត់ក្នុង CI។ Type hints មិន validate input ពី user/network នៅ runtime ទេ; នៅតែត្រូវ parse/validate data។ Type hints ក៏មិនមែន security mechanism ដែរ។

## អនុវត្ត
បន្ថែម types ទៅ task manager function: task list, add_task និង complete_task; បន្ថែម checker និងកែ findings។

## សំណួរ
1. Type hint បង្ខំ type នៅ runtime ដែរឬទេ?
2. ហេតុអ្វី input ពី network ត្រូវ validate ទោះមាន types?
3. Protocol ខុសពី inheritance ដូចម្តេច?

**ចម្លើយ**៖ មិនមែនដោយធម្មតា; external data អាចមិនគោរព annotation; Protocol ពិនិត្យ shape/behavior ដោយមិនតម្រូវឱ្យ subclass។
