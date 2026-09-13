# Git Prune

##### الفكرة ببساطة هي إن *Git Prune* بيستخدم لتنضيف الـ *Git repository* من الـ objects اللي مبقتش ليها أي reference، يعني objects بقت *unreachable* ومفيش أي `branch` أو `tag` أو `reference` بيوصل ليها.

مثال دلوقتي أحمد عنده Repository وعمل شوية commits:

```
A---B---C    main
```

وبعدين عمل حاجة خلت بعض الـ commits القديمة مش متوصلة بأي `branch` أو `tag`.

مثلاً:

```
A---B---C    main
     \
      D---E   ← unreachable
```

هنا `D` و `E` مبقوش reachable من أي reference.

ممكن الـ objects دي تفضل موجودة داخل `.git` لفترة، وGit يقدر يحتفظ بيها كنوع من الـ **recovery**.

لو أحمد عايز ينضف الـ unreachable objects، يقدر يستخدم:

```bash
git prune
```

في الحالة دي Git هيحذف الـ objects اللي مبقاش فيه أي reference بيوصل ليها **ومسموح لها بالحذف حسب قواعد الـ garbage collection**.

ولو عايز تشوف إيه اللي ممكن يتعمله prune قبل الحذف:

```bash
git prune --dry-run
```

وده **مش بيحذف حاجة**، لكنه يعرض الـ objects اللي ممكن يتم حذفها.


لكن مهم جدًا إن `git prune` مش أمر بنستخدمه بشكل عشوائي، لأن الـ objects اللي بيحذفها ممكن **مايبقاش ممكن استرجاعها بسهولة**.

وعشان كده Git نفسه بيستخدم:

```bash
git gc
```


وبكده بنستخدم **Git Prune** لتنضيف الـ repository من الـ objects القديمة وغير المستخدمة، لكن في الاستخدام الطبيعي غالبًا بنسيب Git يتعامل مع عملية التنظيف من خلال `git gc`.