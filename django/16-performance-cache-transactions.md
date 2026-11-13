# មេរៀន ១៦៖ Database Performance, Caching និង Transactions

## Query performance
ស្វែងរក N+1 queries, query ធ្ងន់ និង columns មិនចាំបាច់។ select_related/prefetch_related, only/defer និង annotate អាចជួយ ប៉ុន្តែអាចបង្ក complexity/queries ផ្សេង។ វាស់ដោយ query logging/debug toolbar និង database EXPLAIN តាមសុវត្ថិភាព។

## Indexes និង database design
Index ជួយ lookup/order តាម fields ត្រឹមត្រូវ ប៉ុន្តែប្រើ disk និងធ្វើ writes យឺត។ បង្ក index ដោយផ្អែកលើ query pattern; កុំ index គ្រប់ field។ Unique/Check constraints រក្សា data invariants នៅ database។

## Transactions
~~~python
from django.db import transaction

with transaction.atomic():
    order = Order.objects.create(user=request.user)
    PaymentRecord.objects.create(order=order, status="pending")
~~~
atomic() ធ្វើការកែប្រែជា unit: បើមាន exception DB អាច rollback transaction។ កុំទុក transaction បើកពេល network call យូរ; ប្រើ on_commit សម្រាប់ action ក្រោយ commit ដូច enqueue job។

## Cache
Cache ជួយលទ្ធផលដែលអាច reuse; Django មាន per-site, per-view, template fragment និង low-level cache APIs។ ជ្រើស backend, TTL, invalidation strategy និង key isolation។ កុំ cache user-specific/private data ដោយ key មិនដាក់ identity/permission context; កុំ cache data sensitive ដោយចៃដន្យ។

## អនុវត្ត
វាស់ query count នៅ course listing; បន្ថែម prefetch/annotate; បន្ថែម index តាម query; សាក cache list page ហើយពិនិត្យ invalidation ពេល course update។

## សំណួរ
1. Index មាន tradeoff អ្វី?
2. atomic() ធានាអ្វី?
3. Cache key មិនបញ្ចូល user context អាចបង្កអ្វី?

**ចម្លើយ**៖ read លឿន ប៉ុន្តែ write/storage cost; all-or-nothing transaction; data leak រវាង users ឬ permissions។
