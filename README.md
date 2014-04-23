FDOP2013
========

Fire Danger Operating Plan 2012


<h3>Getting Started</h3>
<hr>1.	Download FireFamilyPlus from:

http://www.firemodels.org/index.php/firefamilyplus-software/firefamilyplus-downloads

2.	Create a Database:
File> New> Name your Database and save it to an appropriate location> Give it a description.
Station Catalog
1.	Download station catalog information from:

https://fam.nwcg.gov/fam-web/kcfast/mnmenu.htm

Select Weather> Station Catalog> Station Information> Select ‘Single Station’> Enter in Station ID> Select Output Destination to “Send file to FTP site”> Save .txt file to appropriate folder
2.	Importing the Station Catalog:
-On the Data Menu> Select Import> Select WIMS Station Catalogs> Select the appropriate .txt file> 
-From the data Menu> Select Stations> This will show you which stations are available for you to work with in the data base and you should see the station catalog you have just imported.  From this screen you can highlight your station and select ‘Edit’.  This will show you all the attributes of your station.  (You should make note of the USFS region – you will need to know that value for when you download your fire data).     
- In your working set dialog box under ‘SIG/Station’> Select your station from the drop down menu. 
Weather
1.	Download weather data from:
https://fam.nwcg.gov/fam-web/kcfast/mnmenu.htm
Select Weather> Data Extract> Historical> Enter in Station ID and date range> Select ‘Raw Datafile – 1998 Data Format> Save .fw9 file to appropriate folder

2.	Importing the  Weather Data:
-From the Data Menu> Select Import> Select Old Wx Import> The Selected Fields should include: Station ID, Obs Date, Obs Time, Obs Type, OMC10, RH, and Windspeed> Select the StationID Box> Select Overwrite Duplicates.  
UPDATED: Select Data> Import> Generic Wx> upload your .fw9 files.


3.	Missing Records:  
-Once you import your weather data> Select from the Weather Menu> ‘View Observations’> ‘Daily’> go through to look for missing SOW’s or missing records.  
-If you have missing information you need to go to: http://www.raws.dri.edu/index.html to down load the missing data.  Select CA> select your RAWS site from the list to the left or select the station on the map> Select ‘Data Lister’ from the list on the left hand side of the screen> Specify the dates in which you are missing data > If you are downloading more than 30 days worth of data you need to enter in a PW (for Southern CA it is wrcc23)> Save this as a .txt file to the appropriate folder.   
In my situation, there were so many non-consecutive missing dates that I downloaded data for the entire 10 years rather than many multiple single date files.  The directions that follow will explain how to edit and filter out only the records you need.     
4.	Editing Weather data
-Open the .fw9 file you downloaded in Notepad++. 
-Remove all html code from the bottom of the file and the top of the file. 
-Remove colons from the beginning of the first two strings of line.  (This is to help format and line up the data correctly for import back into FFP)
-If there are empty lines between string of data: Find and Replace> Find: \n\r\ Replace: [nothing] >Extended Search Mode
-To isolate ‘O’ :  Find and Replace> ‘Mark’ tab> Find What: 00R> Check the bookmark option> Mark All> Search> Bookmark> Remove Bookmarked lines
- To replace first four letters with station ID: Find and Replace> Find What: _ _XXXX> Replace with:  ######
-Remove the top two strings of text that were used to format the data.
-Save as a .txt file for import. 

5.	Importing Edited Weather data
-From the Data Menu> Select ‘Import’> Select ‘New FW9 Files’> Select your .txt file> Import. 

6.	Searching for Anomalies in the data
- Once you have a complete weather database it is important to examine the data for anything that may not be accurate.  Poor quality data is due to either human error in entering in daily weather observations or mechanical errors at the RAWS stations itself.  Things to look out for:
- Do the values make sense? For example, if the temperature was recorded being 100 degrees in December, there may be a problem.   
- Repetitive values for any variable.  In my case there was an occurrence of a Relative Humidity of 4 for about three months straight.  While this may be possible, it is highly unlikely that this is accurate. 
- Are there any missing SOW (State of the Weather)?  If so, consider the time of the year and the SOW of days before and after the date you are determining to give you insight as to what the SOW for that day is likely to be.  
- If you find data that is not accurate or that which yield values that seem to be outrageous you can use some of the resources below to fill in the gaps and/or verify or edit the values.  If there is no data to fix the issues you find, you will have to omit the records.  If this happens to be the case state in the FDOP that there was an omissions of records due to poor quality data.     

