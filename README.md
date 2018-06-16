# data-jam-June-2018
data for a Houston Data Visualization Meet-up data jam

#### Lake Houston Water Quality Data

## Upfront stuff
1. The total data size of everything in this repo is large. You might want to just download the individual files in the converted files folder if you have an old computer. You might also just look at (a) only the columns in all the stations (b) only the lake stations that have similar data taken at different depths (c) cut back on the total length of time examined.
2. If you want to replicate getting this data or get and transform it yourself or see what USGS built with it and other data sources go to : https://webapps.usgs.gov/lake_houston/home/#realtime


## Folders
<b>orig_txt</b> holds the original tab deliminated text files downloaded as described in the jupyter notebook: <First format conversions.ipynb>.

<b>converted_files</b> holds the csv files created from the txt files in the folder mentioned directly above. There are 8 csv files, one for each station, and a ninth that has everything combined but only the data columns that are present in every station and not just some stations. Inside the converted_files folder there is also a <b>pickles</b> folder that holds a Python pickle file of a single dataframe that holds all 8 stations but only the data columns that every station has in common.

<b>watershed_geojsons</b> <i>Extra bonus data! Feel free to ignore.</i> This holds a basic geojson of watersheds in the Houston areas and a few geojsons showing representative point geojson of likely damage from Harvey modeled from an early (and since changed) FEMA damage model. It should be noted that there are known differences between actual damage and modeled damage using this model! So please don't treat it as gospel as it is known to be wrong. It is only being included here for perspective on where this water quality is vs. where flooding was ~ same bodies of water.

<b>pre_made_kepler_map</b>  <i>Extra bonus data! Feel free to ignore.</i> This holds a markdown file of instructions and a json of all data and configuration for the Kepler map. Basically, just go to Kepler demo page <a href="https://uber.github.io/kepler.gl/#/demo">url</a> and load in the json. The map will form itself in your browser. NOTE, the json is nearly 100mb so only download if you're willing to wait :). It takes 40 seconds to load on my computer, your browser might be different.

## Files
<b>datajam_stations_points.geojson</b> <i>Extra bonus data! Feel free to ignore.</i> A geojson created with locations of the 8 water quality stations that feed into Lake Houston. The data for those stations are in the orig_txt and converted_files folders

<b>download_sites.txt</b> Contains information that was used to be build the geojson above

<b>First format conversions.ipynb</b> Is a jupyter notebook used to convert the txt files to the easier to work with csv files in the converted_files folder. Please go to the original txt files for definitions of terms and header labels, etc. 

<b>zoom_videoconf_IntroToDataBySachanShah.mp4</b> A video recording of Sachan Shah introducing the dataset and talking about some of the typical questions people ask?

### The data in "orig_txt" folders was gathered following these methods
- The main website for water quality information around Lake Houston is <a href="https://webapps.usgs.gov/lake_houston/home/#realtime">here</a>.
- If you click on the "GET WATER QUALITY DATA" button, you will be taken <a href="https://waterdata.usgs.gov/tx/nwis/current?multiple_site_no=08067074%2C08068000%2C08068500%2C08069500%2C08070200%2C295826095082200%2C295554095093402%2C294643095035200%2C294607085042700%2C08071330&index_pmcode_STATION_NM=1&index_pmcode_DATETIME=2&format=station_list&group_key=NONE&sort_key_2=site_no&html_table_group_key=NONE&rdb_compression=file&list_of_search_criteria=multiple_site_no%2Crealtime_parameter_selection">here</a> where you will see several stations. If you click on one of the station ids you will be taken to a page for that station.
- For example, this station, <a href="https://waterdata.usgs.gov/tx/nwis/uv/?site_no=08067074&agency_cd=USGS&amp;">"USGS 08067074 CWA Canal at Thompson Rd nr Baytown, TX"</a>
- Now, to get similar data downloaded from each page, select the radio button for "tab-separated output format" and set the earliest date to 2014-02-06.
- Eventually, a page will open (it might take a few tens of seconds) with text. Right click on the page and save as a txt file. 

Repeat for all the stations, and then use the rest of the notebook below to convert the initial txt file into CSV or JSON!

### What is this data?
<b>Short Answer</b> => Water quality data from Lake Houston or rivers that run into Lake Houston. 8 stations in total. Data collected, for the most part, over several years.

<b>What are the gotchas?</b> => 
1. Not all the data stations have all the same fields. 
2. Fields are not always in the same order from station to station. 
3. Starting date of data collection may vary a bit station to station. There are some nulls.

<b>Where do I go to learn more about the fields?</b> => The original data source or check out the orginal text files downloaded from the webpage in this repo. For example, the commented out headers look like this:

```
# File-format description:  https://help.waterdata.usgs.gov/faq/about-tab-delimited-output
# Automated-retrieval info: https://help.waterdata.usgs.gov/faq/automated-retrievals
#
# Contact:   gs-w_support_nwisweb@usgs.gov
# retrieved: 2018-06-10 12:43:16 EDT       (nadww02)
#
# Data for the following 1 site(s) are contained in this file
#    USGS 08070200 E Fk San Jacinto Rv nr New Caney, TX
# -----------------------------------------------------------------------------------
#
# Data provided for site 08070200
#            TS   parameter     Description
#        140344       00060     Discharge, cubic feet per second
#        140346       00065     Gage height, feet
#        140347       00400     pH, water, unfiltered, field, standard units
#        140348       00010     Temperature, water, degrees Celsius
#        140349       00095     Specific conductance, water, unfiltered, microsiemens per centimeter at 25 degrees Celsius
#        140350       00300     Dissolved oxygen, water, unfiltered, milligrams per liter
#        140351       63680     Turbidity, water, unfiltered, monochrome near infra-red LED light, 780-900 nm, detection angle 90 +-2.5 degrees, formazin nephelometric units (FNU)
#
# Data-value qualification codes included in this output:
#        
#     A  Approved for publication -- Processing and review completed.
#     P  Provisional data subject to revision.
#     e  Value has been estimated.
```



### Questions for end-users
1. What would you like to see in this data?
2. How would you like to use this data?
3. What types of water discharge, quality, stream flow, etc. questions can be answered by this type of data that you can't answer very well right now?

### Questions from subject matter expert
1. Which entry point supplies more turbidity into Lake Houston?
2. How does land use change relate to changes in turbidity?
3. How far upstream can we track turbidity plumes?
4. Is land-use changes around Lake Houston affecting water quality?

MORE THOUGHTS FROM SUBJECT MATTER EXPERT

```
Spoke to a colleague just now and he suggested something that's never been looked at:
Spatial Time series of streamflow/discharge and water quality from Lake Conroe down to Lake Houston? If you look at the web app you can zoom to both lakes and follow where Lk Conroe feeds into the river that flows into Lk Houston.

Page 13 of the following report:
Good explanation of turbidity. Figure 6 is a good primer of what is necessary: turbidity variations over time along a particular "fork" or "reach" of a stream that enters into Lake Houston. Basically turbidity over time in relation to land use change, and different weather conditions (drought vs. wet)

https://pubs.usgs.gov/sir/2012/5006/SIR%202012-5006_Lee%20Regression%20Model_FOR%20WEB.pdf

Also other questions:
1. How does pH of the water change during these high intensity storm events? (Tax Day, Memorial Day and Hurricane Harvey)?

2. Relation between streamflow and taste and odor compounds?


```

