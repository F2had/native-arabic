# Accessibility text: describe, do not translate

Accessibility text is the text a person hears or reads in place of something they cannot see or hear: alt text, the accessible name of a control, link text, a spoken announcement, a form hint, a caption. A screen reader reads it aloud, often with no other context. A speech-input user says it to operate the control.

Write it from what the element is and does on this screen, not from the English attribute. An English `aria-label="Trash icon"` or `alt="Image of a chart"` is often wrong in English too. Translating it word for word keeps the mistake and adds a calque.

The project preferences in SKILL.md apply here too. With the defaults (verbal noun, unknown gender), an accessible name is a verbal noun phrase: «حذف الملف», not «احذف الملف» and not «يحذف الملف». A verb gives the reader a gender. A verbal noun shows no gender for the reader, and it needs no agreement with a subject.

## 1. Alt text by image type

First decide what the image does on the page. The same picture needs different alt text in different places.

| Image type | What the alt says | Example |
| --- | --- | --- |
| Decorative (adds nothing a reader needs) | Empty: `alt=""`. Never leave out the attribute, or some screen readers read the file name. | A background pattern, a divider, an illustration beside a heading that says the same thing |
| Informative (a photo or picture that carries content) | The meaning the image gives on this page, in one or two short sentences | «طبيبة تقيس ضغط الدم لمريض في غرفة الفحص.» |
| Functional (the only content of a link or a button) | The action or the destination, not the picture | A magnifier in a search button: «بحث». A printer icon link: «طباعة الفاتورة». |
| Logo | Alone in a link: the product name and the destination. Next to visible product name: `alt=""`. | «{product name}، الصفحة الرئيسية» |
| Image of text | The text itself, word for word | A banner that says «الحجز مفتوح حتى نهاية الشهر» gets that sentence |
| Chart or graph | The finding the chart is there to show. Put the full data in a table or a linked text near it. | «تضاعفت مصروفات السفر في سبتمبر مقارنة بمتوسط الأشهر الستة السابقة.» |
| Profile photo | Next to the visible name: `alt=""`. Alone: the person's name. | «يوسف» |
| Cover or thumbnail | Next to the visible title: `alt=""`. Alone: what it is and its title. | «غلاف كتاب "تاريخ المدن"» |

**Arabic form.**
- Write a noun phrase or a short sentence. Do not address the reader.
- Do not start with «صورة لـ» or «رسم يوضح». The screen reader already says that it is an image.
- Do not repeat the text that is next to the image. Do not use a file name or a link address.
- End a full sentence with a full stop, so the voice pauses before the next element.

Pairs:
- Bad: «صورة لرجل يحمل كتابًا» → Good: «قارئ يستعير كتابًا من مكتب الإعارة.»
- Bad: «أيقونة طابعة» (inside a link) → Good: «طباعة الفاتورة»
- Bad: «رسم بياني شريطي للمصروفات» → Good: «تجاوزت مصروفات الضيافة الميزانية في الربع الثالث.»

## 2. Accessible names for icon buttons and controls

This covers `aria-label`, `aria-labelledby`, and the label properties of native mobile controls.

1. **Name the purpose, not the shape.** «حذف الملف», not «أيقونة سلة المهملات». «مشاركة الحجز», not «سهم منحنٍ».
2. **Do not put the role or the state in the name.** The screen reader adds the role and the state itself, with words such as «زر» or «محدد». The exact words differ between screen readers and their language packs. «زر الحذف» is read as «زر الحذف، زر». Give a toggle state with the state attribute (`aria-pressed`, `aria-expanded`, `aria-checked`), not with a second name.
3. **Give a toggle its state one way only.** Keep the name the same in both states and set `aria-pressed` («كتم الصوت»), or change the name («كتم الصوت» / «إلغاء كتم الصوت») with no `aria-pressed`. Do not change the name and also set `aria-pressed`. Use one of the two.
4. **Start with the visible text, then add the word that tells the controls apart.** Keep the name short. One to three words is usually enough.
5. **Make names unique in a list.** Ten rows with a «حذف» button give ten identical names. Add the object: «حذف الملف: عقد الإيجار»، «حذف الملف: فاتورة المورد».
6. **Do not tell the reader how to operate it.** No «انقر نقرًا مزدوجًا للفتح» and no «اضغط هنا». The device and the screen reader give these instructions, and the gesture differs by device.
7. **Start the name with the visible text.** A speech-input user says the words on the screen. If the button shows «إرسال», then «إرسال الطلب» works and «تقديم الطلب» does not. If the control shows a tooltip, the name matches the tooltip.
8. **Prefer visible text to a hidden name.** A hidden name is easy to forget when the visible label changes, and the two then disagree.
9. **Spell out symbols.** «الحجوزات والمواعيد», not «الحجوزات & المواعيد». «إضافة ملف», not «+ ملف».

**Help text** that tells the reader how to operate a control uses verbs that fit every input. «الضغط على» and «اختيار» fit touch, a keyboard, a switch and a voice. «النقر على» fits only a pointer.

