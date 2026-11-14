# Part 14: Comprehensive FI Practice, Calculations, Migration, and Testing (Questions 451–500)

English translation of the corresponding Japanese FI practice questions. **50 original four-option single-answer questions**, preserving the original question numbers, option order, and answer keys. Answers and explanations appear after each group of ten questions. Transaction codes primarily refer to SAP S/4HANA Private Edition using SAP GUI.

[Japanese version](14_総合演習.md)

## Set 1: Questions 451–460

### Question 451

What is the first important consideration when setting up a new company code?

A. Design organizational assignments, the fiscal year, and the chart of accounts
B. Chart of accounts, posting periods, and master data extension
C. Account group, cost element attributes, and company code settings
D. December 10

### Question 452

A company code has been created, but accounting postings cannot be made. What should be checked?

A. Number range and permitted account types
B. Chart of accounts, posting periods, and master data extension
C. BP creation → invoice → payment proposal → payment → clearing
D. JPY 55,000

### Question 453

What should be checked when adding a new document type?

A. Account group, cost element attributes, and company code settings
B. JPY 2,000
C. Number range and permitted account types
D. JPY 88,000

### Question 454

What should be checked when creating a new expense G/L account?

A. BP creation → invoice → payment proposal → payment → clearing
B. December 10
C. JPY 20,000
D. Account group, cost element attributes, and company code settings

### Question 455

What is the process from creating a new supplier through making a payment?

A. BP creation → invoice → payment proposal → payment → clearing
B. JPY 2,000
C. JPY 55,000
D. Design organizational assignments, the fiscal year, and the chart of accounts

### Question 456

Under payment terms of a 2% discount within 10 days, what is the discount on a tax-exclusive amount of JPY 100,000?

A. December 10
B. JPY 2,000
C. JPY 88,000
D. Chart of accounts, posting periods, and master data extension

### Question 457

For payment terms of 30 days from a baseline date of November 10, what is the due date?

A. JPY 55,000
B. JPY 20,000
C. December 10
D. Number range and permitted account types

### Question 458

What is the tax-inclusive amount of a supplier invoice for JPY 50,000 before tax at a 10% tax rate?

A. JPY 88,000
B. Design organizational assignments, the fiscal year, and the chart of accounts
C. Account group, cost element attributes, and company code settings
D. JPY 55,000

### Question 459

What is the tax-inclusive amount of a customer invoice for JPY 80,000 before tax at a 10% tax rate?

A. JPY 88,000
B. JPY 20,000
C. Chart of accounts, posting periods, and master data extension
D. BP creation → invoice → payment proposal → payment → clearing

### Question 460

How much 10% consumption tax is included in a tax-inclusive amount of JPY 220,000?

A. Design organizational assignments, the fiscal year, and the chart of accounts
B. JPY 20,000
C. Number range and permitted account types
D. JPY 2,000

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 451 | **A** | These form the basis for subsequent FI configuration. |
| 452 | **B** | Creating the organizational unit alone is not sufficient to enable accounting postings. |
| 453 | **C** | Review the settings in OBA7 and related configuration. |
| 454 | **D** | Check requirements for both FI and CO usage. |
| 455 | **A** | Verify configuration and accounting results throughout the end-to-end process. |
| 456 | **B** | Simplified calculation: 100,000 × 0.02 = JPY 2,000. |
| 457 | **C** | It is 30 calendar days later; actual processing follows the baseline date and configured terms. |
| 458 | **D** | 50,000 × 1.10 = JPY 55,000. |
| 459 | **A** | 80,000 × 1.10 = JPY 88,000. |
| 460 | **B** | 220,000 × 10 ÷ 110 = JPY 20,000. |

---

## Set 2: Questions 461–470

### Question 461

What is the JPY amount of an invoice for USD 100 posted at JPY 150 per USD?

A. JPY 200 difference
B. JPY 50,000
C. JPY 15,000
D. JPY 50,000 gain on sale

### Question 462

What is the JPY conversion difference if USD 100 is posted at JPY 150 per USD and collected at JPY 148 per USD?

A. JPY 30,000
B. JPY 600,000
C. JPY 50,000 loss on sale
D. JPY 200 difference

### Question 463

