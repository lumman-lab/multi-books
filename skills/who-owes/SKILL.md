---
name: who-owes
description: Who owes money to each connected Xero, Zoho Books and FreeAgent company, and how late - or whom each company owes - across every company at once, in each currency apart. Use when asked who owes money, about debtors or overdue invoices to chase, or what the companies owe their suppliers. Changes nothing.
---

# Who owes each company, and how late

This skill reads and changes nothing: it sends no reminder and records no payment.

1. Call `companies_list` and take every company, or those the person named. Name at most four companies in each later call.
2. Read `reports_aged_receivables` for what each company is owed, or `reports_aged_payables` for what it owes, as the person asked.
3. For each company, list each contact owing or owed anything, the most overdue first: who, what is not yet due, and what is 1-30, 31-60, 61-90 and over 90 days late, in each currency apart - never add one currency to another - then the company's totals.
4. Where an answer is marked computed, say once that its figures are worked out by Multi Books from the open invoices or bills rather than a report of the program. A Zoho Books company's figures are the program's own report.
5. Then say in one line which company could not be read, and why.

Examples:

- "Who owes money to each of my companies, and how late is each invoice?"
- "Which customers are more than 60 days late across all my companies?"
- "What does each of my companies owe its suppliers, and how late is each bill?"
