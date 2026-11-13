# មេរៀន ២៤៖ Performance, Security និង Python Internals

## Performance: វាស់មុន optimize
ប្រើ timeit សម្រាប់ expression តូច, cProfile សម្រាប់ profiling app, tracemalloc សម្រាប់ allocation។ ចាប់ផ្តើមពី algorithm/data structure និង bottleneck ដែលវាស់ឃើញ មិនមែន optimize code តាមការស្មាន។ Big-O ជួយប្រៀបធៀប growth ប៉ុន្តែ constants/I/O ក៏សំខាន់។

## Algorithm និង memory
Set/dict ជាទូទៅ lookup មធ្យម O(1); list membership O(n); sort ជាទូទៅ O(n log n)។ Generator អាចសន្សំ memory ប៉ុន្តែមិនចាំបាច់លឿនជាង list គ្រប់ករណី។ Cache មានប្រយោជន៍សម្រាប់ repeated work ប៉ុន្តែត្រូវគ្រប់គ្រង stale data/memory។

## Security fundamentals
- កុំ eval/exec input មិនទុកចិត្ត។
- កុំបញ្ចូល user data ទៅ SQL/command/HTML ដោយ raw string; ប្រើ parameterized APIs និង escaping តាម context។
- រក្សា secrets ក្រៅ source control។
- Validate data ព្រំដែន និងកំណត់ size/timeouts សម្រាប់ network/files។
- ប្រើ HTTPS និង dependency versions ដែលគាំទ្រ។
- កុំបង្ហាញ traceback/secrets ទៅ end users; log ព័ត៌មានសុវត្ថិភាពដោយកុំលាតត្រដាងទិន្នន័យ។

## Internals មើលពីខ្ពស់
Python language មាន semantics; CPython ជា implementation ពេញនិយមដែលបកស្រាយ code ទៅ bytecode និងដំណើរការលើ virtual machine។ Objects មាន type/identity/value; garbage collector និង reference counting ជាផ្នែក implementation។ កុំសរសេរ business logic ពឹងលើ implementation details ដែល language មិនធានា។

## Final Python project
ធ្វើ CLI task tracker ដែលរក្សាទុក JSON, មាន modules, type hints, exceptions, logging និង automated tests។ បង្ក venv និង README។ បន្ទាប់មកអាចបន្ត Django ដោយយល់ functions, modules, classes, files និង tests។

## សំណួរ
1. ហេតុអ្វីត្រូវ profile មុន optimize?
2. តើ eval(user_input) មានសុវត្ថិភាពទេ?
3. តើ CPython ដូច Python language ទាំងមូលដែរឬទេ?

**ចម្លើយ**៖ រក bottleneck ពិត និងកុំធ្វើការកែគ្មានប្រយោជន៍; មិនសុវត្ថិភាព; CPython ជា implementation មួយនៃ Python។
