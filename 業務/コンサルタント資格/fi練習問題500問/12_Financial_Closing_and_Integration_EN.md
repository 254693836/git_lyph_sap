# Part 12: Financial Closing, Universal Journal, and MM/SD/CO Integration (Questions 351–400)

English translation of the Japanese practice questions. **50 original four-option single-answer questions**, retaining the original question numbers, option order, and answer keys. Answers and explanations appear after each group of ten questions. Transaction codes primarily reflect SAP S/4HANA Private Edition using SAP GUI.

[Japanese version](12_決算と連携.md)

## Set 1: Questions 351–360

### Question 351

Why check the posting period before financial closing?

A. Ensure that posting is permitted in the relevant period
B. Identify unsettled transactions
C. Valuation key date, valuation method, and ledger
D. Defer expenses attributable to future periods

### Question 352

Why review open items during monthly closing?

A. Revalue foreign currency balances using closing exchange rates
B. Identify unsettled transactions
C. Realized foreign exchange gain or loss
D. Recognize revenue earned but not yet invoiced in the current period

### Question 353

What is the purpose of foreign currency valuation?

A. Valuation key date, valuation method, and ledger
B. Recognize expenses incurred in the correct period
C. Revalue foreign currency balances using closing exchange rates
D. Defer revenue attributable to future periods

### Question 354

Which are important parameters for foreign currency valuation?

A. Realized foreign exchange gain or loss
B. Defer expenses attributable to future periods
C. Avoid double counting
D. Valuation key date, valuation method, and ledger

### Question 355

What difference may arise when a foreign currency receivable is settled?

A. Realized foreign exchange gain or loss
B. Recognize expenses incurred in the correct period
C. Recognize revenue earned but not yet invoiced in the current period
D. Ensure that posting is permitted in the relevant period

### Question 356

Why recognize accrued expenses at closing?

A. Defer expenses attributable to future periods
B. Recognize expenses incurred in the correct period
C. Defer revenue attributable to future periods
D. Identify unsettled transactions

### Question 357

Why recognize prepaid expenses?

A. Recognize revenue earned but not yet invoiced in the current period
B. Avoid double counting
C. Defer expenses attributable to future periods
D. Revalue foreign currency balances using closing exchange rates

### Question 358

Why recognize accrued revenue?

A. Defer revenue attributable to future periods
B. Ensure that posting is permitted in the relevant period
C. Valuation key date, valuation method, and ledger
D. Recognize revenue earned but not yet invoiced in the current period

### Question 359

Why recognize deferred revenue?

A. Defer revenue attributable to future periods
B. Avoid double counting
C. Identify unsettled transactions
D. Realized foreign exchange gain or loss

### Question 360

Why reverse closing adjustment entries in the next period?

A. Ensure that posting is permitted in the relevant period
B. Avoid double counting
C. Revalue foreign currency balances using closing exchange rates
D. Recognize expenses incurred in the correct period

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 351 | **A** | Check whether the relevant periods are open or closed in OB52. |
| 352 | **B** | Review AR, AP, GR/IR, and other open items. |
| 353 | **C** | Recognize unrealized exchange gains and losses, as applicable. |
| 354 | **D** | These determine the balances to be valued and the valuation approach. |
| 355 | **A** | It arises from differences between invoice and settlement exchange rates. |
| 356 | **B** | This follows accrual accounting. |
| 357 | **C** | This allocates expenses to the appropriate periods. |
| 358 | **D** | Revenue is recognized in the period in which it is earned. |
| 359 | **A** | It separates the timing of cash receipt from revenue recognition. |
| 360 | **B** | Accrual entries and similar adjustments are reversed in the following period. |

---

## Set 2: Questions 361–370

### Question 361

Where are year-end profit and loss account balances accumulated?

A. Carry the balances forward to the next fiscal year
B. Separate additional year-end adjustments
C. Retained earnings account
D. Supplier line items and reconciliation account balances

### Question 362

What happens to balance sheet account balances at year-end?

A. Consistency of account settings and fiscal years
B. Identify goods received but not invoiced and invoices without goods receipts
C. Customer line items and reconciliation account balances
D. Carry the balances forward to the next fiscal year

### Question 363

What should be checked before balance carryforward?

A. Consistency of account settings and fiscal years
B. Separate additional year-end adjustments
C. Mismatch between goods receipt and invoice quantities, among other differences
D. Consistency between depreciation postings and the asset register

### Question 364

Why use special posting periods?

A. Identify goods received but not invoiced and invoices without goods receipts
B. Separate additional year-end adjustments
C. Supplier line items and reconciliation account balances
D. Bank statements and bank G/L balances

### Question 365

Why review the GR/IR balance at closing?

A. Mismatch between goods receipt and invoice quantities, among other differences
B. Customer line items and reconciliation account balances
C. Identify goods received but not invoiced and invoices without goods receipts
D. Retained earnings account

### Question 366

What is a common cause of remaining differences in GR/IR?

A. Supplier line items and reconciliation account balances
B. Consistency between depreciation postings and the asset register
C. Carry the balances forward to the next fiscal year
D. Mismatch between goods receipt and invoice quantities, among other differences

