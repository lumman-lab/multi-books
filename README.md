# Multi Books

FreeAgent, Xero, QuickBooks Online and Zoho Books in AI apps: many companies at once - one answer.

Multi Books is a remote MCP server run by Lumman Ltd. It connects the books of several companies - your FreeAgent companies, Xero organisations, QuickBooks Online companies and Zoho Books organisations, all at once - behind one connector, so an AI client can answer one question across every company you run, whichever program keeps it, and do the bookkeeping in each. This repository holds what clients install: the manifests for Claude Code, Cursor, Gemini CLI and Antigravity, and three skills. The server itself is not in it.

## Before you start

You need a Lumman account with at least one company added - in the window your AI client opens when it first connects, or at https://lumman.co/mcp/account/multi-books. Sign in there with Google, Microsoft, a passkey or an emailed code. Each company is added once, with its program's own sign-in - FreeAgent, Xero, Intuit for QuickBooks Online or Zoho for Zoho Books - and stays connected: any number of companies, no switching or reconnecting. Each company's read-only switch is on the same page.

## Add it to your client

### Claude

In Claude, open Settings, Connectors and press Add custom connector. Name it Multi Books, paste `https://books.lumman.co/mcp`, then approve on the Lumman page that opens.

### Claude Code

```
/plugin marketplace add lumman-lab/multi-books
/plugin install multi-books@multi-books
```

The plugin adds the connector at https://books.lumman.co/mcp and the three skills below. The first time a skill reaches the connector, Claude Code asks you to sign in; if it does not, run `/mcp` and choose the multi-books server.

### Cursor

Add the connector to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "multi-books": { "url": "https://books.lumman.co/mcp" }
  }
}
```

### VS Code

Run `MCP: Add Server`, choose `HTTP`, paste `https://books.lumman.co/mcp` and name it `multi-books`. Or add it to your user `mcp.json`:

```json
{
  "servers": {
    "multi-books": { "type": "http", "url": "https://books.lumman.co/mcp" }
  }
}
```

### Gemini CLI

```
gemini extensions install https://github.com/lumman-lab/multi-books
```

The extension adds the connector at https://books.lumman.co/mcp and the three skills below. Its first call opens Lumman's sign-in in your browser; `/mcp auth multi-books` opens it again.

### Antigravity

```
agy plugin install https://github.com/lumman-lab/multi-books
```

The plugin adds the connector at https://books.lumman.co/mcp and the three skills below, for the Antigravity CLI, app and IDE alike. To sign in, run `/mcp` in the CLI, open `multi-books_multi-books` and choose Authenticate, or in the app or IDE press Authenticate next to it under Agent settings, Customizations; approve on the Lumman page that opens, then paste the code Antigravity's page shows back into Antigravity.

### ChatGPT

Works fully on ChatGPT Business, Enterprise and Edu.

1. Open chatgpt.com/plugins, press +, then Add custom MCP server.
2. Name it Multi Books, paste `https://books.lumman.co/mcp`, choose OAuth, tick the box and press Create as a plugin.
3. Install it. On the Lumman page, sign in, add a company if none is connected, and approve.
4. In a chat, type @ and choose Multi Books.

### Any other client

Add a remote MCP server at `https://books.lumman.co/mcp`: Streamable HTTP, OAuth 2.1 with dynamic client registration. No key or client id is needed.

## Signing in

The connector answers a client's first call with where to sign in. The client registers itself with Lumman's authorisation server and opens a Lumman page that names it: sign in, add a company if none is connected, and approve. Every client you approve is listed under Connected AI clients at https://lumman.co/mcp/account/multi-books, where its access can be taken back.

## Skills

Claude Code, Cursor, Gemini CLI and Antigravity load three skills with the connector, and pick one by themselves when a request matches it. In Claude Code each is also a command, such as `/multi-books:month-end`.

- `cash` - every bank balance across your companies, totalled in each currency, and on request a forecast 30, 60 and 90 days ahead with its risks. Changes nothing.
- `month-end` - a month-end check of each company: bank lines still to explain, overdue invoices and bills, last month's profit and loss and VAT. Changes nothing.
- `who-owes` - who owes each company money, or whom each company owes, by how late, in each currency apart. Changes nothing.

Examples:

- "Who owes money to each of my companies, and how late is each invoice?"
- "Compare last month's profit and loss across all my companies."
- "Explain this week's bank transactions in my consulting company - show me before you change anything."

## Ready requests

The connector offers these requests ready-made; a client shows them as prompts or commands.

- `month_end_check` - Month-end check. Unexplained bank lines, overdue invoices and bills, last month's profit and loss and VAT returns, company by company.
- `who_owes_me` - Who owes me. What each customer owes across all your companies, by how late it is.
- `cash_across_companies` - Cash across my companies. Every bank balance across all your companies, totalled in each currency.
- `cash_forecast` - Cash forecast. Cash 30, 60 and 90 days ahead across all your companies, from what is owed each way and what recurs, with its risks.

