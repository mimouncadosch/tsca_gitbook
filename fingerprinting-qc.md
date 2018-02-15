# Fingerprinting Pipeline

---

### 0. FNG\_Compile\_Pileup\_Cnt

Compile Pileup Count

* **Entity:** sample
* **Status: \*\*works\*\***
* **Call on:** all samples in new batch

---

### 1. FNG\_Compile\_db

Compile Fingerprinting database

* **Entity:** sample\_set
* **Status: \*\*works\*\***
* **Call on:** sample set with all cumulative samples \(e.g. Cum\_21\_all\)

---

### 2. FNG\_Query\_db

Query fingerprinting matches

* **Entity: **sample\_set
* **Status: \*\*works\*\***
* **Call on: **sample set with samples in new batch 



