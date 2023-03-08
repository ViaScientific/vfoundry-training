Expected learning outcome
========

To understand the basics of Foundry and run a single-cell RNA-Seq pipeline with sample data.

# Before you start

Please go to https://www.viafoundry.com and log in to your account. If you have any issues with logging in, please let us know (support@viascientific.com). We will set-up an account for you.

<p align="center"> <p align="center"> <img src="sc-rnaseq_images/logging_in.png" width="80%"> </p>

Creating a Project
========

Once logged in, (1) click on the `Projects` drop down on the top menu. This is the place to configure your projects.

To create a new project, (2) select `Add a New Project`.

<p align="center"> <img src="sc-rnaseq_images/creating_project.png" width="80%"> </p>

In the `New Project` pop-up, (3) give the new project a name and (4) click save.

<p align="center"> <img src="sc-rnaseq_images/new_project.png" width="80%"> </p>

Creating a Run
========

Once a project is created, to access pipelines (1) click the `Pipelines` tab and then (2) click `Add Pipeline` in the top right. 

<p align="center"> <img src="sc-rnaseq_images/add_pipeline.png" width="80%"> </p>

In the `Add pipeline` window, (3) click the `Add` button for the "Cell Ranger Pipeline" and close the window (bottom right). 

<p align="center"> <img src="sc-rnaseq_images/add_cellranger_pipeline.png" width="80%"> </p>

To bring up the run page, (4) click the `Run` button of the Cell Ranger pipeline on the table.

<p align="center"> <img src="sc-rnaseq_images/initiate_run.png" width="80%"> </p>

***

[Optional] To provide a run name, (5) click inside the box next to `Run`. Provide a new name and click anywhere outside the box to exit.

[Optional] To provide a run description, (6) click the pencil next to `Run Description`. Provide a description and (7) click on the checkbox to finish editing.

***

Under `Run Environment`, (8) select "Via Run Environment (AWS Batch)"

<p align="center"> <img src="sc-rnaseq_images/run_settings.png" width="80%"> </p>

To add the source data, under `User Inputs` next to `Reads` (9) click `Enter File`

<p align="center"> <img src="sc-rnaseq_images/enter_reads.png" width="80%"> </p>

In the `Select/Add Input File` window, (10) select the `Files` tab and then (11) click `+ Add File`

<p align="center"> <img src="sc-rnaseq_images/select_input.png" width="80%"> </p>

In the `Add File` window, (12) select the `Remote Files` tab and in the `1. File Location` box (13) paste the following path: 

```
s3://viafoundry/run_data/test_data/fastq_10x_pbmc_1k_v3
```

The `Amazon Keys for S3` box should appear. The `Amazon Keys for S3` should automatically set itself to "Via Scientific AWS Key". ```If you prefer to use another AWS Key for another s3 bucket, please change "Amazon Keys for S3" dropdown option.``` 

Click (15) **search button** to see the content of the s3 directory. Leave `2. File Type` as "FASTQ" and in the `3. Collection Type` dropdown, (14) select 'Paired List'. 

<p align="center"> <img src="sc-rnaseq_images/add_file1.png" width="80%"> </p>



Under `4. File Pattern`, check that `R1 Pattern` is set to `_R1` and similarly that the `R2 Pattern` is set to `_R2`. For this sample, there were two sequencing lanes run (L001 and L002). To merge the two lanes, (16) hold shift while clicking on `pbmc_1k_v3_S1_L001_R1_001.fastq.gz` and (17) `pbmc_1k_v3_S1_L002_R1_001.fastq.gz`. The corresponding R2 will be automatically selected. (18) Click "Merge Selected Files" to combine the two lanes.

```
* Note: For other datasets, if you don't need to merge samples, you can select the samples you want to add and click 
"Add Selected Files" button. If you prefer to add all files that match the pattern, you can click "Add All Files" button.
```

<p align="center"> <img src="sc-rnaseq_images/add_file2.png" width="80%"> </p>

(19) Update the 'Name' to `pmbc_1k_v3_S1`. And input `fastq_10x_pbmc_1k_v3` as the `5. Collection Name`. The final three boxes can be left blank. (21) Click "Save Files".

<p align="center"> <img src="sc-rnaseq_images/add_file3.png" width="80%"> </p>

This will return to the `Change Input File` window. (22) Click "Save" again.

<p align="center"> <img src="sc-rnaseq_images/add_file4.png" width="80%"> </p>

Since this sample has paired end reads, (23) ensure the `mate` dropdown is set to "pair". To finish the `Metadata` section (24) click "Enter File".

<p align="center"> <img src="sc-rnaseq_images/user_inputs1.png" width="80%"> </p>

Metadata can be entered in three ways: Via a path to a file in the cloud, dropping a local file into the box, or in simple cases directly in the table. Notice the sample name is pulled in from the sample selection. To finish the table (25) fill in the "Condition" column with `pmbc_1k_v3` and (26) click "Save".

<p align="center"> <img src="sc-rnaseq_images/metadata.png" width="80%"> </p>


Pick the genome by (27) selecting "human_hg38_gencode_v32_cellranger_v6" in the `genome_build` dropdown. 

If you prefer to add custom genome sequence to selected genome_build, enable three inputs:
 - set `run_mkref` to "Yes"
 - set `add_sequences_to_reference` to "Yes"
 - set `run_Download_Genomic Sources` to "Yes"

To supply the new sequences (30) click the wrench in the `add_sequences_to_reference` section.

<p align="center"> <img src="sc-rnaseq_images/user_inputs2.png" width="80%"> </p>

In the `Process Settings` window (31) click "Enter File"

<p align="center"> <img src="sc-rnaseq_images/user_inputs3.png" width="80%"> </p>

In the `Enter File` window (32) you can drag and drop your local genome file (in fasta format) or enter a s3 path into `File Location`:

```
/opt/runs/run132/upload/seq.fa
```

and (33) click "Save" to return to the `Process Settings` window.

<p align="center"> <img src="sc-rnaseq_images/user_inputs4.png" width="80%"> </p>

(34) Click "OK" to submit the changes.
 
<p align="center"> <img src="sc-rnaseq_images/user_inputs5.png" width="80%"> </p>

To finish the "~ User Inputs ~", (36) set `run_Download_Genomic Sources` to 'yes'. In conclusion, all settings should be set to "yes", except `run_Aggregate_Libraries` and `genome_build` which was set to "human_hg38_genecode_v32_cellranger_v6".

<p align="center"> <img src="sc-rnaseq_images/user_inputs6.png" width="80%"> </p>

Finally, to submit the run (37) click "Run" in the top right and (38) select "Start"

<p align="center"> <img src="sc-rnaseq_images/start.png" width="80%"> </p>

Congratulations! You have submitted the single-cell RNA-Seq pipeline on Foundry!