### Question 367

What should be reconciled when verifying accounts payable balances?

A. Supplier line items and reconciliation account balances
B. Customer line items and reconciliation account balances
C. Bank statements and bank G/L balances
D. Consistency of account settings and fiscal years

### Question 368

What should be reconciled when verifying accounts receivable balances?

A. Consistency between depreciation postings and the asset register
B. Customer line items and reconciliation account balances
C. Retained earnings account
D. Separate additional year-end adjustments

### Question 369

What should be checked when closing Fixed Asset Accounting?

A. Bank statements and bank G/L balances
B. Carry the balances forward to the next fiscal year
C. Consistency between depreciation postings and the asset register
D. Identify goods received but not invoiced and invoices without goods receipts

### Question 370

What should be checked when reconciling bank balances at closing?

A. Retained earnings account
B. Consistency of account settings and fiscal years
C. Mismatch between goods receipt and invoice quantities, among other differences
D. Bank statements and bank G/L balances

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 361 | **C** | P&L account balances are not directly carried forward as opening balances of the same accounts. |
| 362 | **D** | Balance sheet balances become opening balances in the next fiscal year. |
| 363 | **A** | Check settings such as the retained earnings account. |
| 364 | **B** | Specify a special period using a posting date in the last regular period. |
| 365 | **C** | Investigate mismatches between goods receipts and invoices. |
| 366 | **D** | Review quantity and price differences. |
| 367 | **A** | Confirm agreement between the subledger and G/L. |
| 368 | **B** | Reconcile the subledger with the G/L. |
| 369 | **C** | Investigate missing depreciation and account discrepancies. |
| 370 | **D** | Investigate outstanding and unprocessed transactions. |

---

## Set 3: Questions 371–380

### Question 371

What is the purpose of a Financial Statement Version?

A. Arrange G/L accounts into balance sheet and P&L hierarchies
B. Segment characteristics and document splitting
C. 0L
D. ACDOCA

### Question 372

What is important for segment financial reporting?

A. Multiple ledgers
B. Segment characteristics and document splitting
C. Record differences for another accounting standard
D. BKPF

### Question 373

What is the main mechanism used for parallel accounting?

A. 0L
B. Post only to specified ledgers
C. Multiple ledgers
D. BSEG

### Question 374

What is the standard code for the leading ledger?

A. Record differences for another accounting standard
B. ACDOCA
C. G/L account master data
D. 0L

### Question 375

What is a purpose of a non-leading ledger?

A. Record differences for another accounting standard
B. Post only to specified ledgers
C. BKPF
D. Arrange G/L accounts into balance sheet and P&L hierarchies

### Question 376

Why post with a ledger group specified?

A. ACDOCA
B. Post only to specified ledgers
C. BSEG
D. Segment characteristics and document splitting

### Question 377

What is the main table of the Universal Journal?

A. BKPF
B. G/L account master data
C. ACDOCA
D. Multiple ledgers

### Question 378

What is the main table for FI document headers?

A. BSEG
B. Arrange G/L accounts into balance sheet and P&L hierarchies
C. 0L
D. BKPF

### Question 379

Which table is commonly used for FI entry-view line items?

A. BSEG
B. G/L account master data
C. Segment characteristics and document splitting
D. Record differences for another accounting standard

### Question 380

Where are cost elements maintained in SAP S/4HANA?

A. Arrange G/L accounts into balance sheet and P&L hierarchies
B. G/L account master data
C. Multiple ledgers
D. Post only to specified ledgers

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 371 | **A** | It defines the financial reporting structure. |
| 372 | **B** | Manage balanced reporting by characteristic. |
| 373 | **C** | Maintain valuations for different accounting standards. |
| 374 | **D** | The standard leading ledger is 0L. |
| 375 | **A** | It supports parallel accounting. |
| 376 | **B** | Record adjustments specific to an accounting standard. |
| 377 | **C** | It integrates line items from FI, CO, and other areas. |
| 378 | **D** | It stores accounting document header information. |
| 379 | **A** | It stores accounting document entry-view information. |
| 380 | **B** | Cost elements and G/L accounts are integrated. |

---

## Set 4: Questions 381–390

### Question 381

What is needed to analyze profit and loss by profit center?

A. CO account assignment on expense postings
B. GR/IR account
C. Appropriate profit center assignment
D. Accounts receivable and revenue

### Question 382

What is needed to analyze expenses by cost center?

A. CO-related line items are recorded in the Universal Journal
B. OBYC
C. MIRO
D. CO account assignment on expense postings

### Question 383

Why can CO internal allocations affect FI reporting?

A. CO-related line items are recorded in the Universal Journal
B. GR/IR account
C. VKOA
D. Valuation class and automatic account determination

### Question 384

Which clearing account is used to integrate MM goods receipts with FI?

A. OBYC
B. GR/IR account
C. Accounts receivable and revenue
D. Manage the department responsible for expenses

### Question 385

Which transaction code is commonly used for MM automatic account determination?

