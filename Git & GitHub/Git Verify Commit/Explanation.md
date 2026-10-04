# Git Verify-Commit

##### الفكرة ببساطة هي إن *Git Verify-Commit* بيستخدم عشان أتأكد إن الـ *commit* معمول له *GPG أو SSH signature* وإن الـ signature دي صحيحة وموثوقة.

يعني بدل ما أسأل: _مين عمل الـ commit؟_  أقدر كمان أتأكد إن الـ commit فعلًا **موقّع بالمفتاح الخاص بالـ developer**.

مثال دلوقتي أحمد عمل commit:

```bash
git commit -S -m "implement login"
```

الـ `-S` هنا معناها إن أحمد عمل **sign للـ commit** باستخدام مفتاحه.

بعد كده يقدر يتأكد من الـ signature باستخدام:

```bash
git verify-commit HEAD
```

هنا HEAD معناها:  آخر commit أنت واقف عليه حاليًا.

ممكن كمان تتحقق من commit معين باستخدام الـ hash:

```bash
git verify-commit a1b2c3d
```

لو الـ signature صحيحة، Git يعرض معلومات عن الـ signer والـ key المستخدمة.

ولو الـ commit **مش signed أصلًا**، Git هيبلغك إن مفيش signature للتحقق منها.

ممكن كمان تستخدم:

```bash
git log --show-signature
```

وده مفيد لو عايز تشوف الـ **commits** ومعاها معلومات الـ signatures أثناء عرض الـ history.


وبكده بنستخدم **Git Verify-Commit** لما نحتاج نتأكد إن الـ **commit** تم توقيعه بشكل صحيح، وده بيساعد في التأكد من **أصالة الـ commits وهوية الـ signer**.