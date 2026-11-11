# تشغيل عيادة سوا التدريبية كموقع مستقل

الموقع بيتكوّن من حاجتين:
- **الصفحة نفسها**: متحطوطة على GitHub Pages (مجانًا).
- **قاعدة البيانات**: Firebase من جوجل (الخطة المجانية Spark كفاية لـ40 أخصائي).

## أولًا: Firebase (حوالي 10 دقايق)

1. ادخلي على https://console.firebase.google.com بحساب جوجل بتاعك، ودوسي **Create a project**.
   - سمّيه مثلًا `sawa-training`.
   - اقفلي Google Analytics (مش محتاجينه)، وكمّلي.
2. من القائمة اللي على الجنب: **Build ← Authentication ← Get started**.
   - من **Sign-in method** فعّلي **Anonymous**.
   - وفعّلي **Email/Password**.
   - من **Users ← Add user** ضيفي إيميلك وباسورد قوي. ده حساب دخولك للداشبورد.
3. من القائمة: **Build ← Firestore Database ← Create database**.
   - اختاري **Production mode**.
   - المكان: `eur3 (europe-west)`.
4. في Firestore افتحي تبويب **Rules**:
   - امسحي اللي مكتوب، والصقي محتوى ملف `firestore.rules` اللي في المشروع.
   - غيّري كلمة `ADMIN_EMAIL` لإيميلك (نفس الإيميل اللي عملتيه في خطوة 2).
   - دوسي **Publish**.
5. من الترس ⚙ جنب **Project Overview ← Project settings**:
   - تحت **Your apps** دوسي أيقونة الويب `</>`.
   - سمّي التطبيق `sawa-web`، ومن غير Firebase Hosting، ودوسي **Register app**.
   - هيظهرلك كود فيه `firebaseConfig = { ... }`. انسخيه وابعتيه لـ Claude.
   - الكود ده مش سري، وده طبيعي يبقى ظاهر في الموقع. الحماية الحقيقية في قواعد خطوة 4.

## ثانيًا: GitHub Pages (دقيقتين)

1. افتحي المستودع على GitHub ← **Settings ← Pages**.
2. تحت **Build and deployment**:
   - **Source**: Deploy from a branch.
   - **Branch**: `claude/psychology-diagnosis-game-afo160`، والفولدر `/docs`.
   - دوسي **Save**.
3. بعد دقيقة أو اتنين، الموقع هيبقى على:
   `https://hendmahmmoud91-rgb.github.io/Diagnosisgame/`

## الاستخدام

- **الأخصائيين**: يفتحوا اللينك، ويختاروا أسماءهم، ويلعبوا. مش محتاجين أي حساب.
- **المشرفة**: تفتح اللينك وتدوس **دخول المشرفة** تحت (أو تضيف `#admin` في آخر اللينك)، وتدخل بالإيميل والباسورد.

## ملاحظات

- أي حد معاه اللينك يقدر يفتح اللعبة ويشوف أسماء الفريق ومحاولاتهم. ماتحطيش أي بيانات مرضى حقيقيين.
- المستودع عام، فالحالات وإجاباتها ممكن حد يشوفها من الكود. ده مقبول للتدريب.