<h4>Fire</h4>

<hr>1.	Download fire data from:  

https://fam.nwcg.gov/fam-web/kcfast/mnmenu.htm

Select Fire> Standard Extract> Enter in Region/Forest and date range

2.	Importing Fire Data:
-From the Data Menu> import>Select from drop down menu ‘USFS’> Select ‘Raw Files’> Select your .raw file
-Region:Unit:Discovery Date:Fire Number:Acerage:Fire Name:Cause:Latitude:Longitude

3.	Obtain LE-66 Data:
-Create an excel spread sheet for your 10 years worth of data.
-The LE-66 data is stored in on the (F:) drive so you need to be connected to the VPN in order to get access. 
	(F:)>data>prevent>Prevention>STATS3421

4.	Preparing LE-66 Data:
-Create columns for date, incident number, cause, comments, latitude, longitude and copy and populate the fields. 
- Save this file as a .txt for import. 
- Make sure the date has been formatted correctly YYYYMMDD (right click>format cells)
- Change all cause codes (refer to FDOP for conversion chart)
-Make sure all the years are correct.  In my experience, I found incidents for 2005 in the 2004 LE-66 stat document, so correct as necessary.   
-Cause will be represented by a letter, number, or a combination of both.  For the years 2009-2012 there is a document on the (f:) that will have a description for each letter/number value.
	(F:)>data>prevent>Prevention>STATS3421>2009 and after log cover causes.doc
  I created another spread sheet in order to edit just the data from 2009-2012.  Once I had this data isolated I performed a filter function on the ‘cause’ column.  Using this function I isolated each variable and replaced it with the cause description.  For the data 2002-2008 refer to 
	(F:)>data>prevent>Prevention>STATS3421>log cover causes.doc
when performing your filter to find and replace the cause variables. 

5.	Additional Editing for LE-66 Data:
-If you do not need your lat and long data to be in DD, then disregard the following instructions..
-The lat and long data I gathered from the LE-66 STATS were in different formats i.e. DMS, DM, and were also in different variations of each format.
-I created ‘working data’ columns of lat and long in order to apply excel formulas to convert these formats all into DD (the format in which my mapping platform of choice required for import).  
	-For DMS ## ## ##:	
=MID(B23,FIND(" ",B23)+2,2)/3600+MID(B23,FIND(" ",B23)+1,2)/60+LEFT(B23,FIND(" ",B23)-1)
	-For DMS ## ##’##”:
	=MID(A1,FIND("'",A1)+2,2)/3600+MID(A1,FIND(" ",A1)+1,2)/60+LEFT(A1,FIND(" ",A1)-1)
	-For MD ## ##.##:
	=MID(A1,FIND(" ",A1)+1,2)/60+Left(A1,FIND(" ",A1)-1)
-Once all the data has been converted to DD I made sure that all the Longitude values were (-). 
-I then created final columns for both lat and long and copied and pasted only the values from my lat and long ‘working data’ columns into my lat and long ‘final data’.

6.	Using Fire Reports
-Using Internet Explorer go to :
http://webrpt.fire.ca.gov/InfoViewApp/logon.aspx
Log on with: sluecc; pinnerMAY06
Log on with:slurpt; broken9b
-Navigate to: MyInbox> Public Folders> CAD Shared Reports> Click on the FC34 Reports> Select: FC34 Detail-All-Seg (Incident Number)
-Enter in YYYY###### to look up each individual fire report. Verify date, author, lat, and long.
-save as a .csv for import.

7.	Creating an Excel from Ignition Data

8.	Populating the ‘SubUnit’ Field
Export your fire data from FF+ as a shapefile. Be sure to include ‘SubUnit’ as a field during export. Import your ignition and FDRA .shps into arc. > Open the Ignition attributes table and create a text field called ‘SubUnit’ > In the ‘Select’ menu chose ‘Select by Location’.
	I want to: ‘select features from’
	The following layer(s): [your ignition data]
	That: ‘are completely within’
	The features in this layer: [your FDRA]
