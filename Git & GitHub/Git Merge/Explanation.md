
# Git Merge

##### الفكرة هي اني باخد الـ *commits* اللي اتعملت على *branch* معين وبدمج التغييرات بتاعتها في *branch* تاني، وغالبًا بيكون الـ *main branch*.

مثال دلوقتي احمد اخد تاسك جديدة وهيا انه يعمل **build login and Register**

ف اخد **branch from main** وسماه **Auth** وكمل شغله وعمل الاتي: 

```bash
git commit -m "implement register"
git commit -m "implement login"
```

دلوقتي احمد خلص الـ **Feature** وعاوز يدمج شغله على **main branch**.

قبل ما يعمل الـ **merge** لازم يتأكد انه واقف في الـ **main branch**:

```bash
git switch main
```

وبعدها ينفذ:

```bash
git merge Auth
```

بكده **Git** اخد التغييرات الموجودة في Auth ودمجها في **main**.

لو الـ **main branch** مفيهوش أي commits جديدة بعد ما احمد عمل الـ branch

في الحالة دي Git بيعمل حاجة اسمها **Fast-Forward Merge**.

يعني الـ **main branch** بقى بيشاور على آخر commit موجود في `Auth`.

وفي الحالة دي **Git مش محتاج يعمل Merge Commit جديد**، لأنه ببساطة قدر يحرك الـ `main` من الـ commit القديم لحد آخر commit في الـ `Auth`.



لكن لو حصلت **commits** جديدة على **main** بعد ما احمد عمل الـ **branch**، شكل الـ **history** هيكون مختلف.

هنا Merge هيحتاج يعمل **Merge** اسمه **Merge 3-Way**

لأن عندنا تغييرات حصلت على الـ `main` وتغييرات حصلت في `Auth`، وبالتالي **Git** بيجمع الـ **Commits** مع بعض في **commit** واحد.

وبكده الـ **main branch** هيكون فيه كل التغييرات اللي أحمد عملها في **Auth** بالاضافة الي التغييرات اللي حصلت علي **main** فعليا.