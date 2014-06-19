Constructing Master List of Colleges & Data
=========================================

### Introduction
The purpose of this project was to:   
1) Create a more complete list of schools,  
2) Collect more data for each school for use in the mode, and  
3) Reconcile the previous list of schools to the new list.

### Goals:
* Establish reliable sources of data
* Discern a unique and complete ID(s)
* Collect as many accredidated colleges by volume 
* Append SAT/ACT, graduation and retention rates
* Append debt, and default rate data

### Getting Started
######Install dependencies:  
`pip install -r requirements.txt`

###Procedure:
#####Establishing sources of data & IDs
We gathered 6 sources that were publicly available:  
* IPEDS (Integrated Postsecondary Education Data System) Data Center from NCES (National Center for Education Statistics) 
http://nces.ed.gov/ipeds/datacenter/
Supplemented by College Navigator
http://nces.ed.gov/collegenavigator/
* Freebase /education Domain & IPEDS Namespace
http://www.freebase.com/education/educational_institution 
http://www.freebase.com/authority/nces/ipeds
* Database of Accredidated Postsecondary Institutions and Programs
http://ope.ed.gov/accreditation/
* Payscale College Salary Report   
http://www.payscale.com/college-salary-report-2014/full-list-of-schools
* CollegeInSight Graduates Debt
http://college-insight.org/#explore/go&h=44b136f4d155362e46d5da65ab244409
* Three-year Official Cohort Default Rates for Schools (ed.gov)
http://www2.ed.gov/offices/OSFAP/defaultmanagement/cdr.html

Four sources of IDs were collected: the IPEDS IDs, OPE IDs, Department of Education IDs, and Freebase IDs. Though each source provides an extended list of schools and more data, the IPEDS ID was chosen as the main ID. The IPEDS ID, provided by NCES, was unique to each university and was the most complete. OPE IDs were unique to each campus (with the main campus's 6-digit ID ending in 00), but were not as comprehensive. 

Considering the three most complete sources - IPEDS, Freebase, and DoE Accredidation, no one data set was a strict subset of another. Due to different IDs, years of recording, and accrediation measures, each set had colleges not contained in others. To construct the master list, the Freebase list and then the DoE tables were outer-joined on the IPEDS ID to the IPEDS data to create the largest set.

###### IPEDS
Download from Data Center:   
Select "Download Custom Data Files"   
Click "Select" to get all institutions   
Use drop-downs and search to select variables   
Download as CSV   

At the time, the latest set available for download was 2012 data. However, the College Navigator uses the most updated data, from 2013-2014. In order to collect a small set of data from colleges that were found in Freebase/DoE lists but not in IPEDS 2012, the College Navigator site was scraped for information in HTML.

To use the College Navigator, search by institution name in the search box, or use the IPEDS ID in the following url: http://nces.ed.gov/collegenavigator/?id=xxxxxx, where 'xxxxxx' is the 6-digit IPEDS ID.
##### SAT/ACT, 4-Year Degree
In the 2012 data set, SAT data was provided as 25th and 75th percentiles, for each of the three categories. ACT data was also provided as 25th and 75th percentiles, for the four categories and as the Composite score. Note that colleges may submit one or the other test, or both.  
Noting the significance 

####Notes:
Majors: http://nces.ed.gov/ipeds/cipcode/resources.aspx?y=55
