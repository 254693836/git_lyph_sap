# Part 10: Banking, Payments, and Foreign Currency (Questions 251–300)

English translation of the corresponding Japanese practice questions. **50 original single-answer multiple-choice questions**, preserving the original choice order, question numbers, and answer keys. Answers and explanations follow every 10 questions. Transaction codes primarily reflect SAP S/4HANA Private Edition using SAP GUI.

[Japanese version](10_銀行と外貨.md)

## Set 1: Questions 251–260

### Question 251

What information is typically maintained in bank master data?

A. Bank key, bank name, and location
B. Define a bank used by the company
C. FBZP
D. Control company-code-specific payment conditions

### Question 252

What is the primary purpose of a house bank?

A. Manage the company's bank accounts
B. Define a bank used by the company
C. F110
D. Ranking order, accounts, and available amounts

### Question 253

What is the purpose of a house bank account?

A. FBZP
B. Define payment instruments available in a country
C. Manage the company's bank accounts
D. Items selected for payment and reasons for exclusion

### Question 254

Which transaction code configures automatic payments?

A. F110
B. Control company-code-specific payment conditions
C. Generate payment instruction data to send to the bank
D. FBZP

### Question 255

Which transaction code runs automatic payments?

A. F110
B. Define payment instruments available in a country
C. Ranking order, accounts, and available amounts
D. Bank key, bank name, and location

### Question 256

Why configure a payment method at country level?

A. Control company-code-specific payment conditions
B. Define payment instruments available in a country
C. Items selected for payment and reasons for exclusion
D. Define a bank used by the company

### Question 257

Why configure a payment method at company code level?

A. Ranking order, accounts, and available amounts
B. Generate payment instruction data to send to the bank
C. Control company-code-specific payment conditions
D. Manage the company's bank accounts

### Question 258

Which settings are important for bank determination?

A. Items selected for payment and reasons for exclusion
B. Bank key, bank name, and location
C. FBZP
D. Ranking order, accounts, and available amounts

### Question 259

What should be checked in a payment proposal log?

A. Items selected for payment and reasons for exclusion
B. Generate payment instruction data to send to the bank
C. Define a bank used by the company
D. F110

### Question 260

What is the main purpose of a payment medium?

A. Bank key, bank name, and location
B. Generate payment instruction data to send to the bank
C. Manage the company's bank accounts
D. Define payment instruments available in a country

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 251 | **A** | Bank master data holds basic information about a bank. |
| 252 | **B** | House banks are used to manage banks and bank accounts for a company code. |
| 253 | **C** | It manages bank account IDs and their relationship to G/L accounts. |
| 254 | **D** | It configures payment methods, bank determination, and related settings. |
| 255 | **A** | It is used to generate payment proposals and execute payments. |
| 256 | **B** | This provides the basic configuration for permitted payment methods. |
| 257 | **C** | This manages conditions such as banks and payment amount limits. |
| 258 | **D** | These settings help select the bank to use for payments. |
| 259 | **A** | Investigate exceptions before executing payments. |
| 260 | **B** | Payment data is converted into the format required by the bank. |

---

## Set 2: Questions 261–270

### Question 261

Why import electronic bank statements?

A. CAMT.053
B. Determine the accounting posting accounts for bank transactions
C. Reflect actual incoming and outgoing bank transactions in accounting
D. Bank reconciliation

### Question 262

Which is an example of a commonly used electronic bank statement format?

A. Identify the type of bank transaction
B. Matching rules and reference information
C. Amount, currency, reference number, and tolerances
D. CAMT.053

### Question 263

What is the purpose of an external transaction code in bank statement processing?

A. Identify the type of bank transaction
B. Determine the accounting posting accounts for bank transactions
C. Investigate exceptions and reprocess them
D. Post bank fees to the appropriate expense account

### Question 264

What is the purpose of a bank statement posting rule?

