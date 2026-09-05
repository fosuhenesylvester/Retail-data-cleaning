# Excel Data Cleaning & Validation: From 38/100 to 88/100

## Project Overview

This repository documents my data-cleaning journey using a deliberately messy retail transaction dataset containing more than 3,000 records.

The purpose of this project was not simply to make a spreadsheet "look clean."

The objective was to approach the dataset as a real data analyst would:

* Inspect the raw data before changing it
* Identify data-quality problems
* Standardize inconsistent values
* Validate numerical fields
* Check business rules
* Identify duplicate and suspicious records
* Preserve evidence instead of silently deleting problems
* Create an audit trail
* Verify that the cleaning process did not introduce new errors
* Produce a dataset that could be used more confidently for analysis and reporting

This project became particularly important to me because my first attempt did not go well.

---

## The First Attempt

My first attempt at the dataset resulted in a score of:

**38/100**

The review exposed several weaknesses in my approach to data cleaning.

Some of the most important mistakes included:

* Deleting records instead of identifying and flagging them
* Altering negative values instead of investigating why they were negative
* Making transformations without sufficiently validating the results
* Having formula errors that I did not detect before considering the work complete
* Treating a formula that successfully returned a result as proof that the underlying data was correct
* Not maintaining a sufficiently strong audit trail for some decisions

The biggest lesson was that data cleaning is not simply about knowing Excel functions.

It is about making defensible decisions about data.

---

## What Changed

Instead of abandoning the project, I went back to the fundamentals.

I worked through structured and progressively more difficult data-cleaning exercises, focusing specifically on the areas where my first attempt had failed.

The principles I focused on were:

> **Never fabricate a value.**

> **Never silently delete a questionable record.**

> **Flag first. Investigate second. Delete only when the evidence supports deletion.**

> **Never trust a formula simply because Excel returned a result. Verify it independently.**

> **Separate cleaning from validation.**

These principles changed the way I approached the same dataset.

---

## The Second Attempt

After rebuilding my process, I returned to the exact dataset that produced my original 38/100 score.

My second attempt received:

**88/100**

The improvement was not the result of simply learning more Excel formulas.

The major improvement was in the way I reasoned about the data.

The second version included a much more structured cleaning and validation process, including:

* Text standardization
* Whitespace and character cleanup
* Category standardization
* Numeric conversion and validation
* Quantity validation
* Unit-price validation
* Revenue calculations
* Revenue consistency checks
* Date cleaning and validation
* Order-reference reconstruction and validation
* Duplicate detection
* Missing-value identification
* Lookup-based validation
* Business-rule checks
* Tracking of records before and after cleaning
* Helper columns for transparency
* An audit-oriented workflow

The final working dataset contained **3,148 records** after the cleaning process.

---

# Data Quality Problems Investigated

The raw dataset contained a variety of issues deliberately introduced to simulate the type of problems that can occur in exported business data.

Examples included:

### 1. Inconsistent Text

Examples of issues included:

* Different capitalization
* Leading/trailing spaces
* Inconsistent category names
* Inconsistent region names
* Formatting variations

These were handled using Excel cleaning and standardization techniques.

Examples of functions used:

```excel
TRIM()
CLEAN()
UPPER()
PROPER()
SUBSTITUTE()
```

---

### 2. Numeric Data Stored as Text

Some numerical fields required conversion before they could be reliably analyzed.

Fields such as:

* Quantity
* Unit Price
* Revenue

were checked and converted where appropriate.

Example approach:

```excel
=VALUE(TRIM([@Quantity]))
```

Validation columns were then used to identify values that could not be safely converted.

---

### 3. Revenue Validation

Revenue was not treated as automatically correct.

The business rule was:

```text
Revenue = Quantity × Unit Price
```

The calculated revenue was compared against the reported revenue so that discrepancies could be identified rather than silently overwritten.

This distinction was one of the important lessons from my first attempt.

---

### 4. Date Validation

The dataset contained inconsistent date representations and invalid dates.

Dates were therefore treated as both:

**A cleaning problem**

and

**A validation problem.**

A date appearing in a recognizable format does not necessarily mean that it is a valid business date.

The dataset was expected to contain transactions within the defined business period.

---

### 5. Duplicate Records

Duplicates were handled more carefully in the second attempt.

A key lesson was that:

**Duplicate Order IDs do not automatically mean duplicate records.**

There is an important distinction between:

* Exact duplicate rows
* Repeated business keys
* Near-duplicate records
* Potentially suspicious records

A record should not be deleted simply because one field is duplicated.

The raw dataset was preserved so that decisions could be traced back to the original evidence.

---

### 6. Missing Values

Missing values were identified and classified rather than automatically replaced.

The approach considered whether a field was:

* Required
* Optional
* Missing
* Invalid
* Available from another reliable source
* Something that should be reviewed rather than guessed

This helped avoid creating false information during the cleaning process.

---

### 7. Business-Rule Validation

The dataset included defined business rules covering areas such as:

* Valid quantities
* Valid unit prices
* Revenue consistency
* Approved regions
* Approved product categories
* Approved customer types
* Approved sales channels
* Valid order dates
* Expected OrderRef structure
* Required fields

The purpose was to move beyond:

