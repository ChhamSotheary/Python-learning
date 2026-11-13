# មេរៀន ៨៖ CRUD, Generic Views និង Pagination

## CRUD ជាអ្វី?
Create, Read, Update, Delete ជាប្រតិបត្តិការមូលដ្ឋានលើ records។ ត្រូវបង្កើត routes និង views សម្រាប់នីមួយៗ ដោយពិនិត្យ ownership/permissions មុនអាន ឬកែ data។

## Function-based pattern
Create form ជាទូទៅ GET បង្ហាញ empty form; POST validate, save និង redirect។ Update ទាញ object តាម get_object_or_404, bind instance, validate ហើយ save។ Delete ធ្វើតាម POST/form confirmation មិនមែន GET។

## Class-based generic views
Django ផ្ដល់ ListView, DetailView, CreateView, UpdateView, DeleteView។ វាជួយកាត់ boilerplate ប៉ុន្តែត្រូវយល់ method resolution, queryset, form_class, success_url និង permission mixins។ សម្រាប់ logic សាមញ្ញ function view អាចអានងាយជាង។

## Pagination
~~~python
from django.core.paginator import Paginator

paginator = Paginator(queryset, 20)
page_obj = paginator.get_page(request.GET.get("page"))
~~~
Pagination កុំយក records ទាំងអស់ចូល memory; បង្ហាញ next/previous links និង current page។ Queryset ត្រូវមាន ordering ស្ថិរភាព ដើម្បីកុំឱ្យ row ផ្លាស់ទីរវាង pages។

## Post/Redirect/Get
ក្រោយ POST ជោគជ័យ redirect ទៅ GET page ដើម្បីការពារការបញ្ជូន form ម្តងទៀតពេល refresh។ ប្រើ named URLs/redirect និង messages ដើម្បីបញ្ជាក់ជោគជ័យ។

## អនុវត្ត
ធ្វើ course list/detail/create/update/delete; កំណត់ permissions សម្រាប់កែ; pagination 10 records/page; delete តាម POST និង confirm page។

## សំណួរ
1. CRUD តំណាងអ្វី?
2. ហេតុអ្វី delete មិនគួរប្រើ GET?
3. Pagination ត្រូវការ ordering ឬទេ?

**ចម្លើយ**៖ Create Read Update Delete; GET គួរមិនផ្លាស់ state និងងាយត្រូវ crawler/prefetch; ត្រូវមាន ordering ស្ថិរភាព។
