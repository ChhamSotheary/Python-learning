# មេរៀន ១៣៖ Settings, Environment និង Middleware

## Settings បែងចែកតាម environment
settings.py កំណត់ INSTALLED_APPS, MIDDLEWARE, DATABASES, templates, static, security និង logging។ កុំទុក secret key/password ក្នុង Git។ ប្រើ environment variables ឬ secret manager; validate ថាតម្លៃចាំបាច់មានក្នុង production។

~~~python
import os

SECRET_KEY = os.environ["DJANGO_SECRET_KEY"]
DEBUG = os.environ.get("DJANGO_DEBUG", "false").lower() == "true"
~~~
នេះគ្រាន់ជាគំរូ parse; production settings ត្រូវមាន defaults/validation ដែលសុវត្ថិភាព និងដាច់ពី dev settings។ DEBUG ត្រូវ false លើ production។

## Middleware
Middleware ជា layer ដែលដំណើរការលើ request មុន view និង response ក្រោយ view។ Order សំខាន់ ព្រោះ middleware អាចបង្កើត/កែ request, response ឬ short-circuit។ Django default middleware រួម Security, Session, Common, CSRF, Authentication, Messages និង Clickjacking; កុំដកចេញដោយមិនយល់ផលប៉ះពាល់។

## Configuration hygiene
- ALLOWED_HOSTS កំណត់ hostnames ដែល app ទទួល។
- DATABASE_URL ឬ DATABASES config មិនគួររួម password ក្នុង source។
- HTTPS proxy/security headers ត្រូវយល់ hosting topology មុនកំណត់។
- Log configuration មិនគួរសរសេរ secret។
- បែងចែក dev/test/prod settings ដោយគ្មានការចម្លង config ដែល drift។

## អនុវត្ត
បង្ក settings module/environment variables សម្រាប់ DEBUG និង SECRET_KEY; បញ្ជាក់ ALLOWED_HOSTS; បន្ថែម custom middleware ដែល log request method/path ដោយមិន log query secrets ឬ body credentials។

## សំណួរ
1. Middleware ស្ថិតនៅចន្លោះណា?
2. ហេតុអ្វី order សំខាន់?
3. SECRET_KEY ត្រូវ commit ទេ?

**ចម្លើយ**៖ មុន view និងក្រោយ view លើ request/response path; middleware អាចពឹងលើ state ដែល middleware មុនបង្កើត; មិនត្រូវ commit secret។
