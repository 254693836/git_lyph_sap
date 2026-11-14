# Part 13: FI Troubleshooting, Configuration Issues, and Practical Cases (Questions 401–450)

English translation of the corresponding Japanese FI practice questions. **50 original four-option single-answer questions**, preserving the original question numbers, option order, and answer keys. Answers and explanations appear after each group of ten questions. Transaction codes primarily refer to SAP S/4HANA Private Edition using SAP GUI.

[Japanese version](13_障害対応と実務ケース.md)

## Set 1: Questions 401–410

### Question 401

A company code's posting period is closed. What should be checked first?

A. Posting periods in OB52 and the posting date
B. Chart of accounts assignment and extension of the G/L account to the company code
C. Business Partner company code data
D. FBZP and the Business Partner's payment method

### Question 402

A G/L posting fails in a new company code. What should be checked?

A. CO account assignment and field controls
B. Chart of accounts assignment and extension of the G/L account to the company code
C. SD account determination settings
D. Payment due date and payment block

### Question 403

An expense posting reports that a cost center is required. What should be checked?

A. Business Partner company code data
B. OBYC and the valuation class
C. CO account assignment and field controls
D. Payment medium generation settings and payment run results

### Question 404

A supplier invoice reports that no reconciliation account is defined. What should be checked?

A. SD account determination settings
B. FBZP and the Business Partner's payment method
C. Reference numbers and matching rules
D. Business Partner company code data

### Question 405

A customer invoice is posted to an incorrect revenue account. What should be checked?

A. SD account determination settings
B. OBYC and the valuation class
C. Payment due date and payment block
D. Posting periods in OB52 and the posting date

### Question 406

An MM goods receipt fails due to G/L account determination. What should be checked?

A. FBZP and the Business Partner's payment method
B. OBYC and the valuation class
C. Payment medium generation settings and payment run results
D. Chart of accounts assignment and extension of the G/L account to the company code

### Question 407

Automatic payment processing reports that no payment method is available. What should be checked?

A. Payment due date and payment block
B. Reference numbers and matching rules
C. FBZP and the Business Partner's payment method
D. CO account assignment and field controls

### Question 408

An invoice is missing from the payment proposal. What should be checked?

A. Payment medium generation settings and payment run results
B. Posting periods in OB52 and the posting date
C. Business Partner company code data
D. Payment due date and payment block

### Question 409

No payment medium file was generated. What should be checked?

A. Payment medium generation settings and payment run results
B. Reference numbers and matching rules
C. Chart of accounts assignment and extension of the G/L account to the company code
D. SD account determination settings

### Question 410

A bank statement item is not cleared automatically. What should be checked?

A. Posting periods in OB52 and the posting date
B. Reference numbers and matching rules
C. CO account assignment and field controls
D. OBYC and the valuation class

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 401 | **A** | Check the posting period variant assigned to the relevant company code. |
| 402 | **B** | Verify organizational assignments and the account master record. |
| 403 | **C** | Check cost center entry requirements and derivation settings. |
| 404 | **D** | Check the supplier's reconciliation account. |
| 405 | **A** | Check revenue account determination, such as VKOA. |
| 406 | **B** | Review automatic account determination in MM. |
| 407 | **C** | Review country-level, company-code-level, and master data conditions. |
| 408 | **D** | Also review selection parameters and the exception log. |
| 409 | **A** | Investigate payment posting separately from payment medium generation. |
| 410 | **B** | Check the criteria used to identify matching items. |

---

## Set 2: Questions 411–420

### Question 411

Foreign currency valuation cannot find an exchange rate. What should be checked?

A. Valuation method, key date, and ledger
B. Depreciation key, start date, and useful life
C. Currency pair, date, and exchange rate type in OB08
D. Items selected for clearing and amount differences

### Question 412

Foreign currency valuation produces an unexpected result. What should be checked?

