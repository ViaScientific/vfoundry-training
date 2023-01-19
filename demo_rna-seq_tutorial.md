Expected learning outcome
========

To understand the basics of Foundry, and do RNA-Seq analysis with mouse test data.

Creating a Run
========

Once logged in, click on the `Projects` section at the top menu and click `Add a New Project` button. This is the place to configure your project. To access pipelines, click `Pipelines` tab and then click `Add Pipeline` button. 

<img src="images/addpipelineBtn.png" width="99%">

1. Click on Add button on "RNA-Seq Pipeline" and close the window. Now click `Run` button for the pipeline.

2. Under Run Environment, select "Via Demo Environment(AWS Batch)"
3. Under User Inputs, next to "reads", click "Enter File"
4. Click "+ Add File"
5. Next to "1. File Location", enter:
```
s3://viascientific/run_data/test_data/fastq_mouse
```
6. and Click the magnifying glass icon. The box below should populate with files ending like so:

<img src="images/addpipelineBtn.png" width="99%">

7. Next to "3. Collection Type", choose "Paired List"
8. Under "4. File Pattern", next to `Forward Pattern`, type `.R1`. Similarly,  type `.R2` for `Reverse Pattern`.
9. Click "Add All Files"
You should now see 6 entries below.

<img src="images/addpipelineBtn.png" width="99%">

10. Next to "5. Collection Name", type "rna-seq mousetest paired".
11. Click "Save Files"
12. On the "Select/Add Input File" screen which should now have 6 entries, click "Save".
13. For "mate", choose "pair"
14. For genome_build, choose "mousetest"
15. Leave the rest as defaults
16. Click Run in the top right and then click Start
17. RNA-Seq pipeline runs typically take several minutes to complete for this dataset.
18. Navigate to the Log tab and click on log.txt to see progress on your run
19. Once the blue "Running" in the top right changes to a green "Completed" go to the Report tab to see the final reports
20. Click on MulitiQC, and scroll to find this plot, which shows aligned reads per library:

<img src="images/addpipelineBtn.png" width="99%">

21. Click on DEBrowser to do Differential Expression Analysis.

Congratulations! You have run and tested a RNA-Seq pipeline on Foundry!
