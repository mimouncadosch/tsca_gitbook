# Update Cohort Reports

---

Here are the steps:

0. First, make sure that the CNV and SNV analysis has been completed for the batch in question. Namely, all the methods have finished running in Firecloud.

1. Go to `/xchip/clf/seq_data/process_for_fc/automatic_fc_workflow`

2. Launch the jupyter notebook `jupyter notebook` and open `02_update_cohort_reports.ipynb`

3. The only parameter that needs to be edited is:
```
data = pd.read_table("/xchip/clf/seq_data/process_for_fc/tsca42__201901_SN0164786/tsca42_201901_SN0164786.import_samples.txt")
```
Replace the path with the path to the `*.import_samples.txt` file corresponding to the current batch.

4. Run the cells in the notebook. The scripts in the cells will launch the Firecloud methods necessary to update the cohorts with the samples contained in the new batch just processed.

5. You're done!
