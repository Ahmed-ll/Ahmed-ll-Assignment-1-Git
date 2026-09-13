# Git Filter-Repo

##### فكرته هي إن *Git Filter-Repo* بيستخدم عشان أعمل *تعديل على Git history بالكامل*، يعني أقدر أغيّر أو أحذف ملفات وبيانات من الـ commits القديمة، مش بس من آخر commit.

وده بيكون مفيد جدًا لو مثلًا أحمد رفع ملف بالغلط على الـ repository، زي:

```
.env
password.txt
secret.json
```

وبعدين عمل:

```bash
git rm --cached .env
```

المشكلة إن كده الملف **اختفى من الـ current version**، لكن لسه موجود في الـ **Git history** والـ commits القديمة.

هنا يقدر يستخدم:

```bash
git filter-repo --path .env --invert-paths
```

الأمر ده معناه:

- `--path .env` → حدد الملف اللي عايز نتعامل معاه.
- `--invert-paths` → احذف الملف ده من الـ history بالكامل.

يعني بدل ما يكون:

```
Commit 1 → .env موجود
Commit 2 → .env موجود
Commit 3 → .env موجود
Commit 4 → .env اتعمله delete
```

بعد `filter-repo`:

```
Commit 1 → ❌ .env
Commit 2 → ❌ .env
Commit 3 → ❌ .env
Commit 4 → ❌ .env
```

يعني الملف اتمسح من **التاريخ نفسه**.

---

### طيب لو عايز أغير اسم أو إيميل قديم؟

ممكن تستخدم:

```bash
git filter-repo --mailmap my-mailmap
```

وده يسمحلك بإعادة كتابة معلومات الـ authorship في الـ history.

---

### ⚠️ مهم جدًا

`git filter-repo` بيعمل **History Rewrite**.

يعني الـ commits القديمة ممكن تتغير، وبالتالي الـ commit hashes هتتغير.

لو الـ repository موجود على GitHub والـ history اتعمله rewrite، غالبًا هتحتاج تعمل:

```bash
git push --force
```

وده ممكن يعمل مشاكل مع باقي الـ developers لو بيشتغلوا على نفس الـ repository.

وعشان كده **ما تستخدمش `filter-repo` كطريقة عادية لتنضيف الـ repository**؛ هو أداة للحالات اللي محتاج فيها فعلًا تعدّل الـ history.


وأهم فرق بينها وبين git rm:

- git rm => يحذف الملف من الـ current version
- git filter-repo => يقدر يحذف الملف من الـ entire Git history

وبالتالي بنستخدم **Git Filter-Repo** لما نحتاج نعمل **History Rewrite**، خصوصًا لو فيه ملف أو بيانات حساسة اتسجلت في commits قديمة.