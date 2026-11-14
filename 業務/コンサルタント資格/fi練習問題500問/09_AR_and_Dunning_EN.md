# Part 9: Accounts Receivable, Customer Payments, and Dunning (Questions 201–250)

English translation of the Japanese practice questions. **50 original four-option single-answer questions**, preserving the original choice order and answer keys. Answers and explanations appear after every ten questions. Standard SAP S/4HANA Private Edition settings are assumed unless stated otherwise.

[Japanese version](09_得意先ARと督促.md)

## Set 1: Questions 201–210

### Question 201

Which Business Partner role is used for customer FI accounting data?

A. FLCU00
B. FLCU01
C. Calculate the due date of an invoice
D. Sales organization, distribution channel, and division

### Question 202

Which Business Partner role is used for customer sales data?

A. Reflect customer receivables in the general ledger
B. FLCU01
C. Send reminders for overdue receivables
D. FB70

### Question 203

What is the purpose of a customer reconciliation account?

A. Calculate the due date of an invoice
B. Reconciliation account and dunning data
C. Reflect customer receivables in the general ledger
D. DR

### Question 204

What do customer payment terms determine?

A. Send reminders for overdue receivables
B. Sales organization, distribution channel, and division
C. Debit customer; credit revenue
D. Calculate the due date of an invoice

### Question 205

Why is a dunning procedure assigned to a customer?

A. Send reminders for overdue receivables
B. Reconciliation account and dunning data
C. FB70
D. FLCU00

### Question 206

Which are examples of customer company code data?

A. Sales organization, distribution channel, and division
B. Reconciliation account and dunning data
C. DR
D. FLCU01

### Question 207

Which fields are examples of customer sales-area data?

A. FB70
B. Debit customer; credit revenue
C. Sales organization, distribution channel, and division
D. Reflect customer receivables in the general ledger

### Question 208

Which transaction code enters a customer invoice directly in FI?

A. DR
B. FLCU00
C. Calculate the due date of an invoice
D. FB70

### Question 209

What is the standard document type for a customer invoice?

A. DR
B. Debit customer; credit revenue
C. FLCU01
D. Send reminders for overdue receivables

### Question 210

What is the basic entry for a sale on credit?

A. FLCU00
B. Debit customer; credit revenue
C. Reflect customer receivables in the general ledger
D. Reconciliation account and dunning data

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 201 | **A** | It maintains company-code-specific accounting data. |
| 202 | **B** | It maintains sales-area data. |
| 203 | **C** | Customer subledger postings update the general ledger through the reconciliation account. |
| 204 | **D** | They can also define cash discount conditions. |
| 205 | **A** | It manages dunning levels and intervals. |
| 206 | **B** | These are company-code-specific accounting settings. |
| 207 | **C** | These are used to manage SD-related sales conditions. |
| 208 | **D** | FB70 posts a customer invoice in FI. |
| 209 | **A** | DR is used for customer invoices in standard configuration. |
| 210 | **B** | It recognizes a receivable and revenue. |

---

## Set 2: Questions 211–220

### Question 211

Which transaction code posts a customer incoming payment?

A. F-32
B. Debit bank; credit customer
C. F-28
D. Clear the invoice

### Question 212

Which transaction code manually clears customer open items?

A. DZ
B. Reduce accounts receivable
C. JPY 20,000
D. F-32

### Question 213

What is the standard document type for an incoming customer payment?

A. DZ
B. Debit bank; credit customer
C. Special G/L transactions
D. The original invoice may remain open

### Question 214

What is the basic journal entry for receiving a customer payment?

A. Reduce accounts receivable
B. Debit bank; credit customer
C. Clear the invoice
D. Clear the original invoice and create a new item for the remainder

### Question 215

What is the effect of a customer credit memo?

A. Special G/L transactions
B. JPY 20,000
C. Reduce accounts receivable
D. F-28

### Question 216

Which mechanism is used for customer down payments?

A. Clear the invoice
B. The original invoice may remain open
C. F-32
D. Special G/L transactions

### Question 217

What should be done when an invoice of JPY 100,000 is matched by a payment of JPY 100,000?

A. Clear the invoice
B. JPY 20,000
C. Clear the original invoice and create a new item for the remainder
D. DZ

### Question 218

What is the difference between an invoice of JPY 100,000 and a payment of JPY 80,000?

A. The original invoice may remain open
B. JPY 20,000
C. F-28
D. Debit bank; credit customer

### Question 219

What is a characteristic of a partial payment?

A. Clear the original invoice and create a new item for the remainder
B. F-32
C. The original invoice may remain open
D. Reduce accounts receivable

### Question 220

What is a characteristic of the residual item method?

