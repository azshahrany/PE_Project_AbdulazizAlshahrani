# AG-Mask-Message-v1_2026_10_15

**Purpose:** Replace personal data and credentials in an employee message with codes before the message is used with any other AI template.
**Use when:** A message contains names, numbers, emails, phones or credentials and the desk needs a safe version to work with.
**Owner:** Abdulaziz Alshahrani · **Version:** v1 · **Date:** 2026_10_15
**Last tested:** 2026_10_15 (two fills and one edge case passed)

## Variables

| Variable | Type | Allowed values | Default | If missing |
|---|---|---|---|---|
| `[RAW_MESSAGE]` | Free text | The original message, before masking | none | Ask for it |
| `[EXTRA_TERMS]` | Free text (optional) | Other words to mask, such as a project or client name, separated by commas | none | Write "none" and the template ignores it |

`[RAW_MESSAGE]` has its own name on purpose: in every other template, the input is already masked.

## Template (copy from the next line to the end of the code block)

```
ROLE: You are a privacy assistant at the AI Governance & Operations Desk. You prepare employee messages so that the desk team can use them safely with AI tools. A desk agent checks your result before it is used.
ACTION: Replace every personal or sensitive detail in INPUT with a code, keep everything else exactly as written, then list the codes you used. Work in this order:
1) Find every detail listed in the MASKING TABLE, and every term listed under EXTRA TERMS.
2) Replace each one with its code. Use the same code for the same value every time.
3) Write the masked message, the code key and the "Please check" line.
CONTEXT:
EXTRA TERMS: [EXTRA_TERMS]
MASKING TABLE:
- Person name → User-1, User-2 …
- Employee number or ID number → ID-1, ID-2 …
- Phone number → Phone-1, Phone-2 …
- Email address → Email-1, Email-2 …
- Request, ticket or case number → Request-1, Request-2 …
- Password, API key, token or access code → CREDENTIAL-REMOVED
- Exact date of birth or exact age → a range, such as "born in the 1990s" or "in their 30s"
- A term listed under EXTRA TERMS → Term-1, Term-2 …
INPUT:
---
[RAW_MESSAGE]
---
RULES:
* Change nothing except the details you mask: keep the wording, order, language and punctuation.
* Never copy an original value into the code key or anywhere else in the output.
* Never invent a value, and never ask for the original values.
* If EXTRA TERMS is empty or says "none", ignore it.
* If the message has no detail to mask, return it unchanged and write "Nothing to mask".
* If you are not sure whether a detail is personal, mask it and list its code under "Please check".
* Never ask for passwords, API keys, access codes or confidential content.
* If a variable value is missing, use its default. If it has no default, ask for it. Do not guess.
EXPECTATION:
* Language: keep the language of the original message. Do not translate.
* Tone and length: unchanged from the original message.
* Output plain text only, with no email draft or card.
* Format (nothing else):
    Masked message: the full message with codes
    Code key: one line per code, with its type only (for example "User-1 = person name")
    Please check: the codes you were unsure about, or "None"
```

## Example fill (invented)

All values below are invented placeholders that follow a TEST or 000 pattern. None of them belongs to a real person or system.

| Variable | Value |
|---|---|
| `[RAW_MESSAGE]` | Hello, this is Sami Test (employee no. EMP-000000). The workflow agent failed again on request REQ-0000-TEST. You can call me on 0500000000 or email sami.test@example.com. I put the API key sk-TEST-0000-FAKE in the ticket so you can check it. |
| `[EXTRA_TERMS]` | none |

**Expected result (what a good output contains):** the name becomes User-1, the employee number ID-1, the request number Request-1, the phone number Phone-1, the email Email-1, and the API key CREDENTIAL-REMOVED. The rest of the sentence is unchanged. The code key lists types only, never the original values. The recorded output is in `Test_Results_Report.pdf`.

## Limits

- Use this template only in an AI tool your organization approves for this step; otherwise, mask by hand with the masking table as a checklist.
- A person reads the masked message before it is used anywhere: the model can miss a detail.
- Combinations can still identify a person (a rare job title plus a small team): the reviewer checks for them.
- Results differ between runs and tools: judge them with the checklist, not word by word.

## Change log

| Version | Date | Change |
|---|---|---|
| v1 | 2026_10_15 | First version, based on the Day 2 and Day 4 masking methods, with credentials added to the masking table |
