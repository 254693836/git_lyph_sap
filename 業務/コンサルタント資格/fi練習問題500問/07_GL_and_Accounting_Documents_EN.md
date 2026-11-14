# Part 7: General Ledger, Accounting Documents, Tax, and Currencies (Questions 101–150)

English translation of the Japanese question set. **50 original single-answer multiple-choice questions**, with the original option order and answer keys retained. Transaction codes primarily refer to SAP S/4HANA Private Edition using SAP GUI. Answers and explanations appear after every ten questions.

## Set 1: Questions 101–110

### Question 101

Which G/L account master attribute determines how an account is treated in year-end balance carryforward?

A. Balance sheet account vs. profit and loss account classification
B. The account cannot be used in that company code
C. A CO account assignment is required
D. Account number range and field layout

### Question 102

What happens if a G/L account has not been extended to a company code?

A. Permitted tax codes and tax entry requirements
B. The account cannot be used in that company code
C. Post through the customer or supplier subledger
D. Account currency

### Question 103

What does the tax category of a G/L account control?

A. A CO account assignment is required
B. Posting block
C. Permitted tax codes and tax entry requirements
D. Track individual posting line items

### Question 104

Why might a cost center be required when posting to an expense account?

A. Post through the customer or supplier subledger
B. Account number range and field layout
C. Distinguish open from cleared items
D. A CO account assignment is required

### Question 105

What is the usual approach when direct posting to a reconciliation account is not allowed?

A. Post through the customer or supplier subledger
B. Posting block
C. Account currency
D. Balance sheet account vs. profit and loss account classification

### Question 106

Which setting blocks new postings to a G/L account while preserving its history?

A. Account number range and field layout
B. Posting block
C. Track individual posting line items
D. The account cannot be used in that company code

### Question 107

What does a G/L account group control?

A. Account currency
B. Distinguish open from cleared items
C. Account number range and field layout
D. Permitted tax codes and tax entry requirements

### Question 108

Which is an example of an account attribute maintained at company code level?

A. Track individual posting line items
B. Balance sheet account vs. profit and loss account classification
C. A CO account assignment is required
D. Account currency

### Question 109

What is the purpose of displaying G/L account line items?

A. Track individual posting line items
B. Distinguish open from cleared items
C. The account cannot be used in that company code
D. Post through the customer or supplier subledger

### Question 110

What is the purpose of open item management for a G/L account?

A. Balance sheet account vs. profit and loss account classification
B. Distinguish open from cleared items
C. Permitted tax codes and tax entry requirements
D. Posting block

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 101 | **A** | Balance sheet account balances are carried forward, whereas P&L balances are transferred to retained earnings. |
| 102 | **B** | A chart-of-accounts-level record alone is not enough for posting. |
| 103 | **C** | The tax category controls tax code use during posting. |
| 104 | **D** | Configuration may require an expense posting to specify a cost object. |
| 105 | **A** | Reconciliation accounts normally reflect subledger postings. |
| 106 | **B** | The block restricts new postings without deleting existing history. |
| 107 | **C** | The account group controls master record creation. |
| 108 | **D** | Company-code-specific account settings are maintained at this level. |
| 109 | **A** | You can examine individual line items as well as account balances. |
| 110 | **B** | It tracks clearing status for items such as GR/IR. |

---

## Set 2: Questions 111–120

### Question 111

Which transaction code is commonly used to display an accounting document?

A. FB02
B. FBRA
C. FB03
D. Personal temporary save of incomplete entry

### Question 112

Which transaction code changes fields that are permitted to be changed in an accounting document?

A. FB08
B. FBV0
C. FBD1
D. FB02

### Question 113

Which transaction code is used to reverse a normal accounting document?

A. FB08
B. FBRA
C. Review and approval before final posting
D. F.14

### Question 114

Which transaction code resets clearing for cleared items?

A. FBV0
B. FBRA
C. Personal temporary save of incomplete entry
D. FBN1

### Question 115

Which transaction code is commonly used to post a parked document?

A. Review and approval before final posting
B. FBD1
C. FBV0
D. FB03

### Question 116

What is the purpose of a parked document?

A. Personal temporary save of incomplete entry
B. F.14
C. FB02
D. Review and approval before final posting

### Question 117

What is the purpose of a held document?

A. Personal temporary save of incomplete entry
B. FBD1
C. FBN1
D. FB08

