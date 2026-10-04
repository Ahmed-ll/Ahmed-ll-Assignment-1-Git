# Git Clean

##### الفكرة هي اني بستخدم *Git Clean* عشان أمسح الـ *untracked files* والـ *untracked folders* من الـ *working directory*، يعني الملفات اللي Git مش بيعمل عليها tracking ولسه مش مضافة للـ staging area.

مثال دلوقتي احمد شغال على **branch** معين، وعنده بعض الملفات اللي Git مش متابعها:

```
Project
│
├── Program.cs
├── User.cs
├── new.cs        ← untracked file
└── Temp/         ← untracked folder
```

دلوقتي احمد عاوز يشوف الأول إيه الملفات اللي **Git Clean** ممكن يمسحها، من غير ما يمسحها فعليًا.

فيستخدم:

```bash
git clean -n
```

الـ `-n` معناها **dry run**، يعني Git هيعرض الملفات اللي هيتم حذفها فقط، من غير ما يحذفها.

بعد ما احمد يتأكد إن الملفات دي فعلًا مش محتاجها، يقدر ينفذ:

```bash
git clean -f
```

بكده **Git** هيحذف الـ **untracked files** من الـ working directory.

ولو عنده **untracked folders** وعاوز يحذفها كمان:

```bash
git clean -fd
```

وبكده بنستخدم **Git Clean** لما نكون عاوزين ننضف الـ **working directory** من الملفات والـ folders اللي Git مش بيعمل عليها tracking، من غير ما نأثر على الـ **tracked files** أو الـ **commits** الموجودة في الـ repository.



![[git clean.png|678]]