# Wealth Tracking Sheet
1. Create a sheet "Wealth"

## Setting up the base : Accounts

1. Name first tab: "Accounts"
2. Create a table named "Accounts"
3. Set up the columns (Name: Data type)
    - Account: Text
    - Type: Dropdown (With values: Cash, Credit, Investing, Debt, Loan)
    - Starting amount: Currency
        - The balance of the account before the first transactions you'll record in the spreadsheet
    - Current value: Currency
        - Used for Investing accounts which value is not related to transactions in them.
    - Balance: Currency
        - Formula: **to be defined once Transaction table is set**

## Setting up the Transaction table

1. Create a new tab Transactions
2. Create a table named "Transactions"
3. Set up the columns (Name: Data type)
    - Date: Date
    - Amount: Currency
    - Account: Dropdown from range (=Accounts!$A$2:$A)

## Calculating accounts balance in real time
1. Add formula to table "Accounts", column balance
```sql
=IF(
    Accounts[Current value],
    Accounts[Current value],
    Accounts[Starting amount] + SUMIF(
        Transactions[Account],
        Accounts[Account],
        Transactions[Amount]
    )
)
```

## Categorizing transactions

### Set up categories
1. Create a new table "Categories" with a new table "Categories"
2. Set up the columns (Name: Data type)
    - Category: Text
3. Add column "Category" in tab "Transactions"
    - Category: Dropdown from range () (Categories!A2:A)

### Set up sub categories
1. Create a new table "Categories" with a new table "Sub categories"
2. Set up the columns (Name: Data type)
    - Sub category: Text
    - Category: Dropdown from range (Categories!A2:A)
3. Add column "Sub category" in tab "Transactions"
    - Sub category: Dropdown from range () (Sub categories!A2:A)

### Set up payees
1. Create a new table "Categories" with a new table "Payees"
2. Set up the columns (Name: Data type)
    - Payee: Text
3. Add column "Payee" in tab "Transactions"
    - Payee: Dropdown from range () (Payees!A2:A)

### Need more precision?
1. Add columns to table "Transactions"
    - Description: Text
    - Tax related: Checkbox
