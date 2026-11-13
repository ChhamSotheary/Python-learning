# មេរៀន ១១៖ File Uploads និង Media Storage

## Upload flow
HTML form ត្រូវមាន enctype multipart/form-data; view បញ្ជូន request.FILES ទៅ form; FileField/ImageField validate ហើយ model/storage រក្សាទុក file។ ImageField ត្រូវការ dependency សម្រាប់ image processing ដូច Pillow (ដំឡើងតាម project requirements)។

~~~html
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Upload</button>
</form>
~~~

## Storage configuration
MEDIA_URL សម្រាប់ URL; MEDIA_ROOT សម្រាប់ local development storage។ Production គួរប្រើ storage ដាច់ដោយឡែក (object storage/CDN ឬ hosting storage) ហើយកំណត់ access control តាម file type/privacy។ កុំច្រឡំ MEDIA_ROOT ជាមួយ STATIC_ROOT។

## Validation និង safety
File name/type/size មកពី user អាចក្លែងក្លាយ។ កំណត់ទំហំអតិបរមា, allowlist extension/content type, inspect actual content, randomize storage names និងដាក់ media ក្នុង serving domain/context ដែលមានហានិភ័យតិច។ កុំ execute uploaded file; កុំទុក private files ក្នុង public media path។ Virus scanning អាចត្រូវការតាម app risk។

## អនុវត្ត
បន្ថែម thumbnail upload សម្រាប់ Course; validate size/type; បង្ហាញ link ឬ preview មាន alt text; test invalid/oversize files។ ប្រើ dummy data មិនមែនឯកសារឯកជន។

## សំណួរ
1. ហេតុអ្វី form ត្រូវ multipart/form-data?
2. Extension តែមួយគ្រប់គ្រាន់សម្រាប់ validate file ដែរឬទេ?
3. STATIC និង MEDIA files ខុសគ្នាដូចម្តេច?

**ចម្លើយ**៖ ដើម្បីផ្ញើ binary files; មិនគ្រប់គ្រាន់ទេ ព្រោះ extension/type អាចក្លែង; static ជា asset របស់ app, media ជា upload របស់ user។
