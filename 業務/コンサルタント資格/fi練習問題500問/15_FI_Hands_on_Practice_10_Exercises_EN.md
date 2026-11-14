# SAP FI Certification Preparation — Hands-on Practice (SAP S/4HANA On-Premise / Private Cloud)

> **These are original exercises for self-study, not official SAP exam tasks or scoring criteria.** Use them alongside the [500 FI practice questions](README.md) to connect knowledge with configuration checks, postings, clearing, and verification in SAP GUI.

- **Audience:** Learners with access to SAP S/4HANA On-Premise / Private Cloud and SAP GUI.
- **Structure:** 10 exercises × 10 points = 100 points (self-study target: 90).
- **Time:** Approximately 3–5 hours, excluding environment setup and troubleshooting; one exercise per day is also possible.
- **Japanese version:** [SAP FI実機演習・10課題](15_FI実機演習_10課題.md).
- **Note:** Transaction codes and screens vary by release, authorizations, and customer-specific configuration. Work only within your permitted scope.

## Safety checks before starting

1. Use a **test client and test company code**. Never change master data or configuration, post accounting documents, or execute payments in production for these exercises.
2. Verify that an existing company code, G/L accounts, test Business Partners, bank-related accounts, and an open posting period are available. Amounts and codes in this guide are examples; follow your system's configuration.
3. Initially **display and inspect only** in `OB52`, `FBZP`, `OB08`, and `OBA7`. Make changes only in an approved test environment with proper authorization.
4. In `F110`, normally stop after **reviewing the payment proposal**. Do not execute payments or transmit payment media to banks.
5. Do not include real customer or supplier names, bank account numbers, or confidential data in screenshots or GitHub records.

## Overview of the 10 exercises

| No. | Exercise | Main transaction codes | Objective | Points |
|---|---|---|---|---:|
| 1 | FI organizational and basic settings | OBY6 / OB52 / OBA7 / FBN1 | Explain company code, posting periods, and document type settings | 10 |
| 2 | G/L accounts and accounting documents | FS00 / FB50 / FB03 | Post an expense entry and verify line items | 10 |
| 3 | Supplier invoice | BP / FB60 / FBL1N | Verify an invoice as an open supplier item | 10 |
| 4 | Supplier payment and clearing | F-53 / FBL1N | Verify clearing after payment | 10 |
| 5 | Customer invoicing and incoming payment | BP / FB70 / F-28 / FBL5N | Verify receivables and clearing | 10 |
| 6 | Automatic payments | FBZP / F110 | Review payment proposal and exclusion reasons | 10 |
| 7 | Asset Accounting | AS01 / F-90 / AW01N | Verify asset acquisition and planned depreciation | 10 |
| 8 | Foreign currency accounting | OB08 / FAGL_FCV | Explain exchange differences and valuation parameters | 10 |
| 9 | Closing and balance reconciliation | FBL1N / FBL5N / AW01N / F.01 / FAGLL03H | Reconcile subledgers with the G/L | 10 |
| 10 | Troubleshooting | OB52 / BP / FBZP / F110 | Explain causes, corrections, and retests | 10 |

---

## Exercise 1: FI Organizational and Basic Settings (10 points)

**Objective:** Determine whether a company code is ready to post accounting documents by reviewing organizational settings, posting periods, and document types. **Do not save changes or post documents in this exercise.**

### Step 1-1: OBY6 — Company Code Basic Settings (3 points)

1. Run `/nOBY6` in the SAP GUI command field.
2. Select the company code used for practice and display its details.
3. Record these six settings:

| Field | What to verify | Your answer |
|---|---|---|
| Company Code | Four-character company code | __________ |
| Chart of Accounts | Assigned chart of accounts | __________ |
| Currency | Company code currency | __________ |
| Fiscal Year Variant | Assigned fiscal year variant | __________ |
| Posting Period Variant | Assigned posting period variant | __________ |
| Field Status Variant | Assigned field status variant | __________ |

