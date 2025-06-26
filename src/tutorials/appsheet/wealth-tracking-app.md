# Wealth Tracking App

This tutorial assumes that Google Sheet - Wealth tracking spreadsheet tutorial has been completed.

## Tracking your transactions

### Setting up the data
1. In the Data navigation section, select the + to add new data
2. Select your Wealth spreadsheet
3. Select all the tabs (Accounts, Categories, Sub categories, Payees, Transactions)

#### Edit Transactions 
1. Validate all data types
    - Date: Date
    - Amount: Price
    - Account: Ref to table Accounts
    - Category: Ref to table Categories
    - Sub category: Ref to table Sub categories
    - Payee: Ref to table Payees
    - Description: LongText
    - Tax related: Yes/No
2. Validate all initial values
    - Date: TODAY()
    - All others should be empty
3. Add virtual column
    - End of month: Date
        - App formula: EOMONTH([Date], 0)
        - [X] Use long date formats
4. Edit formating (Click on the pencil on the left of the column)
    - Date
        - [X] Use long date format
    - Tax related 
        - No value: 'No' (Quotes are important else it will be in uppercase)
        - Yes value: 'Yes'

#### Edit Accounts
1. Validate all data types
    - Account: Text
    - Type: Enum
    - Starting amount: Price
    - Current value: Price
    - Balance: Price (Not editable since formula is in Google Sheet)
2. Edit initial values
    - Starting amount: 0
2. Edit requirements
    - Account: Required
    - Starting amount: Required
    - All others not required

#### Edit Sub categories
1. Validate all data types
    - Sub category: Text
    - Category: Ref to table Categories

### Create the visuals

#### Transactions
1. In the Views section, create a new view
    - View name: Transactions
    - For this data: Transactions
    - View type: Deck
2. Edit View options
    - Sort by: Category - Ascending
    - Group by: Date - Descending
    - Group aggregate: SUM :: Amount
    - Primary header: Date
    - Secondary header: Category
    - Summary column: Amount
    - [ ] Show action bar
3. Edit display options
    - Icon: money-check-edit-alt

#### Accounts
1. In the Views section, create a new view
    - View name: Accounts
    - For this data: Accounts
    - View type: Deck
    - Position: Last
2. Edit View options
    - Sort by: Account - Ascending
    - Group by: Type - Descending
    - Group aggregate: SUM :: Balance
    - Primary header: Account
    - Secondary header: None
    - Summary column: Balance
    - [ ] Show action bar
3. Edit display options
    - Icon: university


## App template
<iframe src="https://www.appsheet.com/start/ec41bd14-bc2e-4280-a168-7cf5dde6e8cf" width="320" height="568" />