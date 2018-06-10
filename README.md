# data-jam-June-2018
data for a Houston Data Visualization Meet-up data jam

## Folders
<b>orig_txt</b> holds the original tab deliminated text files downloaded as described in the jupyter notebook here.

<b>converted_files</b> holds the csv files created from the txt files in the folder mentioned directly above

<b>watershed_geojsons</b> holds a basic geojson of watersheds in the Houston areas and a few geojsons showing representative point geojson of likely damage from Harvey modeled from an early (and since changed) FEMA damage model. It should be noted that there are known differences between actual damage and modeled damage using this model! So don't treat it as gospel.

## Files
<b>datajam_stations_points.geojson</b> A geojson created with locations of the 8 water quality stations that feed into Lake Houston. The data for those stations are in the orig_txt and converted_files folders

<b>download_sites.txt</b> Contains information that was used to be build the geojson above

<b>First format conversions.ipynb</b> Is a jupyter notebook used to convert the txt files to the easier to work with csv files. Please go to the original txt files for definitions of terms and header labels, etc. 


### The data in "orig_txt" folders was gathered following these methods
- The main website for water quality information around Lake Houston is <a href="https://webapps.usgs.gov/lake_houston/home/#realtime">here</a>.
- If you click on the "GET WATER QUALITY DATA" button, you will be taken <a href="https://waterdata.usgs.gov/tx/nwis/current?multiple_site_no=08067074%2C08068000%2C08068500%2C08069500%2C08070200%2C295826095082200%2C295554095093402%2C294643095035200%2C294607085042700%2C08071330&index_pmcode_STATION_NM=1&index_pmcode_DATETIME=2&format=station_list&group_key=NONE&sort_key_2=site_no&html_table_group_key=NONE&rdb_compression=file&list_of_search_criteria=multiple_site_no%2Crealtime_parameter_selection">here</a> where you will see several stations. If you click on one of the station ids you will be taken to a page for that station.
- For example, this station, <a href="https://waterdata.usgs.gov/tx/nwis/uv/?site_no=08067074&agency_cd=USGS&amp;">"USGS 08067074 CWA Canal at Thompson Rd nr Baytown, TX"</a>
- Now, to get similar data downloaded from each page, select the radio button for "tab-separated output format" and set the earliest date to 2014-02-06.
- Eventually, a page will open (it might take a few tens of seconds) with text. Right click on the page and save as a txt file. 

Repeat for all the stations, and then use the rest of the notebook below to convert the initial txt file into CSV or JSON!
