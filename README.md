# Set of some YARA-L rules

## Table of Contents

1. [Intro](#intro)
2. [Data in meta fields](#Data-in-meta-fields)
3. [Building Blocks](#building-blocks)
4. [Checker](#checker)
5. [Example Rules](#Example-Rules)

## Intro

* Quick disclaimer: Depending on your organization the UDM fields that these rules look off of may not match up directly.
The rules may need some tuning. All rules are created and tested by myself. Please use at your own risk. If you think there are any issues with my rules or any requests for Yara-L ones please feel free to reach out. 

## Resources
The following is a link to a few chronicle resources that I commonly use.
* [New To Chronicle Series](https://chronicle.security/blog/?filters=new-to-chronicle-series) An in depth writeup on how to begin writing Yara-L rules. Cannot reccomend this series enough for someone trying to learn the language. Great example rules as well for seeing some of the newer capabilities of Yara-L.
* [List of UDM fields](https://cloud.google.com/chronicle/docs/reference/udm-field-list) List of all UDM fields in the platform. Good link to save as it had all field names and the values for fields which are enumerations.
* [Graph data](https://cloud.google.com/chronicle/docs/detection/context-aware-analytics#outcome_section) Good examples rules for using some of the context graphs on the platform.
* [Rule Examples](https://cloud.google.com/chronicle/docs/detection/yara-l-2-0-overview#yara-l_20_example_rules) NEW UPDATES!!! Chrionicle added more examples that show the flexibility of what can be done in Yara-L. Would recommend reviewing these to understand hw multi event and outcome rules work. 
* [More Graph Rules](https://cloud.google.com/chronicle/docs/detection/use-enriched-data-in-rules) Thorough examples of how the graph data can be used for prevelance based detections.

## Data in meta fields
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

## Example Rules
Yara-L provides features to let users create multi-event rules as well as a new outcomes section. The following rules are a bit more complex and are good examples of rules to look at for learning:
* [Using Or For Different Behavior](https://github.com/amalone341/YARA-L-Work/blob/main/Defense%20Evasion/Windows/Verclsid_activity.yaral)
* [Simple multi event rule](https://github.com/amalone341/YARA-L-Work/blob/main/Initial%20Access/Email_to_google_drive_download.yaral)
* [Three part multi event](https://github.com/amalone341/YARA-L-Work/blob/main/Malware/Async_Rat_Installation.yaral)
* [Fun with outcomes](https://github.com/amalone341/YARA-L-Work/blob/main/Outcomes%20Rules/Suspicious_Failed_Logins.yaral)
* [Long OR](https://github.com/amalone341/YARA-L-Work/blob/main/Ransomware/Lockbit2.yaral)
