# Preparing Data

## Preparing the raw sequencing data

### 1. Downloading the data from the GP servers

You should get an email with the path and credentials necessary to download this data. Go to the CCLF directory in xchip and download the raw sequencing files.

Example:

```
cd /xchip/clf/seq_data/ 
wget --tries=10 --continue --mirror --user SN0138152 --password Ts4DoAKPg3DD --no-check-certificate https://get.broadinstitute.org/pkgs/SN0138152/
```

### 2. Renaming files according to sample names

##### 2.a.
Copy the External Sheet \(received from Paula\) to the `walkup_seq_sample_info/`  directory.

```
cp ~/Downloads/<EXTERNAL_SHEET> /xchip/clf/seq_data/walkup_seq_sample_info/
```

##### 2.b.
Edit the following files:
```
/xchip/clf/seq_data/process_for_fc/prepare_data_for_fc_export.py
/xchip/clf/seq_data/process_for_fc/upload_bams_to_fc.py
```

##### 2.c.
Login to UGER server and prepare the files for export to Firecloud/Google Bucket (files are named according to well positions, and need to be named after samples they represent).
```
ssh mimoun@login.broadinstitute.org
use UGER
ish
```

```
cd /xchip/clf/seq_data/process_for_fc/
use .anaconda-5.0.1
# source venv/bin/activate
python prepare_data_for_fc_export.py
```

**Important:**  
Run all functions once for each plate prefix (`1_` and `2_`), except for the last function `create_sample_info_file(...)`, which you only need to run once.

### 3. Upload to Firecloud \(Google Bucket\)

Run this file to upload files to Firecloud/Google Bucket:
```
python upload_bams_to_fc.py
```

NOTE: [https://github.com/BIMSBbioinfo/intro2UnixandSGE/blob/master/sun\_grid\_engine\_for\_beginners/how\_to\_submit\_a\_job\_using\_qsub.md](More on UGER)

## Uploading the metadata

### 1. Upload batch metadata to Firecloud

##### A.

First, in folder `/xchip/clf/seq_data/process_for_fc/metadata_exports/remote_files`  make sure to add the following files:

* pair\_set\_membership\_TSCAXX.tsv
* remote\_samples\_TSCAXX.txt
* sample\_set\_membership\_TSCAXX.tsv

Where `TSCAXX` is the last batch run.

**Note:** Download these files from Firecloud, by going to your **workspace &gt; Data, **and selecting** **from **pairsets, samples, sample\_sets, **respectively.

##### B.

Second, in the file `/xchip/clf/seq_data/process_for_fc/metadata_exports/paths_to_batches_info.xlsx`make sure to add the path to the `import_samples.txt` file for the batch being run.

The file will be in `/xchip/clf/seq_data/process_for_fc/tscaXX_date_SNID/`

##### C.

Third, load the `firecloud_sugar` library:

```
/xchip/clf/seq_data/process_for_fc/metadata_exports/firecloud_sugar.py
```

Run function `upload_data_new_batch(...)`  and `update_cohorts(...)`

**D.**

For debugging, make sure that:

* The Control sample has a sample ID \(not a null ID\)
* That there aren't any new cohorts not included in the dictionary `cohort_names_dictionary.txt` 


