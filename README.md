<p align="center"><img src="assets/banner.svg" alt="Salah TV" width="100%"></p>

<p align="center">
  <a href="https://alimwork85-web.github.io/salah-tv/"><img src="https://img.shields.io/badge/Live-GitHub%20Pages-3ddc97?logo=github" alt="Live"></a>
  <img src="https://img.shields.io/badge/Fire%20TV%20%7C%20Android%20TV-ready-ff9900?logo=amazonfiretv&logoColor=white" alt="Fire TV">
  <img src="https://img.shields.io/badge/HTML-single%20file-e34f26?logo=html5&logoColor=white" alt="HTML">
  <img src="https://img.shields.io/badge/العربية-RTL-1f6feb" alt="Arabic RTL">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="MIT"></a>
</p>

# Salah TV — أوقات الصلاة والطقس على شاشة التلفاز

صفحة واحدة بالعربية مصمّمة لشاشة التلفاز (Fire TV / Android TV)، تُفتح في متصفح مثل **TV Bro**، فيها:

- **ساعة كبيرة** مع التاريخ الميلادي والهجري.
- **أوقات الصلاة اليوم** (طريقة ISNA لأمريكا الشمالية)، مع تمييز الصلاة القادمة وعدّاد تنازلي لها.
- **الإمساك والإفطار**: يظهران تلقائيًا في رمضان، مع عدّاد «باقي على الإفطار» و«باقي على الإمساك».
- **الطقس بالمقاييس الأمريكية** (°F وmph والبوصة): الطقس الآن، والعظمى والصغرى، واحتمال المطر، والرطوبة، والرياح، **وتوقعات 4 أيام**.
- **تأثير مطر متحرك** على الشاشة حين تمطر فعلًا.
- **تنبيه ذهبي عند دخول الوقت**: يتحول صف الصلاة إلى ذهبي نابض، ويظهر «حان الآن وقت صلاة …» لمدة 15 دقيقة.
- **الأذان بالصوت** عند دخول وقت كل صلاة. إن منع المتصفح الصوت التلقائي ظهر «اضغط OK مرتين لتفعيل صوت الأذان». في TV Bro تُظهر الضغطة الأولى المؤشر وتنقر الثانية.
- خلفية بنقش هندسي إسلامي، ورسم مسجد وهلال أصلي.
- أرقام غربية (0-9) في كل مكان.

<p align="center"><img src="assets/screenshot.png" alt="لقطة شاشة" width="85%"></p>

## الاستخدام

افتح الرابط على التلفاز: **https://alimwork85-web.github.io/salah-tv/**

| الرابط | النتيجة |
|---|---|
| `…/salah-tv/` | تلقائي: الإمساك والإفطار يظهران في رمضان فقط |
| `…/salah-tv/?ramadan=1` | إظهار الإمساك والإفطار دائمًا |
| `…/salah-tv/?ramadan=0` | إخفاؤهما دائمًا |
| `…/salah-tv/?rain=1` | معاينة شكل المطر |
| `…/salah-tv/?sound=0` | تنبيه ذهبي دون صوت، حين يرفع الأذانَ تطبيقٌ آخر مثل Al-Azan |
| `…/salah-tv/?at=12:43` | تشغيل الساعة من وقت معيّن لمعاينة التنبيه والأذان |

على Fire TV مع TV Bro يمكن فتحها من الكمبيوتر بأمر واحد:

```
adb shell am start -a android.intent.action.VIEW -d "https://alimwork85-web.github.io/salah-tv/" com.phlox.tvwebbrowser
```

## تغيير المدينة

عدّل السطر `const LAT = …, LON = …;` في `index.html` واسم المدينة في `#date`.
المدينة الافتراضية **Fresno, CA**.

## مصادر البيانات

- أوقات الصلاة: [Aladhan API](https://aladhan.com/prayer-times-api) — `method=2` (ISNA).
- الطقس: [Open-Meteo](https://open-meteo.com/) — مجاني ولا يحتاج مفتاحًا.
- الأذان، لكل صلاة مؤذنها، والتسجيلات كلها من Wikimedia Commons:

  | الصلاة | الملف | المصدر | الرخصة |
  |---|---|---|---|
  | الفجر | `assets/adhan/fajr.mp3` | [Besim Azemi — Islamic Center Malmö](https://commons.wikimedia.org/wiki/File:Eid_al-Fitr_Fajr_azan_at_Malm%C3%B6_Mosque_-_19_August_2012.webm) | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
  | الظهر | `assets/adhan/dhuhr.mp3` | [Adhan, Great Mosque of Mecca — Seyfula Islam](https://commons.wikimedia.org/wiki/File:Adhan,_Great_Mosque_of_Mecca_-_Jan_21,_2013.webm) | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
  | العصر | `assets/adhan/asr.mp3` | [Call to prayer from the Prophet's Mosque — ejaz215 (freesound)](https://commons.wikimedia.org/wiki/File:33937_ejaz215_call-to-prayer-from-the-prophet-s-mo.ogg) | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) |
  | المغرب | `assets/adhan/maghrib.mp3` | [The Adhan — Aaqib Azeez، برفع Atcovi](https://commons.wikimedia.org/wiki/File:The_Adhan_-_Muslim_Call_to_Prayer_-_Aaqib_Azeez.mp3) | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
  | العشاء | `assets/adhan/isha.mp3` | [Azan — Andrewler](https://commons.wikimedia.org/wiki/File:Azan.ogg) | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |

  حُوّلت التسجيلات إلى MP3 أحادي القناة دون أي تعديل آخر. وتبقى ملفات الصوت تحت رخصها الأصلية، لا تحت رخصة MIT الخاصة بالكود.

لا تجمع الصفحة أي بيانات عن المستخدم، ولا تستخدم كوكيز.

---

**Salah TV** — a single-file Arabic prayer-times, Imsak/Iftar and weather (US units) dashboard for Fire TV and Android TV browsers.

## المطوّر والناشر

**Ali Alhumedi** — © 2026 Ali Alhumedi. الترخيص: [MIT](LICENSE).
