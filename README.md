# Supplier Quality and Performance Dashboard

![](https://github.com/idayatakinwale/Enhancing-Supplier-Quality-Management-through-Data-Analysis/blob/e16a601cb6001b1bad13fb54faba3507fb086980/company%20pic.png)

In today's competitive manufacturing landscape, ensuring the quality of raw materials is essential for operational efficiency and product excellence. This project addresses a critical gap in the procurement and supplier management processes at Synergy Manufacturers Ltd, which currently lacks a centralized system to evaluate and monitor supplier performance.

The initiative was launched in response to the growing need to understand supplier quality across various plants and to identify the sources of defects that impact production. Through a concerted effort, the program management team has successfully consolidated data related to raw materials, defects, and vendors, enabling the organization to analyze supplier performance comprehensively.

### Objectives
---

Utilizing Power BI, this project aims to visualize and interpret the data collected, providing insights into vendor and material performance across different plants. 

The **primary objectives** include identifying vendors and plants with the highest defect rates, assessing the impact of defective materials on production downtime, and uncovering any patterns or correlations between materials, vendors, and plants.

By leveraging data analytics, this project seeks to equip Synergy Manufacturers Ltd. with the knowledge required to make informed decisions, improve the overall quality of raw materials sourced for production, quantify the financial implications of poor quality and identify the primary sources of these issues.

### Key Questions Addressed
---

1.	Which vendors/plants are causing the greatest defect quantity?
2.	Which vendors/plants are causing the greatest downtime?
3.	Are there particular combinations of materials and vendors that perform poorly?
4.	Are there particular combinations of vendors and plants that perform poorly?
5.	How does the same vendor and material perform across different plants?

### Dataset Details

![](https://github.com/idayatakinwale/Enhancing-Supplier-Quality-Management-through-Data-Analysis/blob/43766d3fbd75527a49f390dc4253e173a8bdb5e8/Dataset%20pic.png)

The dataset consists of 5,226 rows and 9 columns. The column details are given below:

**Date:** This is the date when the defect was recorded, with date values ranging from 2018 to 2019.

**Vendor:** This consists of 318 different names or identifier of the supplier providing the materials

**Plant Location:** There are 30 different geographic locations of the plant where the material was used.

**Category:** The materials are categorized/classified into 6 different groups which include Mechanicals, Electricals, Logistics, Materials and Components, Packaging, Goods & Services.

**Material Type:** 22 different types of materials were used such as the Raw materials, Corrugate, Glass etc.

**Defect Type:** The defect observed in the material were classified into three, which include Impact, No Impact and Rejected.

**Defect:** This consists of 268 different defects/faults found in the materials such as Bad seams, Not certified, Print defects etc.

**Total Defect Quantity:** This is the total number of defective materials recorded, ranging from 215 to 999,759.

**Total Downtime Minutes:** This is the total number of minutes of downtime caused by the defective materials, ranging from 0 to 5000 minutes.

## Methodology

### Data Cleaning
Although the data required minimal cleaning, these few validation steps were carried out using the power query editor

•	Data types were validated throughout the columns

•	No missing values were observed, as seen by the 100% validity and 0% emptiness given from the column quality in each column

•	No duplicate values were found in the dataset

### Data Modelling

In order to improve performance and reduce redundancy (i.e. longer-than-usual run times) from the large dataset when generating reports, the following steps were carried out on the power query editor to normalize the cleaned dataset (by splitting the table into fact table & dimension tables) and then connect the normalized tables on the powerbi desktop.

**Segmentation into dimension tables:**

•	The dimension tables were created for the categories like the Vendor, Plant Location, Material Type, Category, Defect & Defect Type. This was achieved by duplicating the original query for each dimension table that was to be created.

•	Each query was renamed according to its respective role in the model, such as **Supplier Fact Table** for the central metrics like Total Defect Quantity & Total Downtime Minutes, and **Dimension Tables** for categories like **Vendor**, **Plant Location**, **Material Type**, **Category**, **Defect** & **Defect Type**.

•	For each dimension table, only the specific column relevant to that dimension was retained. This was to ensure that each table contained only the information necessary for the analysis. Duplicates were removed from each table so as to have only the unique column values.

•	An index column was also added for each dimension, serving as primary key for unique row identification.

**Building the Fact Table:**

•	The primary keys on the dimension tables were replicated on the supplier fact table. This was achieved by merging each dimension table to the fact table through their common column using the inner join. From the drop down beside this new column, only the unique ID column was checked/selected while other columns were deselected.

•	These newly added columns on the fact table which consist of the unique identity values were all renamed accordingly

•	After closing the power query editor and all changes applied, the normalized data tables were loaded into the powerbi desktop.

**Creating the Calendar Table:**

•	An accurate date table that enabled effective time series analysis was built using the DAX (Data Analysis Expressions) functions – ADD COLUMN, CALENDAR AUTO and other Date functions. This automatically creates a date dimension table based on the dates in the data model.

•	On the model view, the automatically derived relationships were adjusted to remove and replace unwanted relationships with the required. Here, the primary keys on the six dimension tables were connected to the foreign key on the fact table, leading to the formation of a **star schema model**. The dimension tables were all joined to the fact table with a **one-to-many relationship**.


