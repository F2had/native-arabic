# Grammar for writers: numbers, agreement, prepositions, tashkeel

The grades فصيحة (best form) and صحيحة (grammatical, accepted, but weaker) mean the same as in calques.md.

## 1. Count strings: six forms, six full sentences

ICU, `Intl.PluralRules` and Fluent sort an Arabic number into six plural categories and choose a branch by them. The category does not decide the grammar of the branch. Number, case and agreement depend on the sentence, so each branch needs its own full sentence. Two steps:

1. **Select:** the plural rules pick the branch from the number.
2. **Realise:** you write the full sentence for that branch. First decide whether the string counts whole things («3 ملفات») or measures a quantity («1.5 ساعة»).

| Category | Which numbers | Usual noun form when counting whole things | Example ("{count} guests attended") |
| --- | --- | --- | --- |
| zero | 0 | none: a negative sentence | «لم يحضر أي ضيف» |
| one | 1 | singular | «حضر ضيف واحد» |
| two | 2 | dual | «حضر ضيفان» |
| few | n % 100 = 3..10 | plural, genitive | «حضر 3 ضيوف» |
| many | n % 100 = 11..99 | singular, accusative | «حضر 11 ضيفًا» |
| other | 100, 101, 102, 1000 …, and decimals (0.5, 1.5, 10.1) | singular, genitive | «حضر 100 ضيف» |

The rule uses n % 100, so 103 is *few* and 111 is *many*.

**Zero.** Remove the digit and write a negative sentence: "0 rooms available" becomes «لا توجد غرف متاحة».

**One and two.** In prose, write 1 as a word and 2 as the dual: «ضيف واحد», «ضيفان», not «1 ضيف» or «2 ضيوف». The rule is for the numbers one and two, not for every number that ends in 1 or 2 («102 ضيف» is correct). Digits are fine in compact UI: badges, counters, tables.

**Decimals and measures.** Decimals fall in *other*, but the *other* branch for whole things («100 ضيف») is not always right for a measure. In UI, a measure after a decimal is usually the singular: «1.5 ساعة». In prose, a phrase is often better: «ساعة ونصف». Check fractions, decimals and compound numbers by hand; do not reuse a counting branch for them.

**Build the whole sentence, not a phrase.** A sentence built from fragments assumes one grammar for every language. Put the plural selector around the whole sentence, so each branch is a sentence a translator can read. A common failure: «لا حجوزات» dropped into «لديك {count} هذا الأسبوع.» reads «لديك لا حجوزات هذا الأسبوع». Also remove repetition that the count phrase already carries, and keep the meaning: «نُقلت إلى مجلدك 3 ملفات من ملفات العميل» → «نُقلت إلى مجلدك 3 من ملفات العميل». («3 ملفات من العميل» would make the client the sender, not the owner of the set.)

ICU skeleton (the English is a placeholder; write each branch as a full Arabic sentence):

```
{count, plural,
  zero  {<negative sentence, no digit>}
  one   {<full sentence for one>}
  two   {<full sentence for two, dual, no digit>}
  few   {<full sentence with #>}
  many  {<full sentence with #>}
  other {<full sentence with #>}
}
```

**Agreement depends on the sentence structure, not on the branch.**
- Verb before the subject: the verb stays singular and agrees in gender only. «حضر ضيف واحد»، «حضر ضيفان»، «حضر ثلاثة ضيوف»، «حضرت ثلاث ضيفات».
- Verb after the subject: the verb agrees in number too. «الضيفان حضرا»، «الضيوف حضروا».
- An adjective agrees with the counted noun: «ضيفان جديدان»، «ثلاثة ضيوف جدد».

Worked example, "{count} rooms available" in a booking app, with a feminine noun:

```
{count, plural,
  zero  {لا توجد غرف متاحة.}
  one   {توجد غرفة واحدة متاحة.}
  two   {توجد غرفتان متاحتان.}
  few   {توجد # غرف متاحة.}
  many  {توجد # غرفة متاحة.}
  other {توجد # غرفة متاحة.}
}
```

**Placeholders.** Find out what fills each placeholder before you write the sentence, because the agreement depends on it. A number, a name, and a noun need different sentences.

