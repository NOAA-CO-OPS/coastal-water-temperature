# CO-OPS Coastal Water Temperature Example Notebooks
# Overview

NOAA's CO-OPS collects trusted coastal data—including water temperature, tides, and currents—that helps keep navigation safe, supports commerce, and protects coastal communities and ecosystems. Since the early 1990s, over 220 water temperature sensors have been installed along U.S. coasts and in the Great Lakes. CO-OPS did an in-depth analysis on 174 stations with at least 20 years of data. An automated quality control system was developed to streamline data processing, flagging suspect data, and calculating daily averages. Manual reviews also caught sensor drifts at 47 stations, ensuring the data is reliable for long-term research.

This repository contains both a station and regional-based notebook along with a zip file containing the cleaned daily water temperature data and a csv with the stations and regions used in the analysis for NOAA Technical Report NOS CO-OPS XXX: Evaluation and Quality Control of CO-OPS Coastal Water Temperature Data. 

## Data Sources and Documentation

All data comes from CO-OPS's sensors. Stations with water temperature data can be found via [CO-OPS Metadata API](https://api.tidesandcurrents.noaa.gov/mdapi/prod/). 6-min water temperature data can be accessed through [CO-OPS Data API](https://api.tidesandcurrents.noaa.gov/api/prod/).

The QA/QCed daily water temperature data is currently available on github with this notebook. Each station’s data is provided in a separate comma-separated values (CSV) file, containing daily means, residuals, and quality control (QC) flags. Each CSV includes the following columns: Date, DAILY_WATER_TEMP, residual, manual_flag, automated_flag, and data_fill_flag. Suspect data in the manual and automated flag columns are marked with a “1”, while data that passed QC remain unflagged. The data_fill_flag column indicates the source of any replacement data (e.g., DCP2 E1, DCP3 E1, DCP1 E2) on the dates it was used, while unfilled data have no entry in this column.

## Set up options

1. **Clone the repository:**  To clone, you will first need to install [Git Bash](https://git-scm.com/downloads). For NOAA users, it is an approved software package that can be self-installed. After installing Git Bash, [use SSH to clone and create a local repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository#cloning-a-repository). After cloning, you can use Git Bash to navigate the repository, including downloading (pulling) new updates and viewing all branches. 
2. **Download the repository:** To download, simply click the green 'Code' dropdown button on the main page of the coastal water temperature repository. In the drop down menu, select Download ZIP, and unzip it to the location where you'd like to run the software. 
3. **Open the notebook in Google Colab directly from github:** Open Google Colab. Go to the file dropdowm button in the top lefthand corner and click on 'Upload Notebook'. In the pop-up window click GitHub and then enter the GitHub URL.

## Running the notebooks

Python notebooks can be run in different environments. These notebooks were created in [Google Colab](https://colab.research.google.com/), but can also be run locally using Jupyter Notebookm VS Code, or PyCharm. To run locally, make sure to edit the file paths to your preferred location as the script outputs graphics. Comment out the code cell under Step 2 if running locally.

## Notebook description

The **Coastal_temp_final_station_graphics.ipynb** allows users to explore the cleaned daily averaged water temperature data at over 100 stations. The code plots and saves different figures that represent each station including a time series plot, a residual plot, an average seasonal cycle plot, a seasonal cycle over the years plot, and a heatmap. There is an option in Step 3 for the user to choose to run a single station or run and save plots for all of the stations. Note if you are running the notebook in Google Colab and you want to save the figures, make sure to download the Daily_Water_Final_Plots folder from the files section on the left side of Google Colab.

The **Coastal_temo_final_reginal_graphics.ipynb** allows users to explore the cleaned daily averaged water temperature data at over 40 regions around the US. The code plots and saves different figures that represent the different statiosn in each region including a time series plot with all stations in a region, the median water temperature, residuals of all stations, ans residuals substracted by group medians. There is an option in Step 3 for the user to choose to run a single region or run and save plots for all of the regions. Note if you are running the notebook in Google Colab and you want to save the figures, make sure to download the Regional_Final_Plots folder from the files section on the left side of Google Colab.

#### For additional information, contact:

NOAA's Center for Operational Oceanographic Products and Services, [Coastal Hazards Branch](https://tidesandcurrents.noaa.gov/coastal_hazards.html)


nos.co-ops.chb@noaa.gov

## NOAA Open Source Disclaimer

This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an 'as is' basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.

## License

Software code created by U.S. Government employees is not subject to copyright in the United States (17 U.S.C. �105). The United States/Department of Commerce reserves all rights to seek and obtain copyright protection in countries other than the United States for Software authored in its entirety by the Department of Commerce. To this end, the Department of Commerce hereby grants to Recipient a royalty-free, nonexclusive license to use, copy, and create derivative works of the Software outside of the United States.