### Question 118

Which transaction code creates a recurring entry original document?

A. F.14
B. FBD1
C. FB03
D. FBRA

### Question 119

Which transaction code executes recurring entries?

A. FBN1
B. FB02
C. F.14
D. FBV0

### Question 120

Which transaction code is commonly used to maintain FI document number ranges?

A. FB03
B. FB08
C. Review and approval before final posting
D. FBN1

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 111 | **C** | FB03 displays accounting documents. |
| 112 | **D** | FB02 allows changes to document fields that are configured as changeable. |
| 113 | **A** | FB08 posts a reversal document. |
| 114 | **B** | Clearing may need to be reset before reversal. |
| 115 | **C** | FBV0 posts a parked document. |
| 116 | **D** | Parked documents can support review and approval workflows before posting. |
| 117 | **A** | A held document differs from a parked document in its save status and subsequent processing. |
| 118 | **B** | FBD1 creates a template for recurring entries, such as monthly journals. |
| 119 | **C** | Running recurring entries generates accounting documents for the relevant period. |
| 120 | **D** | Also check the assignment between document types and number ranges. |

---

## Set 3: Questions 121–130

### Question 121

What happens when the total debits and credits of an accounting document do not balance?

A. Posting is normally not allowed
B. JPY 11,000
C. FTXP
D. Distinguish exchange rates by conversion purpose

### Question 122

What is the gross amount for a net amount of JPY 10,000 with 10% tax added?

A. JPY 1,000
B. JPY 11,000
C. OB40
D. Amounts are translated using configured exchange rates and related rules

### Question 123

What is the included tax in a gross amount of JPY 11,000 at a 10% tax rate?

A. FTXP
B. OB08
C. JPY 1,000
D. Reference document number

### Question 124

Which transaction code is commonly used to create or change tax codes?

A. OB40
B. Distinguish exchange rates by conversion purpose
C. Assignment field
D. FTXP

### Question 125

Which transaction code is used for automatic tax account determination?

A. OB40
B. OB08
C. Amounts are translated using configured exchange rates and related rules
D. Posting is normally not allowed

### Question 126

Which transaction code maintains exchange rates?

A. Distinguish exchange rates by conversion purpose
B. OB08
C. Reference document number
D. JPY 11,000

### Question 127

What is the purpose of an exchange rate type?

A. Amounts are translated using configured exchange rates and related rules
B. Assignment field
C. Distinguish exchange rates by conversion purpose
D. JPY 1,000

### Question 128

What happens if the document currency differs from the company code currency?

A. Reference document number
B. Posting is normally not allowed
C. FTXP
D. Amounts are translated using configured exchange rates and related rules

### Question 129

Which document field helps match an external invoice number?

A. Reference document number
B. Assignment field
C. JPY 11,000
D. OB40

### Question 130

Which field can serve as a matching key for line items?

A. Posting is normally not allowed
B. Assignment field
C. JPY 1,000
D. OB08

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 121 | **A** | Debit-credit balance is a fundamental posting check. |
| 122 | **B** | Calculate 10,000 × 1.10. |
| 123 | **C** | Calculate 11,000 × 10 ÷ 110. |
| 124 | **D** | Tax codes can be maintained using FTXP and related configuration. |
| 125 | **A** | Check the account determination settings for tax postings. |
| 126 | **B** | Check the exchange rate type, currency pair, and validity date. |
| 127 | **C** | The rate type determines which conversion rate is selected for a purpose. |
| 128 | **D** | Amounts are maintained in document currency and local currency. |
| 129 | **A** | This field supports duplicate invoice checks and source document tracing. |
| 130 | **B** | The assignment field can be used for searching and matching. |

---

## Set 4: Questions 131–140

### Question 131

What is the main purpose of document splitting?

A. Balance debits and credits for each splitting characteristic
B. Default account assignment configuration
C. Report debits and credits by characteristics such as segment
D. OBA7

### Question 132

Why are zero-balance clearing lines generated?

A. CO objects such as cost centers
B. Validation
C. OB41
D. Balance debits and credits for each splitting characteristic

### Question 133

Which is an example of a source for profit center derivation?

A. CO objects such as cost centers
B. Default account assignment configuration
C. Substitution
D. OBC4

### Question 134

How can a cost center be supplied automatically during an expense posting?

