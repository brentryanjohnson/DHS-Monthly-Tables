# dhs-monthly-tables

This repository contains a Jupyter Notebook with a Python script that references a source Excel file and reformats it into a flat `csv` file that's used to update the [Monthly Tables charts and tables on the Office of Homeland Security Statistics website](https://ohss.dhs.gov/topics/immigration/immigration-enforcement/immigration-enforcement-and-legal-processes-monthly).

## Notebook

The notebook with the relevant python is titled `monthly merge – CBP SWB Book-outs by Agency.ipynb`

## Files

### Source `xlsx`

There are two examples of the source Excel workbooks:
1. `2024_1108_ohss_immigration-enforcement-and-legal-processes-tables-july-2024.xlsx`
1. `2024_1206_ohss_immigration-enforcement-and-legal-processes-tables-august-2024.xlsx`

We only pass in one of these files for the source Excel file. The data changes every month, so we receive a new file monthly. The new file should be added and referenced in the notebook.

### Output `csv`

There are two examples of the output `csv`:
1. `ielp-table-202407-t.csv`
1. `ielp-table-202408.csv`

The notebook exports a file with a different name (`output.csv`); the included file is the aspirational format that the python code is intended to create from the source excel file.

## How to use the notebook

### Dependencies

I created this notebook with Jupyter Notebook using Python and the pandas library. I used the Anaconda Python distribution on Windows to create this code.

### Assumptions

- We receive a monthly data file in the format expressed in `2024_1206_ohss_immigration-enforcement-and-legal-processes-tables-august-2024.xlsx`.
- We need to output the data in the format expressed in `ielp-table-202407-t.csv`.

### Caveats

- I am not a software engineer, data scientist, or statistician. I'm a content designer. Skilled python developers will likely notice this code could be improved.
- You don't need to use the notebook. You can export (download) the python and run the script outside of the notebook (with python).

### Notebook cells and process

At DHS, you must have Anaconda approved and installed. Once installed:

1. Search for the app `Jupyter Notebook`.
2. Open the Jupyter Notebook app and navigate the file system to find your download

#### Then
1. Review the source Excel file for consistency in sheet and column names.
2. In this cell in the notebook, replace the file name with the updated source file: `ielp_sheet='2024_1206_ohss_immigration-enforcement-and-legal-processes-tables-august-2024.xlsx'` <br>
> [!NOTE]  
> Make sure to use quotes around the file name, and make sure that the file is located in the same directory as the notebook file.
3. Select `Cell`→`Run All` from the top of the notebook.
4. Look for `output.csv` in the same directory as the notebook file.
5. Check the data structure of `output.csv` against the included `ielp-table-202407-t.csv`.
6. Spot check the data of `output.csv` against the relevant data in `2024_1206_ohss_immigration-enforcement-and-legal-processes-tables-august-2024.xlsx`.

#### Spot-check crosswalk

Here's a key to crosswalk (some of) the data fields:

```

Southwest Border Book-Outs visualization requirements:
Southwest border book-outs comes from the sheet "CBP SWB Book-outs by Agency".
Columns T-AA populate the data for the dropdown "At Points of Entry - Office of Field Operations (OFO)"
- Other outcomes - column AA
- OFO Paroles - column Z
- Transfers to HHS - column Y
- Transfers to ICE - column  X
- Migrant Protection Protocols - column W
- T42 expulsions - column V
- T8 repatriations - column U
- Total - column T

Columns L-S populate the data for the dropdown "Between Ports of Entry - U.S. Border Patrol (USBP)"
- Other outcomes - column S
- USBP Releases - column R
- Transfers to HHS - column Q
- Transfers to ICE - column P
- Migrant Protection Protocols - column O
- T42 expulsions - column N
- T8 repatriations - column M
- Total - column L

Columns C-K populate the data for the dropdown "All Southwest Border Book-outs"
- Other outcomes - column K
- OFO Paroles - column J
- USBP Releases - column I
- Transfers to HHS - column H
- Transfers to ICE - column G
- Migrant Protection Protocols - column F
- T42 expulsions - column E
- T8 repatriations - column D
- Total - column C

```

## Compare

`compare.ipynb` compares two `csv` files and outputs a third (`difference.csv`) that shows any differences between the two files. I used this to compare the manually created `csv` against that which I'm outputting with the script in the `monthly merge` notebook. Doing so indicated an error in the original version of the notebook, which I have since corrected.

## Iteration

I continue to iterate on the notebooks, so review the commits to make sure you have the most recent version.