A. Matching rules and reference information
B. Determine the accounting posting accounts for bank transactions
C. Bank reconciliation
D. Exchange rate and bank settings

### Question 265

What is needed for automatic clearing of bank statement items?

A. Investigate exceptions and reprocess them
B. Amount, currency, reference number, and tolerances
C. Matching rules and reference information
D. Reflect actual incoming and outgoing bank transactions in accounting

### Question 266

What should be done when bank statement items remain unmatched?

A. Bank reconciliation
B. Post bank fees to the appropriate expense account
C. CAMT.053
D. Investigate exceptions and reprocess them

### Question 267

What process investigates differences between bank balances and G/L balances?

A. Bank reconciliation
B. Amount, currency, reference number, and tolerances
C. Exchange rate and bank settings
D. Identify the type of bank transaction

### Question 268

What should be checked if an incoming payment cannot be cleared?

A. Post bank fees to the appropriate expense account
B. Amount, currency, reference number, and tolerances
C. Reflect actual incoming and outgoing bank transactions in accounting
D. Determine the accounting posting accounts for bank transactions

### Question 269

How should bank transfer fees be accounted for?

A. Exchange rate and bank settings
B. CAMT.053
C. Post bank fees to the appropriate expense account
D. Matching rules and reference information

### Question 270

What should be checked if the bank account currency differs from the transaction currency?

A. Reflect actual incoming and outgoing bank transactions in accounting
B. Identify the type of bank transaction
C. Investigate exceptions and reprocess them
D. Exchange rate and bank settings

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 261 | **C** | Bank transactions are posted and matched with accounting records. |
| 262 | **D** | CAMT.053 is one of the ISO 20022 bank statement formats. |
| 263 | **A** | External transaction codes are mapped to posting rules. |
| 264 | **B** | Posting rules connect transaction categories with account determination. |
| 265 | **C** | Invoice numbers and other references help identify matching items. |
| 266 | **D** | Transactions that could not be processed automatically need investigation. |
| 267 | **A** | Identify transactions in transit, missing imports, and incorrect postings. |
| 268 | **B** | Investigate mismatches in the matching conditions. |
| 269 | **C** | Bank statement processing can post fees to an expense account. |
| 270 | **D** | Foreign currency settlement can result in exchange differences. |

---

## Set 3: Questions 271–280

### Question 271

Which transaction code maintains exchange rates?

A. OB08
B. Realized foreign exchange gain or loss
C. Open items denominated in foreign currency
D. JPY 500 difference

### Question 272

What may arise when a foreign currency receivable is settled?

A. Unrealized foreign exchange gain or loss
B. Realized foreign exchange gain or loss
C. Post differences to the appropriate G/L accounts
D. Valuation date, exchange rate, and valuation method

### Question 273

What can arise from foreign currency valuation at period-end?

A. Open items denominated in foreign currency
B. JPY 15,000
C. Unrealized foreign exchange gain or loss
D. Record amounts in parallel, such as in a group currency

### Question 274

Which items may be subject to foreign currency valuation?

A. Post differences to the appropriate G/L accounts
B. JPY 500 difference
C. Currency pair, date, and exchange rate type
D. Open items denominated in foreign currency

### Question 275

Why is automatic account determination needed for exchange differences?

A. Post differences to the appropriate G/L accounts
B. JPY 15,000
C. Valuation date, exchange rate, and valuation method
D. OB08

### Question 276

What is the JPY amount of a USD 100 invoice at JPY 150 per USD?

A. JPY 500 difference
B. JPY 15,000
C. Record amounts in parallel, such as in a group currency
D. Realized foreign exchange gain or loss

### Question 277

What is the JPY exchange difference if USD 100 is recorded at JPY 150 and collected at JPY 155 per USD?

A. Valuation date, exchange rate, and valuation method
B. Currency pair, date, and exchange rate type
C. JPY 500 difference
D. Unrealized foreign exchange gain or loss

### Question 278