## Tools

| Tool | Name |
|---|---|
| `companies_list` | List companies |
| `bank_accounts_list` | List bank accounts |
| `bank_transactions_list` | List bank transactions |
| `contacts_list` | List contacts |
| `invoices_list` | List invoices |
| `invoices_get` | Read an invoice |
| `estimates_list` | List estimates |
| `credit_notes_list` | List credit notes |
| `bills_list` | List bills |
| `bills_get` | Read a bill |
| `attachments_get` | Read an attachment |
| `accounts_list` | List categories |
| `reports_profit_and_loss` | Read the profit and loss |
| `reports_balance_sheet` | Read the balance sheet |
| `reports_trial_balance` | Read the trial balance |
| `reports_aged_receivables` | Read who owes the company |
| `reports_aged_payables` | Read whom the company owes |
| `reports_totals_by_contact` | Read totals by customer or supplier |
| `reports_cash_flow` | Read the cash flow statement on Zoho Books |
| `reports_general_ledger` | Read the general ledger on Zoho Books |
| `reports_sales_by_item` | Read sales by item on Zoho Books |
| `tax_returns_list` | List tax returns |
| `projects_list` | List projects |
| `time_entries_list` | List time entries |
| `expenses_list` | List expenses |
| `journals_list` | List journals |
| `recurring_invoices_list` | List recurring invoices |
| `recurring_bills_list` | List recurring bills |
| `purchase_orders_list` | List purchase orders |
| `payments_list` | List payments |
| `tracking_categories_list` | List tracking categories |
| `items_list` | List items |
| `tax_rates_list` | List tax rates |
| `contacts_create` | Create a contact |
| `contacts_update` | Change a contact |
| `invoices_create` | Create an invoice |
| `invoices_update` | Change an invoice |
| `invoices_send` | Send an invoice |
| `invoices_void` | Void an invoice |
| `invoices_delete` | Delete an invoice |
| `estimates_create` | Create an estimate |
| `estimates_update` | Change an estimate |
| `estimates_send` | Send an estimate |
| `credit_notes_create` | Create a credit note |
| `credit_notes_update` | Change a credit note |
| `projects_create` | Create a project |
| `projects_update` | Change a project |
| `time_entries_create` | Record time |
| `time_entries_update` | Change a time entry |
| `time_entries_delete` | Delete a time entry |
| `bills_create` | Create a bill |
| `bills_update` | Change a bill |
| `bills_delete` | Delete a bill |
| `expenses_create` | Record an expense |
| `expenses_update` | Change an expense |
| `expenses_delete` | Delete an expense |
| `bank_transactions_code` | Explain a bank transaction |
| `bank_transactions_uncode` | Undo an explanation |
| `payments_record` | Record a payment |
| `journals_create` | Create a journal |
| `journals_update` | Change a journal |
| `items_create` | Create an item |
| `items_update` | Change an item |

## Where your books go

Every client sends its calls to https://books.lumman.co/mcp, run by Lumman. Signing in runs through the authorisation server that address names. Lumman keeps no copy of your books: they are read from FreeAgent, Xero, QuickBooks Online or Zoho Books each time a client asks. The words of every record are screened for prompt attacks before they reach your AI client, as are the words of everything a client writes before they reach your program, and the books are passed on only to the client you approved. What the connector passes on, and to whom - the screening service among them - is in the privacy policy: https://lumman.co/privacy.

Switch any one company to read only at https://lumman.co/mcp/account/multi-books and every change there is refused before its program is asked. Multi Books never moves money: it records payments but makes none, charges no card and files no tax return.

## Limits

- One call reads at most four companies; a question across more takes several calls.
- Bank transactions are explained and recorded in FreeAgent, Xero and Zoho Books; VAT return figures are read in FreeAgent, QuickBooks and Zoho Books.
- A write whose answer was lost is settled by reading the books back, never by sending it again.
- A record whose words screen as a prompt attack is withheld rather than passed on, and a call whose screening cannot finish is closed. A file's own bytes - an attachment or a receipt - are not screened.

## Security

Report a vulnerability privately through GitHub, as [SECURITY.md](SECURITY.md) describes.

## Support

Write to the address under Contact Us in Lumman's privacy policy: https://lumman.co/privacy.

## Licence

The files in this repository are under the MIT licence in [LICENSE](LICENSE). The Multi Books service they connect to is provided under Lumman's terms: https://lumman.co/terms.

Intuit and QuickBooks are registered trademarks of Intuit Inc. Used with permission. Zoho and Zoho Books are trademarks of Zoho Corporation Private Limited and/or its affiliates.
