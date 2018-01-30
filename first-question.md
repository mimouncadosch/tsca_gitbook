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

Files are named according to well positions, need to be named after samples they represent.

```
cd /xchip/clf/seq_data/process_for_fc
```

Edit and run this file:

```
source venv/bin/activate
prepare_data_for_fc_export.py
```

### 3. Upload to Firecloud \(Google Bucket\)

Edit and run this file:

```
upload_bams_to_fc.py
```

## Uploading the metadata

### 1. Upload batch metadata to Firecloud

First, in folder `/xchip/clf/seq_data/process_for_fc/metadata_exports/remote_files`  make sure to add the files:

* pair\_set\_membership\_TSCAXX.tsv
* remote\_samples\_TSCAXX.txt
* sample\_set\_membership\_TSCAXX.tsv

Where `TSCAXX` is the last batch run. 

! Download these files from Firecloud, by going to your **workspace &gt; Data &gt; pairsets, samples, sample\_sets**.

Second, In the file:

```
/xchip/clf/seq_data/process_for_fc/metadata_exports/firecloud_sugar.py
```

Run function `upload_data_new_batch(...)`  and `update_cohorts(...)`