What should be checked when valuating a foreign currency supplier payable?

A. Record amounts in parallel, such as in a group currency
B. OB08
C. Open items denominated in foreign currency
D. Valuation date, exchange rate, and valuation method

### Question 279

Why use additional currencies besides the company code currency?

A. Record amounts in parallel, such as in a group currency
B. Currency pair, date, and exchange rate type
C. Realized foreign exchange gain or loss
D. Post differences to the appropriate G/L accounts

### Question 280

What should be checked if no exchange rate is found during currency conversion?

A. OB08
B. Currency pair, date, and exchange rate type
C. Unrealized foreign exchange gain or loss
D. JPY 15,000

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 271 | **A** | Check the rate type, currency pair, and effective date. |
| 272 | **B** | It reflects the difference between invoice and settlement exchange rates. |
| 273 | **C** | Foreign currency balances are revalued using closing rates. |
| 274 | **D** | Foreign currency balances may also be valuated depending on settings. |
| 275 | **A** | Processing may fail if the account determination configuration is incomplete. |
| 276 | **B** | 100 × 150 = 15,000 JPY. |
| 277 | **C** | 100 × (155 − 150) = 500 JPY. |
| 278 | **D** | The results depend on the valuation parameters. |
| 279 | **A** | This supports reporting in multiple currencies. |
| 280 | **B** | Conversion may fail if a required rate is missing. |

---

## Set 4: Questions 281–290

### Question 281

What should be checked if a payment medium is not generated?

A. Payment sent to the wrong account
B. Payment documents and clearing information
C. Payment run result and payment medium format settings
D. Use alternative matching keys and manual verification

### Question 282

What is a risk if the recipient's bank account is incorrect?

A. Due dates, selection criteria, and payment blocks
B. An SAP posting alone does not guarantee receipt of funds at the bank
C. Posting rules and account determination settings
D. Payment sent to the wrong account

### Question 283

What should be checked if no items appear in a payment proposal?

A. Due dates, selection criteria, and payment blocks
B. Payment documents and clearing information
C. Check statement IDs and import history
D. Match line items in bank clearing accounts

### Question 284

What should be checked after a payment run to verify accounting results?

A. An SAP posting alone does not guarantee receipt of funds at the bank
B. Payment documents and clearing information
C. Use alternative matching keys and manual verification
D. A valid recipient bank account

### Question 285

Which statement correctly describes the relationship between SAP payment posting and bank transfer?

A. Check statement IDs and import history
B. Posting rules and account determination settings
C. An SAP posting alone does not guarantee receipt of funds at the bank
D. Payment run result and payment medium format settings

### Question 286

What helps prevent duplicate bank statement imports?

A. Use alternative matching keys and manual verification
B. Match line items in bank clearing accounts
C. Payment sent to the wrong account
D. Check statement IDs and import history

### Question 287

What should be done if a bank statement has no reference number?

A. Use alternative matching keys and manual verification
B. Posting rules and account determination settings
C. A valid recipient bank account
D. Due dates, selection criteria, and payment blocks

### Question 288

What should be checked if an incoming bank transaction is posted to the wrong account?

A. Match line items in bank clearing accounts
B. Posting rules and account determination settings
C. Payment run result and payment medium format settings
D. Payment documents and clearing information

### Question 289

What is a purpose of open item management for bank accounts?

A. A valid recipient bank account
B. Payment sent to the wrong account
C. Match line items in bank clearing accounts
D. An SAP posting alone does not guarantee receipt of funds at the bank

### Question 290

What is an example of master data required by a payment method?

