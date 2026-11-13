# មេរៀន ៥៖ Models, Migrations និង Admin

## Model ជាអ្វី?
Model ជា Python class ដែលពិពណ៌នាទិន្នន័យ និង mapping ទៅ database table។ Field ជា column/type/constraints; model instance ជា row។

~~~python
from django.db import models

class Course(models.Model):
    title = models.CharField(max_length=200)
    description = models.TextField(blank=True)
    published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
~~~
ជ្រើស field type តាម data; max_length ត្រូវសម្រាប់ CharField; blank គ្រប់គ្រង validation; null គ្រប់គ្រង database NULL—វាមិនមានន័យដូចគ្នាទេ។ កំណត់ default ដោយចេតនា។

## Migrations ជាអ្វី?
Migration ជាប្រវត្តិ schema change ដែល Django បង្កើត/អនុវត្តជាលំដាប់:
~~~bash
python manage.py makemigrations
python manage.py migrate
~~~
makemigrations បង្កើត migration file តាម model changes; migrate អនុវត្តទៅ database។ ពិនិត្យ migration មុន commit, ជាពិសេស data migrations និង destructive schema changes។ កុំលុប migration ដែលបាន apply ក្នុង team project ដោយចៃដន្យ។

## Admin
~~~python
# courses/admin.py
from django.contrib import admin
from .models import Course

admin.site.register(Course)
~~~
បង្ក superuser ដោយ manage.py createsuperuser។ Admin ជា internal content management interface; កំណត់ permission និងកុំដាក់ public edit access ដោយមិនគិត security។

## Constraints និង model methods
ប្រើ unique=True/constraints/indexes ដើម្បីឱ្យ database ជួយរក្សា invariant; validation ក្នុង model/form មិនជំនួស database constraints ទេ។ __str__ ជួយ admin/debugging។ កុំដាក់ logic មិនទាក់ទង data ក្នុង model ដោយគ្មានការរចនាច្បាស់។

## អនុវត្ត
បង្កើត Course model, migration, migrate, register admin, create superuser និងបន្ថែម record ក្នុង admin local។

## សំណួរ
1. makemigrations និង migrate ខុសគ្នាដូចម្តេច?
2. blank និង null មានតួនាទីអ្វី?
3. ហេតុអ្វី database constraint នៅតែសំខាន់?

**ចម្លើយ**៖ មួយបង្កើត migration files, មួយអនុវត្តទៅ DB; blank ជា validation, null ជា DB storage; ដើម្បីរក្សាច្បាប់ទិន្នន័យទោះ code path ច្រើន ឬ concurrent writes។
