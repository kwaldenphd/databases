# Introduction to Databases

<a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license"><img style="border-width: 0;" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" alt="Creative Commons License" /></a>
Introduction to Databases by <a href="dlac.grinnell.edu" rel="cc:attributionURL">Katherine Walden, Digital Liberal Arts Specialist (Grinnell College)</a> is licensed under a <a href="http://creativecommons.org/licenses/by-nc/4.0/" rel="license">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

The author consulted the following resources when building this tutorial:
- [W3 Schools "Syntax"](https://www.w3schools.com/sql/default.asp)
- [W3 Schools "SQL Syntax"](https://www.w3schools.com/sql/sql_syntax.asp)
- [Library Carpentry "Tidy Data for Librarians"](https://librarycarpentry.org/lc-spreadsheets/)
- [Library Carpentry "Database Design"](https://librarycarpentry.org/lc-sql/08-database-design/index.html)
- [Library Carpentry "Open Refine"](https://librarycarpentry.org/lc-open-refine/)
- [Library Carpentry "SQL"](https://librarycarpentry.org/lc-sql/)

# Table of Contents

- [Tidy Data Principles](#tidy-data-principles)
  * [What Are the Principles](#what-are-the-principles)
  * [Common Spreadsheet Errors](#common-spreadsheet-errors)
  * [Dealing With Messy Data](#dealing-with-messy-data)
    * [Identify Patterns and Brainstorm Solutions](#identify-patterns-and-brainstorm-solutions)
    * [Data Wrangling Using OpenRefine](#data-wrangling-using-openrefine)
    * [Data Wrangling Using a Spreadsheet Program](#data-wrangling-using-a-spreadsheet-program)
- [Workflows for Data Entry](#workflows-for-data-entry)
  * [Survey Versus Spreadsheet](#survey-versus-spreadsheet)
  * [Data Validation](#data-validation)
- [Understanding Relational Databases](#understanding-relational-databases)
  * [Why A Database?](#why-a-database)
  * [What is an ERD?](#what-is-an-erd)
    * [Entities](#entities)
    * [Attributes](#attributes)
    * [Relationships](#relationships)
    * [Cardinality](#cardinality)
  * [Building an ERD](#building-an-erd)
    * [Where Are My Keys?](#where-are-my-keys)
    * [Relational Schema](#relational-schema)
- [SQL Query Syntax](#sql-query-syntax)
  * [Selecting and Sorting](#selecting-and-sorting)
  * [Filtering](#filtering)
  * [Aggregating and Calculating](#aggregating-and-calculating)
  * [Joins](#joins)
- [Optional: Relational Databases in Excel Using PivotTables](#optional-relational-databases-in-excel-using-pivottables)
- [Additional Resources](#additional-resources)
- [Lab Notebook Questions](#lab-notebook-questions)

# Tidy Data Principles

Hadley Wickham's 2014 article in the *Journal of Statistical Software* outlines the foundations and principles of tidy data. Article abstract: "A huge amount of effort is spent cleaning data to get it ready for analysis, but there has been little research on how to make data cleaning as easy and effective as possible. This paper tackles a small, but important, component of data cleaning: data tidying. Tidy datasets are easy to manipulate, model and visualize, and have a specific structure: each variable is a column, each observation is a row, and each type of observational unit is a table. This framework makes it easy to tidy messy datasets because only a small set of tools are needed to deal with a wide range of un-tidy datasets. This structure also makes it easier to develop tidy tools for data analysis, tools that both input and output tidy datasets. The advantages of a consistent data structure and matching tools are demonstrated with a case study free from mundane data manipulation chores." (Hadley Wickham, Tidy Data, Vol. 59, Issue 10, Sep 2014, Journal of Statistical Software. http://www.jstatsoft.org/v59/i10.)

Wickham's tidy data principles have become widely used in data science and other statistical software applications. 

To prepare for this lab, we read Karl W. Broman and Kara H. Woo's 2018 "Data Organization in Spreadsheets" from *The American Statistician*. Article abstract: "Spreadsheets are widely used software tools for data entry, storage, analysis, and visualization. Focusing on the data entry and storage aspects, this article offers practical recommendations for organizing spreadsheet data to reduce errors and ease later analyses. The basic principles are: be consistent, write dates like YYYY-MM-DD, do not leave any cells empty, put just one thing in a cell, organize the data as a single rectangle (with subjects as rows and variables as columns, and with a single header row), create a data dictionary, do not include calculations in the raw data files, do not use font color or highlighting as data, choose good names for things, make backups, use data validation to avoid data entry errors, and save the data in plain text files." ( Karl W. Broman & Kara H. Woo (2018) Data Organization in Spreadsheets, The American Statistician, 72:1, 2-10, DOI: 10.1080/00031305.2017.1375989)

## What Are the Principles

Designing spreadsheets that are “tidy, consistent, and as resistant to mistakes as possible” (2)

1- Be Consistent:
  * Use consistent codes for categorical variables
  * Use a consistent fixed code for any missing values
  * Use consistent variable names
  * Use consistent subject identifiers
  * Use a consistent data layout in multiple files
  * Use consistent file names
  * Use a consistent format for all dates
  * Use consistent phrases in your notes
  * Be careful about extra spaces within cells

2- Choose Good Names for Things:
  * Avoid spaces
  * Avoid special characters
  * Be short but meaningful

3- Write Dates as YYYY-MM-DD
  * Or have separate columns for YEAR, MONTH, DATE

4- No Empty Cells

5- Put Just One Thing in a Cell

6- Make it a Rectangle
  * Single first row with variable names

7- Create a Data Dictionary
  * “This is part of the metadata that you will want to prepare: information about the data” (6)
  * You might also find this information in a codebook that goes with a dataset
  * Things to include:
    a- The exact variable name as in the data file
    b- A version of the variable name that might be used in data visualizations
    c- A longer explanation of what the variable means
    d- The measurement units
    e- Expected minimum and maximum values

8- No Calculations in the Raw Data Files

9- Do Not Use Font Color or Highlighting as Data

10- Make Backups
  * Multiple locations (OneDrive, local computer, etc.)
  * Version control program (i.e. Git)
  * Write protect the file when not entering data

11- Use Data Validation to Avoid Errors

12- Save a Copy of the Data in Plain Text Files
  * File formats can include comma-separated values (CSV) or plain-text (TXT)
  
The principles are also available as a PDF in this repo.

## Common Spreadsheet Errors

As described in Library Carpentry's ["Tidy data for librarians" tutorial](https://librarycarpentry.org/lc-spreadsheets/02-common-mistakes/index.html), common formatting problems for data in spreadsheets include:

- Multiple tables
- Multiple tabs
- Not filling in zeros
- Using bad null values
- Using formatting to convey information
- Using formatting to make the data sheet look pretty
- Placing comments or units in cells
- More than one piece of information in a cell
- Field name problems
- Special characters in data
- Inclusion of metadata in data table
- Date formatting


<blockquote>Q1: What questions do you have about these principles? Which ones are unclear are confusing?</blockquote>
 
## Dealing With Messy Data

Extract the contents of the `database_lab_data.zip` folder.

Open the `CSC_Database_Lab_Player_Birthplaces.csv` and `CSC_Database_Lab_TeamLocations.csv` files in a spreadsheet program.

Explore both files.

<blockquote>Q2: What fields are represented in these datasets? Describe the data fields in your own words. Use the language of string, double, and integer to describe the data fields.</blockquote>

<table>
 <tr>
  <th><Data Type</th>
  <th>Description</th>
  <th>Example</th>
 </tr>
 <tr>
  <td>String</td>
  <td>Used to store text or a string of non-integer characters.</td>
  <td>"This classroom is in the HSSC" or "student".</td>
 </tr>
 <tr>
  <td>Integer</td>
  <td>Used to store positive or negative whole numbers.</td>
  <td>-25, 0, 25</td>
 </tr>
 <tr>
  <td>Double</td>
  <td>Used to store precise numerical values that include decimal points.</td>
  <td>3.14159265359</td>
 </tr>
 </table>
 
 
### Identify Patterns and Brainstorm Solutions

Compare what you see in the `CSC_Database_Lab_Player_Birthplaces.csv` and `CSC_Database_Lab_TeamLocations.csv` files to the tidy data principles outlined above.

Start by looking for small-scale discrepencies and inconsistencies within the datasets.

<blockquote>Q3: Provide 3 distinct examples from the sample datasets that do not conform to tidy data principles. Include the example as well as an explanation.</blockquote>

<blockquote>Q4: Discuss with a colleague what issues you are seeing in these datasetes. What commonalities or patterns are you seeing?</blockquote>

<blockquote>Q5: How would you address these pattern errors so the data conforms to tidy data principles? Describe what steps you would take to address at least 3 pattern errors. For each error, include the following elements: an example of the error, an explanation of your method to address the error, and the same example as tidy data.</blockquote>

### Data Wrangling Using OpenRefine

As described in Library Carpentry's ["Introduction to OpenRefine"](https://librarycarpentry.org/lc-open-refine/01-introduction/index.html):

"OpenRefine is described as 'a power tool for working with messy data' ([David Huynh](http://web.archive.org/web/20141021040915/http://davidhuynh.net/spaces/nicar2011/tutorial.pdf)) - but what does this mean? It is probably easiest to describe the kinds of data OpenRefine is good at working with and the sorts of problems it can help you solve.

"OpenRefine is most useful where you have data in a simple tabular format such as a spreadsheet, a comma separated values file (csv) or a tab delimited file (tsv) but with internal inconsistencies either in data formats, or where data appears, or in terminology used. OpenRefine can be used to standardize and clean data across your file. 

"It can help you:
- Get an overview of a data set
- Resolve inconsistencies in a data set, for example standardizing date formatting
- Help you split data up into more granular parts, for example splitting up cells with multiple authors into separate cells
- Match local data up to other data sets, for example in matching local subjects against the Library of Congress Subject Headings
- Enhance a data set with data from other sources

"Some common scenarios where you might use OpenRefine include:
- Where you want to know how many times a particular value (name, publisher, subject) appears in a column in your data
- Where you want to know how values are distributed across your whole data set
- Where you have a list of dates which are formatted in different ways, and want to change all the dates in the list to a single common date format." 

#### Installing and Loading Data in OpenRefine

[INSTRUCTIONS FOR INSTALLING OPENREFINE ON RASPBERRY PI]

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_a.png?raw=true" alt="Capture_2"  /></p>

Launch OpenRefine.

Click `Create Project` from the menu on the left-hand side. 

Select the option to `Get data from This Computer.`

Select `CSC_Database_Lab_Player_Birthplaces.csv` file.

Click `Next.`

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_1.png?raw=true" alt="Capture_2"  /></p>

You now have a variety of configuration options before creating your project in OpenRefine.

Select an appropriate character encoding schema.

Select the option to `Parse next 1 line(s) as column headers.` This option treats the first row of your file as a table header.

Check to be sure the `Parse cell text into numbers, dates, ...` option is NOT selected. 

In the `Project name` window, name your project. 

Click `Create Project >>` to begin to work with your data as an OpenRefine project. 

#### OpenRefine's Layout

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_2.png?raw=true" alt="Capture_2"  /></p>

As described in Library Carpentry's ["Introduction to OpenRefine"](https://librarycarpentry.org/lc-open-refine/01-introduction/index.html):

"OpenRefine displays data in a tabular format. Each row will usually represent a ‘record’ in the data, while each column represents a type of information. This is very similar to how you might view data in a spreadsheet or database. As with a spreadsheet, the individual bits of data live in ‘cells’ at the intersection of a row and a column.

"OpenRefine only displays a limited number of rows of data at one time. You can adjust the number choosing between 5, 10 (the default), 25 and 50 at the top left of the table of data. You can navigate through the records by using the previous/next/first/last navigation options at the top right of the table of data."

#### Faceting and Filtering

As described in Library Carpentry's ["Introduction to OpenRefine"](https://librarycarpentry.org/lc-open-refine/01-introduction/index.html):

"Facets are one of the most useful features of OpenRefine and can help in both getting an overview of the data and to improve the consistency of the data.

"A ‘Facet’ groups all the values that appear in a column, and then allows you to filter the data by these values and edit values across many records at the same time.

"The simplest type of Facet is called a ‘Text facet’. This simply groups all the text values in a column and lists each value with the number of records it appears in. The facet information always appears in the left hand panel in the OpenRefine interface.

"To create a Text Facet for a column, click on the drop down menu at the top of the publisher column and choose `Facet -> Text Facet`. The facet will then appear in the left hand panel.

"The facet consists of a list of values used in the data. You can filter the data displayed by clicking on one of these headings.

"You can include multiple values from the facet in a filter at one time by using the `Include` option which appears when you put your mouse over a value in the Facet.

"You can also invert the filter to show all records which do not match your selected values. This option appears at the top of the Facet panel when you select a value from the facet to apply as a filter."

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_3.png?raw=true" alt="Capture_2"  /></p>

Select the drop-down arrow for one of the columns that contains a pattern error.

Select `Facet > Text Facet`. 

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_4.png?raw=true" alt="Capture_2"  /></p>

The facet will now appear on the left-hand side of the page.

Click a line in the facet to select rows with that value.

Use the `Include` option to select multiple values.

Use the `Edit` option to address a pattern error.

Do this for other pattern errors. Consult [the key for ISO 3166-1 alpha-2 two-letter country codes](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table) and [the United States Postal Service's List of Acronyms/Abbreviations](https://about.usps.com/publications/pub32/pub32_acn.htm) as needed. You may also need to consult Wikipedia's [list of baseball team abbreviations](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Baseball/Team_abbreviations) and [Glossary of Baseball Jargon](https://en.wiktionary.org/wiki/Appendix:Glossary_of_baseball_jargon_(N)).

#### Exporting from OpenRefine

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_6.png?raw=true" alt="Capture_2"  /></p>

Click on the `Export` button in the top right-hand corner and select the option to export your OpenRefine project as a CSV file. 

<blockquote>NOTE: OpenRefine will only export the rows of data selected in your current review. Be sure to remove all filters or facets before exporting.</blockquote>

Make sure this file has a unique name and is saved in a location where you can find it again.

Open this new CSV file in a spreadsheet program.

Check to see the pattern errors have been addressed.

Go through this same process for the `CSC_Database_Lab_TeamLocations.csv` file.

<blockquote>Q6: Compare your experience working in OpenRefine to other experiences you have had in a text editor or spreadsheet program. In what ways do you understand, perceive, or relate to the data differently through working in OpenRefine? Describe your experience cleaning this data in OpenRefine.</blockquote>

We are barely scratching the surface of what is possible with data wrangling in OpenRefine. The progam can also standardize capitalization, remove leading and trailing spaces, and address other commonly-found data errors. [Library Carpentry's OpenRefine tutorial](https://librarycarpentry.org/lc-open-refine/) goes in to greater detail about many of these other functions.
 
### Data Wrangling Using A Spreadsheet Program

Spreadsheet software programs are another commonly-used tool for interacting with structured data. Some spreadsheet programs like Microsoft Office's Excel or Apple's Numbers are proprietary software installed on a local computer. Other proprietary spreadsheet programs like Google Sheets run online and are not installed locally.

Open-source spreadsheet programs include OpenOffice's Calc and LibreOffice's Calc. The Raspbian operating system comes equipped with LibreOffice Calc. 

This tutorial works with Microsoft Excel.

<blockquote>Q7: Describe a past experience working with a spreadsheet program. What were you trying to do? How did it go? What was your overall feeling about working with data in a spreadsheet program?</blockquote>

We are going to go through a process in Microsoft Excel where we load our individual CSV files into a multi-sheet workbook file. Then we will use some of Excel's built-in table functionality to clean the data.

#### Loading CSV Files into Excel

Open a blank Microsoft Excel file.

Save the blank file as an Excel workbook.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_7.png?raw=true" alt="Capture_2"  /></p>

Click on Data in the top menu bar.

Under `Get External Data` select the `From Text` option.

In `Sheet1`, select the `CSC_Database_Lab_PlayerBirthplaces.csv` file.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_8.png?raw=true" alt="Capture_2"  /></p>

In the pop-up window, choose the `Delimited` option. Because we are importing a `csv` file, our fields are separated by a comma. In this case, the comma is our delimiter.

Select the `My data has headers.` option.

Click `Next`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_9.png?raw=true" alt="Capture_2"  /></p>

In the next window (Step 2 of 3), select `Comma` as your delimiter. 

Check the `Data preview` window.

Click `Next`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_10.png?raw=true" alt="Capture_2"  /></p>

In Step 3 of 3, select `General` for `Column data format`.

Click `Finish`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_11.png?raw=true" alt="Capture_2"  /></p>

In the `Import Data` window, you can tell the program where to import the new data.

Click `OK`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_12.png?raw=true" alt="Capture_2"  /></p>

You should now see the CSV data in the Excel workbook.

Rename `Sheet1` so you know what data is included in that sheet.

Go through the same process for the `CSC_Database_Lab_TeamLocations.csv` file.

Save the updated workbook.

#### Creating a Table

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_13.png?raw=true" alt="Capture_2"  /></p>

Now we need to convert the sheets in our workbook to tables so we can search, sort, and filter.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_14.png?raw=true" alt="Capture_2"  /></p>

Select all the cells that contain data.

<blockquote>One shortcut is to select cell A1, then press <Control> <Shift> and the right arrow key to select all columns with data. Then <Control> <Shift> and the down arrow key to select all rows with data.</blockquote>
 
<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_15.png?raw=true" alt="Capture_2"  /></p>
 
Click `Insert` in the top menu bar.
 
Select `Table` under `Insert` to insert a table.
 
<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_16.png?raw=true" alt="Capture_2"  /></p>
 
In the pop-up window, we have already selected the cells with data. `=$A$1:$I$3616` is an expression that selects selects column A through column I and row 1 through row 3616.
 
Select the `My table has headers` option.
 
Click `OK`.
 
<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_17.png?raw=true" alt="Capture_2"  /></p>
 
We have now converted the data in our sheet to a table.

#### Editing Data
 
<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_18.png?raw=true" alt="Capture_2"  /></p>
 
<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_19.png?raw=true" alt="Capture_2"  /></p>
 
Click the drop-down arrow next to a column header to see additional options for that field.
 
Use these sort, search, and filter options to address data pattern errors.
 
<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_20.png?raw=true" alt="Capture_2"  /></p>

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_21.png?raw=true" alt="Capture_2"  /></p>
 
Alternatively, use the `Replace` option under `Find & Select` (in the `Home` menu section) to address pattern errors.
 
Consult [the key for ISO 3166-1 alpha-2 two-letter country codes](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table) and [the United States Postal Service's List of Acronyms/Abbreviations](https://about.usps.com/publications/pub32/pub32_acn.htm) as needed. You may also need to consult Wikipedia's [list of baseball team abbreviations](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Baseball/Team_abbreviations) and [Glossary of Baseball Jargon](https://en.wiktionary.org/wiki/Appendix:Glossary_of_baseball_jargon_(N)).

<blockquote>To change all cells in a column, click the cell in the first non-header row. Press <Control> and the down arrow key to select all cells with data in that column. Press <Control> and <D> to copy the first value into the other selected cells. Alternatively, move your cursor over the bottom right-hand corner of the cell in the first non-header row. Click and drag the plus icon that appears down through the column to copy the value in the first cell into the subsequent cells.</blockquote>

Go through this same process for the second sheet with data from the `Team_Locations` CSV file. 

#### Options for Saving Your Work

We will save the combined CSV files as an Excel workbook to use later in this lab.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_22.png?raw=true" alt="Capture_2"  /></p>

Click on the `File` menu section to show additional export options.

Under `Export` you can see some of the other options for exporting the data in Excel.

<blockquote>Note: While CSV files are best for digital preservation and interoperability, they only support a single sheet of data.</blockquote>

<blockquote>Q8: Compare your experience working in Excel to your experience working in OpenRefine. In what ways do you understand, perceive, or relate to the data differently through working in Excel? Describe your experience cleaning this data in Excel.</blockquote>

We are barely scratching the surface of what is possible with data wrangling in Excel (or other spreadsheet program). The progam can also standardize capitalization, remove leading and trailing spaces, and address other commonly-found data errors. [Library Carpentry's Tidy Data for Librarians tutorial](https://librarycarpentry.org/lc-spreadsheets/) goes in to greater detail about many of these other functions.

# Workflows for Data Entry

<blockquote>Q9: For the baseball datasets we have been working with in this lab, what do you think may have contributed to or caused the pattern errors we needed to address? How could these pattern errors be addressed in the data entry process?</blockquote>

According to Library Carpentry's ["Tidy data for librarians" tutorial](https://librarycarpentry.org/lc-spreadsheets/04-quality-control/index.html), "Quality assurance stops bad data from ever being entered by checking to see if values are valid during data entry. For example, if research is being conducted at sites A, B, and C, then the value V (which is right next to B on the keyboard) should never be entered. Likewise if one of the kinds of data being collected is a count, only integers greater than or equal to zero should be allowed."

Building in quality assurance constraints into a data entry workflow can help minimize pattern errors that require later cleaning.

## Survey Versus Spreadsheet

One option is use a survey with some pre-defined choices or drop-down options.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_23.png?raw=true" alt="Capture_2"  /></p>

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_24.png?raw=true" alt="Capture_2"  /></p>

Log into your Grinnell OFfice 365 account.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_25.png?raw=true" alt="Capture_2"  /></p>

Select the Microsoft Forms app.

Click on the `New Form` option.

Explore the different question types. 

<blockquote>Q10: Describe how you would go about building a survey form or template for the <code>`CSC_Database_Lab_PlayerBirthplaces.csv`</code> file. You DO NOT need to actually create or submit a survey form. Describe what types of questions and pre-defined question or field options could you use to more effectively generate the data in this file.</blockquote>

## Data Validation

You can also use some of the built-in data validation options in Excel.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_26.png?raw=true" alt="Capture_2"  /></p>

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_27.png?raw=true" alt="Capture_2"  /></p>

Under `Data`, select the `Data Validation` option.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_28.png?raw=true" alt="Capture_2"  /></p>

In the pop-up window, you can limit the  types of values that will be valid in a particular field. 

You can also define a list of options or values which will show up as drop-down options for cells in that field.

Visit Microsoft Office's ["Apply data validation to cells"](https://support.office.com/en-us/article/apply-data-validation-to-cells-29fecbcc-d1b9-42c1-9d76-eff3ce5f7249) article to learn more about data validation options.

<blockquote>Q11: Describe how you would go about using data validation to build a template for the <code>`CSC_Database_Lab_PlayerBirthplaces.csv`</code> file. You DO NOT need to actually create or submit a template. Describe what data validation options and pre-defined field options could you use to more effectively generate the data in this file.</blockquote>

# Understanding Relational Databases

## Why A Database

The data we've been using in this tutorial includes a table with information about baseball player birthplaces and birth dates. It also includes a second table with information about where baseball teams are located.

Open the `CSC_Datbase_Lab_Transactions.csv` file in a spreadsheet program.

<blockquote>Q12: What types of fields do you see in the Transactions table? What kinds of connections could you see across these three tables?</blockquote>

Let's say we wanted to see how many baseball players born in Puerto Rico played for teams located in the state of Iowa.

The `Player_Birthplaces` table includes information about where players were born. The `Team_Locations` table includes information about where teams are located. The `Transactions` table tells us which players played for which teams.

But the `Transactions` table on its own doesn't include the information about player birthplace and team location we need to answer the question of how many baseball players born in Puerto Rico played for teams located in the state of Iowa.

We could add that location information to the `Transactions` table, but we would end up with significant redundant and duplicate information.

Behold the magic of relational databases.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_29.png?raw=true" alt="Capture_2"  /></p>

Image from Library Carpentry's [Introduction to SQL tutorial](https://librarycarpentry.org/lc-sql/01-introduction/index.html).

As described in Library Carpentry's [Introduction to SQL tutorial](https://librarycarpentry.org/lc-sql/01-introduction/index.html), "Relational databases consist of one or more tables of data. These tables have fields (columns) and records (rows). Every field has a data type. Every value in the same field of each record has the same type. These tables can be linked to each other when a field in one table can be matched to a field in another table."

Linking our three individual data tables in a relational database will enable us to answer the question about Puerto Rican players in Iowa without having to change the underlying data structure.

## What is an ERD?

An entity relationship diagram (sometimes called an ER Diagram or ERD) is a visual representation of tabular data structures that are linked as part of a database.

Building an ERD requires understanding the underlying structure of your data, as well as how you want to create links across individual tables.

ERDs have a specific vocabulary for describing database structure.

In 1997, computer scientist Peter Chen outlined a natural language framework for building ER diagrams.
<table>
 <tr>
  <th>English grammar structure</th>
  <th>ER structure</th>
 </tr>
 <tr>
  <td>Common noun</td>
  <td>Entity type</td>
 </tr>
 <tr>
  <td>Proper noun</td>
  <td>Entity</td>
 </tr>
 <tr>
  <td>Transitive verb</td>
  <td>Relationship type</td>
 </tr>
 <tr>
  <td>Intransitive verb</td>
  <td>Attribute type</td>
 </tr>
 <tr>
  <td>Adjective</td>
  <td>Attribute for entity</td>
 </tr>
 <tr>
  <td>Adverb</td>
  <td>Attribute for relationship</td>
 </tr>
</table>

<blockquote>Peter Pin-Shan Chen, "English, Chinese and ER Diagrams," Data & Knowledge Engineering 23 (1997), 5-16. https://doi.org/10.1016/S0169-023X(97)00017-7</blockquote>

### Entities

"A definable thing—-such as a person, object, concept or event-—that can have data stored about it. Think of entities as nouns. Examples: a customer, student, car or product." (["The components and features of an ER diagram,"](https://www.lucidchart.com/pages/er-diagrams#section_3), LucidChart)

<blockquote>Q13: What entities are in the Player_Birthplaces, Team_Locations, and Transactions tables? List the entitites by table and include some explanation of your thought process. If you're getting stuck, try describing the data included in each table using a sentence. Where are the nouns in each sentence?</blockquote>

Entities are represented as rectangles in an ER Diagram.

### Attributes

"A property or characteristic of an entity." (["The components and features of an ER diagram,"](https://www.lucidchart.com/pages/er-diagrams#section_3), LucidChart)

<blockquote>Q14: What attributes are in the Player_Birthplaces, Team_Locations, and Transactions tables? What entities do these attributes describe? List the attributes by entity and table and include some explanation of your thought process. If you're getting stuck, go back to your list of entities from Q13. What non-entity information in each table might describe an entity?</blockquote>

Attributes are represented as ovals in an ER Diagram.

### Relationships

"How entities act upon each other or are associated with each other. Think of relationships as verbs. For example, the named student might register for a course. The two entities would be the student and the course, and the relationship depicted is the act of enrolling." (["The components and features of an ER diagram,"](https://www.lucidchart.com/pages/er-diagrams#section_3), LucidChart)

<blockquote>Q15: What relationships do you see within and across entities in the Player_Birthplaces, Team_Locations, and Transactions tables? What entities do these relationships connect? Include some explanation of your thought process. If you're getting stuck, go back to your list of entities from Q13. How do these entities connect?</blockquote>

Relationships are represented as diamonds with lines that connect entity rectangles.

### Cardinality

"Defines the numerical attributes of the relationship between two entities or entity sets." (["The components and features of an ER diagram,"](https://www.lucidchart.com/pages/er-diagrams#section_3), LucidChart)

Types of cardinality:

- One-to-one relationships
  * For example each Grinnell student has a unique ID number.
- One-to-many relationships
  * A single Grinnell student registers for multiple courses.
- Many-to-many relationships
  * Multiple Grinnell students work with multiple faculty members, and multiple faculty members work with multiple students.

The three main cardinal relationships are one-to-one, one-to-many, and many-many. A one-to-one example would be one student associated with one mailing address. A one-to-many example (or many-to-one, depending on the relationship direction): One student registers for multiple courses, but all those courses have a single line back to that one student. Many-to-many example: Students as a group are associated with multiple faculty members, and faculty members in turn are associated with multiple students.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_30.png?raw=true" alt="Capture_2"  /></p>

Cardinality is indicated through symbols added to the connecting lines of a relationship.

<blockquote>Q16: Include the cardinality for the relationships you identified in Q15. Include some explanation of your thought process.</blockquote>

Visit Lucidchart's ["What is an Entity Relationship Diagram (ERD)?"](https://www.lucidchart.com/pages/er-diagrams#top) to learn more about the history, components, and limits of ER Diagrams.

## Building an ERD

<blockquote>Q17: Work with a colleague to build an ERD for the Player_Birthplaces, Team_Locations, and Transactions tables. Include your diagram as well as an explanation of your process.</blockquote>

You can draw these by hand, use a drawing tool, or use a free online ERD tool like [ERDPlus](https://erdplus.com/) or [LucidChart](https://www.lucidchart.com).

## Where Are My Keys?

At this point you may be wondering why our data tables have various `id` columns. 

The ERD we built in Q17 outlines the conceptual relationships across our data structures.

But relationship database programs require matching data fields and unique identifiers to be able to manifest those conceptual relationships.

These unique identifiers and matching fields are called keys.

"The primary key is defined as a column (or set of columns) where each value is unique and identifies a single row of the table." (["Primary Key-Foreign Key Relationships,"](https://docs.oracle.com/cd/E12100_01/books/admintool/admintool_DataModeling4.html), Oracle)

"A foreign key is a column or a set of columns in one table that references the primary key columns in another table." (["Primary Key-Foreign Key Relationships,"](https://docs.oracle.com/cd/E12100_01/books/admintool/admintool_DataModeling4.html), Oracle)

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_31.png?raw=true" alt="Capture_2"  /></p>

Image from ["Foreign and Primary Key Differences (Visually Explained),"](https://www.essentialsql.com/what-is-the-difference-between-a-primary-key-and-a-foreign-key/) EssentialSQL.

<blockquote>Q18: What fields in our tables are functioning as keys? Which ones are primary keys and which ones are foreign keys? Include some explanation of your thought process.</blockquote>

## Relational Schema

ER Diagrams represent the conceptual relationships in a relational database structure.

But, we might also want to represent our database structure based on tables, primary keys, and foreign keys.

An image from StackExchange's ["ER vs database schema diagrams" page](https://dba.stackexchange.com/questions/119380/er-vs-database-schema-diagrams) that illustrates the difference:

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_c.png?raw=true" alt="Capture_2"  /></p>

<blockquote>Q19: Work with a colleague to build a relational schema for a relational database that includes the Player_Birthplaces, Team_Locations, and Transactions tables. Include your diagram as well as an explanation of your process.</blockquote>

Visit StackOverflow's ["What is the different between ER Diagram and Database Schema?"](https://stackoverflow.com/questions/17641134/what-is-different-between-er-diagram-and-database-schema) page to learn more.

# SQL Query Syntax

As described in Library Carpentry's [Introduction to SQL tutorial](https://librarycarpentry.org/lc-sql/01-introduction/index.html), "Structured Query Language, or SQL (sometimes pronounced 'sequel'), is a powerful language used to interrogate and manipulate relational databases. It is not a general programming language that you can use to write an entire program."

When working in a relational database, we an use SQL to write queries.

As described in Library Carpentry's [Introduction to SQL tutorial](https://librarycarpentry.org/lc-sql/01-introduction/index.html), "a query is a question or request for data. For example, “How many journals does our library subscribe to?” When we query a database, we can ask the same question using a common language called Structured Query Language or SQL in what is called a statement. Some of the most useful queries - the ones we are introducing in this first section - are used to return results from a table that match specific criteria."

This section of the lab will introduce some basic elements of SQL syntax. 

## Selecting and Sorting
```SQL
SELECT [field]
FROM [table];
```

The `SELECT` query selects a specific field (column) from a specific table.

The semicolon `;` is required at the end of every SQL query.

Adding multiple columns after `SELECT` will return data from multiple columns.

```SQL
SELECT [field_1], [field_2], [field_3]
FROM [table];
```

<blockquote>Q20: How would you write an SQL query to select the list of player ids and birthplace countries from the Player_Birthplaces table? What data does this query return?</blockquote>

We might want to write a query to return all the unique values in a particular field.

For example, selecting the entire `country` field in the `Player_Birthplaces` table would return many duplicate values.

```SQL
SELECT DISTINCT [field]
FROM [table];
```

`SELECT DISTINCT` returns a list of unique values.

<blockquote>Q21: How would you write an SQL query to return the unique list of player birthplace countries from the Player_Birthplaces table? What data does this query return?</blockquote>

We might also want to sort the results returned by a query.

```SQL
SELECT *
FROM [table]
ORDER BY [field] ASC;
```

The `*` wildcard operator selects all the fields in a specific table.

`ORDER BY` specifies a field to use in sorting the query results.

`ASC` returns ascending results. `DESC` would return descending results.

<blockquote>Q22: How would you write an SQL query to return the unique list of team names from the Team_Locations table, sorted in reverse alphabetical order? What data does this query return?</blockquote>

```SQL
SELECT *
FROM [table]
ORDER BY [field_1] ASC, [field_2] DESC;
```

We can also sort on multiple fields.

In the query above, the `ORDER BY` statement sorts `[field_1]` first (ascending) and then sorts `[field_2]` (descending).

<blockquote>Q23: How would you write an SQL query to return the data from the Player_Birthplaces table, sorted in chronological order by birth year and reverse alphabetical order by country? What data does this query return?</blockquote>

## Filtering

Sometimes we may only want to return values that fall within a specific range or based on a particular set of conditions.

```SQL
SELECT *
FROM [Player_Birthplaces]
WHERE country='DO';
```

This query returns all columns from the `Player_Birthplaces` table where data in the `country` field is equal to `DO`.

The data returned by this query includes all the records for players born in the Dominican Republic.

We can also use operators to specify a range for the `WHERE` clause.

```SQL
SELECT *
FROM [Player_Birthplaces]
WHERE dob>1996;
```

This query returns all columns from `Player_Birthplaces` where data in the `dob` field is greater than `1996`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_42.png?raw=true" alt="Capture_2"  /></p>

List of operators that can be used in a `WHERE` clause (from W3Schools ["SQL Where Clause" tutorial](https://www.w3schools.com/sql/sql_where.asp)).

SQL query syntax requires single quotes around text values. Numeric fields do not need single quotes.

<blockquote>Q24: How would you write an SQL query to return the data from the Team_Locations table for teams located in states that start with the letter M? What data does this query return?</blockquote>

Learn more about operators at Beginner SQL's [Tutorial on SQL Comparison Keywords](https://beginner-sql-tutorial.com/sql-like-in-operators.htm).

## Aggregating and Calculating

We won't cover these functions in this lab, but SQL syntax includes functions that can group query results by particular fields and perform basic arithmetic functions on values in a database.

To learn more, visit Library Carpentry's ["Aggregating & calculating values" tutorial](https://librarycarpentry.org/lc-sql/04-aggregating-calculating/index.html) and W3Schools' ["SQL Tutorial"](https://www.w3schools.com/sql/default.asp) pages for specific aggregating and calculating functions.

## Joins

The process of building a relational database in which you identify primary and foreign keys and build relationships across  tables does not change the underlying data structure.

We can accomplish this in SQL using `JOIN` functions.

According to W3Schools'["SQL Joins" page](https://www.w3schools.com/sql/sql_join.asp), "A JOIN clause is used to combine rows from two or more tables, based on a related column between them."

```SQL
SELECT *
FROM [transactions]
JOIN [player_birthplaces]
ON transactions.player_ids = player_birthplaces.player_ids;
```

This query uses the `player_id` field to join the `Transactions` and `Player_Birthplaces` tables.

The query returns all columns in the joined query.

<blockquote>Q25: How would you write an SQL query that joins the Transactions and Team_Locations tables and returns all columns?  What data does this query return?</blockquote>

[IMAGE 43]

There are four main types of `JOIN` functions.
- `(INNER) Join` returns matching records in both tables
- `LEFT (OUTER) JOIN` returns all records from the left table and only matching records from the right table
- `RIGHT (OUTER) JOIN` returns all records from the right table and only matching records from the left table
- `FULL (OUTER) JOIN` returns all matching records from both the left and right tables

Learn more about `JOIN` functions at W3Schools' ["SQL Joins" page](https://www.w3schools.com/sql/sql_join.asp).

<blockquote>Q26: Where would you start in writing an SQL query that answers our question about the number of players born in Puerto Rico playing for teams located in Iowa?</blockquote>

<blockquote>Q27: How would you describe the affordances of relational databases to someone who hasn't been through this lab?</blockquote>

<blockquote>Q28: What questions or thoughts do you have about building and interacting with relational databases?</blockquote>

# Optional: Relational Databases in Excel Using PivotTables

We can also work within Microsoft Excel to connect our three tables so we can utilize some of the features and functionality of a relational database from within Excel.

Open the Excel workbook you created earlier in this lab.

Load the `Transactions` file in a new sheet. 

Now you should have three sheets in the same Excel workbook.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_33.png?raw=true" alt="Capture_2"  /></p>

Under the `Data` menu area, select the `Relationships` option.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_34.png?raw=true" alt="Capture_2"  /></p>

In the `Manage Relationships` window, select `New`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_35.png?raw=true" alt="Capture_2"  /></p>

Use the relational schema you built in Q19 to create relationships across the three tables.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_36.png?raw=true" alt="Capture_2"  /></p>

Once you've added relationships, close the `Manage Relationships` window.

Save your workbook.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_37.png?raw=true" alt="Capture_2"  /></p>

Select the `Manage Data Model` option under `Data`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_38.png?raw=true" alt="Capture_2"  /></p>

You can select the `Diagram View` option to see the relational schema you have built in Excel.

Close the Power Pivot window.

Create a new blank sheet.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_39.png?raw=true" alt="Capture_2"  /></p>

Select `PivotTable` under `Insert`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_40.png?raw=true" alt="Capture_2"  /></p>

In the `Create PivotTable` window, select the option to `Use this workbook's Data Model` and select the `Existing Worksheet` for the PivotTable location.

Click `OK`.

<p align="center"><img class=" size-full wp-image-55 aligncenter" src="https://github.com/kwaldenphd/databases/blob/master/screenshots/Image_41.png?raw=true" alt="Capture_2"  /></p>

You are now in the PivotTable interface where you can select data fields across tables using the relationships and data model.

<blockquote>From within the PivotTable, how could you select data fields to answer our question about the number of baseball players born in Puerto Rico who played for teams in Iowa? Describe your process and include a screenshot of the resulting PivotTable.</blockquote>

# Additional Resources

- [W3 Schools "Syntax"](https://www.w3schools.com/sql/default.asp)
- [W3 Schools "SQL Syntax"](https://www.w3schools.com/sql/sql_syntax.asp)
- [Library Carpentry "Tidy Data for Librarians"](https://librarycarpentry.org/lc-spreadsheets/)
- [Library Carpentry "Database Design"](https://librarycarpentry.org/lc-sql/08-database-design/index.html)
- [Library Carpentry "Open Refine"](https://librarycarpentry.org/lc-open-refine/)
- [Library Carpentry "SQL"](https://librarycarpentry.org/lc-sql/)
- [Lucid Chart "Database Design"](https://www.lucidchart.com/pages/database-diagram/database-design)
- [Lucid Chart "ER Diagrams"](https://www.lucidchart.com/pages/er-diagrams)

# Lab Notebook Questions

Q1: What questions do you have about these principles? Which ones are unclear are confusing?
   
Q2: What fields are represented in these datasets? Describe the data fields in your own words. Use the language of string, double, and integer to describe the data fields.
    
Q3: Provide 3 distinct examples from the sample datasets that do not conform to tidy data principles. Include the example as well as an explanation.

Q4: Discuss with a colleague what issues you are seeing in these datasetes. What commonalities or patterns are you seeing?

Q5: How would you address these pattern errors so the data conforms to tidy data principles? Describe what steps you would take to address at least 3 pattern errors. For each error, include the following elements: an example of the error, an explanation of your method to address the error, and the same example as tidy data.
    
Q6: Compare your experience working in OpenRefine to other experiences you have had in a text editor or spreadsheet program. In what ways do you understand, perceive, or relate to the data differently through working in OpenRefine? Describe your experience cleaning this data in OpenRefine.

Q7: Describe a past experience working with a spreadsheet program. What were you trying to do? How did it go? What was your overall feeling about working with data in a spreadsheet program?

Q8: Compare your experience working in Excel to your experience working in OpenRefine. In what ways do you understand, perceive, or relate to the data differently through working in Excel? Describe your experience cleaning this data in Excel.

Q9: For the baseball datasets we have been working with in this lab, what do you think may have contributed to or caused the pattern errors we needed to address? How could these pattern errors be addressed in the data entry process?

Q10: Describe how you would go about building a survey form or template for the `CSC_Database_Lab_PlayerBirthplaces.csv` file. You DO NOT need to actually create or submit a survey form. Describe what types of questions and pre-defined question or field options could you use to more effectively generate the data in this file.

Q11: Describe how you would go about using data validation to build a template for the `CSC_Database_Lab_PlayerBirthplaces.csv` file. You DO NOT need to actually create or submit a template. Describe what data validation options and pre-defined field options could you use to more effectively generate the data in this file.

Q12: What types of fields do you see in the Transactions table? What kinds of connections could you see across these three tables?

Q13: What entities are in the Player_Birthplaces, Team_Locations, and Transactions tables? List the entitites by table and include some explanation of your thought process. If you're getting stuck, try describing the data included in each table using a sentence. Where are the nouns in each sentence?

Q14: What attributes are in the Player_Birthplaces, Team_Locations, and Transactions tables? What entities do these attributes describe? List the attributes by entity and table and include some explanation of your thought process. If you're getting stuck, go back to your list of entities from Q13. What non-entity information in each table might describe an entity?

Q15: What relationships do you see within and across entities in the Player_Birthplaces, Team_Locations, and Transactions tables? What entities do these relationships connect? Include some explanation of your thought process. If you're getting stuck, go back to your list of entities from Q13. How do these entities connect?

Q16: Include the cardinality for the relationships you identified in Q15. Include some explanation of your thought process.

Q17: Work with a colleague to build an ERD for the Player_Birthplaces, Team_Locations, and Transactions tables. Include your diagram as well as an explanation of your process.

Q18: What fields in our tables are functioning as keys? Which ones are primary keys and which ones are foreign keys? Include some explanation of your thought process.

Q19: Work with a colleague to build a relational schema for a relational database that includes the Player_Birthplaces, Team_Locations, and Transactions tables. Include your diagram as well as an explanation of your process.

Q20: How would you write an SQL query to select the list of player ids and birthplace countries from the Player_Birthplaces table? What data does this query return?

Q21: How would you write an SQL query to return the unique list of player birthplace countries from the Player_Birthplaces table? What data does this query return?
 
Q22: How would you write an SQL query to return the unique list of team names from the Team_Locations table, sorted in reverse alphabetical order? What data does this query return?
  
Q23: How would you write an SQL query to return the data from the Player_Birthplaces table, sorted in chronological order by birth year and reverse alphabetical order by country? What data does this query return?
   
Q24: How would you write an SQL query to return the data from the Team_Locations table for teams located in states that start with the letter M? What data does this query return?
   
Q25: How would you write an SQL query that joins the Transactions and Team_Locations tables and returns all columns? What data does this query return?
    
Q26: Where would you start in writing an SQL query that answers our question about the number of players born in Puerto Rico playing for teams located in Iowa?

Q27: How would you describe the affordances of relational databases to someone who hasn't been through this lab?

Q28: What questions or thoughts do you have about building and interacting with relational databases?
