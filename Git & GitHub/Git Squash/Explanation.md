
# Git Squash

##### الفكرة هي اني بجمع اكتر من *commits* ف *commit* واحد فقط وبدمجه ف *main branch*

مثال دلوقتي احمد اخد تاسك جديدة وهيا انه يعمل **build login and Register**
ف اخد **branch from main** وسماه **new-feature** وكمل شغله وعمل الاتي:

```bash
 git commit -m "feat: adding login"
 git commit -m "feat: adding register"
 git commit -m "feat: adding validation"
 git commit -m "fix: validate email"
 git commit -m "feat: implement JWT authentication"
 git commit -m "fix: handle refresh token"
```
  

 دلوقتي احمد عاوز يعمل **merge** لشغله علي **main branch** ولكنه فكر ف فكرة بسيطة وهيا ان زملائه والقائمين علي المشروع مش لازم مهم يعرفوا كل تفاصيل الـ **Feature** دي 

فبحث ولقي انه ممكن يعمل كدا من خلال **Git Squash** وبالفعل اتعلم انه يعملها من خلال الامر التالي: 

```bash
git merge --squash new-feature
```

ولكن قبل كتابة الامر دا لكن يتأكد انه واقف في main branch

```bash
git switch main
```

بكده **Git** اخد كل **التغييرات الناتجة عن كل الـ commits الموجودة في `new-feature` اللي احمد عملها** وطبقها على `main`، ثم وضع التغييرات في **Staging Area**، ولكن **من غير ما ينشئ Commit**.


بعدها أحمد يقدر ينفذ كل التعديلات في **commit** واحد فقط:

```bash
git commit -m "Implement Authentication"
```

وبكده الـ **main branch** هيكون فيه **commit** واحد فقط بدلًا من **الـ commits 3**

```text
main
  │
  └── Implement Authentication
```

وبالتالي تفاصيل الـ commits الأصلية مثل:

```text
feat: adding login
feat: adding register
feat: adding validation
fix: validate email
feat: implement JWT authentication
fix: handle refresh token
```

###### مش هتظهر في **تاريخ الـ `main branch`**، وده اللي أحمد كان عاوزه من الأول.

> **ملاحظة:** الـ commits الأصلية مش هتتحذف من new-feature branch بسبب الـ squash؛ هي هتفضل موجودة على الـ branch نفسه, بس بيكون اختياري اذا كان احمد عاوز يمسحها او لا.