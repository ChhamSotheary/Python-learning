# មេរៀន ៩៖ Authentication, Authorization និង Permissions

## Authentication និង authorization
Authentication ឆ្លើយថា «អ្នកណា?»; authorization ឆ្លើយថា «អាចធ្វើអ្វី?»។ Login មិនមានន័យថាអ្នកប្រើមានសិទ្ធិគ្រប់គ្រង object ទាំងអស់ទេ។

## Built-in users និង password handling
Django auth ផ្តល់ User, password hashing, login/logout, groups និង permissions។ កុំរក្សា password ជា plain text; កុំបង្កើត password hash ផ្ទាល់។ ពិនិត្យ custom user model decision មុន migration ដំបូង ប្រសិនបើ app ត្រូវការវា។

## Protect views
~~~python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    ...
~~~
Permission checks អាចប្រើ permission_required decorator ឬ mixins។ ត្រូវកំណត់ object-level ownership ផងដែរ:
~~~python
course = get_object_or_404(Course, pk=pk, owner=request.user)
~~~
ការកំណត់ queryset តាម user ជួយកុំឱ្យ user ប្តូរ id ក្នុង URL ហើយចូល object អ្នកដទៃ (IDOR)។

## Login/logout flow
ប្រើ Django built-in auth views ឬ implementation ដែលផ្អែកលើ docs។ Redirect target ត្រូវ validate; កុំអនុញ្ញាត open redirect ទៅ domain មិនទុកចិត្ត។ Cookie/session settings, HTTPS និង CSRF ត្រូវគិតនៅ production។

## Groups និង permissions
ផ្តល់ permissions តាម least privilege; groups ជួយដាក់ users ក្នុង role។ កុំ hardcode user IDs ឬទុកតែ UI hide button ជា authorization—view/API ត្រូវ check រាល់ request។

## អនុវត្ត
បង្កើត login-required dashboard, កំណត់ ownership លើ course CRUD, ប្រើ group permission និង test anonymous/user/admin cases។

## សំណួរ
1. Authentication ខុស authorization ដូចម្តេច?
2. ហេតុអ្វី hide button មិនគ្រប់គ្រាន់?
3. តើ IDOR កើតឡើងយ៉ាងដូចម្តេច?

**ចម្លើយ**៖ identity vs permission; request អាចផ្ញើដោយផ្ទាល់; user ប្តូរ object id ហើយ view មិនពិនិត្យ ownership។