## 2. Number and counted noun

| Number | Gender of the number | Counted noun | Example |
| --- | --- | --- | --- |
| 1, 2 | same as the noun; comes after it as an adjective | singular / dual | «وصل طردٌ واحدٌ، ووصلت رسالةٌ واحدةٌ» / «وصل طردان اثنان، ووصلت رسالتان اثنتان» |
| 3–10 | opposite to the singular noun | plural, genitive | «ثلاثةُ ملفاتٍ» / «خمسُ غرفٍ» / «حضر سبعةُ ضيوفٍ» |
| 11, 12 | both parts same as the noun | singular, accusative | «حُجز أحدَ عشرَ مقعدًا» / «وصل اثنا عشرَ ضيفًا، واستقبلنا اثني عشرَ ضيفًا» |
| 13–19 | first part opposite, عشر/عشرة same | singular, accusative | «استُعير أربعةَ عشرَ كتابًا، وأُعيدت خمسَ عشرةَ مجلةً» |
| 20–99 | tens fixed; units 1–2 same, 3–9 opposite | singular, accusative | «سُجّل عشرون مريضًا، وفحص الطبيب عشرين مريضًا» / «واحدٌ وعشرون يومًا» / «تسعٌ وتسعون ليلةً» |
| 100, 1000 … | fixed | singular, genitive | «وصل مئةُ طلبٍ» / «بيع ألفُ تذكرةٍ» |

**Judge 3–10 by the singular, even when the plural ends in ـات.** اجتماع is masculine, so the number is feminine.
- عُقدت ثلاث اجتماعات → عُقدت ثلاثة اجتماعات [فصيحة]
- فُتحت خمس حسابات جديدة → فُتحت خمسة حسابات جديدة [فصيحة]
- وصلت ثماني طلبات اليوم → وصلت ثمانية طلبات اليوم [فصيحة]

**The rule holds when the number follows the noun.**
- أُضيفت حسابات ثلاث → أُضيفت حسابات ثلاثة [فصيحة]

**11 with a feminine noun.**
- أُعيد الإرسال أحدَ عشرَ مرة → أُعيد الإرسال إحدى عشرة مرة [فصيحة]

**Plural of paucity or of abundance after 3–10.** Both are فصيحة: «ثلاثة أسطر» / «ثلاثة سطور».

**Digits.** Default to Western digits. A product with an established Arabic-Indic convention (٠–٩) keeps it. Do not mix the two in one product. Put no space before %: «50%», not «% 50».

## 3. Dual

An English plural can mean two. Use the dual then: «مرفقات» → «مرفقان» for exactly two attachments. The dual takes the case of its place in the sentence: «مرفقان» as a label or a subject, «المرفقين» as an object or after a preposition: «تنزيل المرفقين», not «تنزيل المرفقان».

## 4. Ordinals

**Agree in gender**, as an adjective and in إضافة.
- هذه خامس محاولة → هذه المحاولة الخامسة [فصيحة] / هذه محاولة خامسة [فصيحة]
- In إضافة, the ordinal is feminine before a feminine noun: «هذه ثالثةُ زيارة» [فصيحة]
- «حُجزت الغرفة الرابعة والمقعد السادس»

**Compound ordinals 11–19 with a feminine noun: both parts feminine.**
- الدفعة الثالثة عشرَ → الدفعة الثالثة عشرة [فصيحة]
- الليلة الثانية عشرَ → الليلة الثانية عشرة

**"Item number N": use the ordinal.** The cardinal form is only صحيحة.
- في الطابق خمسة عشر → في الطابق الخامس عشر [فصيحة]
- الإصدار ستة وثلاثين → الإصدار السادس والثلاثون [فصيحة]

**Make clear which noun the ordinal describes.** In a إضافة, the ordinal can attach to either noun. The phrase is grammatical either way; the question is which meaning you intend.
- «موعد الاستجابة الأول»: «الأول» attaches to «موعد» ("the first appointment for a response").
- «موعد الرد الأول»: unclear, because both nouns are masculine.
- For a first-response deadline, write «مهلة الرد الأول». «مهلة» is feminine, so «الأول» can only describe «الرد».