Pairs:
- Bad: «زر الحذف» → Good: «حذف الموعد»
- Bad: «أيقونة الجرس» → Good: «الإشعارات»
- Bad: «اضغط لإغلاق النافذة» → Good: «إغلاق»
- Bad: «يعرض كلمة المرور» → Good: «إظهار كلمة المرور» (with `aria-pressed`)

## 3. Link text

- The link text alone tells the reader where it goes. Screen-reader users often move from link to link with no surrounding text.
- Two links with the same text go to the same place. Different destinations need different text.
- Put the important words inside the link, not before it.
- Do not use «اضغط هنا», «هنا», «المزيد» or «اعرف المزيد» as the whole link.
- When a design repeats a short visible link («التفاصيل»), give each one a full name that starts with the visible word: «التفاصيل: حجز 14 أكتوبر».
- Say when a link downloads a file or opens a new window, in words: «تنزيل الفاتورة (ملف بي دي إف، 2 ميغابايت)»، «سياسة الإلغاء (تُفتح في نافذة جديدة)».

Pairs:
- Bad: «لعرض سجل الاستعارة اضغط هنا» → Good: «عرض سجل الاستعارة»
- Bad: «المزيد» (under each clinic) → Good: «مواعيد عيادة الأسنان»

## 4. Form labels, hints and errors

- **A label for every field.** Link it to the field in code. A placeholder is not a label: it disappears when the reader types, and some screen readers do not read it.
- **Required status in the label text.** «رقم الهاتف (مطلوب)». An asterisk alone is read as «نجمة», or not at all.
- **The format in a hint.** Put it in a separate element linked as the field's description. The screen reader reads it after the label. «الشهر ثم السنة، مثل 09/2027». A slash inside a format mask is acceptable, because it shows the exact characters to type; the slash rule in section 8 is for "or" in running text.
- **General instructions before the form**, not after the submit button.
- **An error names the field, says what is wrong, and gives the fix** (rule 10 in SKILL.md). Do not show an error by colour alone; say it in words next to the field, and announce it.
  - Bad: «إدخال غير صالح» → Good: «تاريخ الانتهاء غير مكتمل. يُرجى إدخال الشهر والسنة، مثل 09/2027.»
- **No gender in labels and errors** with the default: «يجب إدخال رقم الهاتف», not «أدخل رقم هاتفك». Use the attached pronoun once, or drop it: «رقم الهاتف», not «رقم الهاتف الخاص بك».

## 5. Live announcements

A live announcement tells the screen reader about a change without moving the focus: a search result count, a saved form, a file upload, an error.

| Message type | Region | Example |
| --- | --- | --- |
| Result or success | `role="status"` (polite: waits for the voice to finish) | «حُفظت التغييرات.» |
| Error or urgent warning | `role="alert"` (interrupts) | «تعذّر رفع الملف لأن حجمه أكبر من 10 ميغابايت.» |
| A sequence of messages | `role="log"` | Messages in a chat, steps of an import |
| Progress | `role="status"` with short, spaced updates | «اكتمل رفع ثلاثة ملفات من خمسة.» (a count string: write all six forms, rule 7 in SKILL.md) |

- Keep each announcement to one short sentence. The listener hears it once and cannot scroll back.
- Do not announce every keystroke or every percent of progress. Announce the result, or a few steps.
- **A count announcement is a full sentence in six forms** (rule 7 in SKILL.md). It is heard, not seen, so a wrong form is louder than on screen.

```
{count, plural,
  zero  {لا توجد نتائج مطابقة.}
  one   {توجد نتيجة واحدة مطابقة.}
  two   {توجد نتيجتان مطابقتان.}
  few   {توجد # نتائج مطابقة.}
  many  {توجد # نتيجة مطابقة.}
  other {توجد # نتيجة مطابقة.}
}
```

## 6. Headings, landmarks and page title

- **Page title:** what is on the page first, then the product: «الحجوزات القادمة - {product name}». Each page gets its own title.
- **Headings:** one main heading per page, then levels in order. A heading names the section in a few words. Do not use a heading only to make text big.
- **Landmarks:** give a name only when the page has two or more landmarks of one type. Keep the name short and do not repeat the role: `<nav aria-label="الرئيسية">` and `<nav aria-label="إعدادات الحساب">`, not «قائمة التنقل الرئيسية», because the screen reader usually announces the role. When the region has a visible heading, point to it with `aria-labelledby` instead.

## 7. Captions and transcripts

- **Captions** give all the sound a viewer needs: the speech, who speaks when it is not clear, and the sounds that matter. **Subtitles** translate the speech only. A video for a deaf viewer needs captions.
- Write captions in Modern Standard Arabic, as the rest of this skill does. By default, when the speaker uses dialect, caption the meaning in plain standard Arabic, unless the project asks for verbatim captions.
- Put a sound in square brackets, as a short noun phrase: «[رنين الهاتف]»، «[تصفيق]». Mark music with ♪ at the start and the end of the line, on screen only: captions are read by the eye, so the symbol rule in section 8 does not apply.
- Name a speaker who is off screen: «سلمى: ...», or the speaker tag of the caption format.
- Keep two lines per caption. A common guide is about 42 characters per line and about 20 characters per second; follow the platform's own limits.
- Write the numbers one to ten as words, and higher numbers as digits.
- Use «،» and «؟» with no space before them. Do not combine «؟!».
- Spell out a known acronym the first time: «منظمة الصحة العالمية», not «WHO».
- Information that is only visual (a chart, text on screen, an action with no sound) needs a spoken description or a text transcript.

