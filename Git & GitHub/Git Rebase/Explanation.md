
# Git Rebase

##### الفكرة هي اني باخد الـ _commits_ اللي اتعملت على _branch_ معين وبحطها فوق آخر commit موجود في _branch_ تاني، وكأن الـ _branch_ بتاعي اتعمل من آخر نسخة من الـ branch التاني.

مثال دلوقتي احمد اخد تاسك جديدة وهيا انه يعمل **build login and Register**

ف اخد **branch from main** وسماه **Auth** وكمل شغله وعمل الاتي:

```bash
git commit -m "implement register"
git commit -m "implement login"
```

دلوقتي احمد شغال على الـ **Feature** بتاعته، لكن في نفس الوقت حصلت **commits جديدة على main**.

بحيث:

- `C` هو آخر commit موجود على `main`
- `D` و `E` هما الـ commits اللي احمد عملهم على `Auth`

دلوقتي احمد عاوز يخلي الـ **Auth branch** مبني على آخر نسخة من الـ **main**.

قبل ما يعمل الـ **rebase** لازم يتأكد انه واقف في الـ **Auth branch**:

```bash
git switch Auth
```

وبعدها ينفذ:

```bash
git rebase main
```

في الحالة دي **Git** بياخد الـ commits الموجودة في `Auth` وبيحطها فوق آخر commit موجود في `main`.

وبكده كأن احمد كان بدأ شغله من آخر نسخة من الـ **main** من البداية.

بعد كده لو احمد عاوز يدمج الـ  `Auth` في الـ **main**:

```bash
git switch main
git merge Auth
```

غالبًا هنا Git هيعمل **Fast-Forward Merge**، لأن الـ `Auth` بقى امتداد مباشر للـ `main`:


وبكده بنستخدم **Rebase** عشان نعيد ترتيب الـ **history** ونخلي الـ commits بتاعت الـ feature مبنية على أحدث نسخة من الـ `main`.