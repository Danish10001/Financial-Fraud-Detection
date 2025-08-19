SQL-Based Fraud Detection in Financial Transactions

This project demonstrates how SQL queries can be used to detect fraudulent and suspicious activities in financial transactions.
The dataset contains 20,000+ records of payments, transfers, cash-outs, and deposits.

Using SQL, we analyze:

* Balance inconsistencies
* Zero-balance mule accounts
* Large suspicious transfers
* High-frequency transactions
* Money laundering loops (A → B → A, A → B → C → A)
* Structuring (same amount sent to many accounts)


🗂️ Dataset
Table Name: `transactions`
Columns:

  * `transaction_id`
  * `step` (time unit/day)
  * `transaction_type`
  * `amount`
  * `sender_account`, `sender_old_balance`, `sender_new_balance`
  * `recipient_account`, `recipient_old_balance`, `recipient_new_balance`



🔎 Key SQL Queries

1. Overview of transactions (total, average, max).
2. Largest transactions by amount.
3. Balance mismatch detection.
4. Zero-balance mule account detection.
5. Suspiciously large transfers.
6. High-frequency transfers (smurfing).
7. Two-step laundering detection (A ↔ B).
8. Structuring (same amount sent to many accounts).
9. Collector accounts (many unique senders).
10. Distributor accounts (many unique recipients).
11. Chain laundering (A → B → C).
12. Transactions involving mule accounts.
13. Transaction volume by type.
14. Daily suspicious exposure.
15. Accounts that both send and receive.


🚀 How to Run

1. Import the dataset into your SQL database.
2. Create the table:

   
   CREATE TABLE transactions (
       transaction_id INT PRIMARY KEY,
       step INT,
       transaction_type VARCHAR(20),
       amount DECIMAL(12,2),
       sender_account VARCHAR(20),
       sender_old_balance DECIMAL(14,2),
       sender_new_balance DECIMAL(14,2),
       recipient_account VARCHAR(20),
       recipient_old_balance DECIMAL(14,2),
       recipient_new_balance DECIMAL(14,2)
   );
   
3. Load the CSV data into the table.
4. Run the SQL queries in your preferred SQL editor.


📊 Insights

* Fraudulent accounts often have zero balances before and after transactions.
* Large transfers and rapid small transfers are strong indicators of fraud.
* Money laundering can be detected through round-trip transactions and multi-step chains.
* Certain accounts act as hubs, collecting from or distributing to multiple accounts.
