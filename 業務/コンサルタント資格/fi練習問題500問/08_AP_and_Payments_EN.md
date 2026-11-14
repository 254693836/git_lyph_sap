# Part 8: Accounts Payable and Payments (Questions 151–200)

English translation of the corresponding Japanese practice questions. **50 original four-option single-answer questions**, preserving the original answer choice order and answer keys. Answers and explanations appear after every ten questions.

[Japanese version](08_仕入先APと支払.md)

## Set 1: Questions 151–160

### Question 151

Which Business Partner role is used for a supplier's FI accounting data?

A. FLVN00
B. FLVN01
C. Payment due dates and cash discounts
D. Identify the recipient bank account

### Question 152

Which Business Partner role is used for supplier purchasing data?

A. Reconciliation account
B. FLVN01
C. Payment instruments such as bank transfers
D. Number ranges and master data fields

### Question 153

Which important field is maintained in supplier company code data?

A. Payment due dates and cash discounts
B. Temporarily exclude an item from payment
C. Reconciliation account
D. Name, address, and tax identification number

### Question 154

What do a supplier's payment terms determine?

A. Payment instruments such as bank transfers
B. Identify the recipient bank account
C. Extend the company code data
D. Payment due dates and cash discounts

### Question 155

What does a supplier's payment method determine?

A. Payment instruments such as bank transfers
B. Temporarily exclude an item from payment
C. Number ranges and master data fields
D. FLVN00

### Question 156

Why is a payment block set?

A. Identify the recipient bank account
B. Temporarily exclude an item from payment
C. Name, address, and tax identification number
D. FLVN01

### Question 157

What is the purpose of a supplier's bank data?

A. Number ranges and master data fields
B. Extend the company code data
C. Identify the recipient bank account
D. Reconciliation account

### Question 158

What does a supplier account group control?

A. Name, address, and tax identification number
B. FLVN00
C. Payment due dates and cash discounts
D. Number ranges and master data fields

### Question 159

What should be checked to avoid duplicate supplier master records?

A. Name, address, and tax identification number
B. Extend the company code data
C. FLVN01
D. Payment instruments such as bank transfers

### Question 160

What is required to use a supplier in another company code?

A. FLVN00
B. Extend the company code data
C. Reconciliation account
D. Temporarily exclude an item from payment

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 151 | **A** | This role maintains accounting data specific to a company code. |
| 152 | **B** | This role maintains purchasing organization data. |
| 153 | **C** | It determines the G/L account updated from the supplier subledger. |
| 154 | **D** | Payment terms are different from payment methods. |
| 155 | **A** | It works together with configuration such as FBZP. |
| 156 | **B** | Payment can be stopped pending approval or verification. |
| 157 | **C** | Incorrect bank account information can cause payment failures. |
| 158 | **D** | Also check the relationship with Business Partner groupings. |
| 159 | **A** | These details help prevent duplicate records for the same legal entity. |
| 160 | **B** | Company-code-specific data is needed for FI processing. |

---

## Set 2: Questions 161–170

### Question 161

Which transaction code is used to enter an FI supplier invoice?

A. KR
B. Reduce the payable to the supplier
C. FB60
D. Debit GR/IR; credit supplier

### Question 162

What is the standard document type for supplier invoices?

A. Debit expense; credit supplier
B. MIRO
C. Reference number and supplier, among other details
D. KR

### Question 163

What is the basic journal entry when an expense is incurred on credit?

A. Debit expense; credit supplier
B. Reduce the payable to the supplier
C. Debit inventory; credit GR/IR
D. OBB8

### Question 164

What is the basic effect of a supplier credit memo?

A. MIRO
B. Reduce the payable to the supplier
C. Debit GR/IR; credit supplier
D. Special G/L transactions

### Question 165

Which transaction code is used for MM invoice verification?

A. Debit inventory; credit GR/IR
B. Reference number and supplier, among other details
C. MIRO
D. FB60

### Question 166

What is the basic journal entry when ordered inventory is received?

A. Debit GR/IR; credit supplier
B. OBB8
C. KR
D. Debit inventory; credit GR/IR

### Question 167

What is the basic journal entry when a purchase order invoice is verified?

A. Debit GR/IR; credit supplier
B. Reference number and supplier, among other details
C. Special G/L transactions
D. Debit expense; credit supplier

### Question 168

Which details are important for detecting duplicate invoices?

A. OBB8
B. Reference number and supplier, among other details
C. FB60
D. Reduce the payable to the supplier

