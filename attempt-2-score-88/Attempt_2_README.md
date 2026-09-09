# Attempt 2 — Data Cleaning & Validation

**Score: 88/100**

## What Changed

After Attempt 1, I rebuilt my process around the principles I'd failed to apply the first time, then returned to the same dataset. The improvement wasn't from learning more Excel functions — it came from reasoning differently about the data.

This version included a much more structured cleaning and validation process:

* Text standardization (case, whitespace, inconsistent category and region names)
* Numeric conversion and validation (quantity, unit price)
* Revenue calculated and cross-checked against reported values, not assumed correct
* Date cleaning and validation, including checking dates fall within the expected business period
* Order-reference reconstruction and validation
* Duplicate detection — distinguishing exact duplicates, repeated business keys, and near-duplicates rather than deleting on sight
* Missing-value identification and classification, rather than automatic replacement
* Lookup-based validation against reference/business-rule tables
* Before/after row tracking and helper columns for transparency

The final working dataset contained 3,148 records after cleaning.

## Key Shift From Attempt 1

| Area | Attempt 1 | Attempt 2 |
|---|---|---|
| Duplicate handling | Deleted too quickly | Investigated and classified first |
| Negative values | Altered incorrectly | Preserved and flagged for review |
| Formula verification | Insufficient | Checked systematically, not assumed correct |
| Business rules | Incompletely applied | Explicitly incorporated per field |
| Audit trail | Limited | Stronger before/after tracking |
| Mindset | "The formula works" | "The result must be verified" |

## What I Learned

Knowing `TRIM`, `IF`, `VLOOKUP`, `COUNTIFS`, and similar functions is useful, but knowing when to use them, what their output actually means, and whether that output should be trusted, matters far more. This attempt was less about fixing individual cells and more about building a repeatable analytical process.
