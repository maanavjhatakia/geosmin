#Geosmin Occurrences in Marston Reservoir
### Using multivariate linear regression and qualitative system dynamics to understand predictor variable importance and process dynamics

------------

### Maanav Jitesh Jhatakia
#### MSc. Candidate, *Engineering and Policy Analysis* | Delft University of Technology - The Hague, Netherlands
Submitted in fulfillment of the requirements of *TPM593A - Internship Elective* as
part of the MSc. program in Engineering and Policy Analysis at TU Delft.

------------

This is the GitHub repository for the Marston Reservoir Geosmin occurrence project in partnership with Denver Water and TU Delft. The following description is an introduction to the files that are included in this repository and their function in the greater analysis. 

All analysis was done using the *gds* Anaconda environment (meant for data analysis) and Jupyter Notebooks. Please note that the following *Python* libraries should be installed prior to running this code:
- pandas
- numpy
- scipy (stats)
- sklearn (linear_model, StandardScaler)
- seaborn
- statsmodels (lzip)
- matplotlib
- scipy.interpolate

#####Basic data files
**"20220613 Marston C20 10 year Geosmin MIB LiMS data.xlsx"**: The LiMS dataset sequestration of geosmin data gotten from Denver Water. Geosmin data was separated from 2-(MIB) data and boundary readings to find viable occurrences for analysis. 
**"South System Treatment Monthly Report.xlsm"**: LiMS dataset that has nutrient data for Denver Water's South System. 

##### Cleaning and analysis files - operate in order of listing
**"geosmin_data_cleaning.ipynb"**: Jupyter Notebook with that includes cleaning and seperation of the geosmin data into the 4 main locations of interest for this analysis. The file uses the "**geosmin_data_20122022.csv**", which is a sequestered version of all raw geosmin data from the LiMS dataset file. The file produces the following files:
- **sample_res_geosmin.csv**: geosmin readings for Marston Reservoir samples
- **wtp_samples_geosmin.csv:** geosmin readings for Marston WTP samples
- **wtp_influent_geosmin.csv:** geosmin readings for Marston WTP Influent samples
- **conduit20_geosmin.csv**: geosmin readings for the Conduit 20 Forebay Influent (which transports water directly from around Strontia Springs Reservoir).

**flowrate_cleaning.ipynb**: This file had calculations for water temperatures and regional separations of flow rates and available air temperature. This produces the following dataframes, used later in the OLS model preparation:
- **cs_rt_flow_temp.csv**: Flowrate and temperature data for Cheesman Reservoir and Roberts Tunnel points.
- **ss_ch_flow_temp.csv**: Flowrate and temperature data for Strontia Springs Reservoir to Chatfield Reservoir points. 
- **ss_mr_flow_temp.csv**: Flowrate and temperature data for Strontia Springs Reservoir to Marston Reservoir points. 

**nut_interpolations.ipynb**: This is the file with filled interpolations of nutrient information. Interpolations were made with the PCHIP polynomial interpolation method using the *scipy.interpolate* package in Python, and did so with recorded points obtained from LiMS. The following files were produced: 
- **nut_ms_above_conf_filled.csv**: Filled nutrient interpolations for the MSConf. collection point. 
- **nut_nf_above_conf_filled.csv**: Filled nutrient interpolations for the NFConf. collection point.
- **downstream_strontia_nut_filled.csv**: Filled nutrient interpolations for the DS Strontia. collection point.
- **nut_upstream_strontia_filled.csv**: Filled nutrient interpolations for the US Strontia collection point.
- **nut_sp_below_chat_filled.csv**: Filled nutrient interpolations for the SPChat. collection point.

These files will later be used in the analysis in each specific location. 

The following are the primary files that contain OLS models for each specific location (along with regional contribution models). All information used in these files are already available in csv format, thus there should not be many problems running this.
- **cond_20_model_dev.ipynb**: Model development for Conduit 20
- **wtp_samples_model_dev.ipynb**: Model development for Marston WTP samples 
- **wtp_influent_model_dev.ipynb**: Model development for Marston WTP Influent samples. 
- **sample_res_model_dev.ipynb**: Model development for Marston Reservoir samples.

Outputs and explanations of this analysis are provided in the accompanying report.
