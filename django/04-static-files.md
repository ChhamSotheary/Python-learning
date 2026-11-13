# មេរៀន ៤៖ Static Files និង Assets

## Static vs media
**Static files** ជា assets របស់ app ដូច CSS, JavaScript, logo ដែលអ្នកអភិវឌ្ឍន៍ផ្គត់ផ្គង់។ **Media files** ជា uploads របស់អ្នកប្រើ ដូច profile image; ត្រូវចាត់ការសុវត្ថិភាព/storage ផ្សេង។

## Static app directory
~~~text
courses/
└── static/
    └── courses/
        └── site.css
~~~
Template:
~~~html
{% load static %}
<link rel="stylesheet" href="{% static 'courses/site.css' %}">
~~~
Namespace folder ត្រូវបានណែនាំ ដើម្បីកុំឱ្យ file name ដូចគ្នាប៉ះគ្នារវាង apps។

## Settings និង collectstatic
STATIC_URL កំណត់ URL prefix។ នៅ production, collectstatic ប្រមូល static assets ទៅ STATIC_ROOT; web server/CDN/static storage បម្រើ file ទាំងនេះ។ ក្នុង development, Django staticfiles app បម្រើ static តាមការកំណត់ DEBUG។ កុំបើក DEBUG នៅ production។

~~~bash
python manage.py collectstatic
~~~
កុំ commit output build ឬធ្វើ serving static production តាម development server។ ដំណើរការ deployment ជាក់ស្តែងអាស្រ័យ hosting/storage។

## Cache/versioning
Browser/CDN cache អាចរក្សា file ចាស់។ ប្រើ manifest/static storage hashing ក្នុង production pipeline ដើម្បីឱ្យ asset names ផ្លាស់ពេល content ផ្លាស់។ កុំ hardcode upload/static paths ដែលមិនស្រប settings។

## អនុវត្ត
ដាក់ CSS ក្នុង app static directory, ភ្ជាប់ក្នុង template តាម static tag; កំណត់ STATIC_URL; សាក development; រត់ collectstatic ក្នុង environment សាកល្បង។

## សំណួរ
1. Static និង media ខុសគ្នាដូចម្តេច?
2. collectstatic ធ្វើអ្វី?
3. តើ DEBUG គួរបើកលើ production ទេ?

**ចម្លើយ**៖ static ជា assets របស់ app, media ជា user uploads; ប្រមូល files ទៅ STATIC_ROOT សម្រាប់បម្រើក្នុង production; មិនគួរទេ។