What is the difference between a supplier invoice of JPY 120,000 and a payment of JPY 90,000?

A. JPY 30,000
B. JPY 50,000
C. JPY 200,000
D. Payment methods, bank determination, and payment terms

### Question 464

What is the difference between a customer invoice of JPY 250,000 and a receipt of JPY 200,000?

A. JPY 600,000
B. JPY 50,000
C. JPY 50,000 gain on sale
D. Number of automatically cleared items ÷ number of target items

### Question 465

What is the net book value of an asset with an acquisition cost of JPY 900,000 and accumulated depreciation of JPY 300,000?

A. JPY 200,000
B. JPY 50,000 loss on sale
C. JPY 600,000
D. JPY 15,000

### Question 466

What is the annual straight-line depreciation for a depreciable amount of JPY 1,000,000 over five years?

A. JPY 50,000 gain on sale
B. Payment methods, bank determination, and payment terms
C. JPY 200 difference
D. JPY 200,000

### Question 467

What is the gain or loss on selling an asset with a carrying amount of JPY 400,000 for JPY 450,000?

A. JPY 50,000 gain on sale
B. JPY 50,000 loss on sale
C. Number of automatically cleared items ÷ number of target items
D. JPY 30,000

### Question 468

What is the gain or loss on selling an asset with a carrying amount of JPY 400,000 for JPY 350,000?

A. Payment methods, bank determination, and payment terms
B. JPY 50,000 loss on sale
C. JPY 15,000
D. JPY 50,000

### Question 469

What is needed when designing payment processing for a company code?

A. Number of automatically cleared items ÷ number of target items
B. JPY 200 difference
C. Payment methods, bank determination, and payment terms
D. JPY 600,000

### Question 470

Which metric measures the automatic clearing rate of bank statement items?

A. JPY 15,000
B. JPY 30,000
C. JPY 200,000
D. Number of automatically cleared items ÷ number of target items

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 461 | **C** | 100 × 150 = JPY 15,000. |
| 462 | **D** | 100 × (150 − 148) = JPY 200. |
| 463 | **A** | 120,000 − 90,000 = JPY 30,000. |
| 464 | **B** | 250,000 − 200,000 = JPY 50,000. |
| 465 | **C** | 900,000 − 300,000 = JPY 600,000. |
| 466 | **D** | 1,000,000 ÷ 5 = JPY 200,000. |
| 467 | **A** | 450,000 − 400,000 = JPY 50,000. |
| 468 | **B** | 400,000 − 350,000 = JPY 50,000. |
| 469 | **C** | Align the business process with FBZP configuration. |
| 470 | **D** | Use the ratio to quantify matching quality. |

---

## Set 3: Questions 471–480

### Question 471

How can delays in monthly closing be reduced?

A. Clarify processing sequence, responsibilities, and deadlines
B. Current processes, statutory requirements, and future processes
C. Evaluate business gaps and alternative solutions
D. Invoice line items and collection conditions

### Question 472

What should be reviewed first when defining FI business requirements?

A. Prioritize adoption of standard functionality
B. Current processes, statutory requirements, and future processes
C. Opening balances and the account mapping table
D. Acquisition costs, accumulated depreciation, and useful lives

### Question 473

What should be done if a customer requirement can be met using standard functionality?

A. Evaluate business gaps and alternative solutions
B. Amounts, due dates, and references for each open item
C. Prioritize adoption of standard functionality
D. Compare trial balances from the source and target systems

### Question 474

What is needed before considering a customer-specific extension?

A. Opening balances and the account mapping table
B. Invoice line items and collection conditions
C. Sequence of business shutdown, data migration, verification, and restart
D. Evaluate business gaps and alternative solutions

### Question 475

What is important when migrating G/L balances into FI?

A. Opening balances and the account mapping table
B. Amounts, due dates, and references for each open item
C. Acquisition costs, accumulated depreciation, and useful lives
D. Clarify processing sequence, responsibilities, and deadlines

### Question 476

What is important when migrating supplier open items into FI?

A. Invoice line items and collection conditions
B. Amounts, due dates, and references for each open item
C. Compare trial balances from the source and target systems
D. Current processes, statutory requirements, and future processes

### Question 477

What is important when migrating customer open items into FI?

