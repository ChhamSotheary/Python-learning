# មេរៀន ២២៖ Virtual Environments, pip និង Packaging

## Virtual environment
venv បង្ក environment ដាច់ដោយឡែកសម្រាប់ dependencies របស់ project:
~~~bash
python -m venv .venv
~~~
Windows activate:
~~~powershell
.venv\Scripts\Activate.ps1
~~~
macOS/Linux:
~~~bash
source .venv/bin/activate
~~~
បិទដោយ deactivate។ កុំ commit .venv; បន្ថែមទៅ .gitignore។ ប្រើ python -m pip ដើម្បីធានាថា pip ជាប់ interpreter ត្រឹមត្រូវ។

## Install dependencies
~~~bash
python -m pip install requests
python -m pip freeze
~~~
pip ដំឡើង package ពី package index; ជ្រើស package trusted, ពិនិត្យ version/license និង security advisories។ Freeze output អាចជួយ reproduce environment តែ package management strategy អាស្រ័យ project។

## Project packaging
គម្រោងសម័យថ្មីប្រើ pyproject.toml ដើម្បីកំណត់ metadata/build backend/tool config។ រៀប source package, tests និង README; build wheel/sdist ហើយសាក install ក្នុង environment ស្អាត មុន publish។ កុំដាក់ credentials ក្នុង pyproject ឬ repo។

## Dependency hygiene
- Pin/lock dependencies តាម release process។
- កុំ install global ដោយ sudo លើ system Python ដោយមិនយល់ផលប៉ះពាល់។
- Update dependencies ដោយមាន tests និង review release notes។
- Secret/config ទុកក្នុង environment/secret manager, មិន commit។

## អនុវត្ត
បង្កើត venv, ដំឡើង package សាកល្បង, បង្កើត CLI project មាន pyproject.toml, build package និង install ទៅ venv ថ្មី។

## សំណួរ
1. venv ការពារអ្វី?
2. ហេតុអ្វីប្រើ python -m pip?
3. តើ .venv ត្រូវ commit ទេ?

**ចម្លើយ**៖ ដាក់ dependencies ដាច់ពី project/ប្រព័ន្ធផ្សេង; ធានា pip ជាមួយ interpreter ត្រឹមត្រូវ; មិនត្រូវ commit ទេ។