In your attribute table select ‘Show: selected’ > start an editing session> right click on the SubUnit field and select ‘Field Calculator’> select ‘string’> in double quotes enter in the name of this subunit field. Complete this same process for each FDRA. If there are ignitions that fall outside of your FDRAs clear all selections> select all the data> from your Selection by Location dialog select ‘remove from current selection’ and remove all FDRAs that you just assigned. The remaining ignitions can be assigned ‘Other’ via the process described above. 
Save all edits and close editing session. 

Open the ignition shapefile in Quantum. Select the ‘Table Manager’ tab. Arrange the fields in the appropriate order (i.e. region, unit, discovery date, fire number, acreage, fire name, cause, lat, long, subunit) and delete any fields that have been created. Save this as a .csv. 

Open your CSV. If your date appear to be ######## right click on the DiscoveryDate column and select ‘Format Cells’. Select ‘date’ from the menu on the left. Select the default date format (##/##/####). Save the csv. 

Import your CSV back into FF+ and be sure to include ‘SubUnit’ at the end of your field items to import and also verify that the date format matches the format you adjusted your ‘DiscoveryDate’ values in the CSV.
	

<h4>Stats Graphs</h4>
<hr>1.	Fire Occurrence graphs:
a.	One including All FDRAs: Coastal, Inland, and Other
b.	Coastal FDRA
c.	Inland FDRA
i.	‘Fires’>’Summary’>’Working Set’>Select the ‘CAL FIRE’ Tab>Region ‘3RSS’> Unit ‘SLU San Luis Obispo’>Sub Unit ‘COASTAL Coastal’> ‘Ok’
1.	Annual Filter should be set for the entire calendar year for these graphs. 
ii.	Screen Shot the graph and insert into FDOP
iii.	Complete the Steps above for each Sub Unit
All fire occurrence graphs need to be based on the entire calendar year.
2.	Determining Thresholds:  
For each FDRA the thresholds need to be determined.  The program will do this for you however; you need to confirm that the default percentage values for the thresholds are indeed accurate after all climatology statistics graphs have been run.  The given percentages should coincide with the data output of the fire analysis.  
  
3.	Three indice graphs for each FDRA
a.	ERC displaying: min, max, avg 
i.	‘Weather’>’Climatology’>Select the ‘Stats Graph’ box for the Variable ‘Energy Release Component’>’Run’
ii.	Maximize the left portion of the screen 
iii.	Select ‘Options’> ‘Graph Options’> Select the ‘Lines at Average’ tab> Deselect the ‘Mins’ and ‘Maxs’>’Apply’
iv.	Screen Shot the Graph and insert into the FDOP
b.	BI displaying: min, max, avg
i.	‘Weather’>’Climatology’>Select the ‘Stats Graph’ box for the Variable ‘Burning Index’>’Run’
ii.	Maximize the left portion of the screen 
iii.	Select ‘Options’> ‘Graph Options’> Select the ‘Lines at Average’ tab> Deselect the ‘Mins’ and ‘Maxs’>’Apply’
iv.	Screen Shot the Graph and insert into the FDOP
c.	ERC displaying:  a year in which the ERC threshold before the onset of fire season (May 15th) and a year in which the ERC threshold had not been obtained until after the start of fire season.   
i.	‘Weather’>’Climatology’>Select the ‘Stats Graph’ box for the Variable ‘Energy Release Component’>Change the ‘CP #2’ value from 97 to 38 (the point at which an ERC of 200 occurs)>’Run’
ii.	Maximize the left portion of the screen
iii.	Select ‘Options’> ‘Graph Options’> Select the ‘Lines at Average’ tab> Deselect the ‘Mins’ and ‘Maxs’>’Apply’
iv.	The onset of fire season is illustrated here when the ‘Average’ line crosses the 38th percentile threshold.  The purpose of this graph is to show that fire season can start well before the traditional start (May 15th) of fire season and conversely, that fire season sometimes starts after the common start date.  
v.	Select ‘Options’>’Overlays’>’New’>  Toggle between the years and find the year that has the earliest start date (When it crosses the 38th percentile threshold) and which has the latest start date.  Give each a unique color, a line width of 3, and make it a solid line. Select ‘Ok’.  
vi.	Screen Shot the Graph and insert into the FDOP
4.	Decision Points for Dispatch Level 
a.	Decision points should be set using BI. 
i.	Select the ‘A’ on the ribbon at the top of the screen> run the operation with default values selected> Click on the ‘Fires Probability Analysis’ Window> Select ‘View’> ‘Decision Points’> Delete 2 records so you are left with 3 classes
ii.	Set the first class to 0, set the second class to the value at which fires begin to take off.  Visually, this is when there appears to be a large jump from low to high.  The last class should be set at the BI value where the crest of the graph is no longer in a drastic incline and starts to plateau. The second decision class created should hold the greatest number of fires whereas the first and last should contain the least amount of fire occurrence.  
iii.	When these levels have been adjusted to accommodate the fire data select ‘Apply’> Adjust the screen so that all graphs fit appropriately>Screen shot and insert into the FDOP. 
iv.	Adjust the ‘Dispatch Level: Fire Family Plus Analysis Factors and Determinations’ Table (Specifically, the ‘Index Break Points’ section).  
NOTE: All Decision Point graphs need to be based on Fire season (May1-Oct 31), not the calendar year.
5.	When updating numbers and percent values in FDOP:
a.	Follow instructions to look at fire occurrence chart> Select ‘Options’> ‘View Graph Data’
b.	This ‘Fire Occurrence Summary’ page will provide the exact values behind all the graphics illustrated for fire occurrence. 
Staffing Level
Staffing Level is an important component of the Adjective Fire Danger Rating and is calculated in WIMS.  It is a way for us to break up the BI continuum based on percentile to make it more useful.  Staffing level, along with Ignition Component, is a way for describe relative fire risk. 