## 5. Agreement

**Non-human plurals.** A singular feminine adjective and a plural adjective are both فصيحة.
- «غرف واسعة» / «غرف واسعات»; «أيام قليلة» / «أيام قلائل»
- «حُذفت الملفات القديمة» is the usual UI form.

**Unknown subject (tooltips, control descriptions).** A verb must agree with the control, and you often do not know its gender. Use a verbal noun: «ترتيب الملفات حسب التاريخ», not «يرتب الملفات حسب التاريخ».

**Two heads, one genitive; stacked إضافات.** See calques.md, "Genitive and noun phrases".

**Placeholders.** Every verb and adjective must agree with each value that can fill the slot. If the values differ in gender or number, write separate strings.

## 6. Prepositions

| Natural | English-shaped or weaker | Note |
| --- | --- | --- |
| أكّد أهميةَ … | أكّد على أهمية … | على is صحيحة |
| بالنسبة إلى | بالنسبة لـ | لـ is صحيحة |
| يكافح الاحتيال | يكافح ضد الاحتيال | ضد is صحيحة |
| من حيث سعرُها | من حيث سعرِها | حيث takes a clause |
| دون / من دون | بدون | بدون is صحيحة and normal in UI |
| بـ، نتيجة لـ، بناءً على | من خلال (for cause or basis) | من خلال or عبر is correct for a channel: «يمكن تقديم الطلب من خلال التطبيق» |
| في ضوء | على ضوء | |
| verb + preposition: نُظر في الشكوى | an impersonal passive copied from English: «الشكوى نُظرت» | |

## 7. Dates and time

In product UI, date fields and timestamps follow the product's format and precision. These rules are for letters, reports and publications.

- Write the month as a word.
- Use one set of month names across the product. The default is «يناير، فبراير …»; do not mix it with the other set («كانون الثاني، شباط …»).
- When a document gives both a Hijri and a Gregorian date, follow the house order and link the two with «الموافق». Convert dates in code with the official Hijri calendar variant, the ICU / `Intl` calendar id `islamic-umalqura`. Do not use the tabular `islamic` variant: it can differ by a day. Do not compute dates by hand.
- Use the 12-hour clock with ص and م. In prose, write the time in words: «يبدأ الموعد الساعة العاشرة والنصف صباحًا».

## 8. Punctuation

- Arabic comma ، and question mark ؟: «هل اكتمل الدفع؟»
- No space before a comma, colon or period; one space after it.
- UI names in straight double quotes by default: «القائمة "المزيد"». A product with an established «» convention keeps it; do not mix the two.
- Steps of a process: number them, and give each step one short instruction. Verbal-noun steps need a lead-in line, such as «يمكنك اتباع الخطوات التالية:».

## 9. Tashkeel

**Minimal on displayed copy.** By default, mark a vowel only where a word can be misread without it. Mark the vowel that tells the two readings apart, not every vowel. The cases:
- قَبل / قِبَل
- passive against active: «تُرسَل الفاتورة» (passive) / «تُرسِل الفاتورة» (active). Both start with a ضمة; the فتحة or كسرة on the سين tells them apart.
- a passive that a ضمة, and a شدّة where there is one, make clear: «الملفات التي تُرفَع إلى المجلد»، «يُجهَّز الطلب»
- المرسِل (the sender) / المرسَل (sent)

**Passive verbs.** Mark the passive where it can read as active. Often the ضمة on the first letter is enough: «نُظر في الشكوى.», «يُشحن», «حُذف». When the active form also starts with a ضمة (تُرسِل), mark the vowel before the last letter.

**Tanween fatha position.** Both placements are in use: on the alif (جاهزاً) or on the letter before it (جاهزًا). The default is the letter before the alif. Keep one placement across the product.

**Narration scripts for a speech engine.** Unmarked text is the main cause of mispronunciation, and automatic diacritizers do not always get speech text right. In a narration script, mark the words a reader or engine could pronounce two ways. When the engine still misreads words, fuller vocalisation, up to a full sentence, is fine in the script. Engine settings are out of scope for this skill.
