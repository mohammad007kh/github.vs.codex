<div dir="rtl">

# 🤖 ساختار پروژه برای ایجنت‌های هوش مصنوعی
### یک قالب ابزار-محور برای Claude Code و OpenAI Codex

> **مطالعه به زبان دیگر:** [English](./README.md)

این مخزن یک پیاده‌سازی مرجع و راهنمای آموزشی است برای ساختاردهی پروژه‌هایی که هم با **Claude Code** و هم با **OpenAI Codex** — بدون تکرار منطق یا وابستگی به یک ابزار — به‌درستی کار می‌کنند.

---

## 🧠 ایده اصلی

اکثر توسعه‌دهندگان زمینه پروژه‌شان را *برای یک ایجنت* می‌نویسند. وقتی ابزار عوض می‌شود، از صفر شروع می‌کنند. این مخزن نشان می‌دهد چطور **یک بار بنویسید** و هر ایجنت هوش مصنوعی اصلی آن را بفهمد.

راز کار: **سه لایه، یک منبع حقیقت.**

---

## 📐 معماری سه‌لایه

| لایه | محتوا | مکان |
|---|---|---|
| **① دانش مشترک** | مستندات، مراجع، قالب‌ها، منطق اصلی | `/docs`، `/scripts`، `/templates` |
| **② گردش‌کارها (مهارت‌ها)** | راهنماهای وظایف قابل‌استفاده مجدد | `.claude/skills/` و `.agents/` |
| **③ تنظیمات ابزار** | تنظیمات اختصاصی هر ایجنت | `.claude/` و `.codex/` |

---

## 🗂️ ساختار کامل پروژه

</div>

```
your-project/
│
├── AGENTS.md                       ← 🌐 منبع حقیقت جهانی (همه ایجنت‌ها)
├── AGENTS.fa.md                    ← 🌐 نسخه فارسی AGENTS.md
├── CLAUDE.md                       ← تنظیمات اختصاصی Claude
├── CLAUDE.fa.md                    ← نسخه فارسی CLAUDE.md
│
├── docs/                           ← مشترک: معماری، تصمیمات، مراجع
├── scripts/                        ← مشترک: اسکریپت‌های build و deploy
├── templates/                      ← مشترک: قالب‌های کد و مستندات
│
├── .claude/
│   ├── settings.json               ← تنظیمات محلی Claude Code
│   ├── settings.fa.json            ← نسخه فارسی (با توضیحات)
│   └── skills/
│       ├── research.md             ← مهارت پژوهش (Claude)
│       └── research.fa.md          ← نسخه فارسی مهارت
│
├── .codex/
│   ├── config.toml                 ← پیکربندی Codex CLI
│   ├── config.fa.toml              ← نسخه فارسی (با توضیحات)
│   └── agents/
│       ├── researcher.toml         ← زیر-ایجنت Codex
│       └── researcher.fa.toml      ← نسخه فارسی زیر-ایجنت
│
└── .agents/
    ├── research.md                 ← مهارت جهانی
    └── research.fa.md              ← نسخه فارسی مهارت جهانی
```

<div dir="rtl">

---

## 📄 دو فایل کلیدی

### `AGENTS.md` — استاندارد جهانی
این **منبع حقیقت** شماست. از اواخر ۲۰۲۵، فایل `AGENTS.md` یک استاندارد باز تحت بنیاد لینوکس (AAIF) است و به‌صورت بومی توسط این ابزارها خوانده می‌شود:

- ✅ OpenAI Codex CLI
- ✅ Claude Code
- ✅ GitHub Copilot CLI (از آگوست ۲۰۲۵)
- ✅ Google Gemini CLI
- ✅ Cursor، Windsurf، Zed، RooCode، Factory، Amp

**چه چیزی بنویسید:** معرفی پروژه، پشته فناوری، تصمیمات معماری، قراردادهای کدنویسی، رویکرد تست، و نحوه سازماندهی مخزن.

### `CLAUDE.md` — تنظیمات اختصاصی Claude
این فایل را **کوتاه نگه دارید**. چون Claude Code هم `AGENTS.md` را می‌خواند، از تکرار محتوا خودداری کنید. فقط برای رفتارهای اختصاصی Claude مثل قوانین فشرده‌سازی، راهنمایی مجوزها یا مسیریابی زیر-ایجنت استفاده کنید.

---

## 🔄 تفاوت‌های فرمت فایل

