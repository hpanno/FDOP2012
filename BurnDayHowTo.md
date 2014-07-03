###Burn Day How To
---

This analysis can not be completed on SIGS. This has to be done on each weather station. 

######Wind Speed and Relative Humidity Graphs 
1. Set annual filter to April 1-June 30. 
2. Weather > Dinurla Graphs> Select 'Wind Speed' and 'Relative Humidity' from the Varialble options> 'OK' 
3. Capture and save graphics.


######Setting Thresholds 
1. With the same settings as above, select the 'Fire Associations' button. Parameters should be set as follows: 
    - Large Fires: 8 
    - MultiFire Days: 3 
    - Fire Cause: All 
    - Analysis Type: Both 
    - Check the box for 'Conditional Probability Analysis - FireDays Only 
    - Analysis Variable: (Run this Analysis twice for each variable)
    - Wind Speed 
    - Relative Humidity 
    - 'OK' 
2. Select the 'Fires Probability Analysis' Window > Select 'View'> 'Decision Points'> Delete 3 class rows (should only work with 2 classes) 
    - When setting thresholds for Wind Speed Class 1 will be '0' and Class 2 is the threshold left to discretion. 
    - When setting threshold for Relative Humidity Class 1 will be the threshol left to disretion and Class 2 will be '0. The point at which decisions are made should be placed at points where fire days, multi fire days, and large fire days begin to occur. 
3. Capture and save graphics.



######Gathering Statistics Table Data 
1. Set annual filter to reflect the entire calendar year. 
2. Select 'Weather' > 'Climatology' > Select the box for Stats Table for the Wind Speed Variable> 'Run' > Scroll to the bottom of the table and record the values for 'Mean', 'High by Year', and 'Average High'.


######Merging Variables 
Climatology> Stats Graphs> Options> Merge


######Wind Rose 
Weather > Winds> Set annual filter for April 1 - June 30 
number of days and % in the defined working set with 1 or more obs. 
Obs: the # of total observations and % of total # of possible observations @ 24 hours obs.
