## Training Program

This project was completed as part of the Prompt Engineering and Responsible AI Use training program at SDAIA Academy, under the supervision of Abdullah Khalid AlShahrani.

The project demonstrates the practical application of prompt engineering and responsible AI use — building a clean, approved prompt library through structured RACE prompts, reusable templates with variables and fixed output formats, safe handling of sensitive data, verification and responsible-use rules, and a documented three-test quality report.

Official SDAIA Academy GitHub: https://github.com/SDAIAAcademy 


# AI Governance & Operations Desk — Prompt Library
مكتبة أوامر مكتب حوكمة وعمليات الذكاء الاصطناعي

A tested prompt library for an internal desk that helps employees use AI tools and internal agents safely: answering policy questions, routing messages, summarizing AI incidents, masking personal data and referring decisions to the right team. AI drafts; a person reviews and decides.

**Library folder:** [PE_Library_Abdulaziz_Alshahrani](PE_Library_Abdulaziz_Alshahrani/) · **How to use it:** [library_guide.md](PE_Library_Abdulaziz_Alshahrani/library_guide.md) · **Test report:** [Test_Results_Report.pdf](PE_Library_Abdulaziz_Alshahrani/Test_Results_Report.pdf)

## Path and scenario

| | |
|---|---|
| Path | **A — Free path** |
| Scenario | AI Governance & Operations Desk at a mid-size company (invented) |
| Prefix | `AG` |
| Who writes in | Employees, by email or internal chat |
| Who reviews | The governance officer reviews every output before it is used |
| Who receives summaries and memos | Department heads, the AI Platform team and the AI Governance Committee |

## Desk facts (invented)

| # | Fact |
|---|---|
| 1 | The desk is open Sunday to Thursday, 08:00 to 16:00, and answers messages within 1 working day. |
| 2 | Only approved AI tools and internal agents may be used for work. If an approved tool is paused, employees continue the task without AI and do not switch to an unapproved tool. |
| 3 | Public and Internal data may be used in approved tools. Confidential and Personal data must never be pasted into any AI tool. |
| 4 | Access to an approved tool or agent is activated through the IT portal after the line manager's approval. |
| 5 | New AI use cases and any exception to the AI policy are decided by the AI Governance Committee. The desk cannot approve or reject any request. |
| 6 | The desk cannot see agent conversations, usage logs or workflow run logs. Refer technical issues to the AI Platform team through the IT portal. |
| 7 | Personal or Confidential data pasted into an AI tool by mistake must be reported to the desk on the same working day. |
| 8 | The desk never asks for passwords, API keys, access codes or the content of confidential files. |

## The 10 tasks (✅ = built and tested in this library)

| # | Task | Goal | Template |
|---|---|---|---|
| 1 ✅ | Answer an employee inquiry | Write a short, polite answer to an employee's question about AI governance, policy or agent use, using only the Desk Facts. | AG-Reply-Inquiry |
| 2 ✅ | Sort incoming messages | Label each message as Policy, Issue, Activation, Use Case, Incident or Other. | AG-Classify-Message |
| 3 ✅ | Brief for the department head | Summarize an employee's message in three lines for the department head, and label the reported case as Hallucination, Bias, Workflow failure or Other. | AG-Summarize-Message |
| 4 ✅ | Mask before pasting | Replace names, employee numbers, emails, phones and any credentials in a message with codes before it goes to an AI tool. | AG-Mask-Message |
| 5 | Explain a rejection | Rewrite a short rejection message as a clear, respectful explanation for the employee, without changing the decision or adding any reason. | — |
| 6 | Pause notice | Write a calm, polite notice that an AI tool or agent is temporarily paused, with what to do meanwhile, without alarming wording or a promised return time. | — |
| 7 | Bilingual notice | Translate an approved message or notice between Arabic and English without changing any date, rule or fact. | — |
| 8 | AI use FAQ sheet | Turn five common employee questions and their facts into a short, useful FAQ sheet. | — |
| 9 ✅ | Referral memo | Turn an employee's request into a short internal memo to the right team (AI Platform team or AI Governance Committee) when it needs their action or decision. | AG-Draft-Memo |
| 10 | Prompt review feedback | Review an employee's prompt against RACE and give feedback as evidence, effect and edit. | — |

## Test results

Each template is tested three times: prompt quality (RACE), template quality (library readiness) and output quality (verification checklist). Full details and screenshots are in the [Test Results Report](PE_Library_Abdulaziz_Alshahrani/Test_Results_Report.pdf).

| Template | Prompt /5 | Template /6 | Output /5 | Status |
|---|---|---|---|---|
| AG-Reply-Inquiry | 5 | 6 | 5 | Approved |
| AG-Classify-Message | 5 | 6 | 5 | Approved |
| AG-Summarize-Message | 5 | 6 | 5 | Approved |
| AG-Mask-Message | 5 | 6 | 5 | Approved |
| AG-Draft-Memo | 5 | 6 | 5 | Approved |

## Data note

Every organization, person, message and fact in this repository is invented for training. No real data is used anywhere, including the screenshots.