A. Asset class and automatic account determination
B. Posting period, account determination, and depreciation run log
C. Payment documents and clearing information
D. Valuation method, key date, and ledger

### Question 413

A fixed asset acquisition fails due to account configuration. What should be checked?

A. Asset class and automatic account determination
B. Depreciation key, start date, and useful life
C. Asset register and accounting posting line items
D. Clearing status and reversal reason

### Question 414

Depreciation is not being calculated. What should be checked?

A. Posting period, account determination, and depreciation run log
B. Depreciation key, start date, and useful life
C. Items selected for clearing and amount differences
D. Tax code and tax calculation procedure

### Question 415

Depreciation posting fails. What should be checked?

A. Asset register and accounting posting line items
B. Payment documents and clearing information
C. Posting period, account determination, and depreciation run log
D. Currency pair, date, and exchange rate type in OB08

### Question 416

Fixed Asset Accounting and G/L balances do not match. What should be checked?

A. Items selected for clearing and amount differences
B. Clearing status and reversal reason
C. Valuation method, key date, and ledger
D. Asset register and accounting posting line items

### Question 417

A customer invoice remains open after receipt of payment. What should be checked?

A. Items selected for clearing and amount differences
B. Payment documents and clearing information
C. Tax code and tax calculation procedure
D. Asset class and automatic account determination

### Question 418

Supplier open items remain uncleared after payment. What should be checked?

A. Clearing status and reversal reason
B. Payment documents and clearing information
C. Currency pair, date, and exchange rate type in OB08
D. Depreciation key, start date, and useful life

### Question 419

Reversal of an accounting document is rejected. What should be checked?

A. Tax code and tax calculation procedure
B. Valuation method, key date, and ledger
C. Clearing status and reversal reason
D. Posting period, account determination, and depreciation run log

### Question 420

A calculated tax amount is incorrect. What should be checked?

A. Currency pair, date, and exchange rate type in OB08
B. Asset class and automatic account determination
C. Asset register and accounting posting line items
D. Tax code and tax calculation procedure

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 411 | **C** | Verify that the required exchange rate exists. |
| 412 | **D** | Review the parameters used for the valuation run. |
| 413 | **A** | Also review the transaction type and depreciation areas. |
| 414 | **B** | Review the asset master and depreciation settings. |
| 415 | **C** | Isolate the cause using the relevant error information. |
| 416 | **D** | Investigate missing postings and incorrect G/L accounts. |
| 417 | **A** | Posting an incoming payment does not always clear the invoice automatically. |
| 418 | **B** | Verify which open items correspond to the payment. |
| 419 | **C** | For cleared items, resetting clearing with FBRA may be necessary. |
| 420 | **D** | Also verify the tax base and rounding. |

---

## Set 3: Questions 421–430

### Question 421

A required G/L posting field does not appear on the screen. What should be checked?

A. Conflicting field status settings
B. Number ranges and external number assignment
C. Account assignment in the Financial Statement Version
D. Unmatched goods receipt and invoice receipt items

### Question 422

An accounting document number is duplicated. What should be checked?

A. Approval status and posting errors
B. Number ranges and external number assignment
C. Derivation settings from cost centers and other objects
D. Unimported bank statement items and outstanding transactions

### Question 423

A parked document cannot be posted. What should be checked?

A. Account assignment in the Financial Statement Version
B. Document splitting and zero-balance settings
C. Approval status and posting errors
D. Fiscal year variant and posting periods

### Question 424

A G/L account does not appear in the financial statements. What should be checked?

A. Derivation settings from cost centers and other objects
B. Unmatched goods receipt and invoice receipt items
C. Posting date in the last regular period and special period selection
D. Account assignment in the Financial Statement Version

### Question 425

The profit center is blank in a posting. What should be checked?

A. Derivation settings from cost centers and other objects
B. Document splitting and zero-balance settings
C. Unimported bank statement items and outstanding transactions
D. Conflicting field status settings

### Question 426

