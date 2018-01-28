# SNV Pipeline

## 1. SNV Pipeline

---

#### 0. MutationCalling\_Normals {#0-mutationcallingnormals}

Mutation Calling \(MuTect 1 + MuTect 2\) on the **batch normal samples**

* _Entity_: sample
* _Status_: **works**
* _Call on_: **normal samples** in new batch

---

#### 1.CreatePoN\_SNV\_Mutect1 {#1-createponsnvmutect1}

Create PoN for SNVs for MuTect1

* _Entity_: sample\_set
* _Status_: **works**
* _Call on_: **Cum\_PoN\_XX\_all** where XX is the latest batch number

---

#### 1. CreatePoN\_SNV\_Mutect2 {#2-createponsnvmutect2}

Create PoN for SNVs for MuTect2

* _Entity_: sample\_set
* _Status_: **works**
* _Call on_: **Cum\_PoN\_XX\_all** where XX is the latest batch number

---

#### 1. SNV\_FilterGermlineEvents\_NormalSample

* _Entity_: sample
* _Status_: **works**
* _Call on_: **normal samples** in new batch

---

#### 2. SNV\_PostProcessing\_Normals

* _Entity_: sample\_set
* _Status_: **works**
* _Call on_: **normal samples set**

---

#### 2. SNV\_MutationCalling\_Tumors

Dependencies:

* **CreatePoN\_SNV\_Mutect1**
* **CreatePoN\_SNV\_Mutect2**

Run on:

* Entity: pair
* _Status_: **works**
* _Call on_: **tumor pairs** in new batch

---

#### 3. SNV\_FilterGermlineEvents\_TumorSample

Dependencies:

* **SNV\_MutationCalling\_Tumors**

Run on:

* Entity: pair

* _Status_: **works**

* _Call on_: **tumor pairs** in new batch

---

#### 4. SNV\_PostProcessing

Dependencies:

* **SNV\_FilterGermlineEvents\_TumorSample**

Run on:

* Entity: pair\_set

* _Status_: **works**

* _Call on_: **tumor pair\_set**



