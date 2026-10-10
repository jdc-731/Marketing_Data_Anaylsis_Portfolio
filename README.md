# UCI Online Customer & Product Funnel Analysis 
## Executive Summary:
The objective of this project is to identify customer segments and campaign characteristics associated with higher term deposit conversion rates. Using SQL, Python, and Power BI, I analyzed 45,211 customer records to evaluate customer characteristics, campaign performance, and conversion behavior. The analysis provides recommendations for improving customer targeting and marketing campaign efficiency.

### Business Objective:
Marketing teams must determine which customers to target, how frequently to contact them, and where to allocate campaign resources.

Without a clear understanding of customer segmentation and conversion performance, the business is risking repeatedly contacting customers who are unlikely to convert while overlooking segments that respond more favorably. 

### Methodology:
Step 1: Data Preparation 
The dataset was organized for analysis, with relevant customer attributes and campaign outcome measures arranged into fields suitable for aggregation.
Before finalizing the project, the data preparation process should be documented to confirm how missing values, duplicate records, inconsistent categories,a nd any invalid values were handled

Step 2: Customer Segmentation
Pivot tables were used to compare marketing perfomance across available customer attributes, including:
-Job or occupational category
-Marital status
-Education
-Generation or age group, where defined in the data set
-Number of marketing contacts 
-Marketing channel
This segmentation approach allows campaign performance to be. examined across different customer groups rather than relying exclusively on overall averages.

Step 3: Contact Frequency Analysis
Customers were grouped according to marketing contact frequency. Conversion counts and conversion rates were compared across these groups to examine whether additional contact attempts were associated with better or worse conversion performance. 

Step 4: Conversion Rate Analysis
Conversion rate was calculated by dividing the number of contacts or eligible records in each segment, multiple any 100.
The denominator must math the dataset's actual definition of contact or eligible customers.

Step 5: Segment Prioritization
Segment-level conversion efficiency and conversion or revenue volume were compared to help identify potentially valuable audiences.
Where ranking or a combined priority score were used, their calculation and weighting should be documented before making final recommendation. 



###  Preliminary Findings:  
### Limitations and Next Steps: 
