# External Sheet Guidelines

General comments:

* **External Sample ID** should be unique
* **No comments on the spreadsheet other than the rows with sample data**

---
Control sample:

* Control should be part of **"Cancer Cell Line Factory \(CCLF\) / Controls"** Collection

* Collaborator Participant ID should be "**CCLF\_CTRL"**

* External Sample ID should be **"CCLF\_TSCA\_25\_Ctrl"**

* Sample Type sould be "Normal"
---
Most Important Columns (cannot be empty)

* External Sample ID
* Exported DNA SM-ID
* Stock DNA SM-ID
* Sample Type
* Collection
* Collaborator Participant ID
* Collaborator Sample ID

---
Cell Line Decision Columns:

* **Final Decision: **
  * Possible values are: "Tumor", "Normal", "Ambiguous", "Hold for more information"
* **Notes**
  * Variable \(not standardized\). Examples are: sample swap, low coverage
* **Action Items: **
  * Possible values are : "Resubmit", "Move to expansion", "Need WES/RNASeq", "Need cohort report", "Need primary tissue"

---
Duplicates:

There is program to rename duplicates, such that if sample with external id A already exists, the new sample will be called A_2, A_3, and so on.
It will only work however, if the external id you submit is always the basic one, i.e. no "_2", "_3", etc., as the program will be the one adding these.