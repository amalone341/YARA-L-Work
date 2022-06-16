# Set of some YARA-L rules

## Table of Contents

1. [Intro](#intro)
    1. [Data in meta fields](#Data-in-meta-fields)
2. [Building Blocks](#building-blocks)
3. [Checker](#checker)

## Intro

* Quick disclaimer: Depending on your organization the UDM fields that these rules look off of may not match up directly.
The rules may need some tuning. All rules are created and tested by myself. Please use at your own risk. If you think there are any issues with my rules or any requests for Yara-L ones please feel free to reach out. 

### Data in meta fields
For now heres what im going to put in the meta fields since its not specified:
* severity: 
  * `CRITICAL`: A detection of this rule is severe and warrants immediate response.
  * `HIGH`: Detections from this rule need to be looked into reletively soon.
  * `MEDIUM`: Rule that fingerprints interesting activity associated with TTPs. When in coordination with other `MEDIUM` rules on the same host/user the activity should be elevated.
  * `LOW`: Informational rule or rule to display activity of interest
* status:
  * `Experimental`: Rule still needs some testing/tuning to be reliable
  * `Testing`: Rule is pretty consitent but needs some tuning and review of matches to be reliable
  * `Stable` : Tuned rule and needs to be looked at it if there is a detection and its `high` or `critical`

## Building Blocks
These are a set of rules that look for possibly suspicious activty. By themselfs they are very noisy but when used in conjuction with each other they might provide good data. For example if one hostname is the cause of 3+ unique block rules it is worth investigating. 

## Checker
Rules for looking for certian IOCs (emails, IPs, hashes, etc.). 

## Complex Rules
Yara-L provides features to let users create multi-event rules as well as a new outcomes section. The list of the following are rules that are a bit more complex. Good examples of rules to look at for learning:
* [Using Or For Different Behavior](https://github.com/amalone341/YARA-L-Work/blob/main/Defense%20Evasion/Windows/Verclsid_activity.yaral)
* [Simple multi event rule](https://github.com/amalone341/YARA-L-Work/blob/main/Initial%20Access/Email_to_google_drive_download.yaral)
* [Three part multi event](https://github.com/amalone341/YARA-L-Work/blob/main/Malware/Async_Rat_Installation.yaral)
* [Fun with outcomes](https://github.com/amalone341/YARA-L-Work/blob/main/Outcomes%20Rules/Suspicious_Failed_Logins.yaral)
* [Long OR](https://github.com/amalone341/YARA-L-Work/blob/main/Ransomware/Lockbit2.yaral)
