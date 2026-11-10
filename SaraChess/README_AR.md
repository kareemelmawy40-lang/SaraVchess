# Sara Chess — تطبيق شطرنج للأندرويد

- رقعة خضراء وقطع مخصصة (الأشكال التي أرسلتها).
- **العب ضد المحرك** (Sara أو Stockfish 19 من أعلى الشاشة).
  - اختر البوت حسب **شكل القطعة**: البيدق (أضعف ~250/300) ← الحصان ← الفيل ← الملكة ← الملك (~2100) أو أقصى قوة.
  - التقييم يتغير حسب المحرك: Sara أقل بقليل من Stockfish (+50 تقريباً).
  - عند انتهاء المباراة يسألك التطبيق: *هل تريد مراجعة المباراة؟*
- **تحليل مباراة**: أيقونة فوق القطعة ‼️ ❗ 👍 📒 ⁉️ ❓ ❓❓ ❌ ➡️ + سهم لأفضل نقلة + شريط تقييم + ملخص ودقة.

## نسختان من التطبيق
- `SaraChess-lite.apk` خفيفة (بضع ميجابايت): محرك Sara فقط (خوارزميات بدون شبكة عصبية).
- `SaraChess-full.apk` كبيرة (~80 ميجا): Sara + Stockfish 19. الحجم الكبير كله شبكة NNUE العصبية؛ Stockfish 19 لا يعمل بدونها (الحساب الكلاسيكي حُذف منه من الإصدار 16).

## البناء من الهاتف (Termux + GitHub)
1. أنشئ مستودعاً **فارغاً** على github.com + توكن (Personal access token classic) بصلاحيتي `repo` و `workflow`.
2. في Termux:
   ```
   pkg install git unzip
   termux-setup-storage
   cd ~ && unzip SaraChess_project.zip && cd SaraChess
   # ضع ملف Stockfish الجاهز (الذي أرسلته) داخل المشروع:
   mkdir -p ~/sf && tar -xzf ~/storage/downloads/stockfish-android-arm64-universal*.gz -C ~/sf
   cp ~/sf/stockfish/stockfish-android-arm64-universal engine/stockfish/stockfish-android-arm64
   bash push_to_github.sh اسمك اسم_المستودع التوكن
   ```
   (إذا تخطيت خطوة Stockfish يحاول البناء من المصدر في GitHub.)
3. افتح **Actions** وانتظر "Build Sara Chess APK" ثم حمّل APK من **Releases**.

## إن ظهر شريط أحمر "لم يتم العثور على أي محرك"
سيعرض الآن مسار المجلد والملفات الموجودة؛ أرسل لي لقطة الشاشة.
