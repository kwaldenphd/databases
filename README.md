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
  * [Dealing With Messy Data](#dealing-with-messy-data)
    * [Identify Patterns and Brainstorm Solutions](#identify-patterns-and-brainstorm-solutions)
    * [Data Wrangling Using OpenRefine](#data-wrangling-using-openrefine)
    * [Data Wrangling Using a Spreadsheet Program](#data-wrangling-using-a-spreadsheet-program)
- [Workflows for Data Entry](#workflows-for-data-entry)
  * [Survey Versus Spreadsheet](#survey-versus-spreadsheet)
  * [Data Validation](#data-validation)
  * [Developing Meaningful Data Schema](#developing-meaningful-data-schema)
- [Data Structure Fundamentals](#data-structure-fundamentals)
  * [What is an ERD?](#what-is-an-erd)
    * [Entities](#entities)
    * [Attributes](#attributes)
    * [Relationships](#relationships)
  * [Developing a Data Structure](#developing-a-data-structure)
- [Building a Database](#building-a-database)
  * [Types of Databases]
    * [Flat File](#flat-file)
    * [Relational](#relational)
    * [Object Oriented](#object-oriented)
  * [Where Are My Keys?](#where-are-my-keys)
  * [Joins](#joins)
    * [Inner](#inner)
    * [Outer](#outer)
      * [Left Outer](#left-outer)
      * [Right Outer](#right-outer)
      * [Full Outer](#full-outer)
    * [Cross](#cross)
    * [Self-Join](#self-join)
- [SQL Query Syntax](#sql-query-syntax)
  * [Selecting and Sorting](#selecting-and-sorting)
  * [Filtering](#filtering)
  * [Aggregating and Calculating](#aggregating-and-calculating)
  * [Key Terms](#key-terms)
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

[IMAGE_a]

Launch OpenRefine.

Click `Create Project` from the menu on the left-hand side. 

Select the option to `Get data from This Computer.`

Select `CSC_Database_Lab_Player_Birthplaces.csv` file.

Click `Next.`

[IMAGE 1]

You now have a variety of configuration options before creating your project in OpenRefine.

Select an appropriate character encoding schema.

Select the option to `Parse next 1 line(s) as column headers.` This option treats the first row of your file as a table header.

Check to be sure the `Parse cell text into numbers, dates, ...` option is NOT selected. 

In the `Project name` window, name your project. 

Click `Create Project >>` to begin to work with your data as an OpenRefine project. 

#### OpenRefine's Layout

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

[IMAGE]


Select the drop-down arrow for one of the columns that contains a pattern error.

Select `Facet > Text Facet`. 

The facet will now appear on the left-hand side of the page.

Click a line in the facet to select rows with that value.

Use the `Include` option to select multiple values.

<blockquote>Q6: 
 
### Data Wrangling Using A Spreadsheet Program

# Workflows for Data Entry

## Survey Versus Spreadsheet

## Data Validation

## Developing Meaningful Data Schema

# Data Structure Fundamentals

## What is an ERD?

### Entities

### Attributes

### Relationships

## Developing a Data Structure

# Building a Database

## Types of Databases

### Flat File

### Relational

### Object Oriented

## Where Are My Keys?

# Joins

## Inner

## Outer

### Left Outer

### Right Outer

### Full Outer

## Cross

## Self-Join

# SQL Query Syntax

## Selecting and Sorting

## Filtering

## Aggregating and Calculating

## Key Terms

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