A. F-28
B. DZ
C. Special G/L transactions
D. Clear the original invoice and create a new item for the remainder

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 211 | **C** | It is used for incoming payments and clearing customer receivables. |
| 212 | **D** | It clears open customer receivables. |
| 213 | **A** | DZ is used for incoming payment documents in standard configuration. |
| 214 | **B** | It increases bank balances and reduces receivables. |
| 215 | **C** | It can adjust amounts for returns or discounts. |
| 216 | **D** | Down payments are tracked separately from ordinary receivables. |
| 217 | **A** | Confirm that the payment matches the invoice. |
| 218 | **B** | The remaining amount is outstanding. |
| 219 | **C** | Partial payment differs from the residual item method. |
| 220 | **D** | The difference is managed as a new open item. |

---

## Set 3: Questions 221–230

### Question 221

Why display a list of customer open items?

A. Identify receivables awaiting collection
B. Analyze receivables by how long they have been outstanding
C. Escalate dunning according to how overdue an item is
D. Process the difference according to tolerance settings

### Question 222

What is the purpose of an accounts receivable aging report?

A. F150
B. Analyze receivables by how long they have been outstanding
C. Temporarily suspend dunning for specified receivables
D. Manage the unpaid balance as an open or residual item

### Question 223

Which transaction code commonly executes dunning?

A. Escalate dunning according to how overdue an item is
B. Due date and dunning procedure
C. F150
D. A customer advance recorded as a liability

### Question 224

What is the purpose of a dunning level?

A. Temporarily suspend dunning for specified receivables
B. Process the difference according to tolerance settings
C. Match the special G/L balance with the invoice
D. Escalate dunning according to how overdue an item is

### Question 225

What is the purpose of a dunning block?

A. Temporarily suspend dunning for specified receivables
B. Due date and dunning procedure
C. Manage the unpaid balance as an open or residual item
D. Identify receivables awaiting collection

### Question 226

Which criteria are checked during dunning?

A. Process the difference according to tolerance settings
B. Due date and dunning procedure
C. A customer advance recorded as a liability
D. Analyze receivables by how long they have been outstanding

### Question 227

What can be done when an incoming payment difference is within tolerance?

A. Manage the unpaid balance as an open or residual item
B. Match the special G/L balance with the invoice
C. Process the difference according to tolerance settings
D. F150

### Question 228

How should a large incoming payment difference normally be handled?

A. A customer advance recorded as a liability
B. Identify receivables awaiting collection
C. Escalate dunning according to how overdue an item is
D. Manage the unpaid balance as an open or residual item

### Question 229

What is the basic accounting nature of an advance payment received from a customer?

A. A customer advance recorded as a liability
B. Match the special G/L balance with the invoice
C. Analyze receivables by how long they have been outstanding
D. Temporarily suspend dunning for specified receivables

### Question 230

What is important when offsetting a customer down payment against an invoice?

A. Identify receivables awaiting collection
B. Match the special G/L balance with the invoice
C. F150
D. Due date and dunning procedure

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 221 | **A** | It supports analysis of due dates and overdue periods. |
| 222 | **B** | It supports collections and assessment of bad-debt risk. |
| 223 | **C** | It executes dunning for overdue receivables. |
| 224 | **D** | Different notices and conditions can be set for each level. |
| 225 | **A** | It may be used for disputed invoices. |
| 226 | **B** | Eligibility depends on due dates and configuration. |
| 227 | **C** | Automatic clearing or posting of differences may be possible. |
| 228 | **D** | Do not clear a large difference without proper handling. |
| 229 | **A** | Cash received before revenue recognition may represent a liability. |
| 230 | **B** | Handle down-payment clearing or transfer correctly. |

---

## Set 4: Questions 231–240

### Question 231

What is the main purpose of credit management?

A. Credit segment and credit management settings
B. Account determination and accounting posting log
C. Manage customer credit risk and credit limits
D. Existing documents are generally not changed automatically

### Question 232

What should be checked when a customer exceeds their credit limit?

A. Post accounts receivable and revenue
B. VKOA
C. Make it easier to match a payment to an invoice
D. Credit segment and credit management settings

### Question 233

Which accounting entries commonly result from SD billing integration with FI?

A. Post accounts receivable and revenue
B. Account determination and accounting posting log
C. Receivables may be summarized in an incorrect G/L account
D. Matching information such as invoice reference numbers

### Question 234

What should be investigated if an SD billing document is not posted to FI?

A. VKOA
B. Account determination and accounting posting log
C. Existing documents are generally not changed automatically
D. Review payment documents and clearing status, then consider reversal

### Question 235

Which transaction code is commonly used for automatic revenue account determination in SD?

A. Receivables may be summarized in an incorrect G/L account
B. Make it easier to match a payment to an invoice
C. VKOA
D. Manage customer credit risk and credit limits

### Question 236

What can happen if a customer reconciliation account is configured incorrectly?

