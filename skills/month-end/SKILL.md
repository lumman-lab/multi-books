---
name: month-end
description: A month-end check of each connected Xero and FreeAgent company - bank lines still to explain, overdue invoices and bills, last month's profit and loss and VAT - company by company. Use when asked for a month-end check, a close, or what needs doing in the books. Changes nothing.
---

# Month-end check across every company

This skill reads and changes nothing: it explains no bank line and chases no invoice.

1. Call `companies_list` and take every company, or those the person named. Name at most four companies in each later call.
2. For each company, for the month just ended unless the person named another, read:
   - `bank_accounts_list` for how many lines each bank account still has unexplained - on Xero, which gives no bank statement lines, `bank_transactions_list` with unexplained true for the entries not yet reconciled;
   - `invoices_list` and `bills_list`, each with status overdue;
   - `reports_profit_and_loss` from the first to the last day of the month;
   - `tax_returns_list` with kind vat for a VAT return still to file or with an amount still due.
3. Give each company one short section: the lines still to explain per bank account, each overdue invoice with who and how much, each overdue bill with its reference and how much, the month's income, expenses and operating profit, and what VAT is due and when, or, where an answer has none, what it says about where to see it.
4. Then say in one line which company could not be read, and why.

Examples:

- "Run my month-end check across all my companies."
- "What still needs doing in the books for October?"
- "Which bank lines are still unexplained in each company?"
