---
name: photo-expense-tracker
description: Track business expenses from receipt photos and emails. Extracts merchant, amount, VAT, date, and category from images, then appends to a monthly CSV with receipt archiving. Use when a photographer or freelancer sends a receipt photo, forwards a receipt email, or asks about expenses, tax deductions, or bookkeeping.
---

# Photo Expense Tracker

## Setup

Create the expense directory structure at the start of each year:

```
expenses/
└── 2026/
    └── MM/
        ├── expenses.csv
        └── receipts/
```

Directories are created automatically as receipts come in.

## CSV Format

One CSV per month at `expenses/YYYY/MM/expenses.csv`:

```csv
Date,Merchant,Description,Amount (€),Payment Method,Category,TVA Rate,TVA (€),HT (€),Address,Receipt File
```

**Categories:** Equipment, Travel, Meals, Software, Office, Printing, Insurance, Professional Services, Subscriptions, Communication, Other

**Payment methods:** Mastercard 0035, Revolut 8677, Cash, Transfer, Other

## Workflow: Receipt Photo

1. Receive a photo of a receipt (paper receipt, restaurant bill, invoice, etc.)
2. Extract from the image:
   - **Merchant name** and address
   - **Date** of purchase
   - **Total amount** (TTC — all taxes included)
   - **TVA rate** and amount (if shown — common rates: 20%, 10%, 5.5%, 2.1%)
   - **HT amount** (pre-tax, calculate if not shown: HT = TTC / (1 + TVA rate))
   - **Payment method** (if visible on receipt, otherwise ask)
   - **Description** of what was purchased
3. Save original image to `expenses/YYYY/MM/receipts/YYYY-MM-DD_merchant.jpg`
4. Append one line to the monthly CSV
5. Confirm to the user with a summary: merchant, amount, category

## Workflow: Email Receipt

Same as above but extract data from the email body/attachment instead of a photo.

## Rules

- **Never create separate files per expense** — always append to the monthly CSV
- **Keep original receipt images** — French tax authorities require them for 6 years
- If TVA is not visible on receipt, estimate using the standard rate for the category:
  - Meals/restaurants: 10%
  - Equipment/software/services: 20%
  - Books/publications: 5.5%
- If merchant or amount is unclear, ask before recording
- Round amounts to 2 decimal places
- Date format: YYYY-MM-DD

## Quick Queries

Common questions to handle:

- **"How much did I spend this month?"** → Sum the Amount column in current month's CSV
- **"What's my total for [category]?"** → Filter and sum by category
- **"Show me February expenses"** → Read and display the CSV
- **"What can I deduct?"** → All business-related expenses with TVA are deductible; summarize total HT and TVA recoverable

## French Tax Context

See `references/french-freelance-tax.md` for TVA rates, deduction rules, and BNC regime basics.