> "Does the cell look okay?"

and instead ask:

> "Does this record satisfy the business rules?"

---

# Excel Techniques Used

This project involved a wide range of Excel techniques, including:

* Excel Tables
* Sorting and filtering
* Advanced filtering
* Helper columns
* Text cleaning
* Text standardization
* Logical functions
* Conditional aggregation
* Lookup functions
* Duplicate detection
* Data validation
* Error handling
* Date manipulation
* Numeric conversion
* Business-rule validation
* Record tracking
* Audit-oriented checks

Functions and techniques used included:

```text
IF
IFS
AND
OR
COUNTIF
COUNTIFS
SUMIF
SUMIFS
AVERAGEIF
AVERAGEIFS
VLOOKUP
INDEX
MATCH
LOOKUP
TRIM
CLEAN
UPPER
PROPER
LEFT
RIGHT
MID
FIND
SUBSTITUTE
VALUE
DATEVALUE
TEXTJOIN
IFERROR
```

The goal was not to use as many functions as possible.

The goal was to use the appropriate technique for the problem and then verify the result.

---

# Repository Structure

The repository contains the project files used to document the process.

## Raw Dataset

The original dataset before cleaning.

This file is retained as the source of truth so that the cleaning process can be compared against the original data.

## First Attempt

My original attempt at cleaning and validating the dataset.

This version demonstrates the mistakes that resulted in the **38/100** score.

It is intentionally included rather than hidden.

The purpose is to make the learning process transparent.

## Second Attempt

The revised version after rebuilding my data-cleaning process.

This version demonstrates the improved approach to:

* Cleaning
* Validation
* Tracking
* Duplicate handling
* Business rules
* Auditability

## Supporting Files

Additional files may include:

* Data dictionaries
* Business rules
* Tracking sheets
* Notes
* Documentation

---

# Before vs After

| Area                 | First Attempt                    | Second Attempt                         |
| -------------------- | -------------------------------- | -------------------------------------- |
| Score                | 38/100                           | 88/100                                 |
| Data cleaning        | Basic/inconsistent               | More structured                        |
| Duplicate handling   | Records were deleted too quickly | Duplicates investigated and classified |
| Negative values      | Some were altered incorrectly    | Preserved and flagged                  |
| Formula verification | Insufficient                     | More systematic checking               |
| Business rules       | Incompletely applied             | More explicitly incorporated           |
| Audit trail          | Limited                          | Stronger before/after tracking         |
| Validation mindset   | "Formula works"                  | "Result must be verified"              |

---

# What I Learned

The biggest lesson from this project was that **data cleaning is not just an Excel skill.**

Knowing how to use `TRIM`, `IF`, `VLOOKUP`, `COUNTIFS`, or other functions is useful.

But knowing **when to use them, what their output means, and whether that output should be trusted** is much more important.

My first attempt taught me that:

**A technically correct formula can still produce a business-wrong result.**

For example, if a value is negative, removing the minus sign may produce a positive number without actually solving the underlying problem.

Similarly, if a record looks like a duplicate, deleting it without investigating whether it is genuinely duplicated can destroy useful information.

The second attempt was therefore less about "fixing cells" and more about developing a repeatable analytical process.

---

# Key Principles I Now Follow

### 1. Preserve the raw data

Never start by destroying the original evidence.

### 2. Profile before cleaning

Understand the dataset before making transformations.

### 3. Clean and validate separately

Cleaning changes representation.

Validation determines whether the resulting data satisfies defined rules.

### 4. Flag before deleting

A suspicious record should generally be identifiable before a deletion decision is made.

### 5. Never invent data

If the correct value cannot be established from reliable evidence, flag it for review rather than guessing.

### 6. Verify formulas

A formula returning a value does not prove that the value is correct.

### 7. Maintain an audit trail

A reviewer should be able to understand what changed and why.

### 8. Think about the business meaning

Data quality decisions should be connected to the purpose of the data, not just the appearance of the spreadsheet.

---

# Why I Published the Failed Attempt

It would have been easy to publish only the improved version.

I chose not to.

The first version is part of the project because it shows the actual learning process.

The difference between the two versions demonstrates something that a polished final workbook cannot:

**how the analytical process changed.**

The goal of this repository is therefore not to present myself as someone who already knows everything.

It is to demonstrate that I can identify weaknesses, learn from them, rebuild my process, and produce better work.

---

# Current Learning Focus

This project is part of my broader journey toward becoming job-ready in data analytics.

My current focus is building stronger foundations in:

* Excel
* Data cleaning
* Data validation
* Data transformation
* Business-oriented analysis
* Data quality
* Analytical reasoning
* Reporting and visualization

The next stage of the journey will build on these foundations and move further into analysis, PivotTables, reporting, and dashboards.

---

# Final Reflection

The score changed from **38/100 to 88/100**.

But the score is not the most important result.

The important change was learning to stop asking:

> "Did my formula work?"

and start asking:

> **"Is the result correct, defensible, and supported by the data?"**

That is the mindset I am taking forward into the rest of my data analytics journey.

---

## Author

This repository was created as part of my personal data analytics learning journey.

I am sharing both the mistakes and the improvements because learning in public is not only about showing the final result.

It is also about showing the work required to get there.
