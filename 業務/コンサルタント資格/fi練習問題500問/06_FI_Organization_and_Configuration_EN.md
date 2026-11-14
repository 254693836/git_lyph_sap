# Part 6: FI Organizational Structure and Basic Configuration (Questions 51–100)

English translation of the original Japanese practice questions. **50 original four-option questions**, one correct answer each. Answers and explanations appear after every 10 questions. Standard SAP S/4HANA settings are assumed unless stated otherwise.

## Set 1: Questions 51–60

### Question 51

Which FI organizational unit can produce its own balance sheet and income statement?

A. Company Code
B. Controlling Area
C. Segment
D. Sales Organization

### Question 52

Which organizational unit allows CO management across multiple company codes?

A. Profit Center
B. Controlling Area
C. Plant
D. Company (Company ID)

### Question 53

Which unit is used to analyze revenues and expenses by area of responsibility?

A. Segment
B. Purchasing Organization
C. Profit Center
D. Operating Concern

### Question 54

Which characteristic is used for financial reporting by business division?

A. Plant
B. Sales Organization
C. Chart of Depreciation
D. Segment

### Question 55

Which MM organizational unit manages inventory and goods movements and is assigned to a company code?

A. Plant
B. Purchasing Organization
C. Company (Company ID)
D. Company Code

### Question 56

Which organizational unit manages purchasing responsibilities and conditions?

A. Sales Organization
B. Purchasing Organization
C. Operating Concern
D. Controlling Area

### Question 57

Which SD organizational unit manages sales activities to customers?

A. Company (Company ID)
B. Chart of Depreciation
C. Sales Organization
D. Profit Center

### Question 58

Which organizational unit groups company codes for purposes such as consolidation?

A. Operating Concern
B. Company Code
C. Segment
D. Company (Company ID)

### Question 59

Which unit manages profitability by market segment in profitability analysis?

A. Operating Concern
B. Chart of Depreciation
C. Controlling Area
D. Plant

### Question 60

Which configuration object groups depreciation settings for fixed assets?

A. Company Code
B. Chart of Depreciation
C. Profit Center
D. Purchasing Organization

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 51 | **A** | A company code is the key accounting unit for external financial reporting. |
| 52 | **B** | A controlling area defines the organizational scope for cost accounting. |
| 53 | **C** | Profit centers support performance analysis by responsibility area. |
| 54 | **D** | Segment information supports reporting by business division. |
| 55 | **A** | A plant connects logistics operations with financial accounting. |
| 56 | **B** | Purchasing organizations can also be configured across company codes. |
| 57 | **C** | A sales organization is an organizational element of sales processing. |
| 58 | **D** | A company is distinct from a company code and can be used for consolidation purposes. |
| 59 | **A** | An operating concern is the organizational unit of CO-PA. |
| 60 | **B** | A chart of depreciation is assigned to company codes and defines asset valuation areas. |

---

## Set 2: Questions 61–70

### Question 61

What represents the G/L account structure used for daily postings?

A. Country Chart of Accounts
B. Chart of Accounts Segment
C. Operating Chart of Accounts
D. Posting Block

### Question 62

What supplements account mapping for country-specific statutory reporting?

A. Group Chart of Accounts
B. Company Code Segment
C. Reconciliation Account
D. Country Chart of Accounts

### Question 63

What supports a consistent account classification across a corporate group?

A. Group Chart of Accounts
B. Chart of Accounts Segment
C. Account Group
D. Open Item Management

### Question 64

Which G/L master data segment stores common account names and numbers?

A. Company Code Segment
B. Chart of Accounts Segment
C. Posting Block
D. Retained Earnings Account

### Question 65

Which G/L master data segment holds company-specific settings such as account currency and tax category?

A. Account Group
B. Reconciliation Account
C. Company Code Segment
D. Operating Chart of Accounts

### Question 66

What controls G/L account number ranges and master data field layout?

A. Posting Block
B. Open Item Management
C. Country Chart of Accounts
D. Account Group

