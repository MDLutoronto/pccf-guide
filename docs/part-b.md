---
title: Part B. Enrich your dataset with census data
parent: PCCF Guide
nav_order: 2
layout: default
maintainer:
    - name: Leanne Trimble
      link: https://library.utoronto.ca/staff/leanne-trimble
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
created_date: 2023-06-06
---

Part B. Enrich your dataset with census data
--------------------------------------------

In this section of the guide, we will incorporate census data to the dataset created in Part A, by merging on Statistics Canada geographic identifiers.

1. We need to download some census data at the Dissemination Area level of geography. Each Dissemination area will have a unique ID that will be a match to the DAuid column we merged in from the PCCF in Part A.

    We can download the census dataset from the CHASS Data Centre website To access the data from CHASS, you need to login using your UTORid using the following link: [https://login.library.utoronto.ca/index.php?url\=http://dc.chass.utoronto.ca/](https://login.library.utoronto.ca/index.php?url=http://dc.chass.utoronto.ca/)

    <img src='{{ '/assets/images/PCCF_B_001.png' | relative_url }}' alt='A website page that reads: Connect to this resource using your UTORid. This resource is licensed for your use by the University of Toronto Libraries. Off-Campus access is available to current University of Toronto students, staff and faculty. There is a blue button that reads: Log in with your UTORid. ' title='' width='75%' height='500' />

2. After you login, you will be directed to the CHASS Data Centre homepage. From the menu on the left\-hand side, select Canadian Census.

    <img src='{{ '/assets/images/PCCF_B_002.png' | relative_url }}' alt='The homepage for CHASS Data Centre. On the left is a menu with the options: CANSIM; Canadian Census; SDA @ CHASS; Trade Analyser' title='' width='72%' height='481' />

3. This will take you to the Census Analyser page. We will need to select the census profiles by census year and census geography. We will select our census profiles by census year first for this guide. Select 2016 under by Census Year.

    <img src='{{ '/assets/images/PCCF_B_003.png' | relative_url }}' alt='A website page that reads: Welcome to the Canadian Census Analyser. Underneath the title it says: Starting points: 1. Census Profile Tables. Under Census Profile Tables there are two sections: by Census Geography; by Census Year. Under by Census Geography there are hyperlinks labelled: Canada, Provinces and Territories; Federal Electoral District; Forward Sortation Areas (FSA); Census Division; Census Subdivision; Census Tract; Enumeration area/Dissemination area. Under by Census year there are hyperlinks labelled: 2016; 2011 NHS; 2011; 2006; 2001; 1996; 1991; 1986; 1981; 1971; 1961. ' title='' width='60%' height='1249' />

4. Then we select the census geography. Select Profile of Dissemination Areas.

    <img src='{{ '/assets/images/PCCF_B_004.png' | relative_url }}' alt='The CHASS website page for the 2016 Census. There are a list of hyperlinks labelled: Profile of Canada, provinces, territories; Profile of Census Divisions; Profile of Census Subdivisions; Profile of Dissemination Areas; Profile of Aggregate Dissemination Areas; Profile of Census Metropolitan Area and Census Agglomerations; Profile of Census Tract' title='' width='60%' height='1074' />

5. This will direct you to a page where you can make additional choices to make your census profile table. In step 1, you can select a subset of regions or select all. For this guide, we will select “check all”.

    <img src='{{ '/assets/images/PCCF_B_005.png' | relative_url }}' alt='A website page from the CHASS Analyser. The title reads: Step1: Specify Census Geography for retrieval. The tab by Name is selected. Underneath is a list of all letters of the alphabet. All letters are selected. ' title='' width='60%' height='784' />

6. In step 2, you can select the census variables that you are interested in. (Note: you may need to scroll way down the page before you see step 2\).The variables are grouped by topic under the topic tabs (eg. Population and dwellings, Age & sex etc). You will find the list of variables under the tabs. To select a variable, click on the check box to the left of the variable description.

    <img src='{{ '/assets/images/PCCF_B_006.png' | relative_url }}' alt='A website page from the CHASS Analyser. The title reads: Step2: Specify Census Profile variables for retrieval. Underneath is the option to select Census Profile Variables. The Income tab is selected. Under Income - Total Sex, the option Median total income in 2015 among recipients ($) (v1868) is selected.' title='' width='70%' height='867' />

    For this guide, we select the following four variables (you can choose others based on your own research interest):

    1. Income \- Total Sex / Total \- Income statistics in 2015 for the population aged 15 years and over in private households \- 100% data / Number of total income recipients aged 15 years and over in private households \- 100% data / Median total income in 2015 among recipients ($) (v1868\)
    2. Housing \- Total Sex / Total \- Owner households in non\-farm, non\-reserve private dwellings \- 25% sample data / Median monthly shelter costs for owned dwellings ($) (v3942\)
    3. Education \- Total Sex / Total \- Highest certificate, diploma or degree for the population aged 15 years and over in private households \- 25% sample data (v4920\)
    4. Education \- Total Sex / Total \- Highest certificate, diploma or degree for the population aged 15 years and over in private households \- 25% sample data / Postsecondary certificate, diploma or degree / University certificate, diploma or degree at bachelor level or above (v4929\)

7. Scroll down to step 3\. Here, you can select the geographic variables to be included in the census dataset and the output data format to download the census dataset.

    Check all 5 of the geographic variables. In the *Select the output format* box, under *Download to a file*, we select *Comma\-Separated Values (CSV) file for spreadsheet* to download the census dataset as a CSV file. Select Submit Query.

    And finally, we click on Submit Query.

    <img src='{{ '/assets/images/PCCF_B_007.png' | relative_url }}' alt='A website page from the CHASS Analyser. The title reads: Step3: Specify the output details and submit query. Under Output details, all options are selected. At the bottom, there is a section titled: Census variables to be listed as: (apply only to Screen output format). The columns option is selected. ' title='' width='78%' height='765' />

    <img src='{{ '/assets/images/PCCF_B_008.png' | relative_url }}' alt='A section of the CHASS Analyser Output screen. The title reads: Select the output format. Under the title is a box with options for Screen output and the option to Download to a file. The option Comma-Separated Values (CSV) file for spreadsheet is selected. ' title='' width='70%' height='839' />

    The wizard might take a few minutes to complete the query. When the data request is complete, you will be provided with two links. One to download the data file and another one to download a file with descriptions of the column names in the first data file (known as the “header file”).

    Right\-click on the link next to Data file to download the census dataset. Choose Save Link As... We save this data file as census2016\.csv.

    <img src='{{ '/assets/images/PCCF_B_009.png' | relative_url }}' alt='A website page from the CHASS Analyser. The title reads: Data Centre Download Status. Underneath it lists the Data Request Summary. It gives the option to download the files. There is a link for the Data file and a link for the Header file.' title='' width='80%' height='1118' />

    You will also need a copy of the header file with the descriptions of the column names (otherwise you won’t know what data is in what column later). Right\-click on the header file link and choose Save Link As… We save this data file as ColumnHeaders.txt. We will make use of it in a future step.

    Now we will enrich our postal code data with the census data we just downloaded. You should already have your postal code dataset open in SPSS (called PCCF\_Merged). Let’s load the census data into SPSS next, so we can work with it.

    From the File menu, choose **Open \> Data**. Select **Files of type: CSV** and then browse to the location you saved the census dataset. Select the dataset and then select **Open**.

    The Text Import Wizard pops up. Similar to when you used this Wizard earlier, you don’t need to alter much:

    * For steps 1\-3, no changes are required. Select **Next**.
    * For step 4, ensure Comma is selected and Space is not selected. Select **Next**.
    * For step 5, no changed are required. Select **Next**.
    * For step 6, no changes are required. Select **Finish**.

    You now have your data loaded into SPSS. It should look something like this:

    <img src='{{ '/assets/images/PCCF_B_010.png' | relative_url }}' alt='A dataset titled Untitled6 [Dataset3] is open in IBM SPSS Statistics Data Editor. There are nine columns labelled: COL0; COL1; COL2; COL3; COL4; COL5; COL6; COL 7; COL8; COL9' title='' width='95%' height='649' />

    Save a copy of this file as census2016\.sav.

8. We next need to merge PCCF\_Merged.sav with census2016\.sav. As with our merge in part A, we need a common column to match on. This time, we will match on the unique ID number for dissemination areas (the geographic units we downloaded our census data at). In the PCCF\_Merged.sav dataset, the column is called DAuid and is an 8\-digit numeric variable. In census2016\.sav, the comparable column is COL0 – according to your ColumnHeaders doc this column is actually called “GEO UID”, and if you look at its variable information, you will see that it is also an 8\-digit numeric variable. (Side note: We also downloaded a column called “DA name” which may seem tempting, but that is a 4\-digit number which represents the last 4 digits of the full unique ID. The “DA name” column is not unique across all of Canada and so cannot be used here).

    Since the data types for our two columns are the same, the only edit we need to make before merging is to make the column names match. In the census2016 dataset, select Variable View. Change COL0 to DAuid. Then save the dataset.

    <img src='{{ '/assets/images/PCCF_B_011.png' | relative_url }}' alt='A dataset titled: census2016 [Dataset3] is open in SPSS. The first column is now labelled DAuid. Under DAuid is COL1 to COL 9. ' title='' width='95%' height='370' />

9. Now we are ready to merge the files. Within the PCCF\_Merged dataset, choose Data \> Merge Files \> Add Variables…

    Next select the census2016 dataset, which should be listed as an open dataset. Select Continue.

    <img src='{{ '/assets/images/PCCF_B_012.png' | relative_url }}' alt='A pop-up titled: Add Variables to PCCF_Merged.sav[PCCF_Merged2]. The option An open dataset is selected. The dataset census2016.sav[DataSet3] is selected. ' title='' width='80%' height='421' />

10. In the next window, on the Merge Method tab, select “One\-to\-many merge based on key values”. For Select Lookup Table, select whichever one represents the census dataset (the dataset numbers will vary depending on whether you have closed and opened your data files multiple times during your session). Select Sort files by key values before merging. Because each dataset has a column named DAuid, SPSS will have already populated the variable DAuid as the key variable.  Select OK.

    <img src='{{ '/assets/images/PCCF_B_013.png' | relative_url }}' alt='A pop-up titled Add Variables from DataSet3. The tab Merge Method is selected. Underneath, the option One-to-many merge based on key values is selected. Below is a box titled: Select Lookup Table. The option DataSet3 is selected. At the bottom is a box titled: Key variables. In the box is the variable DAuid. ' title='' width='60%' height='667' />

11. Your merge is now complete.

    <img src='{{ '/assets/images/PCCF_B_014.png' | relative_url }}' alt='The dataset PCCF_Merged.sav is open in SPSS. There are 14 columns. The column labels are: PC; CTname; DAuid; SLI; Age; COL1; COL2; COL3; COL4; COL5; COL6; COL7; COL8; COL9' title='' width='100%' height='576' />

    You will likely wish to switch to Variable View and update the variable names & labels to be more descriptive (use the ColumnHeader.txt file as a guide).

    <img src='{{ '/assets/images/PCCF_B_015.png' | relative_url }}' alt='Two screenshots. The one on the left lists the names of the columns for the 2016 Census Profile dataset. On the right is the PCCF_Merged.sav dataset in SPSS Variable view. The variables are now labelled as: PC; CTname; DAuid; SLI; Age; ProvCode; ProvName; CDCode; CDName; DAName; Income; ShelterCost; TotalPop; UniversityEd' title='' width='100%' height='442' />

    Don’t forget to save your file when you are finished!    

**Technique:** [Quantitative Data Analysis](https://mdlutoronto.github.io/tutorials-search/?technique=Quantitative+Data+Analysis) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R), [SAS](https://mdlutoronto.github.io/tutorials-search/?tool=SAS), [SPSS](https://mdlutoronto.github.io/tutorials-search/?tool=SPSS) \| **Data Format:** [Microdata](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Microdata)

