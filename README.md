# 1. Business Problem:
1. Analyze the cost of living, housing sale price, and housing listing price per county.
2. Focus on the following states New York, New Jersey, Connecticut, and Pennsylvania. 
## Business Requirements
- What is the most important location/property factor for our user?
  - Living wage
  - Transportation
  - Pricing Range
- Our system will support the user in identifying a range of properties across states that best fulfill their living arrangements.
  - Dashboard showing measures that fall into the desired price range, location, etc...
    
## Functional Requirements
Question: Outline specific business functions and analytical processes.
- BI Use Case: What reports can we generate to answer business problems
- Analytical workflow: How should the work processes be, and what user interface and interaction? (More details are require to elaborate on this point.)
- Detailed analytics: House price tracking, house sale price, cost of living per county. Perhaps a report for each question. (What else should we analyze)
  
## Data Requirements
- Main data set :
  - https://www.dolthub.com/repositories/dolthub/us-housing-prices-v2
- Secondary data set:
  - mitlivingwage.zip 
  - zip_code_database_april 1.xlsx 
- We’ll be working with the provided data within the last 4 years.
- The data will be nonvolatile since they're existing ones that are no longer updated.
- The format will mainly be in JSON
- A data mart for storage of data to be queried (TBD)
- Pipeline of automated formatting and filtering.

## Compliance Requirement
Question: Outline specific business functions and analytical processes
- Establish clear controls and security to protect data privacy and integrity. Access controls and need to know.
- Identify and address potential vulnerabilities in data handling.
- Establish internal monitoring and audit (inspection, reviews, operations, audits)

---
# Data Dimensions & Facts
- **Dimensions** - These are fields/attributes that can not be aggregated or be done so in a manner that makes logical sense.
  - state | property_zip | property_street_address | property_city | property_county | property_id | property_type |
sale_datetime | source_url | book | page | property_township | sale_id | deed_date | land_type | code | name |
- **Facts** - These are fields/attributes that can be aggregated in a meaningful way. It would produce numerical results that can have meaning extrapolated from them.
  -  sale_price | building_num_units | property_lat | property_lon | building_num_stories | building_num_beds | 
building_num_baths | building_area_sqft | building_assessed_value | land_area_acres | land_area_sqft | land_assessed_value | total_assessed_value | total_appraised_value | building_appraised_value |

# Screenshot of DBSchema layout
![Dimensional Schema](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Screenshots/1.png)

