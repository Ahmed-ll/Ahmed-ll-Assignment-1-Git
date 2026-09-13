# Git Short log

##### الفكرة هي اني بستخدم *Git Shortlog* عشان ألخّص الـ *commits* الموجودة في الـ repository وأشوف كل *developer* عمل كام commit وإيه الـ commits اللي عملها، بدل ما أعرض الـ history كله باستخدام `git log`.

مثال دلوقتي احمد شغال على مشروع، وفيه أكتر من developer اشتغلوا عليه وعملوا الـ commits دي:

```
Ali → implement login
Ali → add register
Omar  → fix validation
Ahmed → fix login bug
Omar  → update database
```

لو احمد عاوز يشوف ملخص للـ **commits** حسب كل developer، يقدر ينفذ:

```bash
git shortlog
```

بكده **Git** هيجمع الـ commits حسب الشخص اللي عملها، وهيعرض الـ **author** وتحت اسمه الـ commits اللي عملها.

مثلاً ممكن تظهر النتيجة بالشكل ده:

```
Ali(2)
	implement login
	add register
	
Omar (2):
      fix validation
      update database
      
Ahmed (1):
      fix login bug
```

ولو احمد عاوز يعرف **عدد الـ commits فقط** لكل developer من غير ما يعرض أسماء الـ commits:

```bash
git shortlog -s
git shortlog -sn
```

بحيث:

- ان `-s` → يعرض **عدد الـ commits** لكل developer.
- وان `-sn` → يرتب النتائج حسب **عدد الـ commits**.

فتكون النتيجة مثلًا:

```
2 Ali
2 Omar
1 Ahmed
```

وبكده بنستخدم **Git Shortlog** لما نكون محتاجين **ملخص سريع للـ commit history حسب الـ developers**، ونعرف مين عمل كام commit وإيه الـ commits اللي عملها، بدل ما نراجع الـ history كله commit وراء commit.