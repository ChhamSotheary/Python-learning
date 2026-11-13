# មេរៀន ៣៖ Django Templates

## Render template ជាមួយ context
~~~python
from django.shortcuts import render

def home(request):
    context = {"title": "វគ្គ Python", "lessons": ["មូលដ្ឋាន", "Functions"]}
    return render(request, "courses/home.html", context)
~~~
render រក template, បញ្ចូល context និងត្រឡប់ response។ កំណត់ APP_DIRS=True តាម default project ដើម្បីរក templates ក្នុង app templates directory។

~~~text
courses/
└── templates/
    └── courses/
        └── home.html
~~~

## Template syntax
~~~html
<h1>{{ title }}</h1>
<ul>
  {% for lesson in lessons %}
    <li>{{ lesson }}</li>
  {% empty %}
    <li>មិនទាន់មានមេរៀន</li>
  {% endfor %}
</ul>
~~~
{{ }} បង្ហាញ variable; {% %} ជា control tags ដូច if/for/include/url; filter ដូច lower/date/length កែ output។ Autoescaping បើកជាទូទៅសម្រាប់ variable ដើម្បីការពារ HTML injection; កុំប្រើ safe លើ user text ដោយមិន sanitize។

## Template inheritance
~~~html
<!-- base.html -->
<!doctype html>
<html lang="km">
<head><meta charset="utf-8"><title>{% block title %}Site{% endblock %}</title></head>
<body>
  <main>{% block content %}{% endblock %}</main>
</body>
</html>
~~~
ទំព័រកូនប្រើ extends និងបំពេញ block។ វាជួយកុំស្ទួន layout; រក្សា blocks មានឈ្មោះមានន័យ។

## URL reversing និង static
ប្រើ {% url 'courses:detail' course.id %} ដើម្បីបង្កើត route តាម name។ Static assets ប្រើ {% load static %} និង {% static 'courses/site.css' %}; រៀន configuration នៅមេរៀន 4។

## អនុវត្ត
បង្កើត base.html និង home.html; បញ្ជូន title, list lessons, បង្ហាញ empty state; បន្ថែម link ទៅ detail ដោយ url tag។

## សំណួរ
1. Context មានតួនាទីអ្វី?
2. Autoescape ជួយការពារអ្វី?
3. extends/block ជួយកាត់បន្ថយអ្វី?

**ចម្លើយ**៖ ផ្ញើទិន្នន័យពី view ទៅ template; HTML injection/XSS ពី output ដែលមិនទុកចិត្ត; កាត់ការចម្លង layout ដដែលៗ។
