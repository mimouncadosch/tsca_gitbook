# Automated Firecloud Submissions

## 1. Running CNVs, SNVs, and Fingerprinting automatically

Log into the `cga02` server, go to the following directory and activate the relevant environment:
```
ssh cga02
cd /xchip/clf/seq_data/process_for_fc/automatic_fc_workflow/
use .anaconda-5.0.1
source activate myenv
```

Edit the following files:
```
cnv_auto.py
snvs_auto.py
fng_auto.py
```

For each file:  
	- edit the parameters in the python file (e.g. tsca_id = "TSCA31" in `cnv_auto.py`)  
	- edit the parameters in the configuration firecloud

**Important:**  
- You have to run `cnv_auto.py` before you can run `snvs_auto.py` or `fng_auto.py`