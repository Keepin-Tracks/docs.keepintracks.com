# Health Tracking App

This tutorial assumes that Google Sheet - Health tracking spreadsheet tutorial has been completed.

## Tracking weight
### Setting up the data
1. In the Data navigation section, select the + to add new data
2. Select your Health spreadsheet and Weight tab, then Add to app
3. Validate all data types
    - Date: DateTime
    - Weight: Decimal
    - Variation: Percent
4. Validate all initial values
    - Date: NOW()
    - All others should be empty
5. Edit formating (Click on the pencil on the left of the column)
    - Date
        - [X] Ignore seconds
        - [X] Use long date format

### Setting up the visuals
1. Access to the Views section from the sidebar just under the data section
2. Add a primary navigation
    - View name: Weight
    - For this data: Weight
    - View type: Chart
    - Edit view options
      - Chart type: Col series
      - Chart columns: Weight
      - Sort by: Date ascending
    - Edit Display options
      - icon: balance-scale

## Tracking exercises

### Exercises data
1. Add the Exercises tabs to the data
2. Validate data types
    - Exercise: Text
    - Notes: LongText
3. Validate requirements

### Exercise entries data
1. Add the ExerciseEntries tabs to the data
2. Validate data types
    - Date: DateTime
    - Exercise: Ref with source table "Exercises"
    - Quantity: Number
    - Duration: Duration
3. Validate requirements
    - Date: Required
    - All others are not required
4. Validate all initial values
    - Date: NOW()
    - All others should be empty
5. Edit formating (Click on the pencil on the left of the column)
    - Date
        - [X] Ignore seconds
        - [X] Use long date format
6. Add virtual columns
    - Total duration
        - App formula: TOTALHOURS([Duration])
        - Type: Decimal
    - End of week
        - App Formula: EOWEEK([Date])
        - Type: Date
        - [X] Use long date format

### Setting up the visuals
1. Access to the Views section from the sidebar just under the data section
2. Add a reference view
    - View name: Exercises quantity
    - For this data: ExerciseEntries
    - View type: Deck
    - Edit view options
        - Sort by: Date - descending
        - Group by:
            - End of week - Descending
            - Exercise - Ascending
        - Group aggregate: SUM::Quantity
        - Primary header: Date
        - Secondary header: None
        - Summary column: Quantity
        - [ ] Show action bar (Makes display cleaner)
    - Edit Display options
      - icon: dumbbell
3. Duplicate Exercises quantity
    - Rename: Exercises duration
    - Group aggregate: SUM :: Total duration
    - icon: running
4. Create a new view
    - View name: Exercise Tracking
    - View type: dashboard
    - Edit view options
        - View entries
            - Exercises quantity
            - Exercises duration
    - Edit display options
        - icon: dumbbell