**Knowledge check:** Explain that the chart of accounts defines the available G/L account structure; the fiscal year variant defines the fiscal period structure; the posting period variant controls whether periods are open for posting; and the field status variant helps control entry fields. The standard `K4` variant is calendar-year based, with regular periods 1–12 and special periods 13–16.

**Scoring:** Basic settings verified: 1 point / fiscal year and posting period variants verified: 1 point / roles of settings explained: 1 point.

### Step 1-2: OB52 — Posting Periods (3 points)

1. Run `/nOB52` and find the **posting period variant** identified in OBY6.
2. Review rows for account types `+` (all types) and `S` (G/L). If relevant, also inspect `D` (customers), `K` (suppliers), `A` (assets), and `M` (materials).
3. Record account ranges, the **first and second posting period intervals** (From/To Period and Year), and any authorization group. The second interval is not necessarily reserved exclusively for special periods.
4. Determine whether a **G/L document dated November 2026** is permitted by the period configuration. If the fiscal year variant is not `K4`, first identify the corresponding fiscal period.

| Item to record | Your answer |
|---|---|
| Posting period variant | __________ |
| `+` period/year settings (first and second intervals) | __________ |
| `S` period/year settings (first and second intervals; state if no row exists) | __________ |
| Account ranges and authorization conditions for the G/L account | __________ |
| Can a November 2026 G/L document be posted? Explain why. | __________ |

**Decision guidance:** Check the relevant account type, account range, and authorization requirements in addition to the `+` row. An open period does not guarantee a successful posting if other master data or document errors exist.

**Scoring:** Variant verified: 1 point / account types and period intervals understood: 1 point / posting decision justified: 1 point.

### Step 1-3: OBA7 — Document Type SA (4 points)

1. Run `/nOBA7` and display document type `SA` (commonly used for general G/L postings).
2. Check the **description, number range, permitted account types, and number assignment settings**.
3. If necessary, inspect the actual number range in `FBN1` in **display-only mode** (check company code and fiscal year).
4. Explain whether `SA` permits debit and credit postings to G/L accounts and what happens if the number range is not configured.

| Item to record | Your answer |
|---|---|
| Document type | SA |
| Description | __________ |
| Number range key and configuration status | __________ |
| Permitted account types | __________ |
| Expected posting eligibility or errors | __________ |

**Scoring:** Identify SA: 1 point / verify number range: 1 point / verify permitted account types: 1 point / explain relationship between configuration and posting: 1 point.

**Exercise 1 deliverables:** Completed OBY6, OB52, and OBA7 tables, plus a justified decision about November 2026 posting eligibility. Exclude confidential data.

---

## Exercise 2: G/L Accounts and Accounting Documents (10 points)

**Task:** Post **JPY 30,000 expense / JPY 30,000 accrued expense liability** in a test company code.

1. In `FS00`, verify that the expense and accrued liability accounts exist, are extended to the company code, and permit posting.
2. In `FB50`, enter the posting date, document date, company code, currency `JPY`, and the following journal entry.
3. If the expense account requires a cost center, provide a suitable test cost center.
4. Simulate to confirm balanced debits and credits, post in the test environment, and inspect the result in `FB03` or G/L line-item reporting.

| Debit | Credit |
|---|---|
| Expense account: JPY 30,000 | Accrued expense liability account: JPY 30,000 |

**Pass criteria:** A posted document number exists; debit and credit are each JPY 30,000; G/L line items agree. **Evidence:** Document number, posting date, accounts, and amounts.

## Exercise 3: Supplier Invoice (10 points)

**Task:** Enter a **JPY 100,000 supplier invoice without tax** for a test supplier.

1. In `BP`, verify role `FLVN00` (FI supplier), company code data, reconciliation account, and payment terms.
2. In `FB60`, enter the test supplier, company code, dates, currency, expense account, and JPY 100,000. This is a **no-tax example**; follow the tax configuration of your test system.
3. After posting, check the open item and due date in `FBL1N`.

| Debit | Credit |
|---|---|
| Expense: JPY 100,000 | Supplier: JPY 100,000 |

