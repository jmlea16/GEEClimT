# GEEClimT - Google Earth Engine Climate Tool
**If you use this tool please cite Lea et al. (submitted) and any citations from the data extracted using the tool.**

**© Copyright, Dr James Lea, University of Liverpool 2023. All Rights Reserved.**

The Google Earth Engine Climate Tool (GEEClimT) is an easy to use point and click interface to extract climate reanalysis data for academic research, education and outreach purposes. More details about the tool and case studies of its use can be found in the associated paper (Lea et al., submitted). Users who are interested in model projections of future climates may also wish to use GEEClimT's partner tool, the [Google Earth Engine CMIP6 Explorer (GEECE) ](https://github.com/jmlea16/GEECE).

## How to use GEEClimT
The following provides a step by step walkthrough of how to use GEEClimT, and demonstrates its functionality. Before trying to access GEEClimT users will need to have access to a non-commercial [Google Earth Engine account](https://code.earthengine.google.com/register). Note that use of GEEClimT through this route is **not** permitted for commercial purposes. Users who wish to use GEEClimT for commercial purposes should [contact the authors](mailto:j.lea@liverpool.ac.uk). 

### Getting started
GEEClimT and its code is run through Google Earth Engine using JavaScript API. To access the tools click [here](https://liverpool.onlinesurveys.ac.uk/geeclimt-geece-user-survey), where you will be asked for brief user information before being provided with a link to the tool.  Once the interface has been opened a welcome page will appear as shown below:

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/8ececc10-2475-4934-b805-436612b17f1c)

### Step 1 - Select export format (CSV or GEoTIFF)
The first step in the interface is to select the desired export format by clicking on the drop-down arrows under step 1(a). The user can choose to export the final dataset as either a CSV spreadsheet (point data) or a GeoTIFF (spatially referenced information in the form of georeferenced raster imagery). For this example, we will select the raster grid (GeoTIFF) format for the data output.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/54d2de76-6ea5-49c6-a505-ca421867904a)

### Step 2 - Select reanalysis dataset
Once the formatting for the data export has been chosen, the user is required to select a reanalysis dataset. By clicking the drop-down menu on step 1(b), all available datasets will be displayed. For this example, we will use the ERA5 Daily Aggregates (0.25 deg), where deg refers to the spatial resolution of the data in degrees.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/af2373eb-b33d-4802-ab98-724228931183)

Once the ERA5 Daily Aggregates data is selected in the drop-down menu, the data will be displayed on top of the map as shown below. For more information on the selected data, click the blue text below step 1 in the interface. This will open a new tab in Earth Engine Data Catalog and provide a description of the dataset, its properties and citations. 

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/10e70a78-4516-4be4-8493-7520b6a458b6)

### Step 3 - Select variables from dataset to be exported
When the selected dataset is loaded, variables can be chosen/refined to suit the user's needs. All available variables are automatically selected. To refine the data, click on the ‘variables selected’ tab and untick the boxes next to any unwanted variables in the menu OR the user can also click  ‘unselect all’ to clear all variables and then reselect those required. See below for this menu. For this example, we have chosen to keep all variables. 

Once the desired variables are chosen, click ok and this will take the user back to the original interface display. 

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/13ced47f-3274-4092-8117-40f5934012fa)
![image](https://github.com/jmlea16/GEEClimT/assets/40822976/6f0672dc-1c60-41fa-b4af-b5f27e3586d3)

### Step 4 - Select date and month range
After the variables are selected, the date range needs defining. The full date range of the dataset will automatically be displayed and does not need altering by the user if the full date range is needed.

If required, users can manually change this in the text box to a desired start and end date in a year-month-day format (YYYY-MM-DD). As an example, we will change this data to start on March 5th, 1989 (1989-03-05) and end on July 18th, 2019 (2019-07-18). Note that month and day values <10 need a leading 0 for the date to be accepted (e.g. 1989-3-5 will result in the interface returning an error, whereas 1989-03-05 will not). 

If only certain months are desired from the dataset, users can define these by clicking on the month options below. This option can be particularly useful when investigating seasonal change. If a range of months that span the end of the year are required (e.g. northern hemisphere winter), the start month selected would be December, and end month would be February. In this example we will use the default months from January to December.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/98ca5a2a-56e4-4769-a20b-71258915a1f2)

