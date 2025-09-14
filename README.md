# پروژه درس هوش مصنوعی

این مخزن برای پروژه درس هوش مصنوعی ساخته شده است که شامل دو زیر مخزن فاز یک (سگمنت‌کردن تصاویر هوایی و ساخت Mask جاده‌ها) و فاز دو (یادگیری تقویتی با الگوریتم Soft Actor Critic و راه‌رفتن یک سگ) می‌باشد.

## اطلاعات پروژه

### اعضای گروه

- [امیرمهدی طهماسبی](https://github.com/ta-tahmasebi) (۴۰۲۱۰۶۱۷۸)
- [امیرحسین محمدزاده](https://github.com/ahmz1833) (۴۰۲۱۰۶۴۳۴)
- [محمدنوید آتشین‌بار](https://github.com/NavidATB) (۴۰۲۱۰۵۵۸۱)

### ترم تحصیلی و مدرس

این پروژه برای ترم تحصیلی بهار ۱۴۰۴ (۱۴۰۳۲) و در تابستان ۱۴۰۴ انجام شده است.

#### **مدرس: دکتر تن‌قطاری**

## فاز اول پروژه

### هدف

در این فاز، هدف بخش‌بندی معنایی (Semantic Segmentation) تصاویر هوایی برای استخراج ماسک دقیق جاده‌ها بود. این کار یکی از مسائل اساسی در زمینه پردازش تصاویر ماهواره‌ای و سیستم‌های نقشه‌برداری خودکار است. برای این منظور، از معماری قدرتمند **UNet** استفاده کردیم.

| نمونه خروجی‌های مدل | |
| :---: | :---: |
| <img src="https://raw.githubusercontent.com/ta-tahmasebi/RoadNet/refs/heads/main/images/loss_plot.png" width="100%"/> | <img src="https://raw.githubusercontent.com/ta-tahmasebi/RoadNet/refs/heads/main/images/i5.png" width="100%"/> |
| <img src="https://raw.githubusercontent.com/ta-tahmasebi/RoadNet/refs/heads/main/images/i1.png" width="100%"/> | <img src="https://raw.githubusercontent.com/ta-tahmasebi/RoadNet/refs/heads/main/images/i2.png" width="100%"/> |
| <img src="https://raw.githubusercontent.com/ta-tahmasebi/RoadNet/refs/heads/main/images/i3.png" width="100%"/> | <img src="https://raw.githubusercontent.com/ta-tahmasebi/RoadNet/refs/heads/main/images/i4.png" width="100%"/> |


### رویکرد

سه نسخه مختلف از این معماری پیاده‌سازی و نتایج آن‌ها با یکدیگر مقایسه شد:

<div dir="rtl">
<ol dir="rtl">
  <li>
    <b>UNet معمولی (Vanilla UNet):</b> پیاده‌سازی پایه‌ی معماری UNet.
  </li>
  <li>
    <b>Attention UNet:</b> افزودن مکانیزم توجه (Attention Gates) برای تمرکز شبکه روی نواحی مهم‌تر تصویر.
  </li>
  <li>
    <b>Residual UNet:</b> در این نسخه، بلوک‌های کانولوشنی استاندارد با <b>بلوک‌های باقی‌مانده (Residual Blocks)</b> جایگزین شدند؛ که شامل Skip Connection هستند. این کار به بهبود جریان گرادیان در طول شبکه کمک کرده و امکان آموزش مدل‌های عمیق‌تر بدون مشکل محو شدگی گرادیان (Vanishing Gradient) را فراهم می‌کند.
  </li>
</ol>
</div>

### ویدئوی ارائه

در ویدیوی زیر، توضیحات کلی معماری UNet، تابع زیان استفاده شده، کاربردهای دیگر آن و نقش Skip-Connection ها به طور کامل توضیح داده شده و کد پروژه مرور می‌شود:

[لینک به گوگل درایو](https://drive.google.com/drive/folders/1O-__YnY3zfOrR-QeRyhTsEkUzPzxL8RA?usp=sharing)

## فاز دوم پروژه

### هدف

فاز دوم پروژه به یادگیری تقویتی (Reinforcement Learning) اختصاص دارد. در این فاز، الگوریتم **Soft Actor-Critic (SAC)** برای آموزش راه رفتن به یک ایجنت **HalfCheetah** در محیط شبیه‌سازی شده `Gymnasium` با موتور فیزیک `MuJoCo` به کار گرفته شد.

<table width="100%">
  <tr>
    <td width="33%">
      <img src="https://raw.githubusercontent.com/ta-tahmasebi/SAC-RL/refs/heads/main/images/3.png" alt="Learn" width="100%">
    </td>
    <td width="33%">
      <img src="https://raw.githubusercontent.com/ta-tahmasebi/SAC-RL/refs/heads/main/images/1.png" alt="Score" width="100%">
    </td>
    <td width="33%">
      <img src="https://raw.githubusercontent.com/ta-tahmasebi/SAC-RL/refs/heads/main/images/2.png" alt="Score" width="100%">
    </td>
  </tr>
</table>

<table width="100%">
  <tr>
    <td width="33%">
      <video src="https://github.com/user-attachments/assets/85caa14a-83f8-47e9-b707-d59fff0da897" width="100%" controls></video>
    </td>
    <td width="33%">
      <video src="https://github.com/user-attachments/assets/61f68d6d-ee64-4026-9fcf-f4ea1a711224" width="100%" controls></video>
    </td>
    <td width="33%">
      <video src="https://github.com/user-attachments/assets/2f9e1a6e-e378-488b-91ed-e87c68370ae2" width="100%" controls></video>
    </td>
  </tr>
  <tr>
    <td width="33%">
      <video src="https://github.com/user-attachments/assets/18e72682-ea92-4fbe-a492-1074723e9436" width="100%" controls></video>
    </td>
    <td width="33%">
      <video src="https://github.com/user-attachments/assets/4b0875d2-6b8c-44b8-99d1-0657f1d5f086" width="100%" controls></video>
    </td>
    <td width="33%">
      <video src="https://github.com/user-attachments/assets/0ab9726b-de3a-4879-8417-f89a6c8e176a" width="100%" controls></video>
    </td>
  </tr>
</table>

### رویکرد

الگوریتم SAC به عنوان یک الگوریتم **Off-Policy** و مبتنی بر **Maximum Entropy**، برای وظایف کنترلی با فضای عمل پیوسته (Continuous Action Space) بسیار مناسب است. هدف ایجنت، یادگیری سیاستی (Policy) است که هم پاداش تجمعی را ماکزیمم کند و هم انتروپی (تصادفی بودن) رفتار خود را، که منجر به کاوش بهتر و پایداری بیشتر می‌شود.

**معماری شبکه‌ها:**

<div dir="rtl">
<ul dir="rtl">
  <li>
    <b>Actor (Policy Network):</b> یک شبکه عصبی پیشخور (MLP) که وضعیت (State) را به عنوان ورودی دریافت کرده و پارامترهای یک توزیع گوسی (میانگین و انحراف معیار) را برای فضای عمل خروجی می‌دهد.
  </li>
  <li>
    <b>Critic (Q-Networks):</b> از تکنیک <b>Clipped Double Q-Learning</b> با دو شبکه Q مجزا برای کاهش بیش‌تخمینی (Overestimation) مقادیر Q استفاده شد. هر دو شبکه نیز MLP هستند.
  </li>
</ul>
</div>


**فرآیند آموزش:**

<div dir="rtl">
<ul dir="rtl">
  <li>
    <b>Replay Buffer:</b> تجربیات ایجنت در یک حافظه ذخیره شده و در هر مرحله از آموزش، یک بچ (Batch) تصادفی از آن برای به‌روزرسانی شبکه‌ها نمونه‌گیری می‌شود.
  </li>
  <li>
    <b>به‌روزرسانی پارامترها:</b> شبکه‌های Actor، Critic و پارامتر دمای انتروپی (α) به صورت متناوب با استفاده از بهینه‌ساز Adam آپدیت می‌شوند.
  </li>
</ul>
</div>


### ویدئوی ارائه

در این ویدیو، الگوریتم SAC، نقش انتروپی در تابع هدف، مفهوم اپراتور بلمن soft و جزئیات پیاده‌سازی پالیسی و توابع Q به طور کامل شرح داده شده است.

[لینک به گوگل درایو](https://drive.google.com/drive/folders/1YTZiOaZV2pDgBDafB7sCj0g5Lixa63-a?usp=sharing)
