# Bank Telemarketing Campaign: <br>
Conversion & Segment Prioritization 
## Executive Summary:
The objective of this project is to identify customer segments and campaign characteristics associated with higher conversion rates. I used SQL in BigQuery and Google Sheets to compare conversion rates across channels, contact frequency, and customer segments, then combined conversion rate with converted account balance into a priority score.
Headline findings
Best channel: Cellular converts at 14.92% and produces about 83% of all conversions. <br>
Contact sweet spot: Conversion holds near 11% through 3 contacts, then declines. Cap outreach at about 3 contacts. <br>
Segment to prioritize: Millennial, single, management, tertiary education ranks first. The top four segments were identical at minimum sizes of 500 and 300 customers. <br>

## Business Objective:
Marketing teams must determine which customers to target, how frequently to contact them, and where to allocate campaign resources.

Without a clear understanding of customer segmentation and conversion performance, the business is risking repeatedly contacting customers who are unlikely to convert while overlooking segments that respond more favorably. 

### Data
Source: UCI Machine Learning Repository, Bank Marketing dataset (bank-full). [https://archive.ics.uci.edu/dataset/222/bank%2Bmarketing.com] 
Size: 45,211 customer records, 5,289 conversions (11.70% overall conversion rate) <br>
One row = one customer. y = TRUE means the customer subscribed to a term deposit (a conversion). <br>
Fields used: age, job, marital, education, balance, contact (marketing channel), campaign (number of contacts to that customer), y. <br>
Tools: BigQuery (SQL) and Google Sheets. <br>
Data quality: Job and marital status have no missing values. Missing information appears in education (1,857 rows, 4.1%) and contact channel (13,020 rows, 28.8%, recorded as "unknown"). There are no duplicate rows, and all values were within expected ranges. Negative balances were kept because they represent overdrawn accounts. <br>

### Methodology:
1. Channel performance: <br>
  Customers were grouped by contact channel, and I calculated customers reached, conversions, and conversion rate. <br>
2. Contact frequency: <br>
   Customers were grouped by number of contacts (1, 2, 3, 4, 5-9, 10+) and conversion rates were compared across groups. <br>
3. Segment prioritization: <br>
   Segments combine generation, job, marital status, and education.
Each segment was ranked on three measures: conversion rate, total converted balance, and average customer balance. The three ranks are added with equal weight to give a combined priority score (lower is better), with ties broken by total converted balance.
Generation uses age-based bands, which are  official birth-year cohorts: Gen Z (29 and under), Millennial (30-45), Gen X (46-61), Boomer (62-80), Silent Generation (81+).
Segments need at least 500 customers so that conversion rates are reliable. A 300-customer sensitivity check produced the same top segments.

### Key Findings:
 1. Which marketing channel converts the most? <br>
    Cellular reaches about 65% of customers and drives about 83% of conversions. Telephone performs nearly as well on a small base and is worth testing at larger scale. About 29% of customers have an unknown channel that converts at roughly one-third the cellular rate, which points to a tracking gap. <br>
    <img width="750" height="393" alt="Channel Analysis " src="https://github.com/user-attachments/assets/17f0b1b9-a78d-45a4-9f9f-a65969caeb75" />

2. What is the <I> sweet spot </i> for the number of contacts? <br>
  Conversion holds steady at about 11.2% for customers contacted 2 or 3 times, then falls with each additional contact, reaching 4.17% at 10+. The sweet spot is up to about 3 contacts. Returns diminish after that.
<img width="676" height="371" alt="Contact Frequency" src="https://github.com/user-attachments/assets/ae9ac3d3-1640-4385-832e-c978ba535d39" />


3. Which customer segments should marketing prioritize? 
<ul>
<li> Priority 1 has the largest converted balance and the second-best conversion rate. </li>
<li> Priority 2 has the highest average balance. </li>
<li> Priority 3 has the highest conversion rate of the four but a small base, which makes it a good efficiency test. </li>
<li> Priority 4 is the largest pool, at a lower rate. </li>
<li> Deprioritize: Millennial, married, technician, secondary (1,783 customers at 7.68%). It reaches the top 10 only because of its size. </li>
</ul>

<img width="750" height="593" alt="original-06147B19-8823-45D0-9794-890E5DC3F1F7" src="https://github.com/user-attachments/assets/0249376d-b08d-4c2c-887d-987ff7826724" />

<img width="9530" height="1000" alt="Screenshot 2026-10-11 at 1 20 01 AM" src="https://github.com/user-attachments/assets/aeb36e91-42d7-4d54-8413-a39623dd3b13" />


### Recommendations:
1. Target management / tertiary-education segments first, in the order shown above. <br>
2. Cap outreach at about 3 contacts per customer. <br>
3. Concentrate volume on cellular device verses a landline, test scaling telephone (landlines), and fix channel tracking for the 29% of customers with an unknown channel. <br>
4. Pilot Gen Z, single, management as a high-conversion, low-volume test group. <br> 


#### Limitations: 
<ul> 
<li> No cost data. Results show conversion and balance, not ROI. </li>
<li> Balance is a proxy for value, not realized revenue. </li>
<li> Selection effect in contact frequency:customers who convert early stop being contacted, so the decline at higher contact counts is a strong signal, not proof that extra contacts cause lower conversion. </li>
<li> Equal weighting of the three ranks is a judgment call, and ranks can reward size over efficiency. </li>
<li> Average balance is calculated across all customers in a segment, not only those who converted. </li>
<li> Unknown channel and education values limit how precisely channels and education levels can be compared.</li>
</ul>
