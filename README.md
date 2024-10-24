# SUPPLIER QUALITY AND PERFORMANCE ANALYSIS

![](https://github.com/idayatakinwale/Enhancing-Supplier-Quality-Management-through-Data-Analysis/blob/e16a601cb6001b1bad13fb54faba3507fb086980/company%20pic.png)

In today's competitive manufacturing landscape, ensuring the quality of raw materials is essential for operational efficiency and product excellence. This project addresses a critical gap in the procurement and supplier management processes at Synergy Manufacturers Ltd, which currently lacks a centralized system to evaluate and monitor supplier performance.

The initiative was launched in response to the growing need to understand supplier quality across various plants and to identify the sources of defects that impact production. Through a concerted effort, the program management team has successfully consolidated data related to raw materials, defects, and vendors, enabling the organization to analyze supplier performance comprehensively.

### OBJECTIVES
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

### DATASET DETAILS

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

## METHODOLOGY

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


### DATA ANALYSIS
---

The data model was brought to life through a series of interactive dashboards and reports that would provide actionable insights and facilitate data-driven decision making.

Based on the available data, the three key metrics I focused on were:

•	**Downtime:** The total hours lost due to defective materials

•	**Defect Quantity:** The number of defective units received from the suppliers

•	**Downtime Cost:** This is the monetary cost or expense incurred during downtime, where I assumed the company was losing $10 per downtime hour.

In alignment with the manufacturing industry’s practice of calculating costs on an hourly basis, the downtime was presented in hours, ensuring consistency in the report.


### Detailed Dashboard/Report Features
---

#### Homepage

![](https://github.com/idayatakinwale/Enhancing-Supplier-Quality-Management-through-Data-Analysis/blob/bea4f770d64e4e82ae6d423c54dc2089c10438f7/Landing%20Page.png)

The added homepage is a clean and professional interface with navigation bar that allows stakeholders /users to effortlessly switch between the core areas of the report, each focusing on different aspect of supplier quality and performance.

The focus here is on leveraging graphic design to create an intuitive, visually appealing dashboard that improves the user experience, enabling stakeholders and even non-technical-decision-makers to explore critical metrics effortlessly.


#### Overview Page

OVERVIEW PAGE PICS

•	The top section of this page provides the most critical metrics which are the **Defects**, **Downtime Hours** & **Downtime Cost**, along with percentage changes compared to the previous month and previous year. A custom **Downtime Cost/Hour** (in this case, $10) was set for calculating the financial impact and to know the cost implication of the downtime.

•	A monthly trend chart was added, which shows how the defect quantity and downtime hours metrics changed throughout the year.

•	Another section of the page indicates the worst performers by vendor, plant, material and defect type.

•	The distribution of the Impact, Non-Impact & Rejected defects across the years were also displayed at the lower section of the page.


#### Vendor Performance Page

VENDOR PAGE PICS

This page generally highlights the suppliers contributing the most to the production issues of the manufacturing company.

•	The top & bottom-performing vendors were displayed using the **Top N Analysis** feature in the dashboard. This allows users to be able to pick a particular number of vendors based on the selected metric (i.e. **Defect Quantity** or **Downtime Hours**), and also helps the company to know the vendors that are either outperforming or underperforming.

•	The correlation between the defect impact and downtime was analyzed by categorizing the vendors into low, medium and high-risk groups. Vendors with downtime exceeding 800 hours were classified as **High-Risk**, **Medium-Risk** if the downtime was within 400-800 hours and **Low-Risk** if the downtime was below 400 hours.

•	The vendor performance across the Impact, No-Impact & Rejected defect types were also displayed based on the defect quantity and downtime metrics. Here, the conditional formatting was applied to highlight vendors based on the degree of defect and downtime impact caused.


#### Plant Performance

PLANT PAGE PICS

•	A Top N Analysis was used to identify the top & bottom performing plants based on the defect quantity and downtime metrics.

•	The geographic distribution of the plants and their performance based on the metrics was visualized using the map.

•	The matrix visual showed the breakdown of the defect impact, no-impact and rejected impact across different plant locations, helping to identify the high-risk locations.


#### Material Performance

PICS

•	In analyzing the material performance, a detailed breakdown of the key metrics was provided, including downtime by material type, defect type and category.

•	The increasing trend in raw materials defect indicates a potential need for supplier audits or improved quality control processes, while the rising trend in corrugate material defect suggests packaging redesign/optimization or improved handling & storage procedures.

•	In visualizing the downtime hours by defects, the greatest downtime was observed from defects tagged ‘Not Certified’ and ‘Bad Seams’. This suggests the need for the implementation of supplier audit and certification programs.

•	The increasing trend in Mechanicals defects indicates a potential need for equipment maintenance or process improvements, while the rising trend in Logistics defects suggests the need for supply chain optimization.


#### Downtime Impact

PICS

•	The great financial impact of downtime caused by the defective materials is seen in the downtime cost analysis, which provides a breakdown of the downtime cost per hour, highlighting specific days where costs were highest, with March and October being the month with the highest cost. 

•	The monthly downtime costs were also visualized using the bar chart, allowing for quick identification of peak cost periods.

•	In determining the best and worst performers, users can analyze the vendor-plant and vendor-material combination from the tables at the bottom of the page.


### KEY INSIGHTS/ FINDINGS

	**Rising Defect & Downtime:** The Total defect quantities increased to **2.6 billion** units, with a corresponding increase in downtime to **216,000 hours**, leading to a financial impact of **$2.16 million** underscoring the direct cost of defective materials on production efficiency.

	**Financial Impact:** A crucial insight from the analysis is the direct correlation between downtime and financial losses. Assuming a downtime cost of $10 per hour, the company incurred over $2 million in downtime costs, with spikes in March and October indicating periods of severe disruption. This financial perspective provides stakeholders with a clear understanding of how supplier quality issues are affecting the bottom line.

	**Worst-Performing Vendors:** Vendors like **Yombu**, **Avamm** and **Meejo** emerged as the worst-performing vendors contributing the highest defect quantities and significant downtime hours. This reflects the need to enhance inspection and testing procedures for materials received from these suppliers.

The positive correlation observed between the downtime and defect quantity indicates that there is direct relationship between the quality of materials and production efficiency, hence vendors with higher defect rates are likely to cause more production disruptions.

	**Plant-Specific Issues:** From the analysis of the plant performance, plant locations in **Hingham**, **Charles City** and **Twin Rocks** had the greatest contribution to defect-related downtime, with each plant reporting defect quantities of about **100 million** and downtime of nearly **9,000 hours**

	**Material Performance:** The **Raw materials** were observed to be the most problematic material type causing a significant downtime of about      , closely followed by the **Corrugates**. This indicates the need for improved quality control processes.

The rising trends in the **mechanical** and **logistics** category of material defects suggests the need for equipment maintenance and supply chain optimization.

	**Defect Categories:** Material defects tagged **Not Certified** and **Bad Seams** were the most frequent recurring issues, indicating the regulatory non-compliance and insufficient quality control measures.

	**Vendor-Material/Plant Combinations:** In analyzing the worst performing vendor-material combination, the vendor **Twitter beat** when supplying **Raw materials** caused significant downtime of about **412 hours** with **5.9 million** defects, resulting in nearly **$4,120** financial loss. Vendor **Seed fire** while supplying **Corrugates** also caused a critical/substantial downtime of **568 hours** with about **5 million** defects.

The **vendor-plant combinations** with the worst performances are vendors **Yombu** supplying material to plant **Prescott**, where a significant downtime of **200 hours** was recorded with **3.2 million** defects. Vendor **Gevee** supplying to plant **Waldoboro** also caused a considerable downtime of  **241 hours** with **3 million** defect, resulting in nearly **$2,500** in lost productivity.

	Even though a positive correlation was observed while visualizing the defect impact on downtime, there were instances where the number of defects were lower but downtimes were higher and vice versa, indicating that downtimes were not always caused by defective material alone i.e. there are other unknown factors causing the downtime such as machine failures, power outages, staffing shortages or delays in receiving materials.


### RECOMMENDATIONS
1.	Targeted Vendor Quality Improvement Initiatives:
•	Develop and implement enhanced inspection and testing procedures for materials received from worst-performing vendors (Yombu, Avamm, Meejo).
•	Establish supplier quality agreements that include performance-based incentives or penalties tied to defect rates and downtime.
•	Develop strategic partnerships with reliable vendors.
•	Implement Total Quality Management (TQM) principles such as employee involvement, customer focus, process approach and fact-based decision making.

2.	Plant-Specific Action plan
o	Develop targeted improvement programs for plants in Hingham, Charles City, and Twin Rocks. This could include process audits, operator training, and equipment maintenance to reduce defect-related downtime.
o	Consider cross-plant quality reviews to share best practices and address common issues.
o	Invest in automation and technology to reduce manual errors, enhance visibility and ensure consistency across operations.
3.	Enhanced Quality Control Measures
o	Implement more rigorous incoming quality inspection and testing for raw materials and corrugates, given their significant contribution to downtime.
o	Work on root cause analysis for mechanical and logistics defects, addressing equipment maintenance needs and optimizing supply chain processes.
o	Focus on resolving the "Not Certified" and "Bad Seams" issues by tightening quality control measures, revising inspection procedures, ensuring compliance with regulatory standards and implementing continuous improvement projects targeting these defect categories.
o	Conduct regular training sessions for production staff on quality control and establish a cross-functional team to monitor and address quality issues
4.	Identify and Mitigate Other Downtime Factors:
o	Investigate non-defect-related causes of downtime, including equipment failures, power issues, and staffing shortages. Implement preventive maintenance and contingency plans.
o	Use downtime data to identify patterns or external factors that correlate with high downtime events.
CONCLUSION
The supplier quality and performance analysis revealed significant correlations between defective materials, downtime and financial losses. Key findings highlighted worst-performing vendors (Yombu, Avamm, Meejo) and plant-specific issues in Hingham, Charles City & Twin Rocks. Raw materials and Corrugates emerged as problematic material types. The analysis demonstrated the need for enhanced quality control measures, regular audits and feedback for vendor improvement.
By addressing supplier quality issues and implementing total quality management, the company can improve production efficiency, reduce costs (estimated $2.16 million), and enhance customer satisfaction. Continuous monitoring and analysis of supplier performance will ensure sustainability. Effective implementation will require employee training, involvement and a cultural shift toward continuous improvement.



