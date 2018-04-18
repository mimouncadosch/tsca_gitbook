# CNV Calling Pipeline

---
### 0. Rename BAM
Rename BAM files (from well name to sample name)
* _Entity_: sample
* _Status_: **works**
* _Call on_: all samples in new batch

---
### 1. CalculateTargetCoverage
Compute depth of coverage for a given sample, at the interval level.
* _Entity_: sample
* _Status_: **works**
* _Call on_: all samples in new batch
---

### 2. CNV_CreatePoNForCNV
Create Panel of Normals for CNV calling
* _Entity_: sample_set
* _Status_: **works**
* _Call on_: sample set pon, e.g. "PoN_TSCA26_all_batch_normals_3_normals_per_cohort_17_total"
---

### 3. CallSomaticCNV
Call somatic CNVs
* _Entity_: sample
* _Status_: **works**
* _Call on_: all samples in new batch
---

### 4. PlotSomaticCNVMaps
* _Entity_: sample_set
* _Status_: **works**
* _Call on_: sample set
