# មេរៀន ១៤៖ Testing Django Applications

## Test types
Unit tests សាក logic តូចៗ; integration tests សាក model/view/template interaction; client tests ប្រើ Django test client ដើម្បីផ្ញើ request ដោយមិនបើក browser; end-to-end tests សាក user flows ពេញលេញជាមួយ browser tooling។

## TestCase និង client
~~~python
from django.test import TestCase
from django.urls import reverse

class CourseViewTests(TestCase):
    def test_home_returns_200(self):
        response = self.client.get(reverse("courses:home"))
        self.assertEqual(response.status_code, 200)
~~~
Django TestCase រៀប test database និង transaction isolation សម្រាប់ tests។ ប្រើ reverse route name ជំនួស hard-coded path; test status, template, context និង response content តាម behavior។

## Test models/forms/permissions
- Model tests ពិនិត្យ methods, constraints, related behavior។
- Form tests ពិនិត្យ valid/invalid input និង cleaned_data។
- Permission tests ពិនិត្យ anonymous, ordinary user, owner, staff roles។
- API tests ពិនិត្យ status, schema, pagination និង auth។
កុំ test implementation detail ងាយប្រែ; test user-visible behavior និង invariants។

## Fixtures/factories និង test isolation
បង្ក data ក្នុង setUp/test method ឬប្រើ factory tooling តាម project; កុំចែក mutable state រវាង tests។ Test ត្រូវ order-independent និងមិនប៉ះ database dev/production។

## Run tests
~~~bash
python manage.py test
~~~
ពិនិត្យ error trace និង coverage ជាឧបករណ៍ជំនួយ មិនមែនគោលដៅភាគរយតែមួយ។ Test មិនជំនួស security review/manual accessibility testing ទេ។

## អនុវត្ត
សរសេរ tests សម្រាប់ course list/detail, missing course 404, form invalid, owner-only edit, anonymous redirect/login និង API permissions។

## សំណួរ
1. Django TestCase ធ្វើអ្វីខ្លះ?
2. ហេតុអ្វី test permission roles ផ្សេងៗ?
3. Test coverage 100% ធានាថាគ្មាន bug ដែរឬទេ?

**ចម្លើយ**៖ ផ្ដល់ test DB/client/framework integration; ដើម្បីរក privilege escalation/denial; មិនធានាទេ—tests អាចមិនសាក behavior ឬ scenario ត្រឹមត្រូវ។
