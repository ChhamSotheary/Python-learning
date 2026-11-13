# មេរៀន ១០៖ Sessions, Messages និង Cookies

## Cookies និង sessions
Cookie ជាទិន្នន័យដែល browser រក្សា និងផ្ញើជាមួយ request; session ជា state ភាគច្រើនរក្សាខាង server ហើយ browser ផ្ទុក session identifier cookie។ Django session backend អាច database/cache/file/cookie តាមការកំណត់។ កុំដាក់ secret ឬទិន្នន័យ sensitive ក្នុង client-readable cookie។

## Session usage
~~~python
request.session["cart_count"] = 2
count = request.session.get("cart_count", 0)
request.session.pop("cart_count", None)
~~~
Session ត្រូវការ SessionMiddleware និង backend configuration។ កំណត់ expiry/secure cookies/SameSite តាម threat model; production ប្រើ HTTPS និង SESSION_COOKIE_SECURE=True។

## Messages framework
~~~python
from django.contrib import messages

messages.success(request, "បានរក្សាទុកដោយជោគជ័យ")
messages.error(request, "សូមពិនិត្យទិន្នន័យ")
~~~
Messages ជាសាររយៈពេលខ្លីសម្រាប់ request បន្ទាប់ ជាញឹកញាប់ក្រោយ Post/Redirect/Get។ Template ត្រូវ render messages និង style តាម level; កុំបង្ហាញ details មិនទុកចិត្តជា HTML safe។

## Security និង privacy
កុំដាក់ password/token ឬ personal data ក្នុង session ឬ message ដោយមិនចាំបាច់។ កំណត់ cookie HttpOnly, Secure, SameSite តាមតម្រូវការ; session storage និង cookie behavior អាស្រ័យ backend។ កុំច្រឡំ session ID ជា authorization ដោយខ្លួនឯង—ត្រូវពិនិត្យ user/permission។

## អនុវត្ត
រក្សា cart count ក្នុង session, បង្ហាញ messages ក្រោយបង្កើត course, test session expiry និង logout behavior។

## សំណួរ
1. Browser ផ្ទុកអ្វីសម្រាប់ server-side session?
2. Messages framework សមសម្រាប់អ្វី?
3. តើដាក់ password ក្នុង cookie/session message បានទេ?

**ចម្លើយ**៖ ជាធម្មតា session identifier cookie; feedback មួយលើក/បន្ទាប់ពី redirect; មិនគួរដាក់ secret ឬ personal data ដោយមិនចាំបាច់។
