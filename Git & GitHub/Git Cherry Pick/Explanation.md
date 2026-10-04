# Git Cherry Pick

##### الفكرة هي اني باخد **commit معين او اكتر** اتعمل على _branch_ معين وبطبق التغييرات بتاعته على _branch_ تاني، من غير ما أدمج كل الـ **commits** الموجودة على الـ branch.

مثال دلوقتي احمد اخد تاسك جديدة وهيا انه يعمل **Calculator**  

ف اخد **branch from main** وسماه **Culc** وكمل شغله وعمل الاتي:

```bash
git commit -m "implement Addition" edbd110
git commit -m "implement Subtraction" tyvc523
git commit -m "implement Multiplication" rbhi684
git commit -m "implement Division" uism438
```

دلوقتي احمد خلص جزء من الـ **Feature** بتاعته، لكن هو محتاج ياخد **commits معينة** من الـ `Culc` ويحطها على الـ `main`، من غير ما يدمج باقي الـ commits الموجودة في `Culc`.


اللي محتاجه هم الـ **commits Addition and Subtraction** فقط ويحط التغييرات بتاعتهم على الـ **main**

قبل ما يعمل الـ **cherry-pick** لازم يتأكد انه واقف في الـ **main branch**:

```bash
git switch main
```

وبعدها ينفذ:

```bash
git cherry-pick edbd110
git cherry-pick tyvc523
```

بكده **Git** بياخد التغييرات الموجودة في الـ **commits edbd110 & tyvc523** ويطبقها على الـ **main**، وبيعمل **commit جديد** على الـ `main` بنفس التغييرات.

في الحالة دي الـ **history** هيكون:

```
A---B---C---D'---E'     main
        |    
        D---E---F--G      Culc
```

بحيث إن D' & 'E مش هما نفس الـ  commits D & E ، لكنهم **commits جداد** على الـ `main` يحتووا على نفس التغييرات.

وبكده احمد قدر ياخد **commits معينة** من الـ `Culc` ويطبّق التغييرات بتاعتهم على الـ `main`، من غير ما يدمج باقي الـ commits الموجودة في الـ `Culc`.

يعني ببساطة **Cherry-Pick** بنستخدمه لما نكون محتاجين **تغيير معين من commit معين**، مش كل التغييرات الموجودة على الـ branch.