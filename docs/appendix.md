---
title: Appendix
parent: PCCF Guide
nav_order: 3
layout: default
---

Appendix
--------
[SAS Code](#sas-code)  
[R Code](#r-code)  
[Stata Code](#stata-code)  
[Python Code](#python-code)  
[SPSS Code](#spss-code-for-merges)

The SAS, R, Stata and Python code to accomplish the steps in part A and part B can be found below. The datasets used in the code are [My\_dataset.csv](https://maps.library.utoronto.ca/workshops/PCCF/My_dataset.csv), the PCCF file and the census file. You need to follow the instructions in the guide to download the PCCF and the census datasets.

Key points to keep in mind about these statistical programs:

* R is case sensitive
* SAS is NOT case sensitive. Each line OF CODE ends with a semi\-colon.
* Stata is case sensitive

### SAS CODE

```
* PCCF GUIDE;

* Instruction: 
*          - Replace the data file paths below with the respective file paths on your computer;

* Part A: Use the PCCF to assign standard geographic data to your postal codes;

* STEP 1: Import datasets;

* Import your dataset;
proc import out=work.mydataset
                           datafile="H:\PCCF Guide\Data\My_dataset.csv" 
                           dbms=csv replace;
         getnames=yes;
         datarow=2;
run;

* Import the PCCF file;
proc import out=work.pccf 
                           datafile="H:\PCCF Guide\Data\pccfNat_fccpNat_082021csv.csv"
                           dbms=csv replace;
         getnames=yes;
         datarow=2;
run;

* STEP 2: Prepare for merge;

* Keep only the postal codes that have a Single Link Indicator (SLI) value of 1 in pccf; 
data pccf; set pccf; if sli=1; run;

* Rename the postal code variables in mydataset and pccf pcode;
data mydataset; set mydataset; rename postal_code = pcode; run;
data pccf; set pccf; rename pc = pcode; run;

* Remove the single space in pcode in mydataset; 
data mydataset; set mydataset; pcode = compress(pcode); run;

* STEP 3: Merge datasets mydataset and pccf;

* Sort each dataset by the pcode variable;
proc sort data=mydataset; by pcode; run;
proc sort data=pccf; by pcode; run;

* Combine the two datasets by matching the pcode variable and only keep your postal codes;
data mydatasetpccf;
        merge mydataset (in=x) pccf;
        by pcode;
        if x=1;
run;

* STEP 4: Export mydatsetpccf;

* Create a libname to point to your output folder;
libname folder "H:\PCCF Guide\Data";

* Save mydatasetpccf as a SAS dataset in your output folder;
data folder.mydatasetpccf; set work.mydatasetpccf; run; 

* Export mydatasetpccf to CSV in your output folder;
proc export data=work.mydatasetpccf
                            outfile="H:\PCCF Guide\Data\mydatasetpccf.csv"
                            dbms=csv replace;
run;

* Part B: Adding census data; 

* Step 1: Import datasets;

* Import mydatasetpccf if you haven't run Part A;
proc import out=work.mydatasetpccf 
                           datafile="H:\PCCF Guide\Data\mydatasetpccf.csv" 
                           dbms=csv replace;
  getnames=yes;
  datarow=2;
run;

* Import the census data file;
proc import out=work.census
                           datafile="H:\PCCF Guide\Data\census2016.csv" 
                           dbms=csv replace;
  getnames=yes;
  datarow=2;
run;

* Step 2: Prepare for merge;

* Rename the col0 variable to dauid in census to match mydatasetpccf;
data census; set census; rename col0 = dauid; run; 

* Convert the data type of dauid from character to numeric in census to match mydatasetpccf;
data census; set census; dauid2 = input(dauid, 10.); drop dauid; rename dauid2=dauid; run;

* Step 3: Merge datasets mydatasetpccf and census;

* Sort each dataset by dauid;
proc sort data=mydatasetpccf; by dauid; run; 
proc sort data=census; by dauid; run; 

* Combine the two datasets by matching the dauid variable and only keep your DAs;
data mydataset2;
        merge mydatasetpccf(in=x) census;
        by dauid;
        if x=1;
run; 

* STEP 4: Export mydataset2; 

* Create a libname to point to your output folder;
libname folder "H:\PCCF Guide\Data";

* Save mydataset2 as a SAS dataset in your output folder;
data folder.mydataset2; set work.mydataset2; run;

* Export mydataset2 to CSV in your output folder;
proc export data=work.mydataset2
                           outfile="H:\PCCF Guide\Data\My_dataset2.csv"
                           dbms=csv replace;
run;
```
 

### R Code

```
# PCCF GUIDE
# Instruction: 
# - Replace the data file paths below with the respective file paths on your computer.

# Part A: Use the PCCF to assign standard geographic data to your postal codes

# STEP 1: Import datasets
# Note: Change all backslashes to forward slashes
# Import your dataset
mydataset <- read.csv("H:/PCCF Guide/Data/My_dataset.csv")
# Import the PCCF file
pccf <- read.csv("H:/PCCF Guide/Data/pccfNat_fccpNat_082021csv.csv")

# STEP 2: Prepare for merge
# Keep only the postal codes that have a Single Link Indicator (SLI) value of 1 in pccf
pccf <- subset(pccf, SLI==1)
# Rename the postal code variables in mydataset and pccf pcode
names(mydataset)[names(mydataset)=="Postal.Code"] <- "pcode"
names(pccf)[1] <- "pcode"
# Remove the single space in pcode in mydataset
mydataset$pcode <- gsub(" ", "", mydataset$pcode) 

# STEP 3: Merge datasets mydataset and pccf
# Combine the two datasets by matching the pcode variable and only keep your postal codes
mydatasetpccf <- merge(mydataset, pccf, by="pcode", all.x=TRUE)

# STEP 4: Export mydatsetpccf 
# Export mydatasetpccf to CSV in your output folder
write.csv(mydatasetpccf,"H:/PCCF Guide/Data/mydatasetpccf.csv", row.names=FALSE)

# PART B: Adding census data

# Step 1: Import datasets
# Note: Change all backslashes to forward slashes
# Import mydatasetpccf if you haven't run Part A
mydatasetpccf <- read.csv("H:/PCCF Guide/Data/mydatasetpccf.csv")
# Import the census data file
census <- read.csv("H:/PCCF Guide/Data/census2016.csv")

# Step 2: Prepare for merge
# Rename the DAuid and COL0 variables in mydatasetpccf and census dauid
names(mydatasetpccf)[names(mydatasetpccf)=="DAuid"] <- "dauid"
names(census)[names(census)=="COL0"] <- "dauid"

# Step 3: Merge datasets mydatasetpccf and census
# Combine the two datasets by matching the dauid variable and only keep your DAs
mydataset2 <- merge(mydatasetpccf, census, by="dauid", all.x=TRUE)

# STEP 4: Export mydataset2
# Export mydataset2 to CSV in your output folder
write.csv(mydataset2,"H:/PCCF Guide/Data/My_dataset2.csv", row.names=FALSE)
```


### Stata Code

```
* PCCF GUIDE

* Part A: Use the PCCF to assign standard geographic data to your postal codes

* Import your dataset
insheet using "H:\PCCF Guide\Data\My_dataset.csv", clear
* Rename the postal code variable in your dataset pcode
rename postalcode pcode
* Remove the space in pcode
replace pcode = subinstr(pcode, " ", "", .)
* Sort by pcode
sort pcode
* Save
save "H:\PCCF Guide\Data\mydataset.dta", replace

* Import the PCCF file
* Note: The following import line of code is typed over a few lines
insheet pc fsa pr cduid csduid csdname csdtype ccscode sac sactype ctname er ///
           dpl fed13uid pop_cntr_ra pop_cntr_ra_type dauid disblock rep_pt_type lat ///
           lon sli pctype comm_name dmt h_dmt birth_date ret_date po qi source ///
           pop_cntr_ra_size_class ///
           using "H:\PCCF Guide\Data\pccfNat_fccpNat_082021csv.csv", clear
* Keep only the postal codes that have a Single Link Indicator (SLI) value of 1
keep if sli==1
* Rename the postal code variable pcode in the PCCF file
rename pc pcode
* Sort by pcode
sort pcode
* Save
save "H:\PCCF Guide\Data\pccf.dta", replace

* Merge: Combine the Stata datasets mydataset and pccf and only keep your postal codes
use "H:\PCCF Guide\Data\mydataset.dta", clear
merge 1:m pcode using "H:\PCCF Guide\Data\pccf.dta"
>keep if _merge==1 | _merge==3
drop _merge
save "H:\PCCF Guide\Data\mydatasetpccf.dta", replace

* Export mydatasetpccf to CSV in your output folder
outsheet using "H:\PCCF Guide\Data\mydatasetpccf.csv", comma replace

* PART B: Adding census data

* Import the mydatasetpccf data file
use "H:\PCCF Guide\Data\mydatasetpccf.dta", clear
* Sort by dauid
sort dauid
* Save
save "H:\PCCF Guide\Data\mydatasetpccf.dta", replace

* Import the census data file
insheet using "H:/PCCF Guide/Data/census2016.csv", clear
* Rename the col0 variable dauid
rename col0 dauid
* Sort by dauid 
sort dauid
* Save
save "H:/PCCF Guide/Data/census.dta", replace

* Merge: Combine the Stata datasets mydatasetpccf and census and only keep your DAs
use "H:\PCCF Guide\Data\mydatasetpccf.dta", clear
merge 1:1 dauid using "H:\PCCF Guide\Data\census.dta"
keep if _merge==1 | _merge==3
drop _merge
save "H:\PCCF Guide\Data\My_dataset2.dta", replace

* Export My_dataset2 to CSV in your output folder
>outsheet using "H:\PCCF Guide\Data\My_dataset2.csv", comma replace
```

### Python Code

```
# PCCF GUIDE 

# Instruction: 
# - Replace the data file paths below with the respective file paths on your computer. 

# Part A: Use the PCCF to assign standard geographic data to your postal codes 

# STEP 1: Import datasets 
# Note: Change all backslashes to forward slashes 

# Import necessary Python library 
import pandas as pd 

# Import your dataset 
mydataset = pd.read_csv("H:/PCCF Guide/Data/My_dataset.csv") 

# Import the PCCF file 
pccf = pd.read_csv("H:/PCCF Guide/Data/pccfNat_fccpNat_082021csv.csv", encoding="latin-1") 

# STEP 2: Prepare for merge 

# Keep only the postal codes that have a Single Link Indicator (SLI) value of 1 in pccf 
pccf = pccf[pccf['SLI']==1] 

# Rename the postal code variables in mydataset and pccf pcode 
mydataset = mydataset.rename({'Postal Code':'pcode'}, axis=1) 
pccf = pccf.rename(columns={pccf.columns[0] : 'pcode'}) 

# Remove the single space in pcode in mydataset 
# Note: Ignore the warning import warnings 
warnings.filterwarnings("ignore") 
for index in range(0,len(mydataset)): 
 mydataset["pcode"][index] = mydataset["pcode"][index].replace(" ", "") 
warnings.resetwarnings() 

# STEP 3: Merge datasets mydataset and pccf 

# Combine the two datasets by matching the pcode variable and only keep your postal codes 
mydatasetpccf = mydataset.merge(pccf, how="left", on="pcode") 

# STEP 4: Export mydatsetpccf 

# Export mydatasetpccf to CSV in your output folder 
mydatasetpccf.to_csv("H:/PCCF Guide/Data/mydatasetpccf.csv", index=False) 

# PART B: Adding census data 

# Step 1: Import datasets 
# Note: Change all backslashes to forward slashes 

# Import mydatasetpccf if you haven't run Part A 
mydatasetpccf = pd.read_csv("H:/PCCF Guide/Data/mydatasetpccf.csv") 

# Import the census data file 
census = pd.read_csv("H:/PCCF Guide/Data/census2016.csv", encoding="latin-1") 

# Step 2: Prepare for merge 

# Rename the DAuid and COL0 variables in mydatasetpccf and census dauid 
mydatasetpccf = mydatasetpccf.rename({'DAuid':'dauid'}, axis=1)
census = census.rename({'COL0':'dauid'}, axis=1) 

# Step 3: Merge datasets mydatasetpccf and census 

# Combine the two datasets by matching the dauid variable and only keep your DAs 
mydataset2 = mydatasetpccf.merge(census, how="left", on="dauid") 

# STEP 4: Export mydataset2 

# Export mydataset2 to CSV in your output folder 
mydataset2.to_csv("H:/PCCF Guide/Data/My_dataset2.csv", index=False)
```

### SPSS code for merges

To work with SPSS syntax, first open a new Syntax editor by selecting File \> New \> Syntax.

<img src='{{ '/assets/images/PCCF_SPSS_001.png' | relative_url }}' alt='The file PCCF_SLI.sav is open in SPSS Statistics Data Editor. In the toolbar, File is selected. From the drop-down menu, New is selected, followed by Syntax.' title='' width='75%' height='651' />

A new window opens, probably called Syntax1\. This is a window that allows you to type and run SPSS syntax (lines of code). In the white area on the right, type or copy\-paste the following lines of code (replace the file path indicated in red text with the file path to wherever you have saved these files:

```
* SORT My_dataset.sav by PC.

GET FILE ='C:\My_dataset.sav'. 
SORT CASES BY PC.
SAVE OUTFILE='C:\My_dataset.sav'.
EXECUTE.

* SORT PCCF_SLI.sav by PC.
GET FILE ='C:\PCCF_SLI.sav'. 
SORT CASES BY PC.
SAVE OUTFILE='C:\PCCF_SLI.sav'.
EXECUTE.

* MERGE My_dataset.sav and PCCF_SLI.sav & KEEP only the rows in My_dataset.sav & SAVE it as PCCF_merged.sav.

MATCH FILES 
/TABLE='C:\My_dataset.sav'/IN=myresearchdata
/FILE='C:\PCCF_SLI.sav'
/BY PC. 
SELECT IF myresearchdata.
EXECUTE.
DELETE VARIABLES myresearchdata.
EXECUTE.
SAVE OUTFILE='C:\PCCF_merged.sav'
EXECUTE.
```
After the text has been entered, select all the text and click on the green triangle.

<img src='{{ '/assets/images/PCCF_SPSS_002.png' | relative_url }}' alt='A pop-up titled: Syntax 1 - IBM SPSS Statistics Editor. On the left is a text box. All text is selected. In the toolbar the cursor highlights a green triangle button that will run the selection. ' title='' width='100%' height='561' />

**Technique:** [Quantitative Data Analysis](https://mdlutoronto.github.io/tutorials-search/?technique=Quantitative+Data+Analysis) \| Tools: [R](https://mdlutoronto.github.io/tutorials-search/?tool=R), [SAS](https://mdlutoronto.github.io/tutorials-search/?tool=SAS), [SPSS](https://mdlutoronto.github.io/tutorials-search/?tool=SPSS) \| Data Format: [Microdata](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Microdata)

**Date Created:** 2023\-06\-06 **Updated:** 2023\-07\-13
