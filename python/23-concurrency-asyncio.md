# មេរៀន ២៣៖ Concurrency — Threads, Processes និង asyncio

## Concurrency vs parallelism
Concurrency គឺរៀបចំ tasks ច្រើនឱ្យរីកចម្រើនក្នុងពេលតែមួយ; parallelism គឺរត់ពិតៗពេលតែមួយលើ CPU cores ច្រើន។ ជ្រើសតាម workload មិនមែនដោយសារចង់ឱ្យ code ទំនើប។

## Threads: I/O-bound
Threads អាចល្អសម្រាប់ network/file I/O ដែលរង់ចាំច្រើន។ ចែក state រវាង threads ត្រូវ lock/queue ដើម្បីជៀស race conditions។ CPython GIL មានឥទ្ធិពលលើ CPU-bound threads; លម្អិតអាស្រ័យ Python build/version។

## Processes: CPU-bound
multiprocessing ដំណើរការ Python code ក្នុង process ផ្សេង ដើម្បីប្រើ cores; តែមាន overhead នៃ serialization, memory និង startup។ ការរត់ script សម្រាប់ multiprocessing ត្រូវប្រើ main guard ជាពិសេស Windows។

## asyncio
~~~python
import asyncio

async def fetch_name():
    await asyncio.sleep(1)
    return "Django"

async def main():
    result = await fetch_name()
    print(result)

asyncio.run(main())
~~~
async def បង្ក coroutine; await ផ្អាក coroutine ដើម្បីឱ្យ event loop ដំណើរការការងារផ្សេង។ asyncio សាកសមសម្រាប់ I/O concurrency ជាមួយ library async-compatible; វាមិនធ្វើឱ្យ CPU-heavy function រត់លឿនដោយខ្លួនឯងទេ។ កុំ block event loop ដោយ synchronous long work។

## អនុវត្ត
ប្រៀបធៀប sequential sleep និង asyncio.gather; បង្ក process pool សម្រាប់ CPU task តូចៗ ហើយវាស់ពេល។ កុំសន្និដ្ឋាន performance ដោយមិនវាស់។

## សំណួរ
1. Threads សមសម្រាប់ workload ណា?
2. Process pool មាន overhead អ្វី?
3. await អនុញ្ញាតអ្វី?

**ចម្លើយ**៖ I/O-bound; startup/serialization/memory; event loop ដំណើរការការងារផ្សេងពេល coroutine កំពុងរង់ចាំ។