A. Validation
B. Default account assignment configuration
C. OBA7
D. An input error occurs

### Question 135

Which mechanism checks input conditions in an FI document?

A. Substitution
B. OB41
C. Validation
D. Report debits and credits by characteristics such as segment

### Question 136

Which mechanism fills or replaces FI document field values based on rules?

A. OBA7
B. OBC4
C. Balance debits and credits for each splitting characteristic
D. Substitution

### Question 137

Which transaction code defines document types?

A. OBA7
B. OB41
C. An input error occurs
D. CO objects such as cost centers

### Question 138

Which transaction code defines posting keys?

A. OBC4
B. OB41
C. Report debits and credits by characteristics such as segment
D. Default account assignment configuration

### Question 139

Which transaction code configures field status groups?

A. An input error occurs
B. Balance debits and credits for each splitting characteristic
C. OBC4
D. Validation

### Question 140

What happens if a required account input field is left blank?

A. Report debits and credits by characteristics such as segment
B. CO objects such as cost centers
C. Substitution
D. An input error occurs

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 131 | **C** | Document splitting supports balance sheet reporting by characteristic. |
| 132 | **D** | The lines are generated according to document splitting configuration. |
| 133 | **A** | A profit center may be derived from the assigned cost center. |
| 134 | **B** | Automatic account assignment can provide the cost center. |
| 135 | **C** | Validation can raise an error when configured conditions are violated. |
| 136 | **D** | Substitution changes values according to defined conditions. |
| 137 | **A** | Document types control number ranges and permitted account types. |
| 138 | **B** | Posting keys control account types and debit/credit indicators. |
| 139 | **C** | OBC4 maintains field status groups within field status variants. |
| 140 | **D** | Required fields generally must be filled before posting. |

---

## Set 5: Questions 141–150

### Question 141

Which method lets the system assign FI document numbers?

A. Internal number assignment
B. External number assignment
C. Additional ledger
D. Error message and affected field

### Question 142

Which method allows a user or external source to specify a permitted document number?

A. Leading ledger
B. External number assignment
C. Ledger group
D. Whether the posted fields are changeable

### Question 143

What is the standard role of ledger 0L?

A. Additional ledger
B. Company code, account, fiscal year, and period
C. Leading ledger
D. Additional currencies can be retained depending on configuration

### Question 144

Which mechanism supports parallel postings for different accounting standards?

A. Ledger group
B. Error message and affected field
C. Impact analysis and posting tests
D. Additional ledger

### Question 145

What is used to restrict a posting to a specified group of ledgers?

A. Ledger group
B. Company code, account, fiscal year, and period
C. Whether the posted fields are changeable
D. Internal number assignment

### Question 146

Which parameters are important when displaying a G/L account balance?

A. Error message and affected field
B. Company code, account, fiscal year, and period
C. Additional currencies can be retained depending on configuration
D. External number assignment

### Question 147

What should be checked first when an accounting document posting fails?

A. Whether the posted fields are changeable
B. Impact analysis and posting tests
C. Error message and affected field
D. Leading ledger

### Question 148

What should be checked before changing an accounting document?

A. Additional currencies can be retained depending on configuration
B. Internal number assignment
C. Additional ledger
D. Whether the posted fields are changeable

### Question 149

What is true about currencies in addition to the ledger and company code currency?

A. Additional currencies can be retained depending on configuration
B. Impact analysis and posting tests
C. External number assignment
D. Ledger group

### Question 150

What is essential before transporting FI configuration to production?

A. Internal number assignment
B. Impact analysis and posting tests
C. Leading ledger
D. Company code, account, fiscal year, and period

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 141 | **A** | The system automatically assigns a number from a number range. |
| 142 | **B** | The document number is supplied externally within the allowed interval. |
| 143 | **C** | 0L is the standard leading ledger. |
| 144 | **D** | Separate ledgers can manage different accounting valuations. |
| 145 | **A** | A ledger group can restrict which ledgers receive a posting. |
| 146 | **B** | Balance display normally requires organizational and period selections. |
| 147 | **C** | Investigate possible causes such as account, period, tax, or authorization. |
| 148 | **D** | Unchangeable fields such as amount or account may require reversal and reposting. |
| 149 | **A** | SAP S/4HANA can record amounts in multiple currencies. |
| 150 | **B** | Verify dependencies among organizational settings, master data, and automatic postings. |

---

