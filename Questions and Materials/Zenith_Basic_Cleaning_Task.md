# Data Cleaning Track — Level 1: BASIC
## Zenith Retail Ghana Ltd — Q1 2026 Transaction Batch (Cleaning Practice)

**Dataset file:** `Zenith_Basic_Cleaning_Practice_RAW.xlsx` (sheet: `RawData_Export`)
**Record count:** 575 rows (excluding header)

This is the first of three cleaning-only exercises (Basic → Intermediate → Advanced). Each one is deliberately narrower than the full integrated assessment you did before — the goal here is to build clean, correct *habits* on simple problems before you meet harder judgment calls. There are no negative numbers, no broken order references, and no suspicious revenue in this file. That's on purpose — this level is about mechanics, not judgment.

**One rule matters more than any formula in this exercise:** cleaning means making a value *readable correctly*, never making it *different*. If a cell says `15`, cleaning can turn it from text into a real number `15` — it can never turn it into `-15`, `150`, or a blank. If you're ever tempted to "fix" a value so a downstream formula behaves, stop — that's not cleaning, and it's exactly what cost you the most marks last time.

---

## What's messy in this file

You'll find, somewhere in the 575 rows:

- Inconsistent capitalization and stray leading/trailing spaces in `Region`, `ProductCategory`, `CustomerType`, `SalesChannel`, and `PaymentMethod`.
- `OrderDate` stored in more than one text format (all genuinely valid calendar dates — no malformed ones this time).
- `Quantity` and `UnitPrice` sometimes stored as text instead of true numbers (plain numeric text, no currency symbols this time).
- A small number of exact duplicate rows.
- A small number of blank cells — some in fields that don't affect a transaction's validity (`PaymentMethod`), and a very small number in fields that matter more (`FirstName`, `LastName`, `SalesChannel`).

I'm telling you what categories of problem exist this time, because at Basic level the goal is executing the right technique cleanly — not detective work. Detective work is Intermediate and Advanced.

---

## Tasks

**1. Standardize the categorical fields**
Make `Region`, `ProductCategory`, `CustomerType`, `SalesChannel`, and `PaymentMethod` each resolve to a single consistent value per genuine category (e.g. every spelling/casing/spacing variant of "Accra" should read as one clean value). Use formulas — do not retype values by hand. State which function(s) you used and why.

**2. Convert text-numbers to real numbers**
Determine which cells in `Quantity` and `UnitPrice` are stored as text rather than numbers (don't assume — show how you checked), and convert them to genuine numeric values **without changing the underlying value**. Report how many cells you had to convert in each column.

**3. Standardize the date field**
Convert `OrderDate` into a single, genuine Excel date format. Report how many distinct raw formats you found before cleaning.

**4. Handle duplicates**
Identify exact duplicate records. State how you confirmed a pair was a true duplicate (not just similar), report how many you found, and remove the redundant copies — keeping exactly one instance of each. Report your row count before and after.

**5. Handle blanks — without inventing data**
Identify every blank cell by column and report the count per column. For each column with blanks, decide and state what the *correct* handling is — and justify it. You are not permitted to fabricate a plausible-looking value to fill a blank (e.g. don't invent a first name). Flagging a blank as missing is always an acceptable answer; guessing a replacement value is not.

**6. Verification (do this last, and do it for real)**
Before you call the file clean, check your own work:
- Confirm no column that should now be numeric still contains any text-formatted numbers (show the check, e.g. a COUNT vs COUNTA-style comparison, or ISNUMBER across the column).
- Confirm your row count after deduplication is exactly (starting rows − duplicates removed).
- Confirm that standardizing your categorical fields produced *exactly* the expected number of unique values per field (8 regions, 6 categories, 3 customer types, 4 channels, 4 payment methods) — if you get more or fewer, you have a variant you haven't caught, or you've accidentally merged two genuine categories. Find and fix it before submitting.

---

## Submission

Send back your cleaned workbook with:
- The original raw data untouched on its own sheet.
- Your cleaned working sheet, with your standardization/conversion formulas visible (not just typed-in final values).
- A short before/after summary: starting row count, duplicates removed, final row count, blank-cell counts by column, and confirmation of your Task 6 verification checks.

I'll mark it, tell you exactly what's right and wrong and why, and then we'll move to Level 2: Intermediate — which introduces messier duplicates (near-duplicates, not just exact ones), numbers with currency prefixes and stray delimiters, and dates that include some genuinely invalid ones you'll have to detect rather than just reformat.
