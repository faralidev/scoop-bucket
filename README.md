# scoop-bucket

مخزن Scoop برای اکوسیستم زبان برنامه‌نویسی فارسی «کولنگ» (Kolang).

این مخزن شامل مانیفست‌های Scoop برای نصب این ابزارها در ویندوز است:

| مانیفست | توضیح |
| --- | --- |
| `kolang` | مفسر زبان برنامه‌نویسی کولنگ |
| `kolang-linter` | لینتر زبان برنامه‌نویسی کولنگ |
| `kolang-ide` | ویرایشگر دسکتاپ (Electron) برای کولنگ |

## نصب

ابتدا Scoop را نصب کنید (اگر هنوز نصب نشده است):

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
irm get.scoop.sh | iex
```

سپس این باکت را اضافه کرده و ابزارها را نصب کنید:

```powershell
scoop bucket add faralidev https://github.com/faralidev/scoop-bucket
scoop install kolang
scoop install kolang-linter
scoop install kolang-ide
```

## مانیفست‌ها چگونه کار می‌کنند؟

همه‌ی مانیفست‌ها از **باینری‌های آماده (پیش‌ساخته)** منتشرشده در GitHub Releases استفاده می‌کنند — هیچ مرحله‌ی ساخت یا کامپایل در کار نیست.

- فایل‌های ZIP از آدرس‌های انتشار (Releases) گیت‌هاب دانلود می‌شوند.
- هیچ‌گونه نیاز به Go Toolchain یا ابزار ساخت دیگری نیست.
- مانیفست فقط فایل ZIP را دانلود، استخراج و نصب می‌کند.

این یعنی برای انتشار نسخه‌ی جدید فقط کافی است یک Release در گیت‌هاب بسازید که شامل فایل‌های ZIP ویندوزی باشد.

## به‌روزرسانی

بعد از هر Release جدید در گیت‌هاب:

۱. شماره‌ی نسخه را در مانیفست‌های داخل پوشه‌ی `bucket/` تغییر دهید (مثلاً از `۰٫۰٫۱` به `۰٫۰٫۲`).

۲. تغییرات را کامیت و پوش کنید.

۳. باقی کارها را Scoop انجام می‌دهد — بلوک‌های `checkver` و `autoupdate` در هر مانیفست، نسخه‌ی جدید را شناسایی و آدرس دانلود را به‌صورت خودکار به‌روزرسانی می‌کنند:

```powershell
scoop update kolang
scoop update kolang-linter
scoop update kolang-ide
```

## نسخه

همه‌ی مانیفست‌ها در نسخه‌ی `۰٫۰٫۱` هستند.

## مجوز

این مخزن تحت مجوز MIT منتشر شده است (فایل `LICENSE` را ببینید).

---

## English

A Scoop bucket for the Kolang Persian programming language ecosystem. Install with:

```powershell
scoop bucket add faralidev https://github.com/faralidev/scoop-bucket
scoop install kolang
scoop install kolang-linter
scoop install kolang-ide
```

Manifests use **prebuilt binaries** from GitHub Releases — no build step. After publishing a new release, bump the `version` in the manifests under `bucket/`; the `checkver` and `autoupdate` blocks handle the rest.

- Version: `0.0.1` (all manifests)
- License: MIT