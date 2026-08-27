# CO-OPS Coastal Water Temperature Example Notebooks

# Overview

NOAA's CO-OPS collects trusted coastal data - including, water levels, currents and water temperature - that helps keep navigation safe, supports commerce, and protects coastal communities and ecosystems. Since the early 1990s, over 220 water temperature sensors have been installed along U.S. coasts and in the Great Lakes. CO-OPS did an in-depth analysis on 174 stations with at least 20 years of data. An automated quality assurance (QA)/ quality control (QC) system was developed to streamline data processing, flagging suspect data, and calculating daily averages. Manual reviews also caught sensor drifts at 47 stations, ensuring the data is reliable for long-term research. Afterwards, CO-OPS did further work with the good quality data with the primary objectives of demonstrating the applicability and usefulness of the data for longer time scale studies by identifying the relationships between water temperature and sea level measured at the same stations, comparing water temperature at tide gauges against a well-known NOAA dataset used for water temperature: NOAA NESDIS OISST, and capturing the local and regional patterns and variability and linear trends of water temperature along the US coasts.

This repository contains both station and regional-based notebooks associated with both the NOAA CO-OPS 114 Report entitled 'Evaluation and quality control of CO-OPS coastal water temperature data' - [https://doi.org/10.25923/n65z-p624](https://repository.library.noaa.gov/view/noaa/70917) and the manuscript ‘Seasonality and Trends in Coastal Water Temperatures from NOAA Water Level Monitoring Stations along US Coasts’ [PREPRINT](https://eartharxiv.org/repository/view/13085/). In the "Evaluation and Quality Control NOAA Report" folder there are two notebooks along with a zip file containing the cleaned daily water temperature data, and a metadata file. In the "Seasonality and Trends Publication" folder there are two notebooks along with a zip file of the metadata, daily and month water temperature data, and analysis results.

## Data Sources and Documentation

All data comes from CO-OPS's sensors. Stations with water temperature data can be found via [CO-OPS Metadata API](https://api.tidesandcurrents.noaa.gov/mdapi/prod/webapi/stations.json?type=watertemp). 6-min water temperature data can be accessed through [CO-OPS Data API](https://api.tidesandcurrents.noaa.gov/api/prod/).

## Evalution and Quality Control NOAA Report Folder

The QA/QC’d daily water temperature data is available on GitHub. Each station's data is provided as a separate comma-separated values (CSV) file containing daily means, residuals, and quality control (QC) flags.

  Each CSV file includes the following columns:

  - `Date`
  - `DAILY_WATER_TEMP`
  - `residual`
  - `manual_flag`
  - `automated_flag`
  - `data_fill_flag`

  In the `manual_flag` and `automated_flag` columns, suspect data are marked with a `"1"`, while data that passed quality control remain unflagged. The `data_fill_flag` column indicates the source of any replacement data (e.g., `DCP2 E1`, `DCP3 E1`, `DCP1 E2`) used on that date. If no replacement was applied, this field is left blank.

A separate csv file, `station_metadata_list`, contains metadata for each station, including:

  - Region name and abbreviation (based on group median)
  - Data availability range
  - Data quality classification

  The **data quality classification** includes three categories:

  1. **Continuous Climatology**  
    Data are mostly continuous and suitable for climatological analysis.

  2. **Semi-Continuous**  
    Data may include significant gaps (over two years), often due to the removal of erroneous or missing records. These stations can support seasonal climatology analyses and may become suitable for more in-depth climatological work as more data are added.

  3. **Incomplete**  
    These data sets require additional, case-by-case review and are **not currently recommended** for climatological use due to various quality issues.

>   ⚠️ **Note:** Stations classified as **Incomplete** should only be used for testing and exploratory work within this notebook. They should not be used for climatological or other analysis outside this context.

### Notebook Description

The Coastal_temp_final_station_graphics.ipynb allows users to explore the cleaned daily averaged water temperature data at over 100 stations. The code plots and saves different figures that represent each station including a time series plot, a residual plot, an average seasonal cycle plot, a seasonal cycle over the years plot, and a heatmap. There is an option in Step 3 for the user to choose to run a single station or run and save plots for all of the stations. Note if you are running the notebook in Google Colab and you want to save the figures, make sure to download the Daily_Water_Final_Plots folder from the files section on the left side of Google Colab.

The Coastal_temp_final_reginal_graphics.ipynb allows users to explore the cleaned daily averaged water temperature data at over 40 regions around the US. The code plots and saves different figures that represent the different stations in each region including a time series plot with all stations in a region, the median water temperature, residuals of all stations, and residuals subtracted by group medians. There is an option in Step 3 for the user to choose to run a single region or run and save plots for all of the regions. Note if you are running the notebook in Google Colab and you want to save the figures, make sure to download the Regional_Final_Plots folder from the files section on the left side of Google Colab.


## Seasonality and Trends Publication Data Folder

There are four master csv(s) which each contain time as rows (day, month, day of year...) and each station in the publication as a column including `MASTER_daily_clean_water_temp.csv`, `MASTER_monthly_mean_water_temp`, `MASTER_Station_DOY_Averages`, and `MASTER_Station_Monthly_Climatology`.

The `Metadata and output results.xlsx` contains 4 data tabs and 4 metadata tabs. 
  - `Station inventory` tab contains basic station info including coordinates, region, POR, and metadata for both the WT and AT data.
  - `Seasonality` tab contains water temperature, air temperature, and mean sea level seasonality data including ranges, climotological peaks, and correlations/shifts between them.
  - `Trends` tab contains the water temperatire trends (monthly, annual max, and annual min) as well as msl trends for each station.
  - `Daily distribution and extremes` tab contains mean observed values, variance, kurtosis, extreme percentiles of daily mean water temperature and daily mean water temperature anomalies.

### Notebook Description

The Coastal_temp_seasonality_trend_viewer.ipynb allows users to calculate the day of year and monthly averaged seasonal cycle as well as calculate a long-term linear trend using an ARIMA model and plot the longterm monthly data. The code plots and saves the 3 figures as well as saves the trends analysis results into a csv. There is an option in Step 3 for the user to choose to run a single station or run and save plots and trends results for all of the stations. Note if you are running the notebook in Google Colab and you want to save the figures, make sure to download the "Monthly_Climatology", "Seasonal_cycles", and "Trends" folders as well as the master_trend_analysis_results.csv from the files section on the left side of Google Colab.

The Coastal_temp_seasonality_trend_regional_graphics.ipynb allows users to recreate some of the summary graphics in the publication including the seasonal water temperature anomaly, comparison of water with air temperature and water levels, and a summary graphic of the water temperature trends. The code plots and saves the three summary figures. Note if you are running the notebook in Google Colab and you want to save the figures, you can download them from the files section on the left side of Google Colab.


## Set up options

1. **Clone the repository:**  To clone, you will first need to install [Git Bash](https://git-scm.com/downloads). For NOAA users, it is an approved software package that can be self-installed. After installing Git Bash, [use SSH to clone and create a local repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository#cloning-a-repository). After cloning, you can use Git Bash to navigate the repository, including downloading (pulling) new updates and viewing all branches. 
2. **Download the repository:** To download, simply click the green 'Code' dropdown button on the main page of the coastal water temperature repository. In the drop down menu, select Download ZIP, and unzip it to the location where you'd like to run the software. 
3. **Open the notebook in Google Colab directly from github:** Open Google Colab. Go to the file dropdown button in the top lefthand corner and click on 'Upload Notebook'. In the pop-up window click GitHub and then enter the GitHub URL.

## Running the notebooks

Python notebooks can be run in different environments. These notebooks were created in [Google Colab](https://colab.research.google.com/), but can also be run locally using Jupyter Notebook, VS Code, or PyCharm. Both of the notebooks create a folder for the graphic outputs in the user's working directory.

#### For additional information, contact:

NOAA's [Center for Operational Oceanographic Products and Services](https://tidesandcurrents.noaa.gov)

Email: tide.predictions@noaa.gov

## NOAA Open Source Disclaimer

This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an 'as is' basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.

## License

Software code created by U.S. Government employees is not subject to copyright in the United States (17 U.S.C. �105). The United States/Department of Commerce reserves all rights to seek and obtain copyright protection in countries other than the United States for Software authored in its entirety by the Department of Commerce. To this end, the Department of Commerce hereby grants to Recipient a royalty-free, nonexclusive license to use, copy, and create derivative works of the Software outside of the United States.
