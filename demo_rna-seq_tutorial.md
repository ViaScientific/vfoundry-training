Expected learning outcome
========

To understand the basics of Foundry, and do RNA-Seq analysis with sample mouse data.

Creating a Run
========

Once logged in, click on the `Projects` section at the top menu and click `Add a New Project` button. This is the place to configure your project. To access pipelines, click `Pipelines` tab and then click `Add Pipeline` button. 

<img src="rnaseq_images/addpipeline1.png" width="99%">

1. Click on `Add` button on "RNA-Seq Pipeline" and close the window. 

<img src="rnaseq_images/addpipeline2.png" width="99%">

3. Now click `Run` button of the pipeline on the table.

<img src="rnaseq_images/addpipeline3.png" width="99%">

4. Run page will be loaded. Under Run Environment, select "Via Demo Environment(AWS Batch)"
5. Under User Inputs, next to `reads`, click `Enter File`
6. Click `Add File` button to enter new files.
7. Next to "1. File Location", enter:
```
s3://viascientific/run_data/test_data/fastq_mouse
```
6. and click the magnifying glass icon. The box below should populate with files ending like so:

<img src="rnaseq_images/addfiles1.png" width="99%">

7. Next to "3. Collection Type", choose "Paired List"
8. Under "4. File Pattern", next to `Forward Pattern`, type `.R1`. Similarly,  type `.R2` for `Reverse Pattern`.

<img src="rnaseq_images/addfiles2.png" width="99%">

10. Click "Add All Files"
You should now see 6 entries below.

<img src="rnaseq_images/addfiles3.png" width="99%">

10. Next to "5. Collection Name", type `rna-seq mousetest paired` and Click `Save Files`
12. On the "Select/Add Input File" screen which should now have 6 entries, click "Save".
13. For "mate", choose "pair"
14. For genome_build, choose "mousetest"
15. Leave the rest as defaults
16. Click Run in the top right. RNA-Seq pipeline runs typically take several minutes to complete for this dataset.
18. Navigate to the Log tab and click on log.txt to see progress on your run.
19. Once the blue "Running" in the top right changes to a green "Completed" go to the Report tab to see the final reports.
20. Click on MulitiQC, and scroll to find this plot, which shows aligned reads per library:

<img src="rnaseq_images/report1.png" width="99%">

20. Click on Summary to check mapping rates:

<img src="rnaseq_images/report2.png" width="99%">

20. Click on RSEM Summary to download count table:

<img src="rnaseq_images/report3.png" width="99%">

21. Click on DEBrowser to do Differential Expression Analysis.

<img src="rnaseq_images/report4.png" width="99%">

Congratulations! You have run and tested a RNA-Seq pipeline on Foundry!