### Question 67

What setting prevents new postings to an account while retaining its master data?

A. Posting Block
B. Reconciliation Account
C. Retained Earnings Account
D. Group Chart of Accounts

### Question 68

Which account reflects customer and supplier subledger balances in the G/L?

A. Open Item Management
B. Reconciliation Account
C. Operating Chart of Accounts
D. Chart of Accounts Segment

### Question 69

What setting tracks open and cleared items separately?

A. Retained Earnings Account
B. Country Chart of Accounts
C. Open Item Management
D. Company Code Segment

### Question 70

To which account are year-end P&L balances transferred?

A. Operating Chart of Accounts
B. Group Chart of Accounts
C. Account Group
D. Retained Earnings Account

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 61 | **C** | A company code normally uses one operating chart of accounts. |
| 62 | **D** | It supports country-specific financial reporting requirements. |
| 63 | **A** | It can be used to standardize consolidated reporting. |
| 64 | **B** | It holds basic account information shared across company codes. |
| 65 | **C** | It stores company-code-specific posting controls. |
| 66 | **D** | An account group controls G/L master record creation. |
| 67 | **A** | It restricts new postings without deleting historical data. |
| 68 | **B** | Postings are normally made through the subledger. |
| 69 | **C** | It tracks the clearing status of individual items, for example in GR/IR. |
| 70 | **D** | P&L balances are transferred during balance carryforward. |

---

## Set 3: Questions 71–80

### Question 71

Which setting defines the periods making up a fiscal year?

A. Fiscal Year Variant
B. Posting Period Variant
C. OB29
D. Posting Date

### Question 72

Which assigned variant controls the periods open for posting by company code?

A. OB52
B. Posting Period Variant
C. Special Periods 13–16
D. Document Date

### Question 73

Which transaction code opens and closes posting periods?

A. OB29
B. Shortened Fiscal Year
C. OB52
D. Entry Date

### Question 74

Which transaction code defines fiscal year variants?

A. Special Periods 13–16
B. Posting Date
C. Year-Dependent Fiscal Year Configuration
D. OB29

### Question 75

What is used for additional year-end adjustment postings?

A. Special Periods 13–16
B. Shortened Fiscal Year
C. Document Date
D. Fiscal Year Variant

### Question 76

What describes a fiscal year shorter than a normal year during a transition?

A. Posting Date
B. Shortened Fiscal Year
C. Entry Date
D. Posting Period Variant

### Question 77

Which document field determines the fiscal year and period from a date?

A. Document Date
B. Year-Dependent Fiscal Year Configuration
C. Posting Date
D. OB52

### Question 78

Which field records the date shown on the original source document?

A. Entry Date
B. Fiscal Year Variant
C. OB29
D. Document Date

### Question 79

Which field records when a document was entered into the system?

A. Entry Date
B. Year-Dependent Fiscal Year Configuration
C. Posting Period Variant
D. Special Periods 13–16

### Question 80

What is used when period start dates vary from year to year?

A. Fiscal Year Variant
B. Year-Dependent Fiscal Year Configuration
C. OB52
D. Shortened Fiscal Year

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 71 | **A** | It defines regular and special periods. |
| 72 | **B** | It can be shared by several company codes. |
| 73 | **C** | Posting periods are maintained for posting period variants. |
| 74 | **D** | It defines the period structure and year-dependent settings. |
| 75 | **A** | Use a posting date in the last regular period and specify the special period. |
| 76 | **B** | It is used when configuring transitional fiscal years. |
| 77 | **C** | This differs from the document date. |
| 78 | **D** | It holds dates such as the invoice date. |
| 79 | **A** | It is different from the posting date. |
| 80 | **B** | It allows the period structure to be specified for individual years. |

---

## Set 4: Questions 81–90

### Question 81

What is the standard document type for general G/L postings?

A. KR
B. KZ
C. SA
D. 50

### Question 82

What is the standard document type for supplier invoices?