1.	Staffing Level will be determined using fuel model G. 
This is determined by running different fuel models against fire and weather history data.  When running the different fuel models with your data you should choose the fuel model that yields the ideal statistical output. The ideal statistical output includes a BI of at least 100, all graphs should be a bell curve, the data should have a linear distribution across the spectrum, and no graphs should be inverted.  If you find a fuel model that yields these results, it means that fuel model is the best for fit for your data set and should be the fuel model you should used in the analysis of staffing level. In this analysis, fuel model G (which also happens to be the standard fuel model) was determined to be the best fit for the data set. 

2.	Select the appropriate ‘SIG/Station’ , ‘Data years’, ‘Annual Filter’: May 1 – Oct 31 > Select ‘Fires’ > ‘Fire Analysis’> Select: Large Fire (Acres):8, Multi Dire Dat (Fires): 3, Select ‘BI’ from the drop down, check the box for ‘Conditional Probability Analysis-FireDays Only>  ‘OK’> Select the ‘Fires Probability Analysis’ Window> Select ‘View’ > ‘Decision Points’>  close the ‘Class Lower Limits” Window  
3.	The default ‘Class BI Ranges’ will be the values entered into the “Staffing Level: Break Points chart”.  Round the Values for the chart.


<h4>Preparedness Level</h4>
<hr>1.	The point at which large fires start to take off based on ERC.  
2.	Select appropriate ‘SIG/Station’> Data Years> Annual Filter set for fire season> Select ‘Fires’> ‘Fire Analysis’> Large Fires (Acres):8> Multi Fire Day (Fire):3> Select ERC from the drop down> Check the ‘Conditional Probability Analysis Fire Days Only’ box> 
-	Close the ‘Cumulative Fires Analysis’ Window. Looking at the ‘Fires Probability Analysis’ you can see when large fires start to take off as illustrated by the magenta line with the open square (Large Fire Day). When the data indicates an increase in occurrence of large fires, this is the point at with the threshold should be placed. Click directly on the pink square to view the value. The X-value in the bottom right hand corner of the screen in the ERC threshold value that will be recorded in FDOP.  In order to verify this threshold value:
-	Select ‘View’> ‘Decision Points’> In the ‘Class Lower Limits’ window delete all but two of the threshold classes> Make Class 1 and value of ‘0’ and Class 2 the threshold X-value> Select ‘Apply’
-	In the ERC Percentile Graph the threshold line should be drawn a the point in which the large fire data starts to rapidly increase. 
-	In the ERC Probability Graph directly below, the threshold line should be drawn through the data point that you clicked before, which is the point at which large fires start to increase. 
-	If the threshold line is not drawn at the necessary position on the graphs adjust the threshold value in the ‘Class Lower Limits’ window to determine the appropriate preparedness threshold value.
3.	Complete this process for both FDRAs and record the appropriate threshold value in the Preparedness Level chart. 

