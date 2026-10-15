# Library Index — AI Governance & Operations Desk

Prompt library for an internal desk that helps employees use AI tools and internal agents safely. Prefix: `AG`. Owner: Abdulaziz Alshahrani.

## Templates

| Template | Task | Variables | Version | Status |
|---|---|---|---|---|
| [AG-Reply-Inquiry](templates/AG-Reply-Inquiry-v1_2026_10_15.md) | Answer an employee inquiry about AI governance, policy or agent use, with a CHECK section for the reviewer | `[INQUIRY]` `[FACTS]` `[LANGUAGE]` `[TONE]` `[MAX_WORDS]` | v1 | Approved |
| [AG-Classify-Message](templates/AG-Classify-Message-v1_2026_10_15.md) | Sort an incoming message into one category | `[MESSAGE]` `[CATEGORIES]` `[FACTS]` `[LANGUAGE]` | v1 | Approved |
| [AG-Summarize-Message](templates/AG-Summarize-Message-v1_2026_10_15.md) | Summarize a message in three lines for the department head and label the reported case | `[MESSAGE]` `[LANGUAGE]` `[MAX_WORDS]` | v1 | Approved |
| [AG-Mask-Message](templates/AG-Mask-Message-v1_2026_10_15.md) | Replace personal data and credentials with codes | `[RAW_MESSAGE]` `[EXTRA_TERMS]` | v1 | Approved |
| [AG-Draft-Memo](templates/AG-Draft-Memo-v1_2026_10_15.md) | Turn a request into an internal memo to the right team | `[REQUEST]` `[FACTS]` `[LANGUAGE]` `[TONE]` `[MAX_WORDS]` | v1 | Approved |

Status values: **Approved** (5/5 · 6/6 · 5/5 in `Test_Results_Report.pdf`) or **Needs work** (reason and proposed fix in the report).

## Shared blocks

| Block | Used by | File |
|---|---|---|
| Desk Facts (8 facts) | AG-Reply-Inquiry, AG-Classify-Message, AG-Draft-Memo | [blocks/AG-Facts-v1_2026_10_15.md](blocks/AG-Facts-v1_2026_10_15.md) |

## Rules

| File | What it is |
|---|---|
| [rules/AG-Rules-v1_2026_10_15.md](rules/AG-Rules-v1_2026_10_15.md) | Five responsible-use rules (data, verification, fairness, policy, human decision) and the verification checklist |

## Variables (same name, same meaning in every template)

| Variable | Type | Allowed values | Default |
|---|---|---|---|
| `[FACTS]` | Block | Text of the Facts block | none: ask for it |
| `[INQUIRY]` / `[MESSAGE]` / `[REQUEST]` | Free text | The **masked** employee text | none: ask for it |
| `[RAW_MESSAGE]` | Free text | The original message before masking (AG-Mask-Message only) | none: ask for it |
| `[LANGUAGE]` | Choice | Arabic · English · Automated · Bilingual · Mixed | Automated |
| `[TONE]` | Choice | Formal · Friendly · Calm · Neutral | Neutral (AG-Draft-Memo: Formal) |
| `[MAX_WORDS]` | Number | 30–120 (Reply, Summarize) · 60–150 (Memo) | 60 · 100 |
| `[CATEGORIES]` | Choice list | Category names | Policy, Issue, Activation, Use Case, Incident, Other |
| `[EXTRA_TERMS]` | Free text | Extra words to mask | none: ignored |

## `[LANGUAGE]` values

| Value | Meaning |
|---|---|
| Arabic | Answer in Arabic only |
| English | Answer in English only |
| Automated (default) | Reply in the main language of the input |
| Bilingual | Two separate versions: Arabic, then English |
| Mixed | One reply that merges Arabic and English |

## Archive

Older versions move to [_archive/](_archive/) with their date. Nothing is deleted.

## Change log

| Date | Change |
|---|---|
| 2026_10_15 | Library created: five templates v1, Facts v1, Rules v1 |
| 2026_10_15 | All five templates tested and approved (5/5 · 6/6 · 5/5); swap test passed for AG-Reply-Inquiry; Test_Results_Report.pdf added |
