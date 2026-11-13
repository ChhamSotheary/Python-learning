# មេរៀន ១៖ ដំឡើង Django និងបង្កើត Project/App

## ១. Project និង app ខុសគ្នា
**Project** រួម settings, root URL config និង configuration សម្រាប់ site ទាំងមូល។ **App** ជា feature module ដែលមាន model/view/template ផ្ទាល់ ដូច blog, courses ឬ accounts។ Project អាចមាន apps ច្រើន; app អាច reuse បាន ប្រសិនបើបង្កើតដោយមានព្រំដែនច្បាស់។

## ២. បង្កើត virtual environment
~~~bash
python -m venv .venv
~~~
Activate លើ Windows:
~~~powershell
.venv\Scripts\Activate.ps1
~~~
លើ macOS/Linux:
~~~bash
source .venv/bin/activate
~~~
បន្ទាប់មកដំឡើង Django 6:
~~~bash
python -m pip install "Django>=6.0,<6.1"
python -m django --version
~~~
នេះជាការកំណត់ major/minor; project ពិតគួរ lock exact dependency តាម tool របស់ project និង commit lock file។ Django 6.0 ត្រូវការ Python 3.12–3.14 តាម compatibility table ផ្លូវការ។

## ៣. បង្កើត project និង app
~~~bash
django-admin startproject config .
python manage.py startapp courses
~~~
ចំណុចនៅ command startproject មានន័យថាដាក់ manage.py នៅ folder បច្ចុប្បន្ន; config ជា package settings។ ឈ្មោះអាចប្តូរបាន; កុំដាក់ Django app ជាន់នឹង package ឈ្មោះដូចគ្នា។

បន្ថែម app ទៅ INSTALLED_APPS ក្នុង settings.py:
~~~python
INSTALLED_APPS = [
    # Django built-in apps...
    "courses",
]
~~~
App config ជាក់លាក់អាចប្រើ "courses.apps.CoursesConfig"។

## ៤. Run development server
~~~bash
python manage.py runserver
~~~
បើក URL local ដែល terminal បង្ហាញ។ Server នេះសម្រាប់ development; កុំ expose ជា production server។

## ៥. File structure
~~~text
project/
├── manage.py
├── config/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
└── courses/
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── tests.py
    └── views.py
~~~

## អនុវត្ត
បង្កើត venv, project school_site និង app courses; ចុះបញ្ជី app ក្នុង settings; runserver ហើយសម្គាល់ file roles។

## សំណួរ
1. Project និង app មានទំនាក់ទំនងអ្វី?
2. ហេតុអ្វីប្រើ venv?
3. runserver សមសម្រាប់ production ដែរឬទេ?

**ចម្លើយ**៖ Project ជាកម្មវិធីទាំងមូល ហើយ app ជា feature module; ដើម្បី isolate dependencies; មិនសមទេ—ប្រើ production WSGI/ASGI deployment setup។