The segment balance sheet is out of balance. What should be checked?

A. Unmatched goods receipt and invoice receipt items
B. Document splitting and zero-balance settings
C. Fiscal year variant and posting periods
D. Number ranges and external number assignment

### Question 427

The GR/IR balance is unusually high at closing. What should be checked?

A. Unimported bank statement items and outstanding transactions
B. Posting date in the last regular period and special period selection
C. Unmatched goods receipt and invoice receipt items
D. Approval status and posting errors

### Question 428

Bank balances do not reconcile. What should be checked?

A. Fiscal year variant and posting periods
B. Conflicting field status settings
C. Account assignment in the Financial Statement Version
D. Unimported bank statement items and outstanding transactions

### Question 429

A posting across fiscal years fails. What should be checked?

A. Fiscal year variant and posting periods
B. Posting date in the last regular period and special period selection
C. Number ranges and external number assignment
D. Derivation settings from cost centers and other objects

### Question 430

Posting to a special period fails. What should be checked?

A. Conflicting field status settings
B. Posting date in the last regular period and special period selection
C. Approval status and posting errors
D. Document splitting and zero-balance settings

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 421 | **A** | Check field controls from both the G/L account and the posting key. |
| 422 | **B** | Review the document type and fiscal-year-specific number ranges. |
| 423 | **C** | Check posting conditions, for example in FBV0. |
| 424 | **D** | Also verify report selection criteria. |
| 425 | **A** | Review account assignments and relevant master data. |
| 426 | **B** | Also review derivation of splitting characteristics. |
| 427 | **C** | Investigate quantity and price differences. |
| 428 | **D** | Reconcile bank statements with the bank G/L account. |
| 429 | **A** | Verify period settings for the target fiscal year. |
| 430 | **B** | Also check whether the special period is open. |

---

## Set 4: Questions 431–440

### Question 431

A newly created document type cannot be used for posting. What should be checked?

A. Account group and number range
B. FLCU00 role and company code data
C. Account types and number ranges in OBA7
D. Reference number and duplicate invoice check settings

### Question 432

A new G/L account cannot be created. What should be checked?

A. FLVN00 role and company code data
B. Business Partner bank data and payment method
C. Clearing document number and payment history
D. Account group and number range

### Question 433

A supplier Business Partner role is missing. What should be checked?

A. FLVN00 role and company code data
B. FLCU00 role and company code data
C. Cash discounts and payment terms
D. Dunning procedure, due date, and dunning block

### Question 434

A customer Business Partner role is missing. What should be checked?

A. Business Partner bank data and payment method
B. FLCU00 role and company code data
C. Reference number and duplicate invoice check settings
D. Aging report and dunning and collection conditions

### Question 435

The recipient's bank account is not selected for payment. What should be checked?

A. Cash discounts and payment terms
B. Clearing document number and payment history
C. Business Partner bank data and payment method
D. Account types and number ranges in OBA7

### Question 436

The payment amount is lower than expected. What should be checked?

A. Reference number and duplicate invoice check settings
B. Dunning procedure, due date, and dunning block
C. Account group and number range
D. Cash discounts and payment terms

### Question 437

A duplicate invoice has been entered. What should be checked?

A. Reference number and duplicate invoice check settings
B. Clearing document number and payment history
C. Aging report and dunning and collection conditions
D. FLVN00 role and company code data

### Question 438

An invoice shows as cleared even though it has not been paid. What should be checked?

A. Dunning procedure, due date, and dunning block
B. Clearing document number and payment history
C. Account types and number ranges in OBA7
D. FLCU00 role and company code data

### Question 439

A customer dunning notice is not generated. What should be checked?

A. Aging report and dunning and collection conditions
B. Account group and number range
C. Dunning procedure, due date, and dunning block
D. Business Partner bank data and payment method

### Question 440

Many customer receivables are overdue. What should be checked?