<h4>Pocket Cards</h4>
<hr>A pocket card must be created for each FDRA, which will display the three largest fires.  
1.	For the Inland FDRA, instead of using the largest fires by acreage we used the top three most well known fires in San Luis County.  This is because these fires are the events that resonate with the SLU.  
Select ‘Weather’> ‘Pocket Card’> 
Fire Danger Area: ‘Inland FDRA’ 
Area Locator Bitmap is located: X://projectdata>master_data>Inland.bmp 
Years to Remember: 1950 – Present
Area Locator Bullets: Line 1 – Interior Valley, Line 2 – Las Tablas RAWS, Line 3 – La Panza RAWS



Fires: 
Fire Name	Date
.	7/1/1985
.	8/18/1994
.	8/15/1996
Fire Name is left Blank because the symbology is cluttered and not legible on the graph.  Once the graph is complete, Photoshop/edit the names in.  (I did so using paint)
Past Experience Text:
Pilitas 1 fire 7/1/1985 burned 84,271 acres
Highway 41 fire 8/18/1995 burned 50,729 acres
Highway 58 fire 8/15/1996 burned 33,094 acres
(This bit of text can be typed into the Pocket card window.  All other descriptive text and logo was edited in using paint.  Unless a fire occurs that exceeds one of these three major fires, these are the fires that are to be displayed on the Inland Pocket Card)
2.	The Coastal FDRA pocket card displayed the top three largest fires in that FDRA. 
3.	The bit map for each FDRA is already created:
X://projectdata>master_data>Coastal.bmp
4.	Under the ‘Fire Danger Area’ enter in the region (i.e. coastal or inland), the RAWS located in the region, 

<h4>Updating the FDOP Annually</h4>
<hr>1.	Enter in all fire and weather records for the past year
2.	Run the above statistical graphics to produce new charts.  These charts shouldn’t change too drastically unless there were exceptionally large or small fires, or drastically hot or cold days.  
a.	Fire Occurrence Graphs will need to be updated.  All descriptive text and percentages need to be adjusted accordingly.  
3.	Climatology Graphs of Temperature and Rainfall.  These can be obtained from:
http://www.weather.com/weather/wxclimatology/monthly/graph/USCA0045
http://www.weather.com/weather/wxclimatology/monthly/graph/USCA0842

4.	Tables in the FDOP that may need to be updated depending on new data include: 
a.	10 Largest Fires Recorded in the Inland FDRA
b.	Historic Fires for Reference Depicted on the Inland FDRA Pocket Card
c.	10 Largest Fires Recorded in the Coastal FDRA
d.	Historic Fires for Reference Depicted on the Coastal FDRA Pocket Card 
5.	If the information in the station catalog in WIMS changes or is updated a new screenshot should be included in place of the current.  
6.	If the conditions of the RAWS change, it should be noted in the ‘RAWS Site Description and Photos’ section.
7.	All pocket cards in the appendix need to be updated.  
Cause Code Conversion Chart:
Cause Code Conversion Chart: CAL FIRE Cause Code to Federal Cause Code 
Cause Code Converter


<h3>CDF Cause Code	Cause Description	Federal Cause Code</h3>


0	Unknown         9<br/>
1	Undetermined	9<br/>
2	Lightning	1<br/>
3	Campfire	4<br/>
4	Smoking	        3<br/>
5	Debris Burning	5<br/>
6	Arson	        7<br/>
7	Equipment Use	2<br/>
8	Playing/Fire	8<br/>
9	Miscellaneous	9<br/>
10	Vehicle	        2<br/>
11	Railroad	6<br/>
12	Powerline	2<br/>


(Obtained from CAL FIRE intranet)
In preparation for statistical analysis, the CAL FIRE cause code must be translated to the federal cause code for use in Fire Family Plus software.  The char above outlines the cause code conversion from CDF to Federal cause codes.  
