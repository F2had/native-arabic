---
name: native-arabic
description: >-
  Write Arabic that reads as if a native professional wrote it in Modern Standard Arabic, not as if
  someone translated it from English. Use this whenever you write, edit, review or fix Arabic that a
  person will read, even a single word or a status label. That covers UI strings and button labels,
  locale files (ar.json, lang/ar/*.php, *.ar.yml), error messages, empty states, notifications, help
  text and articles, emails, narration and video scripts, and formal letters. It also covers
  accessibility text: alt text, aria-label and other accessible names, screen-reader text, live
  announcements and captions. It covers count strings and plural rules, and reviews of Arabic copy
  someone else wrote. Use it even when the request does not say "Arabic style" and you are only
  "translating a string" or "fixing a label". Do not use it when you only quote, search, grep,
  transliterate or read back Arabic that already exists.
---

# Native Arabic

Arabic that is translated word for word is correct on the surface and wrong to a native reader. It copies English word order, English noun stacks and English metaphors. This skill stops that, without changing what the text means.

The target register is correct Modern Standard Arabic as a native professional writes it: plain, not ornate, and never dialect. It avoids rare or showy words, even correct ones, and it never drops to slang. A form that is grammatical and in normal professional use is not an error. Do not "correct" it.

This skill works alone. When they are available, use it first (what to say), then `ux-writing-arabic` (microcopy patterns), then `arabic-design` (fonts, RTL, bidi, diacritics clipping).

## Preferences to settle first

Three choices are project preferences, not rules. Settle them once per project, before you write.

1. **Look for the convention.** Read the project's locale files: its button labels, its step text, and any copy about a person.
2. **If the convention is clear, follow it.** Do not ask.
3. **If it is not clear, ask the user once.** Show both forms with a real example from the task.
4. **Record the answer** where the project keeps instructions (its instruction file, such as CLAUDE.md, or its memory), so nobody asks again.

The questions:

- **Instructions to the reader: imperative or verbal noun?** This covers buttons, steps, menus, tooltips, the fix in an error message, and help text. «افتح الملف» / «فتح الملف»; «احفظ» / «حفظ»; «حاول مرة أخرى» / «يُرجى المحاولة مرة أخرى». The imperative is direct, but it addresses the reader as a man. The verbal noun shows no gender. Steps in verbal nouns need a lead-in line, such as «يمكنك اتباع الخطوات التالية:».
- **Does the product know the reader's gender?** Many products do not store it. To use it, the product needs a gender field in the profile and a second string for each string that inflects for the reader.
- **Does the product know the gender of the people it names?** «اعتمدت هالة المصروف» needs to know that Hala is a woman. The cost is the same: a stored gender for each person, and a second string for each string that inflects for that person.

When you cannot ask, use these defaults: the verbal noun in every instruction to the reader; the product knows neither gender, so use rule 12.

## The method

1. **Decide what the thing is.** Name the job of the text: a button that starts an action, a state, an error, an empty state. Establish the facts the words depend on: who sees a comment, what a list holds, which deadline counts, whether an action moves a thing or only points to it. Find out what fills each placeholder, because agreement depends on the value.
2. **Write it as a person would say it.** Write that job in Arabic from scratch, not from the English sentence or its nouns. You may split, join and reorder. Drop a part only when it is truly redundant. A word-for-word version reads as unnatural, and sometimes as absurd.
3. **Keep the meaning.** Compare the Arabic with the source for obligation, permission, exceptions, limits, timing, uncertainty, the actor, and who sees the result. Check each "must", "may", "only", "unless" and "up to". «لا يلزم إرفاق الإيصال» (not required) and «يجب عدم إرفاق الإيصال» (must not) are different instructions.
4. **Check it.** Run the self-check below. Read the sentence once as a native reader would.

## Rules

Each rule has a short reason and one pair. More pairs are in `references/calques.md`. A rule marked **preference** is a style choice: apply it when the shorter form keeps the meaning.

### 1. Translate the intent, not the words

For an idiom, translate what it means. Empty states fail most often.

- "You're all caught up." Bad: «أنت ملحق بكل شيء» → Good: «لا توجد إشعارات جديدة»
- Bad: «لا حجوزات لك الآن» → Good: «ليس لديك حجوزات الآن»
- Bad: «ما يُرفع إلى هذا المجلد يظهر هنا» → Good: «تظهر هنا الملفات التي تُرفع إلى هذا المجلد»

### 2. Use the everyday word, not the stiff one

Write the word a professional uses at work: clear, friendly and short. A rare word is stiff even when it is correct. Everyday words such as «الدوام» and «القادم» are correct.

- «إلغاء» and «حذف» differ: «إلغاء الحجز» stops the booking and keeps its record; «حذف الحجز» removes the record.
- «خلال» for a period is normal professional Arabic: «يصل الطلب خلال يومين». Do not flag it.
- Stiff: «يتسنى لك تغيير كلمة المرور من الإعدادات» → Plain: «يمكنك تغيير كلمة المرور من الإعدادات»

### 3. Use the verb itself, not قم بـ + verbal noun (preference)

قم بـ and قام بـ are often padding. قام بـ + verbal noun is grammatical, so it is not an error.

- Stiff: «قم بتنزيل الفاتورة» → Plain: «تنزيل الفاتورة» (or «نزّل الفاتورة» where the project uses the imperative)

### 4. Prefer a real verb to يتم / تم + verbal noun (preference)

تمّ means "was completed", so a chain of يتم + verbal noun says less than a real verb. It is grammatical and common in UI, so it is not an error.

- Stiff: «يتم تجهيز الطلب ويتم شحنه خلال يومين» → Plain: «يُجهَّز الطلب ويُشحن خلال يومين»

When the actor is known and matters, an active sentence is usually clearer: «أُلغي الموعد من قِبَل الطبيب» → «ألغى الطبيب الموعد». A passive with «من قِبَل» is a translation habit, but it keeps the topic first. Keep it when that focus matters.

### 5. Prefer the attached pronoun to الخاص بك (preference)

Keep الخاص بك when it marks a needed contrast of owner, or when the attached pronoun makes the phrase unclear.

- Stiff: «الحجوزات الخاصة بك» → Plain: «حجوزاتك»

### 6. Give each noun its own genitive (preference)

Two heads on one genitive copies the English "X and Y of Z".

- Stiff: «تعديل وحذف المواعيد» → Plain: «تعديل المواعيد وحذفها»

### 7. Write a count as a full sentence for each of six forms

ICU and `Intl.PluralRules` sort an Arabic number into six categories: zero, one, two, few, many, other. The category only selects the branch. The grammar of each branch depends on the sentence, so write each branch as a full sentence. A count phrase is not a noun you can put into a fixed sentence: «لا حجوزات» in «لديك {count} هذا الأسبوع.» reads «لديك لا حجوزات هذا الأسبوع». In prose, zero is a negative sentence, one is a word, two is the dual: not «0 ضيوف», «1 ضيف» or «2 ضيوف».

- Good: «لم يحضر أي ضيف» / «حضر ضيف واحد» / «حضر ضيفان» / «حضر 3 ضيوف» / «حضر 11 ضيفًا» / «حضر 100 ضيف»

A verb before its subject stays singular («حضر ثلاثة ضيوف»). A verb after its subject agrees with it («الضيوف حضروا»). Digits are fine for 3 and up, and in compact UI (badges, counters, tables). Remove repetition that the count phrase already carries, and keep the meaning: «نُقلت إلى مجلدك 3 ملفات من ملفات العميل» → «نُقلت إلى مجلدك 3 من ملفات العميل». Decimals, measures and the ICU skeleton are in `references/grammar.md`.

### 8. Use the dual when the thing is two, in the right case

- Bad: «مرفقات» (for exactly two attachments) → Good: «مرفقان»
- «مرفقان» is a label or a subject. As an object or after a preposition: «تنزيل المرفقين», not «تنزيل المرفقان».

### 9. Present for a general result; future for a real future event

Keep the future for an event that is certain to happen: «سنرسل إليك تذكيرًا قبل الموعد بساعة». Keep it for the result of a condition: «إذا أُلغي الحجز، فلن يُسترد العربون».

- Stiff: «في حالة تأخر الشحنة، ستحتاج إلى التواصل مع خدمة العملاء.»
- Good: «إذا تأخرت الشحنة، فيُرجى التواصل مع خدمة العملاء.»

### 10. Say what failed and what to do next, without blame

An error message is short and friendly, has no technical words, and gives one action the reader can take. When the fault is the system's, say so: «عذرًا، تعذّر تحميل الصفحة.» Never put the blame on the reader. Openings such as «تعذّر …»، «فشل …»، «لم يُعثر على …» work well.

- Bad: «لقد أخطأت في إدخال التاريخ» → Good: «تاريخ الميلاد غير صحيح. يُرجى إدخاله بالصيغة يوم/شهر/سنة.»

### 11. Choose the form of address by channel

In product UI, speak to one reader as أنت and refer to the organisation as نحن: «لم نتمكن من العثور على الصفحة المطلوبة.» In formal letters, use the plural of respect: «نأمل تزويدنا بملاحظاتكم», not «بملاحظاتك».

### 12. Gender

**If the product knows the gender** of the reader or of a named person, agree with it: «اعتمدت المديرة المصروف»، «أرسلت سلمى ردًا». A feminine form overrides only the strings that inflect; every other string stays as below.

**If the product does not know it** (the default), write so that no gender shows. In order of preference:

1. **Verbal noun** in every instruction to the reader: buttons, steps, menus, tooltips, error fixes, help text: «اختيار ملف»، «حفظ التغييرات».
2. **يُرجى / يمكن + verbal noun** in a sentence: «يُرجى التحقق من رقم البطاقة ثم إعادة المحاولة.»
3. **An impersonal clause**: «تعديل الحجز متاح لمن يملك صلاحية التعديل», not «إذا كان المستخدم يملك الصلاحية، فيمكنه تعديل الحجز».
4. **A plural or collective noun** for a group: «الحضور»، «فريق العمل»، «الأشخاص».
5. **A name as a label.** In a details panel: «الموافقة: هالة»، «آخر تعديل: يوسف». In an activity feed: «تمت الموافقة · هالة». Not «وافق {name} على الطلب», which is wrong for a woman's name.
6. **A passive with the reader as object, and the actor as a label**: «تمت الإشارة إليك · مازن». Not «أشار {name} إليك», and not «تمت الإشارة إليك من قِبَل مازن».

When none of these reads naturally, use the masculine generic. It is the accepted default in Arabic: «هل تريد المتابعة؟». Do not use slash pairs («الموظف/ـة») or paired forms («أنتَ أو أنتِ», or the dual «أنتما» for one reader) in running text. Name both genders once at most, in a heading or a job title: «مطلوب محاسب أو محاسبة».

In a tooltip, a verb must also guess the gender of the control (Arabic has no neuter "it"), so use a verbal noun: «ترتيب الملفات حسب التاريخ», not «يرتب الملفات حسب التاريخ».

### 13. One term for one concept

A second word makes the reader ask whether it is a second thing. Where a field has a fixed standard term, use it. If the product says «الحجز», do not say «الموعد» on another screen for the same thing. The term still inflects, and the sentence can change around it: «الحجز»، «الحجوزات»، «حجزك» are one term.

### 14. Drop the English-shaped connectors

- Bad: «صدرت الفاتورة الجديدة والتي تشمل رسوم التوصيل» → Good: «صدرت الفاتورة الجديدة التي تشمل رسوم التوصيل»
- Bad: «كلما زاد عدد الضيوف، كلما ارتفعت التكلفة» → Good: «كلما زاد عدد الضيوف، ارتفعت التكلفة»

### 15. Use Arabic punctuation, straight quotes for UI names, Western digits

Use the Arabic comma (،) and question mark (؟), with no space before them. Arabic has no capital letters, so put a button name in straight double quotes. Write numbers in Western digits. A product with an established «» or Arabic-Indic convention keeps it; do not mix the two in one product.

- Bad: «لحفظ الملاحظة، اضغط حفظ.» → Good: «لحفظ الملاحظة، يُرجى الضغط على "حفظ".»

### 16. Spell the hamza and choose the verb for the control

- Hamzat al-qatʿ: «أدخل»، «أرسل»، «أنشئ»، «إدخال»، «إرسال»، «إنشاء»، «إعادة». Hamzat al-wasl: «اختر»، «استخدم»، «انقر»، «اضغط»، «ابحث»، «اختيار»، «استخدام». Not «انشئ»، «ادخل» (for "enter a value"), «إختر»، «إستخدام».
- A value the reader types: «أدخل» / «إدخال». A choice from options: «اختر» / «اختيار» or «حدد» / «تحديد». A button: «اضغط» / «الضغط على», or «انقر» / «النقر على». Prefer «الضغط على» or «اختيار» where touch, keyboard or voice input is possible.
- An action done again: «أعد المحاولة» / «إعادة المحاولة». For "use" or "apply": «استخدم» / «استخدام».

### 17. Let the software act; drop opaque metaphors

Software can be the subject of what it really does: «يرسل التطبيق تذكيرًا»، «يعرض التقويم المواعيد». Do not give it human intentions it does not have («يريد التطبيق…»). Replace an English metaphor that an Arabic reader cannot decode with the concrete thing. When the product has a real timer or real stages, name them plainly: «مدة الحجز المؤقت»، «مراحل التوظيف».

### 18. Know the type of text before you shorten it

- **Button:** names the action, in the form the project chose: «حفظ» / «احفظ». Name the object of a destructive action: «حذف الملف».
- **Status label:** the state of the entity, agreeing with it: «الحجز مؤكد» / «الرحلة مؤكدة», or a phrase: «قيد المعالجة»، «بانتظار الدفع»، «لم يُشحن بعد». Keep «مراجَعة» and «معتمدة» apart when review and approval are separate steps.
- **Success notification:** what happened, in the past: «حُفظت التغييرات» or «تم حفظ التغييرات».
- **Empty state:** what is missing, and what appears here or what to do: «ليس لديك ملفات بعد».
- **Confirmation:** the question names the action and the object; the button repeats the action: «حذف الملف نهائيًا؟» → «حذف» / «إلغاء». «هل تريد حذف الملف؟» is the masculine fallback.
- **Help text and narration:** in help text, quote the real on-screen label so the reader can find it, then explain the action in natural Arabic. In narration over a screen that shows the control, describe the action without quoting a calqued label. When the label itself is a calque and the fix is in scope, recommend a better label. When the text names something the reader must write or choose (a title, a reason, a reply, a note), give one short, realistic example: «مع ذكر السبب، مثل: «البرنامج لا يفتح بعد إعادة التشغيل»». An example shows the kind of content faster than a definition.

### 19. Tashkeel: minimal on screen, more for speech when needed

On displayed copy, default to minimal tashkeel. Mark the vowel that tells two readings apart, not the whole word: «تُرسَل الفاتورة» (passive) / «تُرسِل الفاتورة» (active) differ in the vowel on the سين; «المرسِل» (sender) / «المرسَل» (sent); «قَبل» / «قِبَل». In a narration script, fuller vocalisation is fine where the speech engine misreads words. Always vocalise proper names in narration, because a voice cannot know them: «مُنى», not «منى», which a voice may read as «مَنى». Vocalise the whole name each time it appears, with any attached prefix («ولِمُنى»).

### 20. Accessibility text: describe, do not translate

Alt text, accessible names (`aria-label`), link text, announcements and captions are heard, often with no context. Write them from what the element is and does on this screen, never from the English attribute. Detail and more pairs are in `references/accessibility.md`.

- **Purpose, not shape; no role or state.** The screen reader adds the role and the state itself, with words such as «زر» or «محدد». With the defaults, an action name is a verbal noun phrase, which shows no gender for the reader.
- **Start the name with the visible text,** and make names unique in a list: «حذف الملف: عقد الإيجار».
- **Alt text gives the meaning on this page:** `alt=""` for decoration, the action for an icon in a link, the finding for a chart. Never «صورة لـ».
- **Write for the ear:** words for 1–10 in key sentences, the month as a word, no emoji or «/» for meaning, a full stop at the end.

- Bad: «زر أيقونة سلة المهملات» → Good: «حذف الموعد»
- Bad: «رسم بياني للمصروفات» → Good: «تضاعفت مصروفات السفر في سبتمبر.»
- Bad: «لعرض سجل الاستعارة اضغط هنا» → Good: «عرض سجل الاستعارة»

## Worked cases: establish the facts first

Each word below is right only for the stated facts. Establish the same facts before you reuse it.

- **Who sees a comment.** Only the host sees it: «رسالة إلى المضيف». Everyone sees it: «تعليق علني». «تعليق عام» is unclear, because «عام» also means "general".
- **A list's contents.** It holds all the team's expense claims: «مطالبات الفريق». It holds only those not yet reviewed: «مطالبات الفريق بانتظار المراجعة». Not «صندوق وارد الفريق».
- **First-response deadline.** For the time allowed to send the first reply to a new message, write «مهلة الرد الأول». In «موعد الاستجابة الأول», the masculine «الأول» attaches to «موعد», so it reads "the first appointment for a response". «موعد الرد الأول» stays unclear, because both nouns are masculine. «مهلة» is feminine, so «الأول» can only describe «الرد».
- **"Refer to another branch".** The request moves: «تحويل طلب الاستعارة إلى فرع آخر». The reader only gets a pointer: «إرشاد القارئ إلى فرع آخر».
- **"Mark as paid".** Name the change, not the English verb "mark": «تسجيل السداد», not «وضع علامة كمدفوع».
- **"The clock", "the pipeline", "the folder holds a file".** «مدة الحجز المؤقت»; «مراحل التوظيف»; «يحتوي المجلد على ملف».
- **State of a cancelled item.** «تم الإلغاء» → «ملغى» («ملغاة» for a feminine entity such as «الرحلة»).
- **Obligation.** «ترفق الإيصال أولًا» reads as a description → «يجب إرفاق الإيصال أولًا».
- **Which deadline.** «بدأت المهلة» → «بدأت مهلة سداد الحجز».

## Expected output

| English and context                                 | Arabic                                          | Why                                                                                   |
| --------------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------------------------------- |
| "We couldn't save your changes. Try again." (error) | «تعذّر حفظ التغييرات. يُرجى المحاولة مرة أخرى.» | What failed, then what to do; no blame; no gender                                     |
| "No bookings yet." (empty state)                    | «ليس لديك حجوزات بعد.»                          | A full sentence, not «لا حجوزات»                                                      |
| "Public comment" (a comment everyone sees)          | «تعليق علني»                                    | Visibility decides the word; «رسالة إلى المضيف» is only for a message one person sees |

## Self-check (read the finished Arabic against these lists)

### Errors — always fix

- [ ] Does every verb, adjective and ordinal agree with its noun, with each placeholder value, and with a gender the product knows?
- [ ] Does an ordinal or adjective in a إضافة attach to the wrong noun?
- [ ] Is a count phrase put into a fixed sentence, or does a count string lack one of the six forms?
- [ ] In prose, any «0 X», «1 X» or «2 X»? A dual in the wrong case («تنزيل المرفقان»)? 3–10 with the wrong gender?
- [ ] Did the meaning change: must, may, only, unless, up to, the actor, the timing, who sees it, a dropped qualifier?
- [ ] A wrong hamza («انشئ»، «إختر»)? «أدخل» for a choice, or «اختر» for a typed value?
- [ ] و before a describing التي / الذي? سوف لن?
- [ ] A passive that reads as active because its distinguishing vowel is missing?
- [ ] A Latin comma or question mark in Arabic text?
- [ ] An accessible name with «زر»، «أيقونة» or a state in it, one that does not start with the visible text, or a duplicate in a list?

### Product checks — fix before hand-over

- [ ] Did I establish the facts: who sees it, what a list holds, which deadline, moves or points?
- [ ] Does a deadline say what it counts? Does the same concept have two names in the product?
- [ ] Is the form right for the type: button, status label, success notification, empty state, confirmation?
- [ ] Does an error blame the reader, or leave out what to do next? Does help text quote the real on-screen label?
- [ ] Does the software have a human intention, or an opaque English metaphor?
- [ ] The wrong address form for the channel? A UI name without quotes? Mixed quote or digit styles?
- [ ] Did I follow the project's recorded preferences (imperative or verbal noun; reader's gender; named people's gender)?
- [ ] With the verbal-noun default, does any instruction (button, step, tooltip, error fix, help text) use an imperative? Do verbal-noun steps have a lead-in line?
- [ ] With unknown gender, does a verb guess it where a verbal noun, a plural or a label would not?
- [ ] Alt text and link text: «صورة لـ», «اضغط هنا», a file name, or a translation of the English attribute instead of the meaning here?

### Preferences — fix when the shorter form keeps the meaning

- [ ] قم بـ / قام بـ + verbal noun; الخاص بك; من قِبَل after a passive; two nouns on one genitive.
- [ ] Repetition that the count phrase already carries.
- [ ] يتم / تم + verbal noun where a real verb is easy.
- [ ] بالتالي، بشكل + adjective، عبارة عن، بالنسبة لـ، أكّد على، بما أنّ، يتسنى لك.
- [ ] لقد or stacked إنّ in a report or letter; من خلال for a cause or a basis (keep it for a channel).
- [ ] Slash pairs for gender; more tashkeel than one distinguishing mark on displayed copy.

Do not flag these, because they are correct: كذلك، بدون، اعتبر، نفس الوقت، القادم، ساعات الدوام، يجب أن، يُرجى + verbal noun، إعادة + verbal noun، من خلال for a channel, a future for a real future event or for the result of a condition, and the masculine generic where no neutral form reads naturally.

## Defaults

Use these when the project has no convention and you cannot ask.

- **Instructions to the reader:** verbal noun, with a lead-in line before steps (see "Preferences to settle first").
- **Reader's gender and named people's gender:** unknown; use rule 12, and the masculine generic only when its techniques fail (see "Preferences to settle first").
- **يتم / تم + verbal noun:** prefer a real verb; never treat it as an error.
- **Job titles and groups:** a plural or collective noun; name both genders once at most, in a heading or a job title.
- **«لقد»:** avoid it in reports, letters and articles; it is fine in a short UI confirmation.
- **Zero:** a negative sentence with no digit.
- **UI names and digits:** straight double quotes and Western digits; keep an established «» or Arabic-Indic convention, and never mix the two.
- **Tanween fatha:** on the letter before the alif («جاهزًا»); keep one placement across the product.

## Reference files

- `references/calques.md`: English-shaped constructions and their natural forms. Read it when you review or edit a long passage.
- `references/grammar.md`: count strings (six forms), number agreement, ordinals, prepositions, dates, punctuation, tashkeel. Read it for any string with a number or a placeholder.
- `references/accessibility.md`: alt text by image type, accessible names, link text, form hints and errors, live announcements, landmarks, captions, and how screen readers read Arabic (tashkeel, Latin words, digits, dates, symbols, `lang`/`dir`). Read it for any text that a screen reader speaks.