A. Existing documents are generally not changed automatically
B. Matching information such as invoice reference numbers
C. Credit segment and credit management settings
D. Receivables may be summarized in an incorrect G/L account

### Question 237

What is the effect of changing customer payment terms on existing documents?

A. Existing documents are generally not changed automatically
B. Make it easier to match a payment to an invoice
C. Review payment documents and clearing status, then consider reversal
D. Post accounts receivable and revenue

### Question 238

Why use a customer payment reference number?

A. Matching information such as invoice reference numbers
B. Make it easier to match a payment to an invoice
C. Manage customer credit risk and credit limits
D. Account determination and accounting posting log

### Question 239

What is a key to automatically clearing customer payments from bank statements?

A. Review payment documents and clearing status, then consider reversal
B. Credit segment and credit management settings
C. Matching information such as invoice reference numbers
D. VKOA

### Question 240

What should be done if a customer payment is recorded twice?

A. Manage customer credit risk and credit limits
B. Post accounts receivable and revenue
C. Receivables may be summarized in an incorrect G/L account
D. Review payment documents and clearing status, then consider reversal

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 231 | **C** | It can affect sales orders and deliveries. |
| 232 | **D** | Check the credit management configuration and exposure. |
| 233 | **A** | SD billing documents generate accounting documents. |
| 234 | **B** | Check tax and account settings and any posting blocks. |
| 235 | **C** | VKOA is used for SD revenue account determination. |
| 236 | **D** | This affects reporting between the subledger and general ledger. |
| 237 | **A** | Check the payment terms and baseline date stored on each document. |
| 238 | **B** | It can also support automatic clearing from bank statements. |
| 239 | **C** | Clearing rules and reliable reference information are essential. |
| 240 | **D** | Correct the error while preserving an audit trail. |

---

## Set 5: Questions 241–250

### Question 241

Which process is used when an invoice remains unpaid after its due date?

A. Dunning
B. Improve overdue receivables and cash flow
C. JPY 10,000
D. Consider extending the company code data

### Question 242

Why might customer collection terms be revised?

A. JPY 330,000
B. Improve overdue receivables and cash flow
C. JPY 50,000
D. Review clearing selection, differences, and reference information

### Question 243

What is the gross amount of a JPY 300,000 invoice before 10% tax?

A. JPY 10,000
B. Check the posting period configuration and posting date
C. JPY 330,000
D. Reconcile posting dates, clearing status, and reconciliation accounts

### Question 244

How much 10% tax is included in a gross amount of JPY 110,000?

A. JPY 50,000
B. Consider extending the company code data
C. Invoicing, incoming payment, clearing, dunning, and balance verification
D. JPY 10,000

### Question 245

What remains after receiving JPY 100,000 against an invoice of JPY 150,000?

A. JPY 50,000
B. Check the posting period configuration and posting date
C. Review clearing selection, differences, and reference information
D. Dunning

### Question 246

What should be checked if the posting date of a customer invoice falls in a closed period?

A. Consider extending the company code data
B. Check the posting period configuration and posting date
C. Reconcile posting dates, clearing status, and reconciliation accounts
D. Improve overdue receivables and cash flow

### Question 247

What should be done if customer master data has not been extended to another company code?

A. Review clearing selection, differences, and reference information
B. Invoicing, incoming payment, clearing, dunning, and balance verification
C. Consider extending the company code data
D. JPY 330,000

### Question 248

What should be checked if an invoice remains open after payment?

A. Reconcile posting dates, clearing status, and reconciliation accounts
B. Dunning
C. JPY 10,000
D. Review clearing selection, differences, and reference information

### Question 249

What should be investigated if accounts receivable balances do not match line items?

A. Reconcile posting dates, clearing status, and reconciliation accounts
B. Invoicing, incoming payment, clearing, dunning, and balance verification
C. Improve overdue receivables and cash flow
D. JPY 50,000

### Question 250

What sequence should an end-to-end AR process test cover?

A. Dunning
B. Invoicing, incoming payment, clearing, dunning, and balance verification
C. JPY 330,000
D. Check the posting period configuration and posting date

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 241 | **A** | It is used to follow up on overdue receivables. |
| 242 | **B** | Review business terms that affect receivables collection. |
| 243 | **C** | 300,000 × 1.10 = 330,000. |
| 244 | **D** | 110,000 × 10 ÷ 110 = 10,000. |
| 245 | **A** | 150,000 − 100,000 = 50,000. |
| 246 | **B** | Check OB52 and the approval procedure. |
| 247 | **C** | The company code data is needed for accounting transactions in that company code. |
| 248 | **D** | Posting a payment does not always clear the invoice. |
| 249 | **A** | Check whether report selection criteria and line items are consistent. |
| 250 | **B** | Validate both accounting entries and business outcomes throughout the process. |

---