A. Payment run result and payment medium format settings
B. Due dates, selection criteria, and payment blocks
C. Check statement IDs and import history
D. A valid recipient bank account

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 281 | **C** | Payment posting and payment medium generation are separate steps. |
| 282 | **D** | Approval controls for Business Partner bank details are important. |
| 283 | **A** | Review the exclusion log. |
| 284 | **B** | Confirm that the payment run completed successfully. |
| 285 | **C** | The actual bank transfer result must be checked separately. |
| 286 | **D** | Duplicate imports may lead to duplicate postings. |
| 287 | **A** | Automatic clearing depends on the quality of reference information. |
| 288 | **B** | Correct the underlying cause and reprocess as appropriate. |
| 289 | **C** | Clearing is managed according to the account design. |
| 290 | **D** | Some payment methods require bank information. |

---

## Set 5: Questions 291–300

### Question 291

What should be reviewed before approving a payment proposal?

A. Amount, payee, bank account, and due date
B. Reduce fraud and operational error risk
C. JPY 500
D. Exchange rates and currencies at invoice, settlement, and valuation

### Question 292

Why separate authorization for payment execution?

A. Identify the original document and item, then consider reversal
B. Reduce fraud and operational error risk
C. Bank determination, available amounts, and actual bank balance
D. Standardize reference numbers and improve matching rules

### Question 293

What is the basic response to a duplicate bank transaction posting?

A. JPY 500
B. Valuation key date and target ledger
C. Identify the original document and item, then consider reversal
D. Bank statements, payment documents, and approval records

### Question 294

What is the difference when an invoice is JPY 100,000, bank receipt is JPY 99,500, and the bank fee is JPY 500?

A. Bank determination, available amounts, and actual bank balance
B. Exchange rates and currencies at invoice, settlement, and valuation
C. Payment proposal → payment → payment medium → bank statement → reconciliation
D. JPY 500

### Question 295

What should be checked if funds are insufficient for a payment?

A. Bank determination, available amounts, and actual bank balance
B. Valuation key date and target ledger
C. Standardize reference numbers and improve matching rules
D. Amount, payee, bank account, and due date

### Question 296

What is important to check before running foreign currency valuation?

A. Exchange rates and currencies at invoice, settlement, and valuation
B. Valuation key date and target ledger
C. Bank statements, payment documents, and approval records
D. Reduce fraud and operational error risk

### Question 297

What should be investigated if exchange gains or losses differ from expectations?

A. Standardize reference numbers and improve matching rules
B. Payment proposal → payment → payment medium → bank statement → reconciliation
C. Exchange rates and currencies at invoice, settlement, and valuation
D. Identify the original document and item, then consider reversal

### Question 298

How can the automatic bank statement clearing rate be improved?

A. Bank statements, payment documents, and approval records
B. Amount, payee, bank account, and due date
C. JPY 500
D. Standardize reference numbers and improve matching rules

### Question 299

Which records are needed as an audit trail for bank transactions?

A. Bank statements, payment documents, and approval records
B. Payment proposal → payment → payment medium → bank statement → reconciliation
C. Reduce fraud and operational error risk
D. Bank determination, available amounts, and actual bank balance

### Question 300

What is the end-to-end test sequence for bank payment processing?

A. Amount, payee, bank account, and due date
B. Payment proposal → payment → payment medium → bank statement → reconciliation
C. Identify the original document and item, then consider reversal
D. Valuation key date and target ledger

### Answers and Explanations

| Question | Correct Answer | Explanation |
|---|---|---|
| 291 | **A** | Reviewing these details helps prevent wrong and duplicate payments. |
| 292 | **B** | Segregation of duties is an important control. |
| 293 | **C** | Correct the error while preserving the audit trail. |
| 294 | **D** | Accounting for the difference, such as a bank fee expense, depends on configuration. |
| 295 | **A** | Distinguish SAP configuration from the bank's actual balance. |
| 296 | **B** | Avoid valuation in an incorrect period or ledger. |
| 297 | **C** | Compare the different exchange rates involved. |
| 298 | **D** | Improve the accuracy of matching conditions. |
| 299 | **A** | They allow transactions to be traced through accounting. |
| 300 | **B** | Verify processing in both SAP and the banking system. |

---

