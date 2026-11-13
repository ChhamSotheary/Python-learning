# Django Framework: រៀនពីមូលដ្ឋានដល់កម្រិតខ្ពស់

Django ជា Python web framework ដែលផ្ដល់ routing, views, templates, ORM, forms, authentication, admin និង security protections សម្រាប់បង្កើត web applications។

## មុនចាប់ផ្តើម
រៀន Python ផ្នែកមូលដ្ឋានជាមុន៖ functions, modules, classes, exceptions, virtual environments និង tests។ ចាប់ពី [Python course](../python/README.md)។

## Version និង Python support
វគ្គនេះផ្អែកលើ **Django 6.0**។ ឯកសារ compatibility បច្ចុប្បន្នគាំទ្រ Python 3.12, 3.13 និង 3.14 សម្រាប់ Django 6.0។ ពិនិត្យ docs ពេលដំឡើង ព្រោះ compatibility អាចផ្លាស់ប្តូរ។ កុំយក code ពី tutorial Django 4.x/5.x មកច្របល់ដោយមិនពិនិត្យ version។

## ផែនទីមេរៀន

### Part 1 — Project និង request-response
1. [ដំឡើង Django និងបង្កើត project/app](01-install-project-app.md)
2. [URL routing និង views](02-urls-views.md)
3. [Templates និង template language](03-templates.md)
4. [Static files និង assets](04-static-files.md)

### Part 2 — Data, Forms និង users
5. [Models, migrations និង admin](05-models-migrations-admin.md)
6. [ORM, QuerySets និង relationships](06-orm-querysets.md)
7. [Forms និង validation](07-forms-validation.md)
8. [CRUD, generic views និង pagination](08-crud-generic-views.md)
9. [Authentication, authorization និង permissions](09-auth-permissions.md)
10. [Sessions, messages និង cookies](10-sessions-messages-cookies.md)
11. [File uploads និង media storage](11-file-uploads.md)

### Part 3 — Production-quality Django
12. [JSON APIs និង Django REST Framework](12-json-apis.md)
13. [Settings, environment និង middleware](13-settings-middleware.md)
14. [Testing Django applications](14-testing.md)
15. [Security និង threat modeling](15-security.md)
16. [Database performance, caching និង transactions](16-performance-cache-transactions.md)
17. [Async, background work និង integrations](17-async-background-tasks.md)
18. [Deployment, WSGI/ASGI និង final capstone](18-deployment-capstone.md)

## របៀបរៀន
- បញ្ចប់មួយ chapter ម្តង; run code ក្នុង project ដែលអ្នកកាន់កាប់។
- ប្រើ venv និង requirements/lock file។
- ពិនិត្យ migration, test suite និង security checklist មុន deployment។
- មិនដាក់ secret key, database password, token ឬ user data ក្នុង repository។
- Development server សម្រាប់ local testing ប៉ុណ្ណោះ; deployment ត្រូវតាម checklist ផ្លូវការ។

## ឯកសារផ្លូវការ
- [Django 6.0 docs](https://docs.djangoproject.com/en/6.0/)
- [Official tutorial](https://docs.djangoproject.com/en/6.0/intro/tutorial01/)
- [Model layer](https://docs.djangoproject.com/en/6.0/topics/db/models/)
- [Forms](https://docs.djangoproject.com/en/6.0/topics/forms/)
- [Security](https://docs.djangoproject.com/en/6.0/topics/security/)
- [Deployment checklist](https://docs.djangoproject.com/en/6.0/howto/deployment/checklist/)
