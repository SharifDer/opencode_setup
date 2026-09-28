# OpenCode Setup Guide / دليل تثبيت OpenCode

**[English](#english)** | **[العربية](#العربية)**

---

## English

### Prerequisites

- Windows 10 or 11
- Internet connection
- PowerShell (built into Windows)

No Node.js, no admin rights, no package manager needed.

---

### Step 1 — Install OpenCode

Open **PowerShell** and paste these three lines:

```powershell
Invoke-WebRequest -Uri "https://github.com/anomalyco/opencode/releases/latest/download/opencode-windows-x64.zip" -OutFile "$env:TEMP\opencode.zip"
Expand-Archive "$env:TEMP\opencode.zip" -DestinationPath "$env:LOCALAPPDATA\opencode" -Force
[Environment]::SetEnvironmentVariable("Path", [Environment]::GetEnvironmentVariable("Path","User") + ";$env:LOCALAPPDATA\opencode", "User")
```

This downloads the latest OpenCode release, extracts it to `%LOCALAPPDATA%\opencode`, and adds it to your PATH.

### Step 2 — Verify the installation

**Close and reopen PowerShell** (so the new PATH loads), then run:

```powershell
opencode --version
```

You should see a version number.

### Step 3 — Place the config file (manual)

1. Get the file `opencode(Alaadin Alqobati).json` from **Sharif** and copy it to your machine.
2. Press **Win + R**, type `%USERPROFILE%`, and hit **Enter** — this opens your user folder (`C:\Users\<YourName>`).
3. Inside it, create a folder named `.config`, and inside that, a folder named `opencode`.
4. Move the file into that `opencode` folder and rename it to exactly: **`opencode.json`**

Final result:

```
C:\Users\<YourName>\.config\opencode\opencode.json
```

> ⚠️ **Watch out for hidden extensions:** if File Explorer hides file extensions, you may accidentally create `opencode.json.json`. Enable **View → File name extensions** to make sure the name is exactly `opencode.json`.

### Step 4 — Launch OpenCode

```powershell
opencode
```

On the first start, OpenCode automatically downloads the LiteLLM plugin and discovers the available models from the company proxy. No further setup needed.

### Step 5 — Verify the config (optional)

```powershell
opencode debug config
```

This shows which config file was loaded. You should see your `opencode.json` path listed.

---

### Notes

- **The config file contains an API key — treat it like a password.** Do not share it, and never commit `opencode.json` to a git repository.
- **Very old computers** (pre-2013 CPUs without AVX2): if OpenCode crashes on launch, repeat Step 1 using `opencode-windows-x64-baseline.zip` instead of `opencode-windows-x64.zip` in the download URL.
- **The download URL always fetches the latest version**, so these instructions stay valid over time.
- OpenCode will ask for your approval before editing files or fetching URLs — this is configured on purpose.
- Problems? Contact **Sharif**.

---

---

## العربية

### المتطلبات

- ويندوز 10 أو 11
- اتصال بالإنترنت
- PowerShell (موجود مسبقاً في ويندوز)

لا حاجة إلى Node.js، ولا صلاحيات مسؤول، ولا أي مدير حزم.

---

### الخطوة 1 — تثبيت OpenCode

افتح **PowerShell** والصق هذه الأسطر الثلاثة:

```powershell
Invoke-WebRequest -Uri "https://github.com/anomalyco/opencode/releases/latest/download/opencode-windows-x64.zip" -OutFile "$env:TEMP\opencode.zip"
Expand-Archive "$env:TEMP\opencode.zip" -DestinationPath "$env:LOCALAPPDATA\opencode" -Force
[Environment]::SetEnvironmentVariable("Path", [Environment]::GetEnvironmentVariable("Path","User") + ";$env:LOCALAPPDATA\opencode", "User")
```

هذا الأمر يحمّل أحدث إصدار من OpenCode، ويفك ضغطه في `%LOCALAPPDATA%\opencode`، ويضيفه إلى متغير PATH.

### الخطوة 2 — التحقق من التثبيت

**أغلق PowerShell وافتحه من جديد** (حتى يتم تحميل PATH الجديد)، ثم نفّذ:

```powershell
opencode --version
```

يجب أن يظهر رقم الإصدار.

### الخطوة 3 — وضع ملف الإعدادات (يدوياً)

1. خذ الملف `opencode(Alaadin Alqobati).json` من **شريف** وانسخه إلى جهازك.
2. اضغط **Win + R**، واكتب `%USERPROFILE%`، ثم اضغط **Enter** — سيفتح مجلد المستخدم الخاص بك (`C:\Users\<اسمك>`).
3. بداخله، أنشئ مجلداً باسم `.config`، وبداخله مجلداً باسم `opencode`.
4. انقل الملف إلى مجلد `opencode` وأعد تسميته بالضبط إلى: **`opencode.json`**

النتيجة النهائية:

```
C:\Users\<اسمك>\.config\opencode\opencode.json
```

> ⚠️ **انتبه للامتدادات المخفية:** إذا كان مستكشف الملفات يخفي الامتدادات، قد تنشئ عن طريق الخطأ ملفاً باسم `opencode.json.json`. فعّل **View ← File name extensions** (عرض ← امتدادات أسماء الملفات) للتأكد من أن الاسم هو `opencode.json` بالضبط.

### الخطوة 4 — تشغيل OpenCode

```powershell
opencode
```

عند أول تشغيل، يقوم OpenCode تلقائياً بتحميل إضافة LiteLLM واكتشاف النماذج المتاحة من خادم الشركة. لا حاجة لأي إعداد إضافي.

### الخطوة 5 — التحقق من الإعدادات (اختياري)

```powershell
opencode debug config
```

يعرض هذا الأمر ملف الإعدادات الذي تم تحميله. يجب أن ترى مسار ملف `opencode.json` الخاص بك.

---

### ملاحظات

- **ملف الإعدادات يحتوي على مفتاح API — تعامل معه ككلمة مرور.** لا تشاركه مع أحد، ولا ترفع ملف `opencode.json` إلى أي مستودع git إطلاقاً.
- **الأجهزة القديمة جداً** (معالجات قبل 2013 بدون AVX2): إذا تعطل OpenCode عند التشغيل، أعد الخطوة 1 باستخدام `opencode-windows-x64-baseline.zip` بدلاً من `opencode-windows-x64.zip` في رابط التحميل.
- **رابط التحميل يجلب دائماً أحدث إصدار**، لذا تبقى هذه التعليمات صالحة مع الوقت.
- سيطلب منك OpenCode الموافقة قبل تعديل الملفات أو جلب الروابط — هذا مقصود ومعدّ مسبقاً.
- لديك مشكلة؟ تواصل مع **شريف**.