**Pass criteria:** A JPY 100,000 open item appears for the supplier. **Evidence:** Invoice document number, supplier, due date, and open-item status.

## Exercise 4: Supplier Payment and Clearing (10 points)

**Task:** Process payment for the JPY 100,000 invoice from Exercise 3 and verify clearing.

1. In `F-53`, enter the payment date, company code, amount, and a **test bank clearing account or equivalent**.
2. Select the supplier open item from Exercise 3 and verify that there is no amount difference.
3. Post in the test environment, then verify the invoice and payment clearing status in `FBL1N`.

| Debit | Credit |
|---|---|
| Supplier: JPY 100,000 | Bank-related account: JPY 100,000 |

**Pass criteria:** The invoice is cleared and the clearing document number is visible. **Caution:** SAP payment posting and an actual bank transfer are separate processes. Do not send money to a real bank.

## Exercise 5: Customer Invoice and Incoming Payment Clearing (10 points)

**Task:** Issue a **JPY 80,000 invoice without tax** to a test customer and clear it with an equal incoming payment.

1. In `BP`, verify role `FLCU00` (FI customer), company code data, and reconciliation account.
2. In `FB70`, post a JPY 80,000 customer invoice. Entry: **Debit customer JPY 80,000 / Credit revenue JPY 80,000**.
3. In `F-28`, post JPY 80,000 incoming payment and select the invoice for clearing. Entry: **Debit bank-related account JPY 80,000 / Credit customer JPY 80,000**.
4. In `FBL5N`, confirm the transition from open to cleared status.

**Pass criteria:** Invoice, incoming payment, and clearing details can all be traced.

## Exercise 6: F110 Automatic Payment (10 points)

**Task:** Run **through payment proposal only** for a test supplier invoice.

1. In `FBZP`, **display and review** payment methods (country and company code), bank determination, paying company codes, and related settings.
2. Prepare a due, unpaid test supplier invoice. Check payment blocks, the BP payment method, and bank details.
3. In `F110`, specify a run date and identification, then maintain parameters including company codes, payment methods, posting date, next payment date, and supplier selection ranges.
4. Generate the **payment proposal** and inspect selected items, exception logs, and reasons for exclusion. **Do not execute payment or transmit bank files.**

**Pass criteria:** Explain why an item is selected or excluded using due dates, payment blocks, payment methods, and bank configuration. **Evidence:** Run date, identification, and proposal log with confidential information removed.

## Exercise 7: Asset Accounting (10 points)

**Task:** Create a test asset with **acquisition cost JPY 600,000, useful life 5 years, zero residual value, and straight-line depreciation**.

1. In `AS01`, create the asset master with an appropriate test asset class, company code, cost center, and other required data.
2. Review depreciation areas, depreciation key, useful life, and depreciation start date.
3. In `F-90`, acquire the JPY 600,000 asset from a test supplier (or follow the acquisition process configured in your system).
4. In `AW01N`, inspect acquisition cost, planned depreciation, and asset values, then reconcile with G/L postings.

**Illustrative annual straight-line depreciation:** JPY 600,000 ÷ 5 = **JPY 120,000**. Actual depreciation by period depends on the depreciation key, period control, acquisition date, and related settings.

**Pass criteria:** Acquisition cost agrees with accounting postings, and you can explain the planned depreciation. **Caution:** Run actual depreciation posting with `AFAB` only in an approved test environment.

## Exercise 8: Foreign Currency Accounting (10 points)

**Task:** Calculate the settlement exchange difference for a USD-denominated receivable and distinguish it from foreign currency valuation.

| Item | Value |
|---|---|
| Invoice amount | USD 100 |
| Exchange rate at invoicing | USD 1 = JPY 150 |
| Exchange rate at settlement | USD 1 = JPY 148 |
| Invoice value in JPY | JPY 15,000 |
| Settlement value in JPY | JPY 14,800 |
| Difference | **JPY 200 realized foreign exchange loss (receivable example)** |

