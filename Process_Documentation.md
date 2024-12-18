# Process documentations
The goal is to document what we did as a group for this semester's projecting, starting with the ELT process and ending with the final steps.

# 1. EXTRACT
Using Python, we created scripts to run for each state of interest, including New York, New Jersey, Connecticut, and Pennsylvania, to pull our relevant data.
Since the original dataset had an amount of 112 GB worth of information, we chose to optimize our data scraping through writing a SQL query within our Python script. This was done by choosing our states
and a time frame that was relevant to us. We then stored the data in our Azure Blob Storage

Snippets of the working code for NY and PA
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/7.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/8.png)

Snippets of the Azure Blob Storage
![blobstorage](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/9.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/10.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/11.png)


Link to download Python notebook 
[CIS_4400_Python_Notebook](https://github.com/YChen099/CIS-4400-Group-7-Project/blob/main/CIS_4400_Team_7_Data_ELT_Code.ipynb)

# 2. LOAD: Azure to Snowflake
With the data we acquired from DoltHub located inside Azure Blob Storage, we then staged the data into Snowflake. Once all the files for the different states were consolidated, we created one table that hosted all
the data we collected. From there we moved to the next process using Dbt.

Snippets of the Snowflake data warehouse
![msazure](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/12.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/13.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/14.png)



# 3. TRANSFORMATION: Dbt
Using Dbt, we did our transformations and made the final fact and dimension tables. 

Snippets of Dbt Work
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/15.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/16.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/17.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/18.png)

Snippets of the final fact and dimension tables
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/19.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/20.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/21.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/22.png)

# 4. Visualizations
Once all the transformations were completed with Dbt. We began our Tableau work, we made a connection from the Snowflake server and began doing the analysis and look out for trends.

Snippets of the graph of interest
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/23.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/24.png)
![image](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/25.png)
