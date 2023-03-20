Expected learning outcome
========

To understand the basics of Metadata Tracking System, and import sample GEO metadata.

# Before you start

Please go to https://www.viafoundry.com and login into your account. If you have an issue about login, please let us know about it (support@viascientific.com). We will set an account for you.

Creating a Run
========

Once logged in, click on the `Projects` section at the top menu and click `Add a New Project` button. Enter your project name and click OK. This is the place to configure your project. Click on the `Add Metadata Tracker` icon to add new `Metadata` tab into your project. 

<img src="metadata_geo_images/geo1.png" width="99%">

1. Click on `Metadata` tab. This window is the `Data View` section of the Metadata tracker where you will insert your data. Before inserting new data, we need to configure the database structure. To start configuring click on "Configure Metadata" button at the right. 

<img src="metadata_geo_images/geo2.png" width="99%">

2. In this configuration window there are couple of tabs available.
   - All Collections: List of project collections(tables).
   - All Events: List of events that are defined for Data view.
   - Tree View: Shows your project collections(tables) in tree visualization.
   - Templates: Predefined collections templates to import into your project

<img src="metadata_geo_images/geo3.png" width="99%">

3. Please click `Templates` tab to import predefined collections. Select all the collections by clicking checkboxes. After choosing them, click `Import Collection` Button.

<img src="metadata_geo_images/geo4.png" width="99%">


4. Now you can revisit `All Collections` and `Tree View` Tabs to see imported collection and their relationships.

<img src="metadata_geo_images/geo5.png" width="99%">
<img src="metadata_geo_images/geo6.png" width="99%">

5. Let visit NCBI SRA Run Selector (https://www.ncbi.nlm.nih.gov/Traces/study/) to download sample project metadata. Enter `GSE196908` into `Accession` field and click search button.

<img src="metadata_geo_images/geo7ncbi.png" width="99%">

6. Click on the `Metadata` button to download comma separated metadata file. 
<img src="metadata_geo_images/geo8ncbi.png" width="99%">

7. To visualize the file in excel or another spreadsheet viewer, change the file extension to csv.
   ``` 
   SraRunTable.txt -> SraRunTable.csv
   ```

8. Open the file to check its content.

<img src="metadata_geo_images/geo9ncbi.png" width="99%">

9. Lets distribute these column headers into 4 groups (series, biosamples, samples, file) to save into our project.

| series      | biosamples        | samples        |  files    |
| :----:      |    :----:         |    :----:      |  :----:   |
| BioProject  | BioSample         | Sample Name    |    Run    |
|             | Organism          | Assay Type     |    |
|             | source_name       | Library Name   |   |
|             | TREATMENT         | LibraryLayout      |   |
|             | weeks_treatment   | LibrarySelection      |    |
|             |                   | LibrarySource     |    |
|             |                   | Instrument     |    |
|             |                   | Platform       |    |


10. Return back to Foundry Metadata tracker, and click the Series tab. Change the `NamingPattern` of `id` column:

| Column      | Field of change        | Old Value        |  New Value        | 
| :----:      |    :----:              |    :----:      |   :----:      | 
| id          | NamingPattern          | ```SE-${AUTOINCREMENT}```  | ```${series.name}```    |  


11. Click Biosamples Tab and change the `NamingPattern` of `id` column as follows: 

| Column      | Field of change        | Old Value        |  New Value        | 
| :----:      |    :----:              |    :----:      |   :----:      | 
| id          | NamingPattern          | ```B-${AUTOINCREMENT}```  | ```${biosamp.name}```    |  

12. Insert new columns by clicking plus button at the top left.

| New Column Name      | New Column Label       | 
| :----:      |    :----:              |    
| BioSample          | BioSample          | 
| Organism          | Organism          | 
| source_name          | source_name          | 
| TREATMENT          | TREATMENT          | 
| weeks_treatment          | weeks_treatment          | 





13. Click Samples Tab and change the `NamingPattern` of `id` column as follows: 

| Column      | Field of change        | Old Value        |  New Value        | 
| :----:      |    :----:              |    :----:      |   :----:      | 
| id          | NamingPattern          | ```SA-${AUTOINCREMENT}```  | ```${sample.name}```    |  

14. Insert new columns by clicking plus button at the top left.

| New Column Name      | New Column Label       | 
| :----:      |    :----:              |    
| Sample Name           | Sample Name           | 
| Assay Type            | Assay Type            | 
| LibraryLayout          | LibraryLayout          | 
| LibrarySelection          | LibrarySelection          | 
| LibrarySource          | LibrarySource          | 
| Instrument          | Instrument          | 
| Platform          | Platform          | 


15. Click Samples Tab and change the `NamingPattern` of `id` column as follows: 

| Column      | Field of change        | Old Value        |  New Value        | 
| :----:      |    :----:              |    :----:      |   :----:      | 
| id          | NamingPattern          | ```F-${AUTOINCREMENT}```  | ```${file.name}```    | 










Congratulations! You have configured metadata tracker for your project and imported GEO data into foundry!
