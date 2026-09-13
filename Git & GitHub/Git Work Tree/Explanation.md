# Git Work Tree

##### فكرة *Git Worktree* هي إنه بيسمحلي إني أشتغل على *أكتر من branch في نفس الوقت*، كل branch في *folder منفصل*، من غير ما أضطر أعمل `switch` بين الـ branches كل شوية.

مثال دلوقتي أحمد شغال على main branch وعنده Feature جديدة اسمها Auth

عادةً لو عايز ينتقل من `main` لـ `Auth` بيعمل:

```bash
git switch Auth
```

لكن تخيل إن أحمد شغال على `Auth` ولسه مخلصش الـ feature، وفي نفس الوقت المدير طلب منه يروح يعمل **urgent bug fix** على `main`.

بدل ما يعمل `switch` ويوقف شغله الحالي، يقدر يستخدم:

```bash
git worktree add ../BugFix main
```

كدا Git هيعمل folder جديد اسمه `BugFix`، ويخليه مرتبط بالـ `main`.

فيبقى عند أحمد:

```
Project/
│
├── Auth/       ← شغال على Auth
│
└── BugFix/     ← شغال على main
```

وبالتالي يقدر يفتح الـ `BugFix` ويشتغل على `main`، وفي نفس الوقت الـ `Auth` يفضل موجود زي ما هو.

### أعرف الـ Worktrees الموجودة إزاي؟

```bash
git worktree list
```

ممكن تشوف حاجة بالشكل ده:

```
D:/Project       abc1234 [Auth]
D:/BugFix        xyz5678 [main]
```

يعني عندك **اتنين Worktrees** شغالين على branches مختلفة.

### ولما أخلص Worktree؟

تحذفه باستخدام:

```bash
git worktree remove ../BugFix
```

وده بيشيل الـ Worktree نفسه، **مش الـ branch بالضرورة**.


وبكده بنستخدم **Git Worktree** لما نحتاج نشتغل على **أكتر من branch في نفس الوقت**، خصوصًا لما يكون عندنا Feature شغالة وفجأة محتاجين نعمل **Bug Fix** على branch تاني من غير ما نوقف شغلنا الحالي.