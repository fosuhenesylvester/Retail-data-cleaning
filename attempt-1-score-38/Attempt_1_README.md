# Attempt 1 — Data Cleaning & Validation

**Score: 38/100**

## What Happened

This was my first attempt at cleaning and validating a deliberately messy retail transaction dataset. The review exposed several weaknesses in my approach:

* Deleting records instead of identifying and flagging them
* Altering negative values instead of investigating why they were negative
* Making transformations without sufficiently validating the results
* Formula errors that I didn't detect before considering the work complete
* Treating a formula that successfully returned a result as proof that the underlying data was correct
* Not maintaining a sufficiently strong audit trail for some decisions

## What I Learned

Data cleaning is not simply about knowing Excel functions. It's about making defensible decisions about data.

A technically correct formula can still produce a business-wrong result. For example, if a value is negative, removing the minus sign produces a positive number without solving the underlying problem — the real issue (why is it negative?) never gets investigated.

Similarly, deleting a record that looks like a duplicate, without checking whether it's genuinely duplicated, can destroy useful information permanently.

## Principles I Took Into the Next Attempt

> Never fabricate a value.

> Never silently delete a questionable record.

> Flag first. Investigate second. Delete only when the evidence supports deletion.

> Never trust a formula simply because Excel returned a result — verify it independently.

> Separate cleaning from validation.

This attempt is kept in the repository, mistakes included, because it's part of the actual process — not something to hide before moving on.
