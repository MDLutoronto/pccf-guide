---
title: Part A. Use the PCCF to assign standard geographic codes/names to your postal codes
parent: PCCF Guide
nav_order: 1
layout: default
maintainer:
    - name: Leanne Trimble
      link: https://library.utoronto.ca/staff/leanne-trimble
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
created_date: 2023-06-06
---

Part A: Use the PCCF to assign standard geographic codes/names to your postal codes
-----------------------------------------------------------------------------------

1. Start with a dataset that includes postal code level data. Make sure you have a separate field for the postal code. You must have full 6\-digit postal codes to work with the standard PCCF file (if you have 3, 4 or 5 digits of the postal code, you can use the PCCF\+). For this tutorial, we will demonstrate using this [sample dataset](https://maps.library.utoronto.ca/workshops/PCCF/My_dataset.csv). It contains two columns, postal code (consisting of 50 randomly generated postal codes within Toronto) and age (consisting of 50 randomly generated values between 1 and 99\). As you work, imagine that this dataset represents the participants in a study you conducted. Or, use your own data.

    Download the sample dataset: <https://maps.library.utoronto.ca/workshops/PCCF/My_dataset.csv>

    <img src='{{ '/assets/images/PCCF_A_001.png' | relative_url }}' alt='An Excel spreadsheet with two columns: Postal code; Age' title='' width='70%' height='721' />

2. Bring your postal code data into SPSS. In this exercise, we will be loading in a csv file, but SPSS can accommodate many file types. If you run into difficulties loading your own data into SPSS, contact us for assistance.

    Open SPSS on your computer. From the File menu, choose **Open \> Data**.

    <img src='{{ '/assets/images/PCCF_A_002.png' | relative_url }}' alt='On the toolbar at the top of the screen, Open is selected, followed by Data' title='' width='75%' height='689' />

    Select **Files of type: CSV** and then browse to your dataset (or wherever you saved the sample file provided for this tutorial). Select **Open**.

    <img src='{{ '/assets/images/PCCF_A_003.png' | relative_url }}' alt='A menu for opening a file. The file is called My_dataset.csv. Files of type is set to CSV. Encoding is set to Unicode (UTF-8). ' title='' width='75%' height='448' />

    The Text Import Wizard pops up. Our sample data is a very simple CSV file with only one column, so we can mostly just skip through this wizard without changing anything. (If you are loading your own dataset, make the appropriate choices for your dataset at each step).

    For steps 1\-3, no changes are required. Select **Next**.

    For step 4, ensure Comma is selected and Space is not selected. Select **Next**.

    For step 5, You will get a pop\-up that says it found invalid variable names. This is because spaces are not allowed in variable names (column headers) in SPSS. Select **OK** and the wizard will remove the space in our variable name for us (to ‘PostalCode’). Select **Next**.

    <img src='{{ '/assets/images/PCCF_A_004.png' | relative_url }}' alt='A Text Wizard notification that says: Invalid variable names for this application have been found and changed.' title='' width='80%' height='156' />

    On step 6, no changes are required. Select **Finish**.

    You now have your data loaded into SPSS.

    <img src='{{ '/assets/images/PCCF_A_005.png' | relative_url }}' alt='A spreadsheet in SPSS Statistics Data Editor. There are two columns: Postal code; Age ' title='' width='60%' height='726' />

    Save the dataset by selecting **File \> Save As**. Save it as a .sav file.

    <img src='{{ '/assets/images/PCCF_A_006.png' | relative_url }}' alt='A pop-up titled: Save Data As. File name is set to My_dataset. Save as type is set to SPSS Statistics (.sav). ' title='' width='75%' height='416' />

    Leave the file open in SPSS for now, we will return to it shortly.

3. Download the PCCF dataset from the MDL website: [https://mdl.library.utoronto.ca/collections/numeric\-data/census\-canada/postal\-code\-conversion\-file](https://mdl.library.utoronto.ca/collections/numeric-data/census-canada/postal-code-conversion-file).

    Choose the census year of interest.

    <img src='{{ '/assets/images/PCCF_A_007.png' | relative_url }}' alt='Map and Data Library website page about the Postal code conversion file. Under the title reads To download PCCF data, select the census year you are interested in: 2016; 2011; 2006; 2001; 1996; 1991; 1986; 1981. An arrow points to 2016. ' title='' width='85%' height='370' />

    Choose the SPSS version of the file (the Map & Data Library has already done the work of preparing the original file for use in SPSS!)

    <img src='{{ '/assets/images/PCCF_A_008.png' | relative_url }}' alt='Map and Data Library website page. Title reads: Postal code conversion file: 2016 census geography. Under the subheading PCCF original edition, an arrow points to the line Access data SPSS (.sav) file generated by MDL (restricted). Access data is a hyperlink.' title='' width='90%' height='380' />

    Please carefully read through the end\-user license agreement.

    <img src='{{ '/assets/images/PCCF_A_009.png' | relative_url }}' alt='University of Toronto Libraries End-Use License Agreement for Postal Code(om) Conversion Files' title='' width='85%' height='414' />

    At the bottom of the page, click the link to authenticate with your UTORid. The download will then start automatically.

    <img src='{{ '/assets/images/PCCF_A_010.png' | relative_url }}' alt='The bottom of the End-Use License Agreement with an arrow pointing to the link that says To access Postal Code Data log in with your UTORid via University of Toronto Web Login. Log in with your UTORid via University of Toronto Web Login is a hyperlink.' title='' width='90%' height='376' />

    If you wish, move the file from your Downloads folder to some location where you will find it again later.

    The download is a compressed file which must be uncompressed (or “unzipped”). Right\-click on the file and choose Extract All. On a Mac you can simply double\-click on the file.

    <img src='{{ '/assets/images/PCCF_A_011.png' | relative_url }}' alt='In File Explorer the pccfNat_fccpNat_082020 file is highlighted. A drop-down menu is open from the file, the mouse highlighting the option: Extract all.' title='' width='75%' height='398' />

4. Open the PCCF data in SPSS. You can do this from within SPSS, by selecting **File \> Open \> Data** again. Another option when you are opening a file that is already in the native SPSS format (.sav) is to simply browse to the file on your computer and double\-click it. This will cause it to open in SPSS automatically.

    Note: You may see the following message:

    <img src='{{ '/assets/images/PCCF_A_012.png' | relative_url }}' alt='A pop-up from Open Data reads: IBM SPSS Statistics is running in Unicode encoding mode. This file is encoded in a locale-specific (code page) encoding. The defined width of any string variables will be automatically tripled in order to avoid possible data loss. To set the width of all string variables to the minimum required to hold the data, select Yes. There are three buttons: Yes, No, Cancel. The Yes button is selected. ' title='' width='75%' height='291' />

    You can answer “Yes”.

    You should now have two SPSS datasets open on your computer:

    <img src='{{ '/assets/images/PCCF_A_013.png' | relative_url }}' alt='Two datasets are open in IBM SPSS Statistics Data Editor: pccfNat_fccpNat_082020.sav and My_dataset.sav' title='' width='150%' height='570' />

5. Prepare your own postal code dataset for a merge. To merge two datasets, you need to have a common column to match on. In this case, we want to match on the postal code field. Ultimately, we want to keep one row for every record in our dataset (e.g. the 50 postal codes in My\_dataset) and add in the data from the PCCF file columns (the province, census division, census subdivision, census tract, dissemination area etc. codes that match our postal codes).

    Have a look at the two postal code fields in our two datasets. You can see that they are formatted differently. In the PCCF, it is a 6\-character alphanumeric field, whereas in our sample data it is a 7\-character alphanumeric field with a space in it. We will need to remove the space from our data before we can proceed.

    Select the PostalCode column in the sample dataset.

    <img src='{{ '/assets/images/PCCF_A_014.png' | relative_url }}' alt='My_dataset.sav is open in SPSS. There are two columns: Postal Code; Age. All items in the Postal Code column are selected. ' title='' width='45%' height='884' />

    In the Edit menu, select Find…

    <img src='{{ '/assets/images/PCCF_A_015.png' | relative_url }}' alt='On the toolbar Edit is selected. There is a drop down menu. Find is selected. ' title='' width='60%' height='864' />

    Choose the Replace tab. In the Find box, type a space. Leave the Replace with box as it is. Select Replace All.

    <img src='{{ '/assets/images/PCCF_A_016.png' | relative_url }}' alt='A pop-up titled: Find and Replace - Data view. The Replace tab is selected. The Find box contains one space. The Replace With box is empty. The Replace All button is selected.' title='' width='72%' height='439' />

    50 replacements will be made. Close the dialog when finished.

    The other issue we need to address is that SPSS expects the fields being merged to have the same variable name. In our sample data, let’s change the PostalCode variable to be named PC instead, to match the PCCF file.

    While looking at your sample dataset, select Variable View. In the Name column, overwrite the name of the PostalCode column to PC.

    <img src='{{ '/assets/images/PCCF_A_017.png' | relative_url }}' alt='My_dataset.sav is open in SPSS. There are two rows: PostalCode; Age. PostalCode is selected. ' title='' width='85%' height='264' />

    <img src='{{ '/assets/images/PCCF_A_018.png' | relative_url }}' alt='My_dataset.sav is open in SPSS. There are two rows: PC; Age. ' title='' width='85%' height='269' />

    While we are at it, let’s also change the width of the PC variable to 6, since the data only takes up 6 characters now that the spaces have been removed.

    <img src='{{ '/assets/images/PCCF_A_019.png' | relative_url }}' alt='My_dataset.sav is open in SPSS. There are two rows: PC; Age. There are five columns: Name; Type; Width; Decimals; Label. In the PC row, under Width, it reads: 6. ' title='' width='60%' height='392' />

    If you are working with your own data, perform any further data cleanup necessary to ensure your postal codes are formatted the same as those in the PCCF file. Save your dataset.

6. Prepare the PCCF dataset for a merge. Because of the nature of postal codes, it is common for postal codes to match more than one standard census geography (e.g. a postal code overlaps 2 dissemination areas). The PCCF provides a field called the Single Link Indicator (SLI) which can be used to select one matching geography (the one where the most dwellings are located). Note: if you need a more nuanced approach to selecting which geography to match your postal codes to, consider using the PCCF\+ instead.

    We will select only those records where the SLI value \= 1 so that we will not end up with duplicate records.

    From the **Data** menu, choose **Select Cases**.

    <img src='{{ '/assets/images/PCCF_A_020.png' | relative_url }}' alt='On the toolbar, Data is selected. There is a drop down menu. Select Cases... is selected. ' title='' width='72%' height='824' />

    The Select Cases dialog appears. Choose If condition is satisfied, and select the If… button.

    <img src='{{ '/assets/images/PCCF_A_021.png' | relative_url }}' alt='A pop-up titled: Select cases. On the right is a box titled: Select. The option If condition is satisfied is selected. There is a button underneath that reads If... ' title='' width='75%' height='592' />

    Select Single link indicator from the variable list, then click the arrow to bring it over into the expression box. Then type \= ‘1’. (The number must be surrounded by quotation marks because the variable is coded as a String variable). Select Continue.

    <img src='{{ '/assets/images/PCCF_A_022.png' | relative_url }}' alt="A pop-up titled: Select cases: If. On the left is a list of variables. SLI is selected. On the right is an expression box. Inside the box reads: SLI = '1' " title='' width='80%' height='457' />

    Under Output, choose Copy selected cases to a new dataset. Call it PCCF\_SLI. Select OK.

    <img src='{{ '/assets/images/PCCF_A_023.png' | relative_url }}' alt="A pop-up titled: Select cases. On the right is a box titled: Select. The option 'If condition is satisfied' is selected. There is a button underneath that reads 'If...' Next to the button it says: SLI = '1'. Underneath is a box titled: Output. The option Copy dataset to a new dataset is selected. The Dataset name is set to PCCF_SLI." title='' width='75%' height='627' />

    If you examine the new dataset PCCF\_SLI, you’ll notice there are now roughly half as many records (rows). Save this new dataset, we will work with it from now on. You can close the original PCCF file.

7. Now we are ready to merge the two files. We will show the steps to do this using the Merge dialog in the SPSS GUI. However, this dialog is confusingly organized and does not provide all the merge options that are actually available in SPSS. For that reason, you may wish to consider performing merges in SPSS using SPSS syntax (code). The steps to do this are located in the final appendix of this guide (called ‘SPSS code for merges’).

    To do this using the Merge dialog: from within the PCCF\_SLI dataset, choose Data \> Merge Files \> Add Variables…

    <img src='{{ '/assets/images/PCCF_A_024.png' | relative_url }}' alt='On the toolbar, Data is selected. There is a drop-down menu. Merge Files is selected. There is a menu from there. Add Variables is selected.' title='' width='75%' height='891' />

    Next select your own dataset, which should be listed as an open dataset. Select Continue.

    <img src='{{ '/assets/images/PCCF_A_025.png' | relative_url }}' alt='A pop-up titled: Add Variables to PCCF_SLI.sav[Dataset4]. The pop-up reads: Select a dataset from the list of open datasets or from a file to merge with the active dataset. The option An open dataset is selected. The file My_dataset.sav[Dataset1] is selected. ' title='' width='80%' height='334' />

    In the next window, on the Merge Method tab, select “One\-to\-many merge based on key values”. For Select Lookup Table, select whichever one represents the sample dataset (the dataset numbers will vary depending on whether you have closed and opened your data files multiple times during your session). Select Sort files by key values before merging. Because each dataset has a column named PC, SPSS will have already populated the variable PC as the key variable.

    <img src='{{ '/assets/images/PCCF_A_026.png' | relative_url }}' alt='A pop-up titled: Add Variables from Dataset1. The tab Merge Method is selected. Underneath the option One-to-many merge based on key values is selected. Underneath is a box that reads: Select Look-up Table. DataSet1 is selected. Underneath reads: For a merge based on key values, files must be sorted in order of the key values. The option Sort files by key values before merging is selected. Underneath is a box titled: Key Variables. Inside the box the key variable PC is selected. ' title='' width='55%' height='664' />

    Click on the Variables tab at the top. Let’s remove some extraneous PCCF columns at this point. Let’s say you are only interested in census tracts and dissemination areas (we already know all our data is within Toronto, so any larger geographies aren’t very helpful to us). Use Shift\+select to highlight all of the variables in the Included box, then click the arrow to move them over to the Excluded box.

    <img src='{{ '/assets/images/PCCF_A_027.png' | relative_url }}' alt='A pop-up titled: Add Variables from Dataset1. The Variables tab is selected. On the right is a box titled: Included Variables. All variables are selected.' title='' width='55%' height='707' />

    Now choose the variables CTname, DAuid, SLI and Age, and move them back over to the Included Variables box. Select OK.

    <img src='{{ '/assets/images/PCCF_A_028.png' | relative_url }}' alt='A pop-up titled: Add Variables from Dataset1. The Variables tab is selected. On the left is a box titled: Excluded Variables. There is a list of variables in the box. On the left is a box titled: Included Variables. The variables inside the Included Variables box are: CTname; DAuid; SLI; Age.' title='' width='55%' height='735' />

    Your merge is now complete. You’ll notice that initially there appear to be no values in the Age column. This is because we only had Age values for 50 out of the 1\.8 million postal codes that are in this file. We need to remove the extraneous postal codes from the file now, so we are left with only our own postal codes of interest.

    In the Data menu, choose Select Cases. Choose If condition is satisfied, then select the If… button. In the expression builder box, type the following statement: NOT(SYSMIS(Age)). This should select all rows where the age value is not missing (i.e. all those which have an age value). **NOTE: This will only work if you have a column in your dataset where there are values in every cell (no missing values). If that is not the case, you will need to perform your merge using SPSS syntax instead – see the code sample included in the appendix at the end of this guide (called ‘SPSS code for merges’).** If you have a column of data without missing values, you can continue with these steps.

    Select Continue.

    <img src='{{ '/assets/images/PCCF_A_029.png' | relative_url }}' alt='A pop-up titled: Select Cases: If. There is a text box on the top right. Inside the box reads: NOT(SYSMIS(Age))' title='' width='80%' height='490' />

    Choose Copy selected cases to a new dataset, and give it the name PCCF\_Merged. (You could also choose to Delete the unselected cases from your existing dataset, but only do this if you are very confident your expression will do what you expect it to!). Select OK.

    <img src='{{ '/assets/images/PCCF_A_030.png' | relative_url }}' alt='A pop-up titled: Select Cases. On the right is a box titled: Select. Within the box, the option If condition is satisfied is selected. Underneath is a button labelled If... Beside the button, text reads: NOT(SYSMIS(Age)). Underneath the Select box is a box titled: Output. The Copy selected cases to a new dataset option is selected. Dataset name is set to: PCCF_Merged' title='' width='65%' height='689' />

    Ta da! You now have your original data columns plus the codes for the census tract and the dissemination area that matches your postal codes of interest. In the next part of this tutorial, we will use the DAuid to pull in some census data to enrich this dataset.

    <img src='{{ '/assets/images/PCCF_A_031.png' | relative_url }}' alt='A dataset is open in IBM SPSS Statistics Data Editor. The dataset has five columns: PC; CTname; DAuid; SLI; Age. ' title='' width='90%' height='716' />

    Save this data file as PCCF\_Merged.sav.

**Technique:** [Quantitative Data Analysis](https://mdlutoronto.github.io/tutorials-search/?technique=Quantitative+Data+Analysis) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R), [SAS](https://mdlutoronto.github.io/tutorials-search/?tool=SAS), [SPSS](https://mdlutoronto.github.io/tutorials-search/?tool=SPSS) \| **Data Format:** [Microdata](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Microdata)


