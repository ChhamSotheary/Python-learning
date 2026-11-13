# មេរៀន ១២៖ JSON APIs និង Django REST Framework

## JSON response ជាមួយ Django
~~~python
from django.http import JsonResponse

def course_api(request):
    data = {"results": [{"id": 1, "title": "Python"}]}
    return JsonResponse(data)
~~~
JsonResponse បម្លែង dict ទៅ JSON response។ សម្រាប់ request POST JSON ត្រូវអាន body, decode JSON, ចាប់ JSONDecodeError, validate schema/fields និងពិនិត្យ auth/permission។ JSON syntax ត្រឹមត្រូវមិនមានន័យថាទិន្នន័យ valid ឬ authorized ទេ។

## API design
ប្រើ HTTP methods មានន័យ៖ GET អាន, POST បង្កើត, PUT/PATCH កែ, DELETE លុប; status codes ត្រឹមត្រូវ (200/201/204/400/401/403/404/405) តាម semantics។ កុំបង្ហាញ internal exception/stack trace; កំណត់ pagination, filtering និង versioning តាម product needs។

## Django REST Framework (DRF)
DRF ជា third-party toolkit សម្រាប់ serializers, API views/viewsets, routers, authentication, permissions និង browsable API។ ដំឡើងតាម dependency ដែលត្រូវនឹង Django/Python versions; អាន official DRF docs និង lock versions។ វាមិនមែនជា Django core; project អាចជ្រើស Django JsonResponse សម្រាប់ API តូចៗ។

## Serializer និង permissions
Serializer បំលែង model/data ទៅ primitive JSON និង validate incoming data។ កំណត់ fields allowlist ដូច forms; កុំ serialize internal/private fields ដោយស្វ័យប្រវត្តិ។ Authentication បញ្ជាក់ caller; permissions កំណត់ actions; throttling/rate limiting ការពារការប្រើខុសប្រក្រតី តាម use case។

## អនុវត្ត
បង្ក course list API ដែលមាន pagination និង status codes; validate JSON POST; បើប្រើ DRF បង្ក serializer, API view និង permission test។

## សំណួរ
1. JSON valid មានន័យថា input trustworthy ដែរឬទេ?
2. Serializer មានតួនាទីអ្វី?
3. DRF ជា Django core package ដែរឬទេ?

**ចម្លើយ**៖ មិនមានន័យនោះទេ; serialize output និង validate/deserialize input; មិនមែនទេ, វាជា third-party package។