A. Acquisition costs, accumulated depreciation, and useful lives
B. Sequence of business shutdown, data migration, verification, and restart
C. Invoice line items and collection conditions
D. Prioritize adoption of standard functionality

### Question 478

What is important when migrating fixed assets into FI?

A. Compare trial balances from the source and target systems
B. Clarify processing sequence, responsibilities, and deadlines
C. Evaluate business gaps and alternative solutions
D. Acquisition costs, accumulated depreciation, and useful lives

### Question 479

How should balances be verified after an FI migration?

A. Compare trial balances from the source and target systems
B. Sequence of business shutdown, data migration, verification, and restart
C. Current processes, statutory requirements, and future processes
D. Opening balances and the account mapping table

### Question 480

What is important in an FI migration cutover plan?

A. Clarify processing sequence, responsibilities, and deadlines
B. Sequence of business shutdown, data migration, verification, and restart
C. Prioritize adoption of standard functionality
D. Amounts, due dates, and references for each open item

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 471 | **A** | Use checklists and automation. |
| 472 | **B** | These provide the basis for Fit-to-Standard. |
| 473 | **C** | Consider maintainability and clean core principles. |
| 474 | **D** | First check whether standard functionality and configuration can meet the requirement. |
| 475 | **A** | Confirm consistency between source and target systems. |
| 476 | **B** | Preserve the data needed for subsequent payment processing. |
| 477 | **C** | Maintain continuity for incoming payment clearing and dunning. |
| 478 | **D** | Reconcile net book values and depreciation schedules after migration. |
| 479 | **A** | Analyze differences by account and company code. |
| 480 | **B** | Clearly define responsibilities and steps for the cutover. |

---

## Set 4: Questions 481–490

### Question 481

What should be included as a positive test case in FI testing?

A. Closed posting periods, incomplete master data, and payment blocks
B. Enable later verification of configuration and business results
C. Standard invoicing, payment, and clearing
D. Duplicate checks, required fields, and change approvals

### Question 482

What should be included as a negative test case in FI testing?

A. Upper and lower tolerance limits
B. Separate authorization for master data changes and payment approvals
C. Confirm the issue, reproduction steps, and error messages
D. Closed posting periods, incomplete master data, and payment blocks

### Question 483

What should be tested as boundary values in FI testing?

A. Upper and lower tolerance limits
B. Enable later verification of configuration and business results
C. Request, approval, testing, and transport history
D. Requirements, acceptance criteria, and responsibilities

### Question 484

Why preserve an audit trail during FI testing?

A. Separate authorization for master data changes and payment approvals
B. Enable later verification of configuration and business results
C. Duplicate checks, required fields, and change approvals
D. Configuration values, rationale, dependencies, and test results

### Question 485

Why is segregation of duties necessary in FI production operations?

A. Request, approval, testing, and transport history
B. Confirm the issue, reproduction steps, and error messages
C. Separate authorization for master data changes and payment approvals
D. Standard invoicing, payment, and clearing

### Question 486

What is important in FI change management?

A. Duplicate checks, required fields, and change approvals
B. Requirements, acceptance criteria, and responsibilities
C. Closed posting periods, incomplete master data, and payment blocks
D. Request, approval, testing, and transport history

### Question 487

What is important for FI master data quality management?

A. Duplicate checks, required fields, and change approvals
B. Confirm the issue, reproduction steps, and error messages
C. Configuration values, rationale, dependencies, and test results
D. Upper and lower tolerance limits

### Question 488

What is the first step in an FI consultant's incident analysis?

A. Requirements, acceptance criteria, and responsibilities
B. Confirm the issue, reproduction steps, and error messages
C. Standard invoicing, payment, and clearing
D. Enable later verification of configuration and business results

### Question 489

What should an FI consultant agree on with the business department?

A. Configuration values, rationale, dependencies, and test results
B. Closed posting periods, incomplete master data, and payment blocks
C. Requirements, acceptance criteria, and responsibilities
D. Separate authorization for master data changes and payment approvals

### Question 490

What information should be recorded in an FI configuration document?