### Question 169

Which transaction code configures payment terms?

A. Special G/L transactions
B. KR
C. OBB8
D. MIRO

### Question 170

Which mechanism is used for supplier down payments?

A. FB60
B. Debit expense; credit supplier
C. Debit inventory; credit GR/IR
D. Special G/L transactions

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 161 | **C** | It is used for direct FI supplier invoice entry. |
| 162 | **D** | KR is used for supplier invoices in standard configuration. |
| 163 | **A** | This records an expense increase and the related payable. |
| 164 | **B** | Credit memos are used for returns and discounts, among other cases. |
| 165 | **C** | It matches an invoice with purchase orders and goods receipts. |
| 166 | **D** | Inventory increases when the goods are received. |
| 167 | **A** | This is the simplified entry, excluding taxes and price differences. |
| 168 | **B** | Also compare the invoice date and amount. |
| 169 | **C** | It defines rules for due dates and cash discounts. |
| 170 | **D** | Down payments are managed separately from ordinary payables. |

---

## Set 3: Questions 171–180

### Question 171

Which transaction code runs automatic payments?

A. F110
B. FBZP
C. Clear supplier payables and post payments
D. It affects the period for selecting payable items

### Question 172

Which transaction code configures automatic payments?

A. Review proposed payments and exceptions before execution
B. FBZP
C. F-53
D. Payment method configuration and Business Partner data

### Question 173

What is the main purpose of a payment proposal?

A. Clear supplier payables and post payments
B. Create bank transfer data for the bank
C. Review proposed payments and exceptions before execution
D. Due date, payment block, and selection criteria

### Question 174

What is the accounting result of executing a payment run?

A. F-53
B. It affects the period for selecting payable items
C. Identify reasons why items were not selected
D. Clear supplier payables and post payments

### Question 175

Which transaction code is used for manual supplier payments?

A. F-53
B. Create bank transfer data for the bank
C. Payment method configuration and Business Partner data
D. F110

### Question 176

What is the purpose of payment medium generation?

A. It affects the period for selecting payable items
B. Create bank transfer data for the bank
C. Due date, payment block, and selection criteria
D. FBZP

### Question 177

Why is the next payment run date important in F110?

A. Payment method configuration and Business Partner data
B. Identify reasons why items were not selected
C. It affects the period for selecting payable items
D. Review proposed payments and exceptions before execution

### Question 178

What should be checked if a payment method is missing?

A. Due date, payment block, and selection criteria
B. F110
C. Clear supplier payables and post payments
D. Payment method configuration and Business Partner data

### Question 179

What should be checked when an invoice is omitted from a payment proposal?

A. Due date, payment block, and selection criteria
B. Identify reasons why items were not selected
C. FBZP
D. F-53

### Question 180

Why should payment proposal exceptions be reviewed?

A. F110
B. Identify reasons why items were not selected
C. Review proposed payments and exceptions before execution
D. Create bank transfer data for the bank

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 171 | **A** | It supports payment proposals and payment runs. |
| 172 | **B** | It configures payment methods, bank determination, and related settings. |
| 173 | **C** | It allows payment selection to be checked before the run. |
| 174 | **D** | Successfully paid open items become cleared. |
| 175 | **A** | It posts manual outgoing payments. |
| 176 | **B** | It converts payment run results into a bank submission format. |
| 177 | **C** | Payment due dates are evaluated against run parameters. |
| 178 | **D** | Check country, company code, and partner conditions. |
| 179 | **A** | The payment proposal log can show why it was excluded. |
| 180 | **B** | Exceptions may reveal missing bank details or payment method issues. |

---

## Set 4: Questions 181–190

### Question 181

Which transaction code is used for manual supplier clearing?

A. F-03
B. The original invoice can remain open
C. F-44
D. Payment date, clearing document, and bank statement

### Question 182

Which transaction code is used for manual G/L account clearing?

A. FBRA
B. Clear the original item and create a new item for the remaining amount
C. Consider reversal and reposting as necessary
D. F-03

### Question 183

Which transaction code resets clearing?

A. FBRA
B. The original invoice can remain open
C. Trace which document settled the items
D. Each item's due date and discount conditions

### Question 184

What is a characteristic of a partial payment?

A. Clear the original item and create a new item for the remaining amount
B. The original invoice can remain open
C. Payment date, clearing document, and bank statement
D. Difference processing and tolerance settings

### Question 185

What is a characteristic of a residual item payment?