| جنبه | Claude Code | OpenAI Codex |
|---|---|---|
| فایل دستورالعمل اصلی | `CLAUDE.md` | `AGENTS.md` |
| فرمت ایجنت/مهارت | `.md` (Markdown) | `.toml` |
| فرمت پیکربندی | `settings.json` | `config.toml` |
| سبک فراخوانی | خودکار بر اساس قوانین | مسیریابی صریح |
| محیط اجرا | ترمینال محلی | sandbox ابری (ناهمزمان) |
| AGENTS.md می‌خواند؟ | ✅ بله (از ۲۰۲۵) | ✅ بله (فایل اصلی) |

---

## ⚡ ترفند انتقال نشست

اگر یک ایجنت گیر کرد یا می‌خواهید در میان کار ابزار عوض کنید:

۱. از ایجنت فعلی بخواهید: *«یک خلاصه نشست تولید کن شامل: وضعیت فعلی، فایل‌های تغییریافته، و مراحل بعدی.»*
۲. خروجی را کپی کنید.
۳. آن را به‌عنوان اولین پیام در ایجنت دیگر paste کنید.

هیچ زمینه‌ای از دست نمی‌رود. هیچ شروع مجددی لازم نیست.

---

## 🚀 دستور تبدیل سریع

پروژه Claude Code دارید و می‌خواهید پشتیبانی Codex اضافه کنید؟ این دستور را داخل Codex اجرا کنید:

</div>

```
این پروژه را در Claude Code ساختم و می‌خواهم در Codex هم کار کند.
پروژه را بررسی کن و فایل‌های آداپتور Codex لازم را بساز.
یک AGENTS.md بر اساس CLAUDE.md بساز، یک .codex/config.toml تنظیم کن،
و مهارت‌های موجود را به پوشه .agents/ منتقل کن.
منطق نباید تکرار شود — فقط تطبیق داده شود.
```

<div dir="rtl">

---

## ⚠️ مشکلات رایج

| مشکل | راه‌حل |
|---|---|
| ایجنت دستورالعمل‌ها را در میان نشست نادیده می‌گیرد | فایل‌ها را کوتاه نگه دارید؛ قوانین مهم را بالا بگذارید؛ برای وظایف جدید نشست تازه شروع کنید |
| ارجاعات قدیمی به ساختار پوشه‌ها ایجنت را گمراه می‌کند | ساختار پوشه را با جزئیات مستند نکنید — سریع منسوخ می‌شود |
| تکرار محتوا در AGENTS.md و CLAUDE.md | CLAUDE.md را فقط به‌عنوان اشاره‌گر نگه دارید، نه کپی |
| Codex مهارت‌های شما را پیدا نمی‌کند | محتوای `.claude/skills/` را در `.agents/` آینه کنید |

---

## 📁 فایل‌های این مخزن

| فایل | نسخه انگلیسی | نسخه فارسی |
|---|---|---|
| زمینه جهانی پروژه | [`AGENTS.md`](./AGENTS.md) | [`AGENTS.fa.md`](./AGENTS.fa.md) |
| تنظیمات Claude | [`CLAUDE.md`](./CLAUDE.md) | [`CLAUDE.fa.md`](./CLAUDE.fa.md) |
| مهارت پژوهش (Claude) | [`.claude/skills/research.md`](./.claude/skills/research.md) | [`.claude/skills/research.fa.md`](./.claude/skills/research.fa.md) |
| مهارت پژوهش (جهانی) | [`.agents/research.md`](./.agents/research.md) | [`.agents/research.fa.md`](./.agents/research.fa.md) |
| پیکربندی Codex | [`.codex/config.toml`](./.codex/config.toml) | [`.codex/config.fa.toml`](./.codex/config.fa.toml) |
| زیر-ایجنت Codex | [`.codex/agents/researcher.toml`](./.codex/agents/researcher.toml) | [`.codex/agents/researcher.fa.toml`](./.codex/agents/researcher.fa.toml) |
| تنظیمات Claude Code | [`.claude/settings.json`](./.claude/settings.json) | [`.claude/settings.fa.json`](./.claude/settings.fa.json) |

---

## 🌐 مطالعه بیشتر

- [مشخصات AGENTS.md — بنیاد هوش مصنوعی ایجنتی](https://github.com/agentic-ai-foundation/agents-md)
- [مستندات Claude Code](https://docs.anthropic.com/claude-code)
- [OpenAI Codex CLI](https://github.com/openai/codex)

---

<p align="center">ساخته‌شده برای توسعه‌دهندگانی که نمی‌خواهند به یک ابزار وابسته باشند.</p>

</div>