A. VKOA
B. MIRO
C. OBYC
D. Appropriate profit center assignment

### Question 386

Which transaction code is commonly used for SD revenue account determination?

A. Accounts receivable and revenue
B. Valuation class and automatic account determination
C. CO account assignment on expense postings
D. VKOA

### Question 387

What are the basic postings transferred from SD billing to FI?

A. Accounts receivable and revenue
B. MIRO
C. Manage the department responsible for expenses
D. CO-related line items are recorded in the Universal Journal

### Question 388

Which transaction code is commonly used for purchasing invoice verification?

A. Valuation class and automatic account determination
B. MIRO
C. Appropriate profit center assignment
D. GR/IR account

### Question 389

What influences MM inventory valuation postings?

A. Manage the department responsible for expenses
B. CO account assignment on expense postings
C. Valuation class and automatic account determination
D. OBYC

### Question 390

What is the primary role of a cost center?

A. Appropriate profit center assignment
B. CO-related line items are recorded in the Universal Journal
C. VKOA
D. Manage the department responsible for expenses

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 381 | **C** | Responsibility areas are retained in posting line items. |
| 382 | **D** | Check cost center input and derivation. |
| 383 | **A** | FI and CO integration enables cross-functional reporting. |
| 384 | **B** | It manages the timing difference between goods receipts and invoice receipts. |
| 385 | **C** | It is relevant to account determination for inventory and GR/IR postings. |
| 386 | **D** | It determines revenue accounts for billing documents. |
| 387 | **A** | Tax and other amounts are also posted according to configuration. |
| 388 | **B** | It matches purchase orders, goods receipts, and invoices. |
| 389 | **C** | These determine the G/L accounts used for inventory postings. |
| 390 | **D** | It collects expenses as a CO organizational object. |

---

## Set 5: Questions 391–400

### Question 391

What should be checked to avoid running foreign currency valuation twice during closing?

A. Valuation history and execution parameters
B. Reverse and repost correctly
C. Make missed tasks and responsibilities visible
D. Valuation gain of JPY 10,000

### Question 392

What is the basic response to an incorrect posting found during closing?

A. Previous-period posting status and authorizations
B. Reverse and repost correctly
C. Debit expense; credit accrued expenses
D. Bank statements and incoming payment documents

### Question 393

What should be checked before posting to the previous fiscal period after closing?

A. Make missed tasks and responsibilities visible
B. Debit prepaid expenses; credit expense
C. Previous-period posting status and authorizations
D. Ledger, period, currency, and Financial Statement Version

### Question 394

What is the purpose of a monthly closing checklist?

A. Debit expense; credit accrued expenses
B. Valuation gain of JPY 10,000
C. Balance reconciliation → valuation → adjustments → carryforward → reporting
D. Make missed tasks and responsibilities visible

### Question 395

What is the journal entry to accrue an unpaid expense of JPY 100,000?

A. Debit expense; credit accrued expenses
B. Debit prepaid expenses; credit expense
C. Bank statements and incoming payment documents
D. Valuation history and execution parameters

### Question 396

What is the basic entry to recognize JPY 100,000 of prepaid expenses?

A. Valuation gain of JPY 10,000
B. Debit prepaid expenses; credit expense
C. Ledger, period, currency, and Financial Statement Version
D. Reverse and repost correctly

### Question 397

What is the profit or loss effect if a foreign currency valuation difference is a gain of JPY 10,000?

A. Bank statements and incoming payment documents
B. Balance reconciliation → valuation → adjustments → carryforward → reporting
C. Valuation gain of JPY 10,000
D. Previous-period posting status and authorizations

### Question 398

Which documents should be used to investigate an outstanding incoming bank payment?

A. Ledger, period, currency, and Financial Statement Version
B. Valuation history and execution parameters
C. Make missed tasks and responsibilities visible
D. Bank statements and incoming payment documents

### Question 399

What should be investigated if financial closing report figures do not reconcile?

A. Ledger, period, currency, and Financial Statement Version
B. Balance reconciliation → valuation → adjustments → carryforward → reporting
C. Reverse and repost correctly
D. Debit expense; credit accrued expenses

### Question 400

What sequence should be verified in an end-to-end closing test?

A. Valuation history and execution parameters
B. Balance reconciliation → valuation → adjustments → carryforward → reporting
C. Previous-period posting status and authorizations
D. Debit prepaid expenses; credit expense

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 391 | **A** | Check for duplicate valuations and any reversals. |
| 392 | **B** | Maintain an audit trail. |
| 393 | **C** | Changes to closed periods require approval. |
| 394 | **D** | It improves closing quality and repeatability. |
| 395 | **A** | Recognize the incurred but unpaid amount as a liability. |
| 396 | **B** | Reclassify the portion relating to future periods out of current expenses. |
| 397 | **C** | Posting depends on the valued item and accounting configuration. |
| 398 | **D** | Investigate differences in recording dates. |
| 399 | **A** | Compare reports using consistent selection criteria. |
| 400 | **B** | Validate each processing result and the financial statements. |

---