A. Trace which document settled the items
B. Consider reversal and reposting as necessary
C. Clear the original item and create a new item for the remaining amount
D. F-44

### Question 186

What is the purpose of a clearing document number?

A. Payment date, clearing document, and bank statement
B. Each item's due date and discount conditions
C. F-03
D. Trace which document settled the items

### Question 187

Which details help investigate a supplier's payment history?

A. Payment date, clearing document, and bank statement
B. Consider reversal and reposting as necessary
C. Difference processing and tolerance settings
D. FBRA

### Question 188

What is the basic approach to correcting an original invoice after payment?

A. Each item's due date and discount conditions
B. Consider reversal and reposting as necessary
C. F-44
D. The original invoice can remain open

### Question 189

What should be checked when paying invoices with different payment terms together?

A. Difference processing and tolerance settings
B. F-03
C. Each item's due date and discount conditions
D. Clear the original item and create a new item for the remaining amount

### Question 190

What should be checked if amounts to be cleared do not match?

A. F-44
B. FBRA
C. Trace which document settled the items
D. Difference processing and tolerance settings

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 181 | **C** | It clears supplier open items. |
| 182 | **D** | It clears G/L account open items. |
| 183 | **A** | It resets clearing so that items can be processed again. |
| 184 | **B** | With a partial payment, both the invoice and payment item may remain open. |
| 185 | **C** | The remaining balance is carried as a separate open item. |
| 186 | **D** | It helps reconcile cleared items. |
| 187 | **A** | Reconcile the accounting entries with bank results. |
| 188 | **B** | Posted amounts and other restricted fields cannot simply be edited. |
| 189 | **C** | Due dates and cash discounts may differ by line item. |
| 190 | **D** | Handling of differences depends on configuration. |

---

## Set 5: Questions 191–200

### Question 191

What should be checked when a supplier invoice fails because the posting period is closed?

A. OB52 and posting date
B. Business Partner company code data and G/L account master
C. Bank account, payment medium, and bank response
D. JPY 40,000

### Question 192

What should be checked if the reconciliation account is configured incorrectly?

A. Tax code and tax calculation configuration
B. Business Partner company code data and G/L account master
C. Payment block key and reason
D. JPY 220,000

### Question 193

What should be checked if tax is incorrect on a supplier invoice?

A. Bank account, payment medium, and bank response
B. Bank statement and unprocessed items
C. Tax code and tax calculation configuration
D. December 1

### Question 194

What should be checked if a bank transfer fails?

A. Payment block key and reason
B. JPY 40,000
C. Discount deadline and baseline date
D. Bank account, payment medium, and bank response

### Question 195

What should be checked if a payment block excludes an item from a proposal?

A. Payment block key and reason
B. Bank statement and unprocessed items
C. JPY 220,000
D. OB52 and posting date

### Question 196

What should be checked if the bank balance and payment documents do not reconcile?

A. JPY 40,000
B. Bank statement and unprocessed items
C. December 1
D. Business Partner company code data and G/L account master

### Question 197

What remains on an invoice of JPY 100,000 after paying JPY 60,000?

A. JPY 220,000
B. Discount deadline and baseline date
C. JPY 40,000
D. Tax code and tax calculation configuration

### Question 198

What is the gross amount for a net invoice of JPY 200,000 with 10% tax?

A. December 1
B. OB52 and posting date
C. Bank account, payment medium, and bank response
D. JPY 220,000

### Question 199

What date is 30 calendar days after a baseline date of November 1?

A. December 1
B. Discount deadline and baseline date
C. Business Partner company code data and G/L account master
D. Payment block key and reason

### Question 200

What should be checked to determine whether a cash discount applies?

A. OB52 and posting date
B. Discount deadline and baseline date
C. Tax code and tax calculation configuration
D. Bank statement and unprocessed items

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 191 | **A** | Check posting period configuration and authorizations. |
| 192 | **B** | Review the company-code-specific settings. |
| 193 | **C** | Check the tax base and tax rate. |
| 194 | **D** | Investigate the accounting posting and bank transmission separately. |
| 195 | **A** | Confirm approval status before removing the block. |
| 196 | **B** | Investigate the differences through bank reconciliation. |
| 197 | **C** | 100,000 − 60,000 = 40,000. |
| 198 | **D** | 200,000 × 1.10 = 220,000. |
| 199 | **A** | Actual due-date calculation follows configuration; a simple 30-day calculation gives December 1. |
| 200 | **B** | The discount is calculated based on dates and the discount rate. |

---