## Define region of interest (ROI)
**To view walkthrough for obtaining image data in GeoTIFF format click [here](https://github.com/jmlea16/GEEClimT/edit/main/README.md#step-5-imagegeotiff).**

**To view walkthrough for obtaining vector data in spreadsheet format click [here](https://github.com/jmlea16/GEEClimT/edit/main/README.md#step-5-vectorcsv).**

### Step 5 (image/GeoTIFF)

This step has 2 options for the user when exporting data in CSV or GeoTIFF format.

1. Manually draw a region of interest (ROI) as a polygon using the drawing tools in the top left of the map display.
2. Manually enter a comma separated list of latitudes and longitudes and import as a polygon. Coordinates will be imported within a WGS84 projection (EPSG:4326).

In this example we will define a ROI using the drawing tools. 

The user again has 2 options when drawing a ROI. 
1. Select ‘draw a shape’ ![image](https://github.com/jmlea16/GEEClimT/assets/40822976/6273df59-7f7a-4adb-a0ad-b257f0322fab)
. This will allow the user to draw points on the map, which when joined, creates a ROI in the form of a polygon.
2. Select ‘draw a rectangle’ ![image](https://github.com/jmlea16/GEEClimT/assets/40822976/acd1f56c-6f46-45a4-98f5-2fc739f89ca6)
. This will allow the user to draw a rectangle on the map which will define the ROI.

In this example, we will define a ROI using the ‘draw a shape’ tool. The ROI example is displayed as a pink polygon over Australia.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/9abd0889-a30c-41ee-9d2a-e66ffa995526)

### Step 6 (image/GeoTIFF) - Creating an export task
When the user is happy with the data output type, variables, date range and ROI, click ‘create export task(s)’ in step 5. This will process the data and once complete, a message will be displayed at the top of the interface. 

If the user wishes to create a new dataset to export the user can click on the reset button in the bottom right of the interface. 

*Note that resetting will change the interface back to the original display but will keep any tasks created from step 5. If a user clicks the 'Run' button above the code editor window this will remove any unsubmitted tasks.*

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/36a4fd7a-4910-4aef-83ee-4f7d92772140)

### Step 7 (image/GeoTIFF) - Run the export task(s)
To export the data, drag the top of the interface down using the grey line with two rows of dots. This will reveal the code editor and task export panel. Click tasks highlighted in orange.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/c5bf4f75-bd2c-4253-82a0-4fc54c0d6082)

After tasks have been selected, it will display the name of the data variables selected (GeoTIFF data), along with CSV files that contain timestamp information for each output band of the selected variables. As we selected all 9 variables from the data, a total of 9 tasks will need running. However, as the ROI is quite large, each variable from this example is split into 3 different tasks, therefore a total of 27 GeoTIFF tasks are displayed, alongside 3 CSV files. 

*Note that the number of tasks at the end will vary depending on the number of variables selected and the ROI.*

Click run on each task to submit to the server. The user can change the name of the dataset from the pop-up ‘initiate image export’ box. If this is all ok, click run again.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/e7f88505-0d90-4e45-ae3f-eb06707d801f)

Run tasks...

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/5c5fc252-c78a-49ce-a36f-743cf854df01)

The task will be moved to submitted tasks and will turn from a grey to blue background once complete. The user can keep an eye on the runtime to the right of the task.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/e3c415cf-02ee-4dbb-904a-b5ede07c71ad)

Once completed, the bar showing the submitted task will turn blue:

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/47ea2734-810d-4ba2-b6d5-1d846e5837aa)

At this point, the output data can be downloaded from a user's Google Drive for use in further analysis and/or visualisation.

*Tip: if your query generates a lot of export tasks, the [Open Earth Engine Google Chrome browser extension](https://chrome.google.com/webstore/detail/open-earth-engine-extensi/dhkobehdekjgdahfldleahkekjffibhg) developed by Mathieu Gravey provides users with a "Run all tasks" option.*


### Step 5 (vector/CSV)
If a CSV format was selected as the data output in step 1, the steps in the interface will be displayed slightly differently. Follow steps 1-3 as outlined above and input the desired daterange.  When the user gets to step 4, they are required to choose how GEEClimT will process the data for export. There are two processing options in GEEClimT:

1. Mean of all point locations/polygon - this will return the mean of all the points/the entire region defined by the ROI (e.g. if three points are defined in the ROI the values returned will be the average of the three points). This option is likely to be most useful where the ROI is a polygon.
2. Values of individual point locations (data for multiple points/polygon) - this will return data for each individual data point that overlaps with the the ROI (e.g. if three points are defined in the ROI the values for each of the three individual data points will be returned). This option is likely to be most useful where the ROI a point/multiple points.

For this example, where we have defined a polygon, we will tick the ‘table of mean values across entire ROI’ option.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/93382db1-4439-4900-af22-9982b417d9f4)

