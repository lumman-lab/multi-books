---
name: cash
description: The cash across every connected Xero, Zoho Books and FreeAgent company - each bank balance today, totalled in each currency - and, when asked, a forecast 30, 60 and 90 days ahead from what is owed each way and what recurs, with its risks. Use when asked about cash, bank balances or a cash forecast. Changes nothing.
---

# Cash across every company

This skill reads and changes nothing.

1. Call `companies_list` and take every company, or those the person named. Name at most four companies in each later call.
2. Read `bank_accounts_list` for every company. List each company's bank accounts with their balances, then the total for each company and across all of them in each currency apart - never add one currency to another; a Xero balance counts in its balance currency.
3. Only for a forecast, also read, every page of each:
   - `reports_aged_receivables` and `reports_aged_payables` for what is owed each way and how late;
   - `invoices_list` and `bills_list`, each with status open, for the day each amount not yet due falls due;
   - `recurring_invoices_list` and `recurring_bills_list` for what repeats, how often and when next.

   In each currency apart, start from today's balance, add each invoice and take away each bill on the day it falls due, what is already overdue within the first 30 days, and each recurring invoice and bill on each day it would be settled inside the 90 days - the day it recurs plus its payment terms where it names them. Give each company's balance at 30, 60 and 90 days, then the same across all of them.
4. For a forecast, name its risks: the overdue money it counts on, the latest first; any customer whose payments carry a large part of it; any company or currency that runs below zero, and when; and what it leaves out - whatever no invoice or bill records, such as wages, tax, card spending and transfers between the companies. Say once that the forecast is worked out by Multi Books from the books rather than a report of any program.
5. Then say in one line which company could not be read, and why.

Examples:

- "How much cash do my companies have right now?"
- "Forecast my companies' cash for the next 90 days."
- "Will any of my companies run out of cash this quarter?"
