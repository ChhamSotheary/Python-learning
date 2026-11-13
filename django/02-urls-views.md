# មេរៀន ២៖ URL Routing និង Views

## Request-response flow
Browser ផ្ញើ HTTP request → Django middleware → URL resolver ផ្គូផ្គង path → view function/class ដំណើរការ → បង្កើត HttpResponse/template response → middleware → browser។ URL config បែងចែក address; view ជា logic សម្រេច response។

## View function
~~~python
# courses/views.py
from django.http import HttpResponse

def home(request):
    return HttpResponse("ស្វាគមន៍មកកាន់វគ្គសិក្សា")
~~~
request ជា HttpRequest មាន method, path, headers, user និង data។ View ត្រូវត្រឡប់ HttpResponse ឬ subclass; កុំ return string ធម្មតា។

## URL patterns និង include
~~~python
# courses/urls.py
from django.urls import path
from . import views

app_name = "courses"
urlpatterns = [
    path("", views.home, name="home"),
]
~~~
ភ្ជាប់ក្នុង root config:
~~~python
# config/urls.py
from django.urls import include, path

urlpatterns = [
    path("courses/", include("courses.urls")),
]
~~~
name ជា route name សម្រាប់ reverse URL; app_name namespace ជួយជៀសឈ្មោះជាន់គ្នា។ Template/redirect គួរប្រើ reverse/name ជំនួស hard-code URL ដែលចម្លងច្រើន។

## Path converters និង parameters
~~~python
path("<int:course_id>/", views.detail, name="detail")
~~~
Converter int បំលែង segment ទៅ int ហើយបញ្ជូន keyword argument ទៅ view។ Converter string, slug, uuid មានប្រើផ្សេងៗ។ URL path មិនមែន validation ទាំងអស់ទេ—view/model ត្រូវគ្រប់គ្រង resource ដែលមិនមាន។

## HTTP methods
ប្រើ GET សម្រាប់អាន/ស្វែងរកដែលមិនផ្លាស់ state; POST សម្រាប់បង្កើត/បញ្ជូន data ដែលប្តូរ state។ ប្រើ require_GET/require_POST ឬ class-based patterns តាមគោលបំណង។ កុំធ្វើ delete/update តាម GET។

## អនុវត្ត
បង្កើត routes home និង detail; detail ទទួល course_id; ឆ្លើយ 404 សម្រាប់ course មិនមាន; ដាក់ namespace និង reverse URL។

## សំណួរ
1. View ត្រូវ return អ្វី?
2. ហេតុអ្វី route name ប្រសើរជាង URL string ចម្លង?
3. តើ GET គួរប្រើដើម្បីលុបទិន្នន័យទេ?

**ចម្លើយ**៖ HttpResponse/subclass; reverse URL អាចតាម URL config ថ្មីដោយមិនកែ templates ទាំងអស់; មិនគួរ—GET ត្រូវគ្មាន side effect។