# Screenshot of Information Architecture
![image](https://github.com/user-attachments/assets/3dca83ca-ef7a-4c6f-841b-369f1df58ea5)

# Screenshot of Data Architecture
![image](https://github.com/user-attachments/assets/6d5476a6-1d53-4352-93a8-7c7321b25cbf)

--- 
# 2. Business Impact
Question: You will need to consider any risks, costs, and benefits that are related to this project.  How will the persona/company benefit from it?

- **Risks** :
    - One of the primary risks for this project would be data inaccuracy. Outdated or incorrect information regarding housing prices, and crime rates can lead users to make poorly informed decisions. This will create a negative impact in their experience and also negatively affect the platforms credibility. 
    - Cost of living being different based on family size and personal preferences, means we will have to find more diverse data on the cost of living to fit with different users
    - Another risk is privacy concerns, handling sensitive information like user search history or preferences can pose risks if not properly managed.

- **Costs** :
    - Dealing with a large set of data we will have server costs, as well as maintenance costs once we have our system up and running
    - Data acquisition for accurate and comprehensive datasets. Development cost for building the data pipeline.

- **Benefits** :
    - The direct benefit for consumers is being able to filter through different counties not only by the price of the home but by the cost of living as well, giving a better understanding if it is truly possible to move there
    - Another benefit is being able to see price changes over time for specific countries. As well as seeing how the cost of living is different in surrounding counties compared to home prices. This gives an important view on moving to a new area as housing costs are not the only major burden.
    - This could then lead to monetization if done properly to major real estate corporations to aid them in finding the correct areas for people in a direct and efficient way.
    - One of the benefits will be increased business for real estate agents. Another benefit will be market differentiation. With this platform,m the company can stand out by offering a complete data analysis of the housing market which is very different from the outdated basic housing lists.
---

# 3. Business Persona
Our ideal fictitious persona is someone looking to relocate to the neighboring states of New York. They can defined as a casual consumer who like to view what their options are and select the best choice for themselves and their family using the visualization dashboard we create.

--- 
# 4. Data
**Housing Data**
- Source: https://www.dolthub.com/repositories/dolthub/us-housing-prices-v2
- The source file is approximately 112Gb large.
- Strength: Provide the vital data we need to complete this data. These include the sale price, address, zip code, county, and other metrics for properties necessary to gain insight into the job market.
- Weakness: Smaller detail information such as quantities for bedroom, bathroom, living room, and square footage are not provided. The granularity of analysis becomes shallow.
  
**MITLiving Data**
- Zip file provided
- The file is small. The file will provide the necessary information such as job title and salary to make a comparison of whether it is reasonable to move to another state.
- Strength: Get various occupation, salary, wage, and expense data.
- Weakness: The majority of the data tend to be similar in number, almost as they were duplicates.

**Zipcode CSV**
- CSV file provided

---
# 5. Methods 
For this project, we primarily utilized Python as our programming language. We leveraged the requests library to extract data from the source and store it in Azure Blob Storage. To optimize the data extraction process, we focused on data from the four states of interest and limited the timeframe to sales after 2019.

We employed Snowflake to import the extracted data from Azure Blob Storage into a staging area. Subsequently, we utilized dbt to perform data cleaning, transformation, and modeling, creating the necessary tables for our visualizations.

---
# 6. Data Tools
## Core Technologies:
- Programming Language: Python, SQL
- Cloud Platforms: Azure for storage, dbt for ELT
- Data Warehouse: Snowflake
- Visualization: Tableau
---

# 7. Interface
## Visualizations
![image](https://github.com/user-attachments/assets/72ac81dd-44f4-4a5a-be52-bb55b90ac568)
This graph shows the salary distribution of the professions from our given dataset. We see that jobs that are more technical or jobs that require much training or education are paid higher.
![image](https://github.com/user-attachments/assets/29873862-18a5-4dbb-a44c-1e1d2e0cea90)
This dashboard shows the average salary for a profession versus the average housing sale price per county. What can we learn from this? First: we see that counties within New York City (Kings in this case) are extremely expensive, relative to the average salary for the occupation. Second: As the orange bar becomes larger, it begs the question of whether or not purchasing said property is reasonable as you will be expected to pay it off for several decades.
![image](https://github.com/user-attachments/assets/6125b22b-2ccf-46ee-82a3-c6cda276e0e1)
This graph shows a scatterplot between the average sale price for houses versus its average assessed value. From this, we can see there are more expensive counties that are out there that you can live in, an example of this is Westchester County, per our data, the people there are wealthy. Houses in Westchester are selling at over 200% of the assessed value, which explains that there is housing inflation in that area. 

## Conclusion
1. Trying to buy a house can be expensive.
2. You are more likely to buy a house if you are employed in one of the fields at make more than the national average salary which is about $64,000.
3. You are more likely able to buy a house outside of New York City, in a more suburban area of New York, where the sale price is closer to its assessed price.

## In the future
1. We can spend more time cleaning the data and doing the transformation portion. Most of the data has a lot of null which we had to filter out in Tableau.
2. Gather data from various sources and scale the current data warehouse to make it a more comprehensive tool for analysts to use. Examples of data that can improve the data warehouse are states outside of the ones we gathered, mortgage rate data, house metrics (bedrooms, bathrooms, etc), and more salary information) 


# 8. Documentation
[Work process documentation with screenshots](https://github.com/Woooch/HousingPrice_DataWarehouse/blob/main/Process_Documentation.md)

[Powerpoint Presentation Reference in PDF](https://github.com/YChen099/CIS-4400-Group-7-Project/blob/main/CIS4400%20Group%2007%20Presentation.pdf)

[Tableau Analysis](https://public.tableau.com/app/profile/shum.chang.wu.chen/viz/HPVisualsFinal1/Story1)
