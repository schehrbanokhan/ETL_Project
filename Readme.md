# Purpose

South Korea entered into a trade agreement with the US that was implemented in March 2012.

To examine the influence of the tariff adjustments under the agreement, data pertaining to aluminum powder imports over the years 2008 to 2016, and the tariffs thereof, were the target of the following ETL process. Note that aluminum powder has a tariff duty Ad Valorum, meaning as a percentage of cost.

Text files of the tariff data and .csv files of the imports were extracted from government databases into pandas dataframes, cleaned using the pandas library, and then uploaded to a SQLite table using SQLalchemy in tandem with pandas.

**Information sources**:  

* U.S. - Korea Free Trade Agreement. (n.d.). Retrieved from https://ustr.gov/trade-agreements/free-trade-agreements/korus-fta

**Data sources**:  

_Imports_
* Product Profiles of U.S. Merchandise Trade with a Selected Market. (n.d.). Retrieved from http://tse.export.gov/tse/
    * searched for Selected Markets: "Geographic Regions/Asia", then selected "flow: imports" and "item: HS - 76" for aluminum products, "Display Data for: 2008 to: 2016"  


* Global Patterns of U.S. Merchandise Trade (n.d.). Retrieved from http://tse.export.gov/tse/
    * searched for Selected Markets: Selected "flow: imports" and "item: HS - 7603" for aluminum powder and flakes, "Display Data for: 2008 to: 2016"  


_Tariffs_
* Annual Tariff Data. (n.d.). Retrieved from https://dataweb.usitc.gov/tariff/annual

# Extract

Data was downloaded from http://tse.export.gov/tse/ as .txt files, which are saved in the local resources folder. 

The following extracts the data into dataframes for cleanup. Only the years 2008 to 2016 are to be analyzed

# Transform

The dataframes formed during extraction contain 111 columns and over 10,000 rows, and the target data regards only aluminum powders and flakes (hts8 codes 7603-1000 and 7603-2000).

# Load

Upload aluminum tariff data and South Korea/Asia imports data to SQLite as tables for the analysts. Separate tables are uploaded for tariffs and for imports, otherwise the import data would have to be repeated excessively in a join. Analyst can choose whether they would like to examine powder, flakes, or both via a join in SQL.