1. In `OB08`, check the currency pair, exchange rate type, and effective date (**do not change them**).
2. Calculate and explain the JPY 200 realized exchange loss.
3. If `FAGL_FCV` is available, review the valuation key date, valuation method, and ledger for **period-end valuation of open foreign currency items**; inspect results using test or simulation mode.
4. Distinguish **realized exchange gains/losses on settlement** from **unrealized exchange gains/losses on period-end valuation**.

**Pass criteria:** Calculate the JPY 200 loss and explain the role of valuation dates, rates, and ledgers. Example rates may not match those maintained in the SAP system.

## Exercise 9: Financial Closing and Balance Reconciliation (10 points)

**Task:** Reconcile the following using consistent company code, reporting period, ledger, and currency:

1. Supplier line items in `FBL1N` against the accounts payable reconciliation account balance.
2. Customer line items in `FBL5N` against the accounts receivable reconciliation account balance.
3. Asset register values in `AW01N` or equivalent reports against fixed asset G/L balances.
4. Financial statements in `F.01` against G/L line items in `FAGLL03H` or other reports available in the environment.

**Pass criteria:** Explain any differences and their possible causes. When comparing open-item balances with entire account balances, ensure that the **population, key date, clearing status, and accounts** are aligned. **Evidence:** Selection criteria, balances, differences, and findings.

## Exercise 10: FI Troubleshooting (10 points)

**Task:** For each of the following cases, document **error → possible cause → where to check → proposed correction → retest**.

| Case | Main checks | Example retest |
|---|---|---|
| Posting period is closed | OB52, posting date, posting period variant | Simulate a posting in an authorized period |
| Supplier invoice cannot be entered | BP company code data, reconciliation account, field controls | Enter and simulate in FB60 |
| Invoice is missing from an F110 proposal | Due date, payment block, payment method, selection criteria, exception log | Recreate the proposal with the same criteria and inspect the log |

**Pass criteria:** For each case, provide a plausible, evidence-based cause, investigation steps, and retest conditions. Configuration changes require approval and an authorized test environment.

---

## Scoring Sheet

Exercise 1 uses **OBY6: 3 points + OB52: 3 points + OBA7: 4 points**. Exercises 2–10 each use the following 10-point rubric:

| Criterion | Points |
|---|---:|
| Correct configuration checks and operations | 4 |
| Correct accounting or processing results | 4 |
| Evidence such as document numbers, logs, or line items | 2 |
| **Total** | **10** |

| Exercise | Score (0–10) | Document number / log / comments |
|---|---:|---|
| 1. FI basic settings | ___ | ___ |
| 2. G/L | ___ | ___ |
| 3. AP invoice | ___ | ___ |
| 4. AP payment and clearing | ___ | ___ |
| 5. AR invoice and receipt | ___ | ___ |
| 6. F110 | ___ | ___ |
| 7. Asset Accounting | ___ | ___ |
| 8. Foreign currency | ___ | ___ |
| 9. Closing and reconciliation | ___ | ___ |
| 10. Troubleshooting | ___ | ___ |
| **Total** | **___ / 100** | |

**Self-study target:** 90 points or higher. This is **not an official SAP passing threshold**. Record the cause of any unsuccessful exercise and repeat it.

## Additional Configuration Exercises (Approved Test Environment Only)

- `OBA7`: Design a custom document type and number range; check consistency with `FBN1`.
- `FBZP`: Configure payment methods and bank determination; check the impact on `F110` proposals.
- `OB52`: Test open and closed posting period controls and reproduce errors (consider impacts on other users).
- `MIGO` / `MIRO`: Check MM goods receipt, invoice verification, and GR/IR postings when the required MM data is available.

## Recommended Study Sequence

1. Review the related questions from the 500-question set for 20 minutes.
2. Perform the day's SAP exercise for 40 minutes and record the results.
3. When a step fails, record the error message, relevant settings, and posting result before retrying.
4. Finally, explain the full flow **configuration → posting → clearing → balance reconciliation** independently.

**Related resources:** [FI practice questions 500 — Japanese and English index](README.md) / [SAP official certifications](https://learning.sap.com/certifications)