### Step 6 (vector/CSV) - Select how the data are to be extracted
This step requires the user to choose whether the data will be extracted from the dataset as either:

1. Values from the nearest grid cell within the dataset, or
2. Interpolated values from the grid cells nearest to ROI. For points data this will be based on bilinear interpolation of the four nearest grid cell values, and for a polygon ROI where the boundaries include part of a grid cell results will be spatially weighted to account for this.

Here we will select results to be analysed from ‘nearest full grid squares returned’. 

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/27d134ef-00d7-4461-add7-7e5867ccaea4)

### Step 7 (vector/CSV) - Define point(s)/ Region of interest
In this step, once the previous steps are completed, the ROI can be defined. Within this step there are two options that are also the same for the raster/image export example [GeoTIFF data](https://github.com/jmlea16/GEEClimT/edit/main/README.md#step-5-imagegeotiff): 

1. The first option allows the user to manually draw the ROI required, whether points or a single polygon, using the drawing tools in the top left of the map. 
2. The second option instead allows data to be defined through longitude/latitude coordinates, and site names to be defined. These can be entered into the boxes as comma separated lists (note that the interface will automatically remove any spaces and/or trailing commas).

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/98de988b-166f-474a-906f-8bf9b33aa967)

Once the above is defined, the import option must be specified, between points or polygon data. This is only required when defining custom point location/polygon coordinates. This then completes the actions required for step 6 in the interface. This example will use the first option to manually draw the ROI (e.g. see the raster/image export example [GeoTIFF data](https://github.com/jmlea16/GEEClimT/edit/main/README.md#step-5-imagegeotiff)).

### Step 8 (vector/CSV) - Generating gridded area of interest
To generate the gridded area of interest, click the *Generate gridded area of interest* and *Get data* buttons to prepare the data for export,:

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/5b437d33-6805-41cd-9e95-937eba023e0c)

Once the *Get data* button is clicked, a ‘Processing’ bar will appear on the screen for a few seconds to confirm that data is being processed in preparation for export. The time taken for this process to complete depends on the dataset size requested.

### Step 9 (vector/CSV) - Previewing and exporting the data
Once the data has been processed, a preview of the data will appear on the left panel of the screen that also provides the opportunity for users to view data for different sites and different variables selected. *Note that this preview is limited to the first 1000 observations. If the dataset size exceeds 1000 observations per site these data have been processed, but are not visualised*.

The export task for the processed data can then be generated.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/5f503b6d-db06-431d-99de-c516916e3c3a)

The code editor and export panel can be revealed when dragging the top of the screen downwards.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/6cbf8f4d-07d3-4b60-9b32-aae8a3ec853e)

In the export panel, click *Run* to submit the export task for processing. While the data is exported, you must wait. This is indicated by the bar having a grey background. When this is finished, the background will turn blue.

![image](https://github.com/jmlea16/GEEClimT/assets/40822976/747d11c0-e401-48cf-bd89-334a56642cf2)

*Tip: if your query generates a lot of export tasks, the [Open Earth Engine Google Chrome browser extension](https://chrome.google.com/webstore/detail/open-earth-engine-extensi/dhkobehdekjgdahfldleahkekjffibhg) developed by Mathieu Gravey provides users with a "Run all tasks" option.*

This means that all the steps have been completed, and resulting data can then be downloaded from a user’s Google Drive.

Well done! You have now completed all the steps for receiving data from GEEClimT.

## Acknowledgements
This readme file was written by Georgia Carr and Natasha Jones (University of Liverpool). James Lea is responsible for the accuracy of the workflow description above, and any queries should be directed to him.

## Disclaimer
Data in GEEClimT are provided as given, and the authors take no responsibility for how data extracted from GEEClimT are used. GEEClimT is strictly intended for non-commercial use. To discuss potential commercial applications, users should contact James Lea (j.lea@liverpool.ac.uk).
