# Process documentations
The goal is to document what we did as a group for this semester's projecting, starting with the ELT process and ending with the final steps.

# 1. EXTRACT
Using Python, we created scripts to run for each state of interest, including New York, New Jersey, Connecticut, and Pennsylvania, to pull our relevant data.
Since the original dataset had an amount of 112 GB worth of information, we chose to optimize our data scraping through writing a SQL query within our Python script. This was done by choosing our states
and a time frame that was relevant to us. We then stored the data in our Azure Blob Storage

Snippets of the working code for NY and PA
![image](https://github.com/user-attachments/assets/3b6590b8-d479-484d-abb5-bb5162a8f83f)
![image](https://github.com/user-attachments/assets/379845e9-29f9-4e6c-a696-250683fe2ec4)

Snippets of the Azure Blob Storage
![blobstorage](https://github.com/user-attachments/assets/ee5fbee8-8eb0-46c1-af07-2c1034b5b209)
![image](https://github.com/user-attachments/assets/f6284277-2475-4e79-86fe-eb5b3a4b81ce)
![image](https://github.com/user-attachments/assets/d1cd633a-fc17-454c-a30d-34ad9cf36eaf)


Link to download Python notebook 
[CIS_4400_Python_Notebook](https://github.com/YChen099/CIS-4400-Group-7-Project/blob/main/CIS_4400_Team_7_Data_ELT_Code.ipynb)

# 2. LOAD: Azure to Snowflake
With the data we acquired from DoltHub located inside Azure Blob Storage, we then staged the data into Snowflake. Once all the files for the different states were consolidated, we created one table that hosted all
the data we collected. From there we moved to the next process using Dbt.

Snippets of the Snowflake data warehouse
![msazure](https://github.com/user-attachments/assets/b4a44a2d-7de2-48c7-99d8-17332e56f153)
![image](https://github.com/user-attachments/assets/f1bc0c6e-2656-4d29-bb34-333d9e97f853)
![image](https://github.com/user-attachments/assets/c69fcbc6-bcc6-428a-9aee-c96052f770d6)



# 3. TRANSFORMATION: Dbt
Using Dbt, we did our transformations and made the final fact and dimension tables. 

Snippets of Dbt Work
![image](https://github.com/user-attachments/assets/4a2c4ab7-2f74-498d-ba7e-0fa6f0d06cf8)
![image](https://github.com/user-attachments/assets/167d4b6b-61fc-4662-948b-058374de1ce4)
![image](https://github.com/user-attachments/assets/f6567732-552b-43aa-be2c-963814049278)
![image](https://github.com/user-attachments/assets/2fef2c73-c683-4800-a86d-4b7d1245ce63)

Snippets of the final fact and dimension tables
![image](https://github.com/user-attachments/assets/d94a883d-2234-425c-92a9-575c06fdce4e)
![image](https://github.com/user-attachments/assets/d0b5bca9-9b6a-4b5c-8a5b-6f34f21d6537)
![image](https://github.com/user-attachments/assets/752b8601-4b52-46d9-9acd-d686f2f56372)
![image](https://github.com/user-attachments/assets/7f395455-d6a1-441d-ad4a-8149000cc36b)

# 4. Visualizations
Once all the transformations were completed with Dbt. We began our Tableau work, we made a connection from the Snowflake server and began doing the analysis and look out for trends.

Snippets of the graph of interest
![image](https://github.com/user-attachments/assets/13f5d3f4-6a82-4fc8-92e6-5ed6155a7ebb)
![image](https://github.com/user-attachments/assets/c19974f9-0a27-4a0c-a49a-8a07def78f9c)
![image](https://github.com/user-attachments/assets/5a6f3eea-28dd-4df0-b1a9-0b4a06c28cb0)
