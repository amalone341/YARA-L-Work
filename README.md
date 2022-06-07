# Set of some YARA-L rules

## Table of Contents

1. [Intro](#intro)
    1. [Data in meta fields](#Data-in-meta-fields)
2. [Building Blocks](#building-blocks)
3. [Checker](#checker)

## Intro

* Quick disclaimer: Depending on your organization the UDM fields that these rules look off of may not match up directly with what your organization uses.
The rules may need some tuning. 

### Data in meta fields
For the non straighforward ones now heres what im going to put in the meta fields since its not specified:
* severity: 
  * `CRITICAL`: This rule is highly tuned and warrants immediate checking and/or escalation.
  * `HIGH`: The activity in this rule indicates activity that should be looked into. These rules may have higher false positive rates.
  * `MEDIUM`: Rule that fingerprints interesting activity associated with TTPs. When in coordination with other MEDIUM rules on the same host/user the activity should be elevated
  * `LOW`: Informational rule or rule to display activity of interest
* status:
  * `Experimental`: Rule still needs some testing/tuning to be reliable
  * `Testing`: Rule is pretty consitent but needs some tuning and review of matches to be reliable
  * `Stable` : Tuned rule and needs to look at it if there is a detection and its `high` or `critical`

## Building Blocks
These are a set of rules that look for possibly suspicious activty. By themselfs they are very noisy but when used in conjuction with each other they might provide good data. For example if one hostname is the cause of 3+ unique block rules it is worth investigating. 

## Checker
Rules for looking for certian IOCs (emails, IPs, hashes, etc.). 
