# មេរៀន ១៧៖ Async, Background Tasks និង Integrations

## Async Django
Django គាំទ្រ asynchronous views/middleware តាម ASGI និង APIs ដែលសមស្រប។ async view អាចមាន awaitable I/O calls; synchronous ORM/third-party libraries អាច block event loop ឬត្រូវ adapter ដូច sync_to_async។ ពិនិត្យ async support របស់ version/library មុនប្រើ។

~~~python
import asyncio
from django.http import HttpResponse

async def health(request):
    await asyncio.sleep(0)
    return HttpResponse("ok")
~~~
Async មិនមានន័យថា CPU-bound code លឿន ឬគ្រប់ request concurrency ត្រូវបានល្អប្រសើរទេ។ ប្រើសម្រាប់ I/O concurrency ដែល stack គាំទ្រ និងវាស់ under load។

## Background tasks
ការងារយូរ ដូច email/report/image processing មិនគួររារាំង HTTP response។ អាចដាក់ queue task ដោយ task queue system (third-party) ឬប្រើ transaction.on_commit ដើម្បី enqueue ក្រោយ database commit។ ការងារត្រូវ idempotent ព្រោះ retry អាចធ្វើឱ្យរត់ម្តងច្រើន; កំណត់ retries/timeouts និង log task IDs។

## External integrations
កំណត់ connect/read timeouts; retry តែ operation ដែល retry-safe; validate response; កុំ log credentials; ប្រើ secrets manager/environment។ កុំធ្វើ HTTP call ទៅ user-supplied URL ដោយគ្មាន SSRF defenses និង allowlist policy។

## អនុវត្ត
បង្កើត endpoint ដែល enqueue email/report task ក្រោយ transaction commit; សាក timeout/failure/retry និង ensure duplicate job មិនបង្ក duplicate side effect។

## សំណួរ
1. Async សមសម្រាប់ការងារបែបណា?
2. ហេតុអ្វី background task ត្រូវ idempotent?
3. តើ external HTTP call គួរកំណត់ timeout ដែរឬទេ?

**ចម្លើយ**៖ I/O-bound concurrent work ដែល libraries គាំទ្រ; retry អាចដំណើរការឡើងវិញ; ត្រូវកំណត់ timeout ដើម្បីកុំឱ្យ worker/request ជាប់រង់ចាំ។