## 8. How screen readers read Arabic

Speech engines differ in quality, and some are much weaker in Arabic than others. Write so the text has one reading on every engine.

**Tashkeel.** Most Arabic has no short vowels, so the engine guesses them. One spelling can be several words (كتب: "he wrote", "it was written", "books"), and the engine guesses wrong often.
- Change the words until the sentence has one reading. Do not depend on the engine.
- A passive written without marks is often read as active. Use an active sentence with the actor («رفض المدير الطلب»), a form with its own letters («تم رفض الطلب»), or one distinguishing mark («رُفض الطلب»).
- Add one mark only where a word is truly ambiguous (rule 19 in SKILL.md). Do not vocalise all UI copy. Some screen readers skip marks when they read letter by letter.

**Latin words and acronyms.**
- An accessible name is usually read with one voice. A Latin word in it can be read with the Arabic voice or spelled letter by letter. In a name with no visible text, use the Arabic word or write it in Arabic letters: «تصدير بصيغة بي دي إف». When the visible label shows the Latin word, keep it, because the name starts with the visible text.
- In body text, mark each Latin run: `<span lang="en" dir="ltr">PDF</span>`. Many screen readers switch to an English voice when one is installed and language switching is on.
- An acronym can be read as a word or letter by letter, and engines differ. Give the full form once, or write the letters in Arabic: «رسالة نصية» or «إس إم إس».
- A name or a term already used in Arabic needs no language mark.

**Digits and counts.**
- Use one digit set across the product (rule 15 in SKILL.md).
- The engine must guess gender and case for a counted noun after a digit, and it guesses wrong often. In a key sentence, write 1, 2 and 3–10 as words: «مهمتان»، «ثلاث مهام»، «خمسة أيام».

**Dates and times.**
- «12/10/2026» can be read as numbers or as a date, in either order. Write the month as a word: «12 أكتوبر 2026».
- Write «هجري» or «ميلادي» in full where both calendars can appear.
- In text that is heard, write «صباحًا» and «مساءً» in full. «ص» and «م» alone can be read as letters.

**Currency and percent.**
- Write the currency name as a word after the amount. A symbol, a code or an abbreviation with dots is often not in the engine's dictionary, so it is read as letters or skipped.
- Write «في المئة», or use the Latin «%». The Arabic percent sign «٪» is not known to every engine.

**Symbols and emoji.**
- Do not use an emoji, an arrow or a coloured shape to carry meaning. An emoji is read by its Unicode name, which can be long or misleading (✅ is "check mark button"). Give the status in words: «مكتمل»، «متأخر».
- Hide decorative icons from the screen reader (`aria-hidden="true"`).
- Do not use «/» for "or": «الحجز أو الموعد», not «الحجز/الموعد». Some engines read the slash aloud.
- Spell out «&», «+», «~» and «@» in Arabic text.

**Punctuation and pauses.**
- Use «،» and «؟» in Arabic text. Both give a pause.
- End each sentence with a full stop. Without it, the voice runs on into the next element.
- Do not use tatweel («ـ») to stretch a word. It can break the word for the engine.
- Keep sentences short. A weak voice gives few pauses inside a long sentence.

**Abbreviations.** Write «صفحة» in place of «ص». Write «الدكتور» or «الدكتورة» in place of «د.» only when the product knows the gender. If not, use the title from the visible text, or leave the title out. Arabic abbreviations with dots are read as letters or expanded wrongly.

**`lang`, `dir` and reading order.**
- Set `<html lang="ar" dir="rtl">` on every Arabic page. Without `dir`, the screen shows mixed text and punctuation in the wrong order. `lang` lets the screen reader select an Arabic voice.
- Screen readers read the order of the code, not the order on screen. Never reverse a string, and never use CSS `order` or `row-reverse` to put RTL content in place. The screen then shows one order and the voice reads another.
- Wrap a user name or a value of unknown direction in `<bdi>`. It fixes the display and does not change what is read.
- Direction marks (LRM, RLM) and isolates are usually silent in normal reading. They do not fix a wrong order in the code.

## 9. Words about disability

Mention a disability only when it is relevant. Put the person first, and use a neutral word: «شخص ذو إعاقة»، «المستخدمون ذوو الإعاقة البصرية»، «مستخدمو قارئ الشاشة». Do not use «يعاني من», «مصاب بـ» or «معاق».

## 10. Check it by ear

Read the text aloud as a screen reader would, with the role and the state it adds. «حذف الملف: عقد الإيجار، زر» is clear. «زر الحذف، زر» is not. When a string is important, test it with a real screen reader in Arabic.
