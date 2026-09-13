# Git Help

##### الفكرة هي اني بستخدم *Git Help* عشان أعرف طريقة استخدام أي *Git Command*، أو أشوف الـ *options* والـ *arguments* اللي ممكن أستخدمها مع الـ command.

مثال دلوقتي احمد عاوز يستخدم أمر **git cherry-pick**، لكنه مش فاكر الـ **syntax** بتاع الأمر أو الـ **options** اللي بيدعمها.

ف يقدر يستخدم:

``` bash
git help cherry-pick
```

بكده **Git** هيفتح الـ **documentation** الخاصة بـ `cherry-pick`، واللي بتوضح طريقة استخدام الأمر والـ **options** المتاحة ليه.

ولو احمد عاوز مساعدة سريعة من غير ما يفتح الـ **documentation** الكاملة، يقدر يستخدم:

```bash
git cherry-pick -h
```

بكده **Git** هيعرض الـ **options** الأساسية الخاصة بالأمر مباشرة في الـ **terminal**.

وكمان يقدر يستخدم:

```bash
git --help
```

عشان يفتح الـ **documentation** العامة الخاصة بـ Git.

وبكده بنستخدم **Git Help** لما نكون محتاجين نعرف **إزاي نستخدم Git Command معين، وإيه الـ options اللي بيدعمها** بدل ما نحفظ كل الأوامر والـ options.