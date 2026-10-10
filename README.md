# ألفة (Ulfa) — نسخة أندرويد

نموذج أولي لتطبيق يحوّل الوقت أمام الشاشات إلى وقت عائلي: تتفق الأسرة على **ميثاق** (حد استخدام مشترك في أوقات محددة)،
وعند بلوغ الحد يظهر **وضع ألفة** على التطبيقات المختارة، ويُفك الحجب بـ**حوار حقيقي** بين أفراد الأسرة
أو بإنجاز **مهام مشتركة**.

الحزمة: `com.ulfa.app` — Kotlin و Jetpack Compose و Hilt و Room و Firebase (الخطة المجانية).


---

## 📱 معرض واجهات التطبيق

<p align="center">
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_103946.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104118.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104126.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104220.png" width="22%" alt="واجهة التطبيق" />
</p>
<p align="center">
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104245.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104336.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104348.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104436.png" width="22%" alt="واجهة التطبيق" />
</p>
<p align="center">
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104500.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104531.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104551.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104600.png" width="22%" alt="واجهة التطبيق" />
</p>
<p align="center">
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104623.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104639.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104703.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_104717.png" width="22%" alt="واجهة التطبيق" />
</p>
<p align="center">
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105044.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105110.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105206.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105227.png" width="22%" alt="واجهة التطبيق" />
</p>
<p align="center">
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105236.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105248.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105433.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105541.png" width="22%" alt="واجهة التطبيق" />
</p>
<p align="center">
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105553.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105611.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105705.png" width="22%" alt="واجهة التطبيق" />
  <img src="Ulfa%20-%20Screenshot/Screenshot_20261010_105727.png" width="22%" alt="واجهة التطبيق" />
</p>

---


## الواجهات (34) والنوافذ (8)
تفصيلها في `Ulfa_Screens_List.md`. كلها منفّذة. وبيانات الفعاليات والكوبونات والمستشارين **تجريبية** (P2).

## البنية
app/src/main/java/com/ulfa/app/
core/ أدوات عامة (النتائج، الوقت، التشفير، الصلاحيات)
domain/ النماذج وحالات الاستخدام (منطق نقي قابل للاختبار) وواجهات المستودعات
data/ Room (مهام فردية مشفّرة) و Firestore والبيانات التجريبية
system/ قياس الاستخدام، خدمة الوصول والطبقة، الصوت، المزامنة، الإشعارات
ui/ Compose: الشاشات و ViewModels والتنقل والثيم
di/ وحدات Hilt

## التشغيل
1. افتح المجلد في Android Studio، وانتظر مزامنة Gradle.
2. اربط Firebase (مرة واحدة):
   - أنشئ مشروعاً في [console.firebase.google.com](https://console.firebase.google.com) وأضف تطبيق أندرويد بالحزمة `com.ulfa.app`.
   - أضف بصمة SHA-1: `keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android | grep SHA1`
   - فعّل **Authentication** (Google و Email/Password) و **Firestore Database**.
   - نزّل `google-services.json` وضعه في `app/` (يستبدل الملف المؤقت).
3. انشر قواعد الأمان: انسخ `firebase/firestore.rules` إلى Firestore ← Rules ← **Publish**
   (`cat firebase/firestore.rules | pbcopy`). **أعد النشر بعد أي تحديث للقواعد.**
4. شغّل التطبيق على جوال حقيقي (يُنصح) أو محاكي.

## أوامر مفيدة
```bash
bash scripts/run_tests.sh            # كل اختبارات الوحدة + ملخص
bash scripts/build_apk.sh            # APK على سطح المكتب
bash scripts/make_release_keystore.sh  # (اختياري) توقيع نسخة الإصدار
~/Library/Android/sdk/platform-tools/adb install -r ~/Desktop/Ulfa-debug.apk
```

## تجربة سريعة بجهازين
1. الجهاز أ: أنشئ حساباً ← أنشئ أسرة ← أكمل الصلاحيات ← اختر تطبيقاً (مثل Chrome).
2. الجهاز ب: حساب آخر ← انضمام برمز الدعوة.
3. من الجهاز أ : **الإعدادات ← وضع العرض** (الحد دقيقة، وشروط الحوار 20 ثانية).
4. استخدم التطبيق المختار دقيقة ← يظهر **وضع ألفة**.
5. **الحوار ← ابدأ جلسة** على أ، وانضم من ب، وتحدثا ← نجاح الجلسة ← رصيد ← يُفك الحجب.

## الخصوصية (ضمانات مفحوصة بالاختبارات)
- لا يُسجَّل الصوت ولا يُخزَّن ولا يُرسل: يُعالَج إطاراً بإطار في الذاكرة، ويُرفع فقط أرقام فترات الكلام.
- خدمة الوصول تعرف اسم التطبيق المفتوح فقط (`canRetrieveWindowContent=false`).
- المهام الفردية مشفّرة (AES-256-GCM عبر Android Keystore) ومحلية.
- الاستبيان الأسبوعي مجهول، ولا يظهر معدله إلا بعد مشاركة فردين فأكثر.
- يمكن تصدير بياناتك وحذف حسابك من **الإعدادات ← الخصوصية والبيانات**.

## حدود النموذج الأولي (للشفافية).
- بعض الشركات تُغلق التطبيقات في الخلفية بقوة؛ يلزم تعطيل تقييد البطارية (ضمن دليل الصلاحيات).
- قواعد Firestore تقيّد الوصول بأعضاء الأسرة، لكنها **لا تفرض** اشتراط موافقة الجميع على تعديل الميثاق (يُفرض في التطبيق).
- حدود الخطة المجانية لـ Firestore (قراءات/كتابات يومية) مناسبة للتجربة لا للاستخدام الواسع.
- عتبات كشف الكلام (`VoiceActivityDetector`) قيم أولية قد تحتاج ضبطاً حسب الجهاز والبيئة.
- التوقيت بين الأجهزة يعتمد على ساعاتها (متزامنة عادةً بالإنترنت).
