# មេរៀន ១៥៖ Django Security និង Threat Modeling

## Security baseline
Django ផ្តល់ protections ជាច្រើន ប៉ុន្តែ configuration និង code របស់ app នៅតែអាចបង្ក vulnerabilities។ រៀបចំ threat model: ទិន្នន័យអ្វីសំខាន់, អ្នកវាយប្រហារអាចធ្វើអ្វី, endpoints ណាទទួល input និងផលប៉ះពាល់បើត្រូវលួច/កែ។

## ការពារសំខាន់
- **CSRF**៖ ទុក CSRF middleware; ប្រើ csrf_token ក្នុង POST forms; កុំបិទដើម្បីដោះ error។
- **XSS**៖ template autoescape; កុំប្រើ safe លើ user content; sanitize rich text តាម policy។
- **SQL injection**៖ ប្រើ ORM/parameterized queries; កុំ interpolate input ទៅ raw SQL។
- **Clickjacking**៖ រក្សា XFrameOptions/CSP policies សមស្រប។
- **Host header**៖ កំណត់ ALLOWED_HOSTS។
- **HTTPS/Cookies**៖ production បង្ខំ HTTPS; Secure/HttpOnly/SameSite និង HSTS តាម hosting setup។
- **Authentication/authorization**៖ check permissions/object ownership លើ server រាល់ request។
- **Secrets**៖ key/password/token នៅ environment/secret manager; rotate បើលេចធ្លាយ។

## File/upload/input
កំណត់ upload size/type, validate server side និងកុំ serve executable uploads ពី domain ដូច app។ កំណត់ rate limits និង timeouts តាម abuse risk។ Validate input តាម type/length/format ហើយ encode output តាម context។

## Production checklist command
~~~bash
python manage.py check --deploy
~~~
នេះជួយបង្ហាញ configuration issues ប៉ុន្តែមិនមែន security audit ពេញលេញទេ។ ពិនិត្យ official deployment checklist, dependency advisories, logs, backups និង incident process។

## អនុវត្ត
បង្ក security checklist សម្រាប់ project; test CSRF, authz/object ownership, XSS output escaping, bad Host, upload size និង DEBUG=False ក្នុង production config។

## សំណួរ
1. CSRF token ការពារអ្វី?
2. Login មានន័យថាគ្រប់គ្នាអាចចូល object បានដែរឬទេ?
3. check --deploy ជំនួស audit ដែរឬទេ?

**ចម្លើយ**៖ forged cross-site state-changing requests; មិនបានទេ, ត្រូវ check object permission; មិនជំនួសទេ, វាជាការត្រួតពិនិត្យមួយផ្នែក។
