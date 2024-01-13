# From-spreadsheets-to-BigQuery
In this repository I used spreadsheets to clean my data before importing it into SQL for analysis.
# About the project and dataset
I have been working for a national store chain as a data analyst. Management is interested in the amount of inventory being kept in storage at regional sites. I was asked to perform an analysis on inventory and sales data to make recommendations for changes to inventory management practices. I have been provided with three datasets containing information about inventory, products, and sales. To get started, I downloaded the three store data CSV files: inventory, products, and sales. Link below.
# https://drive.google.com/u/0/uc?id=1FCo85-_jwlOkqucuiizlP3WyCEu1uXBH&export=download
# https://drive.google.com/u/0/uc?id=1hQ3_EqXPANEPhyY-VDKa9LTuB73E_DVT&export=download
# https://drive.google.com/u/0/uc?id=1Qm1FFskt30Cc1I8XbptukBnT3T1ZHeJ-&export=download
Before i uploaded these files to SQL, i imported them into a spreadsheet in Sheets to get comfortable with the data before i start analyzing it in BigQuery. From the file menu on Google sheets i imported the first file and in new sheets i imported the remaining files. Inspected the files by applying filters to identify any data that needs to be cleaned. On the inventory sheet, i looked out for blanks or incorrectly entered values. The 'storename' column returned one row with a missing entry. To correct this i Cleared the Storename filter and used the StoreId column filter for other stores with the ID 21791 (same  ID for the missing storename). The other stores with this ID are all Dollar Tree, so it’s probably safe to input that as the StoreName value in the blank cell. Inspected the other columns and SheetS, In the Products sheet, the ProductID column has NA value, despite the fact that this column should only have numeric values. In this case, i checked in with the dataset owner, who said i can delete this row because it was inputed by mistake and does not belong in this dataset.
Next i moved to BigQuery. Created a dataset and custom table from the explorer pane, for the dataset i named it 'sales' because that was the file i was starting with and for the table i named it 'sales_info'. Opened the new table 'sales_info' in the explorer pane, inspected the data to determine how much of it will be useful for your final analysis. I ensured that the import was successful by running the below query.
# https://console.cloud.google.com/bigquery?sq=909859753623:4384a33c03bb4a188e2dc9893e8e8305
Next,i inspected the data to find out how many years of sales data it includes using the MIN and MAX functions to get the oldest and newest dates
# https://console.cloud.google.com/bigquery?sq=909859753623:11e73e5b4a5a41a09585c682984f4511
Now i know what years this data covers. Next, I grouped the data by month because management wants to see year-over-year changes to inventory by month. Link is below, this will return the total quantity sold for each ProductId grouped by the month and year it was sold.
# https://console.cloud.google.com/bigquery?sq=909859753623:638530e322154dc8831c9f5c0d8e5584
Next, i exported to spreadsheet because the stakeholder requested it in that form and that can be easily done since the subset of data i queried is few. After running the query, i clicked SAVE RESULTS. There is a pop-up menu with the option to choose the file type for export. Selected CSV Google Drive. Once it is downloaded, i opened the new CSV file in Drive and with 'google sheets'. Repeated these steps for the other 2 files.
# Summary
 In spreadsheets, you are able to observe and interact with data directly; with SQL, you interact with data through queries to the database. Switching between spreadsheets and SQL can be challenging because they’re so different, but being used to both tools, i am able to use both more easily. With SQL, you can only observe the results of your query, which requires a different mindset than spreadsheets — but SQL is very powerful when you’re working with databases and larger datasets! 
