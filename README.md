# Finance Skills for Claude — المحاسب والمدير المالي

مجموعة مجانية من الـ Skills لـ Claude، مكتوبة لعمل المحاسب والمراقب المالي والمدير المالي: من مطابقة البنك اليومية حتى رأي المدير المالي في قرار تمويل أو توظيف.

A free set of Claude Skills for accountants, controllers and CFOs — from the daily bank reconciliation to a CFO-level view on a funding or hiring decision.

---

## ما الموجود هنا

### أولاً: 10 Skills للمحاسب

مرتبة من المهام اليومية البسيطة إلى العمل الذي يجمع نتائج ما قبله.

| # | Skill | ماذا تعمل |
|---|---|---|
| 1 | [bank-reconciliation](skills/bank-reconciliation/SKILL.md) | مطابقة كشف البنك مع دفتر النقدية، وتصنيف البنود غير المطابقة، واقتراح قيود التسوية |
| 2 | [expense-categorization](skills/expense-categorization/SKILL.md) | ترميز الحركات على دليل الحسابات مع معاملة الضريبة ودرجة ثقة لكل سطر |
| 3 | [invoice-data-extraction](skills/invoice-data-extraction/SKILL.md) | استخراج بيانات الفواتير إلى جدول جاهز للإدخال |
| 4 | [fixed-asset-depreciation](skills/fixed-asset-depreciation/SKILL.md) | جدول الأصول الثابتة والإهلاك وقيد الإهلاك الشهري |
| 5 | [journal-entry-prep](skills/journal-entry-prep/SKILL.md) | تجهيز قيود اليومية (استحقاقات، مدفوعات مقدمة، تسويات) للمراجعة |
| 6 | [gl-subledger-reconciliation](skills/gl-subledger-reconciliation/SKILL.md) | مطابقة الأستاذ العام مع الدفاتر المساعدة (عملاء، موردين، مخزون) |
| 7 | [variance-analysis](skills/variance-analysis/SKILL.md) | الفعلي مقابل الموازنة: ما تغيّر، لماذا، وما المطلوب |
| 8 | [cash-flow-forecast-13-week](skills/cash-flow-forecast-13-week/SKILL.md) | توقع التدفق النقدي لـ 13 أسبوعاً |
| 9 | [month-end-close](skills/month-end-close/SKILL.md) | قائمة إقفال نهاية الشهر وفحوصات ميزان المراجعة وسجل الاعتماد |
| 10 | [management-reporting-pack](skills/management-reporting-pack/SKILL.md) | التقرير الإداري الشهري للإدارة أو مجلس الإدارة |

### ثانياً: Skill المدير المالي

| Skill | ماذا تعمل |
|---|---|
| [ai-group-cfo](skills/ai-group-cfo/SKILL.md) | تجعل Claude يعمل كمدير مالي لمجموعة متعددة الشركات والدول: يتحقق من صحة الأرقام قبل تحليلها، يفصل بين الحقيقة والافتراض، يرفع المخاطر دون أن تسأله، ويختم بتوصية وقرار. معها 6 ملفات مرجعية (التوحيد، اقتصاديات الأعمال، النقد والتخطيط، التقييم، المحفظة الاستثمارية، مصادر البحث) يقرؤها Claude فقط عند الحاجة |

---

## طريقة التثبيت

### على claude.ai (الأسهل)

1. نزّل ملف الـ ZIP للـ Skill من مجلد [`zips/`](zips/)، أو `all-skills.zip` لكل المجموعة ثم فك ضغطه لتحصل على ملف ZIP لكل Skill.
2. في claude.ai افتح Settings ← Capabilities، وتأكد أن Code execution مفعّل.
3. من قسم Skills اضغط Upload skill وارفع ملف الـ ZIP كما هو، دون فك ضغطه.

### على Claude Code

انسخ مجلد الـ Skill إلى `~/.claude/skills/` ليكون متاحاً في كل مشاريعك، أو إلى `.claude/skills/` داخل مشروع واحد.

```bash
git clone https://github.com/waleedalsafadi/finance-claude-skills.git
cp -r finance-claude-skills/skills/* ~/.claude/skills/
```

---

## طريقة الاستخدام

لا تحتاج أن تذكر اسم الـ Skill. اكتب طلبك كما تكتبه لزميل، وارفع الملفات، وClaude يختار الـ Skill المناسبة من وصفها:

- "هذا كشف البنك لشهر أكتوبر ودفتر النقدية، طابقهم"
- "صنّف هذه المصروفات على دليل الحسابات المرفق"
- "عندي ميزان مراجعة هالشهر والموازنة، شو أهم الانحرافات؟"
- "بدنا نوظف 3 مطورين، شو أثرهم على الكاش والـ runway؟"

التعليمات داخل الملفات بالإنجليزية لأن Claude يلتزم بها بدقة أعلى، والرد يأتيك بلغتك.

### قبل أن تبدأ

- النتائج مسودات للمراجعة. لا شيء يُرحّل أو يُعتمد دون محاسب أو مدير مالي.
- لا ترفع بيانات عملاء حقيقية إلى أي أداة قبل التأكد من سياسة شركتك في حماية البيانات.
- القواعد الضريبية والتنظيمية تتغير. الـ Skills تطلب من Claude التحقق منها وقت الاستخدام، لكن القرار النهائي يبقى لمختص.

---

## عن الكاتب

وليد الصفدي — CMA, FMVA، ماجستير في إدارة المخاطر المالية. مدير مالي بنظام الساعات (Fractional CFO) لشركات صغيرة ومتوسطة وشركات ناشئة ومنظمات في تركيا وسوريا والخليج، ومؤسس Budget Consultancy and Development.

إذا أردت تطبيق هذه الـ Skills على أنظمة شركتك، أو تدريب فريقك المالي على استخدام الذكاء الاصطناعي في العمل اليومي:

- البريد: walsafadi@budget-cd.com
- واتساب: https://wa.me/message/VWPWRNAYF3D4C1
- الموقع: https://budget-cd.com

---

## License

MIT — free to use, adapt and share. A mention of the source is appreciated.