A. Account types and number ranges in OBA7
B. FLVN00 role and company code data
C. Cash discounts and payment terms
D. Aging report and dunning and collection conditions

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 431 | **C** | Review document type controls. |
| 432 | **D** | Also review master data field controls. |
| 433 | **A** | Add or verify the FI supplier role as appropriate. |
| 434 | **B** | Verify the FI customer role. |
| 435 | **C** | Also review bank determination settings. |
| 436 | **D** | Review discount deadlines and tax treatment. |
| 437 | **A** | Review business rules that prevent duplicate entry. |
| 438 | **B** | Verify whether the clearing was valid. |
| 439 | **C** | Check the conditions for the affected open items. |
| 440 | **D** | Categorize overdue receivables and plan follow-up actions. |

---

## Set 5: Questions 441–450

### Question 441

An incoming foreign currency payment results in a large exchange gain or loss. What should be checked?

A. Invoice and settlement exchange rates and amounts
B. Ledger group postings and valuation differences
C. Substitution rules and master data account assignments
D. Transported objects, dependent settings, and master data differences

### Question 442

Balances differ across multiple ledgers. What should be checked?

A. Journal entry line items and closing adjustment postings
B. Ledger group postings and valuation differences
C. Activation of validation and its prerequisite conditions
D. Analyze business requirements and gaps against standard functionality

### Question 443

Monthly closing figures show an unexpected change from the prior month. What should be checked?

A. Substitution rules and master data account assignments
B. Authorization roles and error details
C. Journal entry line items and closing adjustment postings
D. Side effects on existing business processes

### Question 444

A cost center on an accounting document is incorrect. What should be checked?

A. Activation of validation and its prerequisite conditions
B. Transported objects, dependent settings, and master data differences
C. Reproduction conditions, root cause, corrective action, and verification results
D. Substitution rules and master data account assignments

### Question 445

Document input validation does not run. What should be checked?

A. Activation of validation and its prerequisite conditions
B. Authorization roles and error details
C. Analyze business requirements and gaps against standard functionality
D. Invoice and settlement exchange rates and amounts

### Question 446

A user cannot display an FI document because of insufficient authorization. What should be checked?

A. Transported objects, dependent settings, and master data differences
B. Authorization roles and error details
C. Side effects on existing business processes
D. Ledger group postings and valuation differences

### Question 447

Posting fails after transporting configuration to production. What should be checked?

A. Analyze business requirements and gaps against standard functionality
B. Reproduction conditions, root cause, corrective action, and verification results
C. Transported objects, dependent settings, and master data differences
D. Journal entry line items and closing adjustment postings

### Question 448

A customer's requirement differs from standard SAP functionality. What should be done first?

A. Side effects on existing business processes
B. Invoice and settlement exchange rates and amounts
C. Substitution rules and master data account assignments
D. Analyze business requirements and gaps against standard functionality

### Question 449

What should regression testing cover after changing FI configuration?

A. Side effects on existing business processes
B. Reproduction conditions, root cause, corrective action, and verification results
C. Ledger group postings and valuation differences
D. Activation of validation and its prerequisite conditions

### Question 450

What information should be recorded when resolving an incident?

A. Invoice and settlement exchange rates and amounts
B. Reproduction conditions, root cause, corrective action, and verification results
C. Journal entry line items and closing adjustment postings
D. Authorization roles and error details

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 441 | **A** | Recalculate and validate the exchange difference. |
| 442 | **B** | Review differences arising from accounting standards. |
| 443 | **C** | Trace the cause of unusual movements. |
| 444 | **D** | Review automatic derivation settings. |
| 445 | **A** | Review the call-up point and conditions. |
| 446 | **B** | Determine the minimum necessary authorization. |
| 447 | **C** | Compare configuration and data between environments. |
| 448 | **D** | Assess whether the standard solution can meet the requirement before extending it. |
| 449 | **A** | Test normal, error, and boundary cases. |
| 450 | **B** | This supports prevention of recurrence and handover. |

---

