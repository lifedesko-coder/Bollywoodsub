# BollywoodSub AI - مشروع الترجمة المحلي (Python)

مشروع محلي متكامل لترجمة الأفلام والمسلسلات الهندية (Bollywood & OTT) إلى العربية بدقة فائقة مع حرق الترجمة ومنع خطأ الـ 100 ثانية نهائياً.

## 🚀 المميزات
- استخراج الصوت بنقاء 44.1kHz ومزامنة صفرية مطلقة عبر FFmpeg (`-avoid_negative_ts make_zero -af aresample=async=1`).
- ترجمة حوارات الهندية و Hinglish والراب السريع وأغاني الأفلام باستخدام Google Gemini API (`@google/genai`).
- منع خطأ الـ 100 ثانية عبر معادلة برمجية حتمية: `المجموع بالثواني = (الدقائق × 60) + الثواني`.
- دعم اللهجات: الفصحى الحديثة، المصرية، الشامية، الخليجية، العراقية.
- توليد ملفات `SRT` قياسية وملفات `ASS` بتنسيقات عربية سينمائية بخط Cairo.
- حرق الترجمة تلقائياً داخل الفيديو (Hardcode/Burn) بجودة عالية.

## 🛠️ متطلبات التشغيل
1. تثبيت بايثون 3.10 أو أحدث.
2. تثبيت FFmpeg وإضافته لمتغيرات النظام PATH:
   - Ubuntu/Debian: `sudo apt install ffmpeg`
   - Mac (Homebrew): `brew install ffmpeg`
   - Windows: تحميل FFmpeg وإضافته إلى System PATH.

3. تثبيت المكتبات:
```bash
pip install -r requirements.txt
```

4. تعيين مفتاح API لـ Google Gemini في ملف `.env` أو في سطر الأوامر:
```bash
export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
```

## 🎬 كيفية الاستخدام

### 1. ترجمة فيديو هندي وتوليد ملفات SRT و ASS:
```bash
python gemini_subtitler.py --video "path/to/bollywood_movie.mp4" --dialect msa
```

### 2. ترجمة مع حرق الترجمة داخل الفيديو مباشرة:
```bash
python gemini_subtitler.py --video "movie.mp4" --dialect egyptian --burn
```

### 3. خيارات اللهجات المتاحة (`--dialect`):
- `msa`: الفصحى الحديثة
- `egyptian`: اللهجة المصرية
- `levantine`: اللهجة الشامية
- `gulf`: اللهجة الخليجية
- `iraqi`: اللهجة العراقية

### 4. خيارات النماذج (`--model`):
- `gemini-3.8-flash` (افتراضي وسريع ودقيق)
- `gemini-3.5-flash`
