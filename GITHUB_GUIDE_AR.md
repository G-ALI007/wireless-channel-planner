# دليل رفع المشروع على GitHub

## الخطوات السريعة

### 1. إنشاء مستودع على GitHub

1. اذهب إلى [github.com](https://github.com) وسجل الدخول
2. اضغط على زر "+" في الأعلى واختر "New repository"
3. اختر اسم للمستودع: `wireless-channel-planner`
4. أضف وصف: "C++ library for wireless channel and frequency planning"
5. اختر Public أو Private حسب رغبتك
6. **لا تقم** بتحديد "Initialize with README" (لأننا لدينا README بالفعل)
7. اضغط "Create repository"

### 2. رفع المشروع من جهازك

افتح Terminal/Command Prompt في مجلد المشروع ونفذ الأوامر التالية:

```bash
# الانتقال إلى مجلد المشروع
cd wireless-channel-planner

# تهيئة Git (إذا لم يكن مهيأ بالفعل)
git init

# إضافة جميع الملفات
git add .

# عمل أول commit
git commit -m "Initial commit: Wireless Channel Planner library"

# ربط المشروع بمستودع GitHub (استبدل YOUR_USERNAME باسم المستخدم الخاص بك)
git remote add origin https://github.com/YOUR_USERNAME/wireless-channel-planner.git

# رفع المشروع
git push -u origin main
```

**ملاحظة:** إذا كان الفرع الرئيسي يسمى "master" وليس "main"، استخدم:
```bash
git branch -M main
git push -u origin main
```

### 3. إذا طلب منك تسجيل الدخول

GitHub قد يطلب منك المصادقة. يمكنك:

**الطريقة الأولى - Personal Access Token (موصى بها):**
1. اذهب إلى Settings > Developer settings > Personal access tokens
2. اختر "Tokens (classic)" ثم "Generate new token"
3. أعطه اسم وحدد صلاحيات "repo"
4. انسخ التوكن (لن تراه مرة أخرى!)
5. استخدمه كـ password عند رفع الكود

**الطريقة الثانية - SSH Key:**
```bash
# توليد SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# نسخ المفتاح العام
cat ~/.ssh/id_ed25519.pub

# أضفه في GitHub Settings > SSH and GPG keys
```

ثم استخدم رابط SSH بدلاً من HTTPS:
```bash
git remote set-url origin git@github.com:YOUR_USERNAME/wireless-channel-planner.git
```

### 4. تحديث المعلومات الشخصية

قبل الرفع، تأكد من تعديل:

1. **في README.md:**
   - استبدل `[Your Name]` باسمك
   - استبدل `yourusername` باسم المستخدم على GitHub

2. **في LICENSE:**
   - استبدل `[Your Name]` باسمك

3. **في ملفات الكود:**
   - أضف اسمك في تعليقات `@author`

### 5. إضافات اختيارية (بعد الرفع)

#### إضافة وسوم (Tags):
```bash
git tag -a v1.0.0 -m "First release"
git push origin v1.0.0
```

#### إضافة GitHub Actions للبناء التلقائي:
أنشئ ملف `.github/workflows/build.yml`

#### إضافة Badge إلى README:
أضف في بداية README.md:
```markdown
![Build Status](https://github.com/YOUR_USERNAME/wireless-channel-planner/actions/workflows/build.yml/badge.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![C++](https://img.shields.io/badge/C++-11-blue.svg)
```

### 6. نصائح لجعل المشروع أكثر جاذبية

1. **أضف لقطات شاشة:** إذا أمكن، أضف صور للمخرجات
2. **أضف أمثلة أكثر:** في مجلد examples
3. **اكتب وثائق API:** استخدم Doxygen
4. **أضف Tests:** اكتب اختبارات في مجلد tests
5. **CONTRIBUTING.md:** أنشئ ملف لشرح كيفية المساهمة
6. **CHANGELOG.md:** لتتبع التغييرات بين الإصدارات

### 7. الترويج للمشروع

- أضف topics في GitHub: `cpp`, `wireless`, `wifi`, `networking`, `channel-planning`
- شارك المشروع على LinkedIn
- اذكره في سيرتك الذاتية
- شارك في مجتمعات البرمجة

---

## أوامر Git المفيدة

```bash
# عرض حالة الملفات
git status

# إضافة ملفات جديدة
git add filename.cpp

# عمل commit
git commit -m "Add new feature"

# رفع التحديثات
git push

# سحب آخر التحديثات
git pull

# عرض السجل
git log --oneline

# إنشاء فرع جديد
git checkout -b feature-name

# دمج فرع
git merge feature-name
```

---

## مشاكل شائعة وحلولها

### المشكلة: "fatal: not a git repository"
**الحل:**
```bash
git init
```

### المشكلة: "error: failed to push some refs"
**الحل:**
```bash
git pull origin main --rebase
git push origin main
```

### المشكلة: ملفات كبيرة جداً
**الحل:**
أضفها في `.gitignore` قبل الرفع

---

## موارد إضافية

- [دليل Git الرسمي](https://git-scm.com/doc)
- [دليل GitHub](https://docs.github.com)
- [MarkDown Guide](https://www.markdownguide.org/)

---

**بالتوفيق في رحلتك مع GitHub! 🚀**