A. DR
B. DZ
C. 31
D. KR

### Question 83

What is the standard document type for customer invoices?

A. DR
B. KZ
C. 40
D. 21

### Question 84

What is the standard document type for supplier payments?

A. DZ
B. KZ
C. 50
D. 01

### Question 85

What is the standard document type for customer incoming payments?

A. 40
B. 31
C. DZ
D. SA

### Question 86

Which standard posting key represents a G/L debit?

A. 50
B. 21
C. KR
D. 40

### Question 87

Which standard posting key represents a G/L credit?

A. 50
B. 31
C. 01
D. DR

### Question 88

Which standard posting key represents a supplier credit?

A. 21
B. 31
C. SA
D. KZ

### Question 89

Which standard posting key represents a supplier debit?

A. 01
B. KR
C. 21
D. DZ

### Question 90

Which standard posting key represents a customer debit?

A. SA
B. DR
C. 40
D. 01

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 81 | **C** | SA is the standard general accounting document type. |
| 82 | **D** | KR is the standard supplier invoice document type. |
| 83 | **A** | DR is the standard customer invoice document type. |
| 84 | **B** | KZ is the standard supplier payment document type. |
| 85 | **C** | DZ is the standard customer incoming payment document type. |
| 86 | **D** | Posting key 40 is used for G/L debit entries. |
| 87 | **A** | Posting key 50 is used for G/L credit entries. |
| 88 | **B** | Posting key 31 is used for supplier credit entries. |
| 89 | **C** | Posting key 21 is used for supplier debit entries. |
| 90 | **D** | Posting key 01 is used for customer debit entries. |

---

## Set 5: Questions 91–100

### Question 91

Which transaction code configures document types and their number ranges?

A. OBA7
B. OB41
C. Internal Number Assignment
D. Reference Document Number

### Question 92

Which transaction code configures posting keys?

A. Field Status Group
B. OB41
C. External Number Assignment
D. Reversal Posting

### Question 93

What setting makes G/L line-item fields required, optional, or hidden?

A. Internal Number Assignment
B. Header Text
C. Field Status Group
D. Company Code Currency

### Question 94

What numbering method assigns document numbers automatically from a defined range?

A. External Number Assignment
B. Reference Document Number
C. Change Impact Analysis
D. Internal Number Assignment

### Question 95

What numbering method allows a number to be supplied externally within an allowed range?

A. External Number Assignment
B. Header Text
C. Reversal Posting
D. OBA7

### Question 96

Which field stores a description applying to the whole accounting document?

A. Reference Document Number
B. Header Text
C. Company Code Currency
D. OB41

### Question 97

Which field helps match external invoice numbers?

A. Reversal Posting
B. Change Impact Analysis
C. Reference Document Number
D. Field Status Group

### Question 98

What process cancels an incorrect posting while preserving the audit trail?

A. Company Code Currency
B. OBA7
C. Internal Number Assignment
D. Reversal Posting

### Question 99

What currency is configured as the local currency of a company code?

A. Company Code Currency
B. Change Impact Analysis
C. OB41
D. External Number Assignment

### Question 100

What activity evaluates chart-of-accounts, company-code, and document dependencies before moving configuration into production?

A. OBA7
B. Change Impact Analysis
C. Field Status Group
D. Header Text

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 91 | **A** | Document types are assigned number ranges and other controls. |
| 92 | **B** | Posting keys define account types and debit/credit indicators. |
| 93 | **C** | It controls input fields for G/L account line items. |
| 94 | **D** | The system assigns a number from a configured interval. |
| 95 | **A** | A permitted document number is supplied by an external source. |
| 96 | **B** | Its scope differs from individual line-item texts. |
| 97 | **C** | It helps trace source documents and identify duplicates. |
| 98 | **D** | A reversal document is recorded rather than deleting the original document. |
| 99 | **A** | Additional currencies can be configured separately. |
| 100 | **B** | Dependencies should be assessed before FI configuration changes. |

---

