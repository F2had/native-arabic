# native-arabic

An agent skill that makes AI write Arabic the way a native professional writes
it in Modern Standard Arabic, not the way a translation of English reads.

Word-for-word Arabic is grammatical on the surface and wrong to a native
reader: it keeps English word order, English noun stacks and English
metaphors. This skill stops that without changing what the text means.

| Translated | Native |
| --- | --- |
| لا حجوزات لك الآن | ليس لديك حجوزات الآن |
| يتم تجهيز الطلب ويتم شحنه خلال يومين | يُجهَّز الطلب ويُشحن خلال يومين |
| الحجوزات الخاصة بك | حجوزاتك |
| لديك لا حجوزات هذا الأسبوع | a full sentence for each of the six plural forms |

## What it covers

- UI strings, buttons, status labels, errors, empty states, notifications
- Locale files (`ar.json`, `lang/ar/*.php`, `*.ar.yml`) and count strings with
  all six Arabic plural forms
- Help text, emails, formal letters, narration and video scripts
- Accessibility text: alt text, accessible names, live announcements, captions
- Reviews of Arabic copy someone else wrote

It asks two project preferences once and records the answers: imperative or
verbal noun for instructions, and whether the product knows the reader's
gender. When it cannot ask, it uses forms that show no gender.

## Install

With the [skills](https://github.com/vercel-labs/skills) CLI:

```sh
npx skills add F2had/native-arabic
```

Or by hand, for Claude Code:

```sh
git clone https://github.com/F2had/native-arabic ~/.claude/skills/native-arabic
```

The skill triggers on its own whenever the agent writes or reviews Arabic that
a person will read.

## Files

- `SKILL.md`: the method, the rules, the self-check and the defaults
- `references/calques.md`: English-shaped constructions and their natural forms
- `references/grammar.md`: numbers and count strings, agreement, ordinals,
  dates, punctuation, tashkeel
- `references/accessibility.md`: alt text, accessible names, announcements,
  captions, and how screen readers read Arabic

## Licence

MIT. See `LICENSE`.
