# SAP FI Certification: 50 Practice Questions in English (with Answers and Explanations)

> Created: November 14, 2026. These are **50 original, single-answer multiple-choice questions**, not official SAP past exam questions. The C_TS4FI / C_S4CFI certifications use practical assessments; this set is intended to check FI knowledge.

[FI Certification Guide (Japanese)](../fi資格.md) | [SAP Official Certifications](https://learning.sap.com/certifications) | [Japanese version](05_FI基礎.md)

- **50 questions**, 10 per topic, **2 points each** (100 points total).
- Suggested self-study target: **80 points or more**. This is **not** an official SAP passing score.
- Answer each group of 10 questions before checking the answer key and explanations immediately below it.

## Part 1: FI Fundamentals, Organizational Structure, and Basic Configuration (Questions 1–10)

### Question 1

What is the primary purpose of a company code?

A. A unit for managing warehouses
B. An accounting unit for which independent financial statements can be prepared
C. A unit for managing sales prices
D. A unit for managing purchase orders

### Question 2

How many operating charts of accounts are normally assigned to one company code?

A. One
B. Two
C. An unlimited number
D. None is required

### Question 3

What is defined by a fiscal year variant?

A. Tax rates
B. The structure of the fiscal year and posting periods
C. Payment methods
D. Document number ranges

### Question 4

When using special periods 13–16, which statement about the posting date is correct?

A. Use a date in January of the following fiscal year
B. Any date may be used
C. Use a date within the final regular posting period of the fiscal year
D. Only the document date needs to be entered

### Question 5

What is transaction code OB52 used for?

A. Opening and closing posting periods
B. Creating G/L accounts
C. Running automatic payments
D. Creating asset classes

### Question 6

Which statement about a posting period variant is correct?

A. It can be shared by multiple company codes
B. Each company code must have a different variant
C. It can only be assigned to a controlling area
D. It is the same as a fiscal year variant

### Question 7

What is the primary purpose of a document type?

A. Determining debit and credit
B. Controlling document number ranges and permitted account types
C. Calculating account balances
D. Determining consumption tax rates

### Question 8

What key information is determined by a posting key?

A. Fiscal year and company code
B. Account type and debit or credit indicator
C. Currency and exchange rate
D. Document type and number range

### Question 9

What is the primary purpose of a field status group?

A. Controlling whether line-item fields are required, optional, or hidden
B. Calculating taxes automatically
C. Determining payment dates
D. Opening posting periods

### Question 10

Which statement about a reconciliation account is correct?

A. It is intended for directly posting all journal entries manually
B. It links subledgers, such as customer and supplier accounts, to the general ledger
C. It controls asset depreciation rates
D. It is used to create tax codes

### Part 1: Answer Key and Explanations

| Question | Answer | Explanation |
|---|---|---|
| 1 | **B** | A company code is a fundamental FI organizational unit for which a balance sheet and income statement can be prepared. |
| 2 | **A** | One operating chart of accounts is assigned to each company code. |
| 3 | **B** | The period structure of a fiscal year is defined in OB29. |
| 4 | **C** | Special periods are used for year-end adjustments. The posting date must fall within the final regular period, and the special period must also be specified. |
| 5 | **A** | OB52 specifies which posting periods are open for each posting period variant. |
| 6 | **A** | The same posting period variant can be assigned to multiple company codes. |
| 7 | **B** | Document types are configured in OBA7 and control settings such as number ranges and allowed account types. |
| 8 | **B** | Posting keys are defined in OB41. Key 40 is commonly used for a G/L debit and key 50 for a G/L credit. |
| 9 | **A** | Field status controls field visibility and input requirements. The interaction with field controls from posting keys must also be considered. |
| 10 | **B** | Customer and supplier postings update the G/L through reconciliation accounts. Direct postings to reconciliation accounts are normally not permitted. |

---

## Part 2: Master Data and Accounting Documents (Questions 11–20)

### Question 11

In SAP S/4HANA, which Business Partner role is used to maintain a supplier's FI accounting data?

A. FLVN01
B. FLCU00
C. FLVN00
D. FLCU01

### Question 12

What is transaction code FS00 used for?

A. Creating, changing, and displaying G/L account master data
B. Posting accounting documents
C. Importing bank statements
D. Creating Business Partners

### Question 13

Which statement about a profit and loss (P&L) account is correct?

A. Its balance is always carried forward to the same account in the next fiscal year
B. Its year-end balance is transferred to a retained earnings account during balance carryforward
C. It can only be used for customers
D. It can only be used for fixed assets

### Question 14

Which date primarily determines the fiscal year and posting period of an accounting document?

A. Posting date
B. Document date
C. Entry date
D. Payment date

### Question 15

Which statement correctly describes the difference between document date and posting date?

A. They must always be identical
B. The document date is the date on the source document, while the posting date determines the accounting period
C. Only the document date determines the accounting period
D. The posting date must always equal the system date

### Question 16

What is the main purpose of an FI tax code?

A. Controlling tax calculation and tax-related postings
B. Determining the company code
C. Issuing document numbers
D. Determining supplier numbers

### Question 17

What information is maintained in payment terms?

A. Bank account balances
B. Document number ranges
C. Payment due dates and cash discount conditions
D. Company code currency

### Question 18

What is the purpose of a G/L account group?

A. Determining the debit or credit indicator of a document
B. Opening or closing posting periods
C. Maintaining exchange rates
D. Controlling G/L account master number ranges and field layout

### Question 19

What is the purpose of open item management?

A. Tracking open and cleared line items
B. Creating fiscal years
C. Calculating asset useful lives
D. Creating charts of accounts

### Question 20

Which statement about primary cost elements in SAP S/4HANA is correct?

A. They are maintained as CO-only master records entirely separate from FI
B. They are maintained as G/L account master records with a cost element category
C. They are a type of supplier master record
D. They are a type of asset class

### Part 2: Answer Key and Explanations

| Question | Answer | Explanation |
|---|---|---|
| 11 | **C** | FLVN00 is the supplier FI role. FLVN01 is the supplier purchasing role. |
| 12 | **A** | FS00 is used to maintain G/L account master data. |
| 13 | **B** | P&L account balances are aggregated into the retained earnings account during year-end balance carryforward. |
| 14 | **A** | The posting date, together with the fiscal year variant, determines the posting period. |
| 15 | **B** | For example, an invoice dated October 31 can normally be posted in November if the posting date is November 1. |
| 16 | **A** | Tax is calculated using the tax code together with the tax calculation procedure and other relevant settings. |
| 17 | **C** | Payment terms are configured in OBB8 and are used for due-date calculation and cash discounts. |
| 18 | **D** | G/L account groups control number ranges and screen fields when G/L master records are created. |
| 19 | **A** | Open item management is used for line-item tracking in accounts such as GR/IR and clearing accounts. |
| 20 | **B** | In SAP S/4HANA, FI and CO master data are integrated, and cost elements are maintained as G/L accounts. |

---

## Part 3: Accounts Payable, Accounts Receivable, Payments, and Clearing (Questions 21–30)

### Question 21

What is the main purpose of transaction code FB60?

A. Entering a supplier invoice
B. Entering a customer invoice
C. Creating a G/L account master record
D. Running automatic payments

### Question 22

What is transaction code FB70 used to enter?

A. A supplier payment document
B. A customer invoice
C. A fixed asset master record
D. A bank statement

### Question 23

What is the main purpose of transaction code FB50?

A. Running automatic payments
B. Creating supplier master records
C. Posting accounting documents to G/L accounts
D. Posting asset depreciation

### Question 24

Which transaction code is commonly used to post a manual outgoing payment to a supplier?

A. F-53
B. F-28
C. FB70
D. FS00

### Question 25

Which transaction code is commonly used to post and clear an incoming payment from a customer?

A. F-44
B. F-28
C. FB60
D. OB52

### Question 26

Which transaction code is used to clear supplier open items?

A. F-03
B. F-32
C. F-44
D. FB50

### Question 27

Which transaction code is used to clear customer open items?

A. F-53
B. F-03
C. F-44
D. F-32

### Question 28

Which transaction code is used to clear G/L account open items?

A. F-03
B. F-28
C. F-110
D. FB60

### Question 29

What is the main purpose of transaction code F110?

A. Creating G/L account master records
B. Running the automatic payment program
C. Configuring posting periods
D. Creating fixed assets

### Question 30

Which statement about a payment method is correct?

A. It determines the fiscal year
B. It issues supplier numbers
C. It defines payment instruments such as bank transfers and checks
D. It carries forward G/L balances

### Part 3: Answer Key and Explanations

| Question | Answer | Explanation |
|---|---|---|
| 21 | **A** | FB60 is used for FI supplier invoice entry. A typical posting debits an expense and credits the supplier account. |
| 22 | **B** | FB70 is used to enter customer invoices. A typical posting debits the customer and credits revenue. |
| 23 | **C** | FB50 is used to enter G/L accounting documents. |
| 24 | **A** | F-53 is used to post manual outgoing payments. |
| 25 | **B** | F-28 is used to post customer incoming payments and clear open items. |
| 26 | **C** | F-44 is used to clear open items in supplier accounts. |
| 27 | **D** | F-32 is used to clear open items in customer accounts. |
| 28 | **A** | F-03 is used to clear open items in G/L accounts. |
| 29 | **B** | F110 supports automatic payment processing, including payment proposals and payment runs. |
| 30 | **C** | Payment methods define payment instruments such as transfers and checks. They are different from payment terms. |

---

## Part 4: Asset Accounting (Questions 31–40)

### Question 31

What is the primary purpose of an asset class?

A. Setting customer payment terms
B. Classifying fixed assets and controlling account determination and number ranges
C. Managing bank accounts
D. Opening or closing posting periods

### Question 32

Why are depreciation areas used?

A. To maintain different asset valuations for different accounting standards or valuation purposes
B. To manage customer credit limits
C. To configure supplier payment terms
D. To assign accounting document numbers

### Question 33

What is the role of a depreciation key?

A. Determining fixed asset numbers
B. Determining company codes
C. Determining supplier numbers
D. Controlling depreciation calculation methods

### Question 34

Under the straight-line depreciation method, what normally happens to annual depreciation when useful life increases?

A. It increases
B. It stays the same
C. It decreases
D. It always becomes zero

### Question 35

What is the main purpose of transaction code AFAB?

A. Executing depreciation posting
B. Entering supplier invoices
C. Posting customer incoming payments
D. Configuring posting periods

### Question 36

Which is the basic journal entry when a fixed asset is purchased on credit from a supplier? (Ignore tax.)

A. Debit: Expense / Credit: Revenue
B. Debit: Fixed Asset / Credit: Supplier
C. Debit: Supplier / Credit: Fixed Asset
D. Debit: Bank / Credit: Revenue

### Question 37

Which statement correctly describes the accounting treatment of an asset sale?

A. Only the asset master record needs to be deleted
B. The acquisition cost always remains unchanged
C. Only depreciation needs to be stopped
D. The asset's carrying amount is derecognized and any applicable gain or loss on disposal is recognized

### Question 38

What is the purpose of an Asset under Construction (AuC)?

A. Collecting and capitalizing costs related to an asset being constructed
B. Managing customer incoming payments
C. Managing supplier payment terms
D. Managing tax rates

### Question 39

Why is a cost center assigned to an asset master record?

A. To determine the fixed asset number
B. To determine the asset class
C. To assign expenses such as depreciation to the appropriate cost center
D. To change the company code

### Question 40

Which statement about accumulated depreciation is correct?

A. It increases the acquisition cost of a fixed asset
B. It is a component that reduces the net carrying amount of a fixed asset
C. It increases payables to suppliers
D. It increases customer receivables

### Part 4: Answer Key and Explanations

| Question | Answer | Explanation |
|---|---|---|
| 31 | **B** | Asset classes categorize assets such as buildings, machinery, and vehicles and control settings including account determination. |
| 32 | **A** | Depreciation areas support different valuation purposes, such as financial reporting and taxation. |
| 33 | **D** | Depreciation keys define rules for depreciation calculation, including methods and period controls. |
| 34 | **C** | With the same depreciable amount, a longer useful life results in a lower annual depreciation expense. |
| 35 | **A** | AFAB is used to post fixed asset depreciation. Depending on the SAP S/4HANA environment, a Fiori app may also be available. |
| 36 | **B** | The acquisition increases fixed assets and creates a payable to the supplier. |
| 37 | **D** | A sale requires asset retirement accounting and calculation of any gain or loss. |
| 38 | **A** | Costs can be collected in an AuC and transferred to a completed fixed asset when construction is finished. |
| 39 | **C** | Cost centers identify where expenses such as depreciation are charged. |
| 40 | **B** | Net book value is calculated by subtracting accumulated depreciation and applicable other adjustments from acquisition cost. |

---

## Part 5: Closing, Universal Journal, and Integration with Other Modules (Questions 41–50)

### Question 41

Which is the main line-item table of the Universal Journal in SAP S/4HANA?

A. ACDOCA
B. BKPF
C. MARA
D. VBAK

### Question 42

Which table typically stores FI accounting document header data?

A. MARC
B. BKPF
C. EKKO
D. KNA1

### Question 43

Which approach supports parallel accounting under different accounting standards in SAP S/4HANA?

A. Deleting all company codes
B. Changing only the document date
C. Using different ledgers to manage postings and valuations by accounting standard
D. Duplicating supplier master records

### Question 44

What is the purpose of foreign currency valuation?

A. Changing the company code currency every month
B. Changing supplier numbers
C. Changing asset useful lives
D. Revaluing foreign-currency open items and relevant balances at a valuation key date

### Question 45

What is the primary purpose of a GR/IR account?

A. Temporarily tracking differences or outstanding items between goods receipts and invoice receipts
B. Managing customer incoming payments
C. Managing fixed asset depreciation
D. Managing payroll payments

### Question 46

Which transaction code is commonly used for automatic account determination in MM–FI integration?

A. FB60
B. OBYC
C. F110
D. OB52

### Question 47

What is the main purpose of dunning?

A. Executing automatic supplier payments
B. Posting fixed asset depreciation
C. Following up on overdue customer receivables
D. Changing the fiscal year

### Question 48

Which statement about bank statement processing is correct?

A. It automatically creates fixed asset master records
B. It changes the fiscal year variant
C. It deletes the chart of accounts
D. It posts, matches, and clears incoming and outgoing bank transactions based on bank statements

### Question 49

What is the purpose of a Financial Statement Version?

A. Assigning G/L accounts to balance sheet and income statement items
B. Configuring supplier payment methods
C. Assigning fixed asset numbers
D. Opening bank accounts

### Question 50

Which statement about year-end balance carryforward is correct?

A. All accounting documents are deleted
B. Balance sheet account balances are carried into the next fiscal year, while P&L balances are transferred to retained earnings
C. All G/L accounts are recreated
D. All supplier master records are deleted

### Part 5: Answer Key and Explanations

| Question | Answer | Explanation |
|---|---|---|
| 41 | **A** | ACDOCA is the main Universal Journal line-item table and integrates information from FI, CO, and other areas. |
| 42 | **B** | BKPF stores accounting document headers. BSEG is used for accounting document entry-view line items. |
| 43 | **C** | Ledgers can be used to manage postings and valuations for different accounting standards. |
| 44 | **D** | Foreign-currency balances are revalued at closing, and applicable exchange gains or losses are recognized. |
| 45 | **A** | GR/IR is a clearing account connecting goods receipts and invoice receipts. |
| 46 | **B** | OBYC is used to configure automatic account determination for MM transactions such as inventory postings. |
| 47 | **C** | Dunning generates reminders or related notices for overdue receivables. A commonly used transaction code is F150. |
| 48 | **D** | Electronic bank statement processing supports accounting postings and clearing related to bank transactions. |
| 49 | **A** | A Financial Statement Version organizes G/L accounts into a hierarchy for financial statement reporting. |
| 50 | **B** | Balance sheet balances carry forward, and P&L balances are aggregated into the retained earnings account. |

---

## Key Topics to Review

- **FI fundamentals:** Company code, chart of accounts, fiscal year, OB52, OBA7, posting keys, reconciliation accounts.
- **G/L and Business Partners:** FS00, Business Partner roles, tax codes, payment terms, open item management.
- **AP and AR:** FB60, FB70, F-53, F-28, F-44, F-32, F-03, F110.
- **Asset Accounting:** Asset classes, depreciation areas, depreciation keys, AFAB, AuC.
- **Closing:** ACDOCA, BKPF, ledgers, foreign currency valuation, GR/IR, OBYC, dunning, balance carryforward.

To prepare for a practical certification assessment, use a real SAP environment to practice configuration, posting, clearing, and checking results after studying each topic.
