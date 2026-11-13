# មេរៀន ១៨៖ Deployment និង Final Capstone

## WSGI និង ASGI
WSGI ជា interface សម្រាប់ synchronous Python web apps; ASGI គាំទ្រ async protocols/use cases។ ជ្រើស server/runtime ដែលគាំទ្រ configuration និង dependencies របស់ app។ runserver មិនមែន production server ទេ។

## Production preparation
- DEBUG=False និង SECRET_KEY/credentials ពី secret store។
- ALLOWED_HOSTS ត្រឹមត្រូវ; HTTPS, proxy headers, secure cookies តាម host។
- Database production (ជាទូទៅ PostgreSQL តាមតម្រូវការ) មាន backup/restore plan។
- Run migrations ជា release step ដោយគ្រប់គ្រង rollback/data changes។
- collectstatic ហើយបម្រើ static/media តាម storage/server សមស្រប។
- Configure logging/error monitoring, health checks, timeouts និង resource limits។
- Update dependencies, run tests និង check --deploy។
- កុំឱ្យ production server សរសេរទៅ source tree ឬ log secrets។

## Capstone: Course Learning Platform
បង្កើត web app មាន:
1. Course/Lesson models និង admin។
2. List/detail pages, search/filter/pagination។
3. User registration/login និង role permissions/ownership។
4. Forms សម្រាប់ create/update និង CSRF protection។
5. Upload optional thumbnail ដោយ validation។
6. JSON API សម្រាប់ public course data និង permission tests។
7. Unit/integration tests សម្រាប់ routes, forms, auth, queries។
8. Responsive templates/static assets។
9. Environment-based settings, production checklist និង deployment diagram។

## Release checklist
1. Run tests និង system checks។
2. ពិនិត្យ secrets, DEBUG, ALLOWED_HOSTS និង HTTPS។
3. Backup database និង rehearsal restore។
4. Apply migrations និង collectstatic តាម release process។
5. Run health checks, inspect logs/metrics និង rollback plan។
6. Recheck access controls និង public routes។

## សំណួរពិនិត្យចុងវគ្គ
1. WSGI/ASGI ខុសគ្នាដូចម្តេច?
2. ហេតុអ្វី runserver មិនសម production?
3. ហេតុអ្វី backup ត្រូវសាក restore?
4. តើ migrations production គួររត់ពេលណា?

**ចម្លើយ**៖ WSGI synchronous interface, ASGI async-capable; runserver development-only; backup ដែលមិនទាន់ restore test មិនធានាថាអាចស្ដារ; ដំណើរការជា release step ដែលបានគ្រប់គ្រង។
