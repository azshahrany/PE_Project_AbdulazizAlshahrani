# Library Guide — How to use this library

This library helps the AI Governance & Operations Desk answer, sort, summarize, mask and route employee messages with tested prompt templates. AI writes the draft; a person checks it and decides.

## What is inside

| Path | What it is |
|---|---|
| `library_index.md` | The list of templates, variables, versions and status |
| `templates/` | Five approved templates, one file each |
| `blocks/` | The Facts block that goes into `[FACTS]` |
| `rules/` | Five responsible-use rules and the verification checklist |
| `Test_Results_Report.pdf` | The three test scores and a screenshot for each template |
| `_archive/` | Older versions, kept for history |

## How to use a template: Pick, Mask, Fill, Run, Check

1. **Pick** the template for the task from `library_index.md`.
2. **Mask** the employee text first. Use AG-Mask-Message, or replace names, numbers, emails, phones and credentials with codes such as User-1, Phone-1 or Email-1 by hand. Never paste real personal data.
3. **Copy** the template text from its code block, and **fill** every `[VARIABLE]`:
   - Paste the Facts block into `[FACTS]`.
   - Choose `[LANGUAGE]` and `[TONE]` from the allowed values, or leave them empty to use the defaults.
   - Keep the `---` lines around the input.
4. **Run** it in an approved AI tool, in a fresh chat.
5. **Check** the output with the five-point verification checklist in `rules/AG-Rules-v1_2026_10_15.md`:
   - Every fact is in the Facts block. Read the CHECK section where there is one, and verify every quoted line.
   - Numbers, dates, names and codes are exact.
   - No promise and no "I did this".
   - No personal data repeated.
   - Every question answered, and a native reader accepts the Arabic.
6. **Approve or fix.** Only an output that scores 5 out of 5 is used. Delete the CHECK section before sending. Record the template version and the approver.

## Things a person always decides

Use cases, policy exceptions, incidents, and claims of bias or hallucination are decided by the governance officer or the AI Governance Committee, never by AI.

## Changing the library

- One owner per template. A second person tests every change.
- Every change gets a new version number and a line in the change log. The old file moves to `_archive/`.
- When a fact changes, update the Facts block first (new version and date), then retest the templates that use it.
- Templates are text files (.md). No real data anywhere, including examples.

## Owners

| File | Owner |
|---|---|
| All templates, the Facts block and the rules | Abdulaziz Alshahrani |

All facts, names and messages in this library are invented for a training project.