A. Standard invoicing, payment, and clearing
B. Upper and lower tolerance limits
C. Request, approval, testing, and transport history
D. Configuration values, rationale, dependencies, and test results

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 481 | **C** | Verify that basic business processes work correctly. |
| 482 | **D** | Verify that expected error controls work. |
| 483 | **A** | Check behavior at configuration boundaries. |
| 484 | **B** | Test evidence supports quality and accountability. |
| 485 | **C** | This reduces the risk of fraud and erroneous payments. |
| 486 | **D** | Make configuration changes traceable. |
| 487 | **A** | Prevent problems in payments and financial closing. |
| 488 | **B** | Perform evidence-based root cause isolation. |
| 489 | **C** | Align expected outcomes with testing criteria. |
| 490 | **D** | This supports maintenance and audits. |

---

## Set 5: Questions 491–500

### Question 491

What should be included in an FI operating procedure manual?

A. Operating steps, prerequisites, error handling, and approvers
B. Repeatedly configure settings and verify results in an SAP system
C. Payment documents, clearing, and bank results
D. Explain why the answer was wrong and the correct configuration and journal entry

### Question 492

What is important when preparing for the C_TS4FI practical assessment?

A. G/L master data, posting period settings, and posting tests
B. Repeatedly configure settings and verify results in an SAP system
C. Asset values and G/L postings
D. Business requirements → configuration → posting → result verification

### Question 493

After configuring a company code in an FI hands-on exercise, what should be done next?

A. Payment documents, clearing, and bank results
B. Identify the cause, correct it, and rerun the process
C. G/L master data, posting period settings, and posting tests
D. Confirm the scope and hands-on learning materials

### Question 494

After executing payment processing in an FI hands-on exercise, what should be checked?

A. Asset values and G/L postings
B. Explain why the answer was wrong and the correct configuration and journal entry
C. Ability to configure, post, clear, and verify independently
D. Payment documents, clearing, and bank results

### Question 495

After acquiring an asset in an FI hands-on exercise, what should be checked?

A. Asset values and G/L postings
B. Identify the cause, correct it, and rerun the process
C. Business requirements → configuration → posting → result verification
D. Operating steps, prerequisites, error handling, and approvers

### Question 496

What should be done when an error occurs during an FI hands-on exercise?

A. Explain why the answer was wrong and the correct configuration and journal entry
B. Identify the cause, correct it, and rerun the process
C. Confirm the scope and hands-on learning materials
D. Repeatedly configure settings and verify results in an SAP system

### Question 497

How should incorrectly answered questions in an FI mock exam be reviewed?

A. Business requirements → configuration → posting → result verification
B. Ability to configure, post, clear, and verify independently
C. Explain why the answer was wrong and the correct configuration and journal entry
D. G/L master data, posting period settings, and posting tests

### Question 498

What is the recommended order when solving an FI practical case?

A. Confirm the scope and hands-on learning materials
B. Operating steps, prerequisites, error handling, and approvers
C. Payment documents, clearing, and bank results
D. Business requirements → configuration → posting → result verification

### Question 499

Why use the official Learning Journey when preparing for an FI certification exam?

A. Confirm the scope and hands-on learning materials
B. Ability to configure, post, clear, and verify independently
C. Repeatedly configure settings and verify results in an SAP system
D. Asset values and G/L postings

### Question 500

What should be emphasized in the final assessment of FI certification readiness?

A. Operating steps, prerequisites, error handling, and approvers
B. Ability to configure, post, clear, and verify independently
C. G/L master data, posting period settings, and posting tests
D. Identify the cause, correct it, and rerun the process

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 491 | **A** | Ensure repeatable operations and appropriate controls. |
| 492 | **B** | Multiple-choice knowledge alone is not enough preparation for practical assessment. |
| 493 | **C** | Connect configuration to actual accounting processing. |
| 494 | **D** | Verify outcomes, not only screen operations. |
| 495 | **A** | Reconcile the asset register with accounting results. |
| 496 | **B** | Develop troubleshooting skills. |
| 497 | **C** | Focus on understanding and hands-on practice rather than memorization. |
| 498 | **D** | Understand causes and outcomes as one process. |
| 499 | **A** | Prioritize the latest official requirements. |
| 500 | **B** | Correctly answering 500 multiple-choice questions alone does not guarantee passing. |

---

