# LengthOfStay Predictive Dashboard

# Project Overview: 
This project analyzes hospital admission data to predict patient length of stay (LoS). By identifying risk factors at admission, this dashboard aims to improve resource allocation and patient flow management.

###### Dataset: Microsoft Hospital Length of Stay dataset (100,000+ admissions, 28 clinical features)

# Data Cleaning:

###  Data Preparation
- Renamed columns for consistency and readability:
  * Original names are now clear and have descriptive names
  * Ensured consistent naming convention (ex: all flags end with "_Flag")
- This allows for seamless analysis across Excel, SQL, R, and Tableau

### Data Optimization
- Reorganized fields to prioritize unique identifiers moved Facility_ID to the front of the dataset. This improves:
  * Data navigation
  * Lookup performance
  * Quick identification of primary keys

### Feature Engineering
- Created new temporal features from Admission_Date:
  * **Admission_Month:** Allows for seasonal pattern analysis (ex: higher LoS in winter months)
  * **Day_of_Week:** Identifies admission day patterns (ex: weekend admissions may have different LoS due to staffing)
- These features are critical for understanding how timing affects patient outcomes and resource needs.

### Data Quality Verification
- Confirmed no null values in Episode_ID, Facility_ID, Admission_Date fields
- Validated that Length_Of_Stay is positive (0-17 days)
- Verified clinical flags contain only binary values (0/1)

<img width="1438" height="683" alt="Screenshot 2026-02-24 at 8 58 14 PM" src="https://github.com/user-attachments/assets/74e6153e-4bf3-4a79-ad03-5a037b35f83d" />

# Exploratory Analysis: 
- Question: What factors strongly correlate with longer length of stay?

## Length of Stay Distribution
- Mean: 4.0 days
- Median: 4.0 days
  * Key Insight: The equal mean and median shows that there are no outliers that are skewing the average, hospital stays are around 4 days.
  * The consistent 4 day length of stay shows that this is a community hospital with routine medical or surgical needs, not a tertiary care center. This allows hospitals to be confident in staffing and bed allocation planning.

- Questions:
   * Does length of stay increase during winter months?
      * Findings:
         * Staffing needs are predictable year round
         * Holidays and winters do not impact length of stay
<img width="830" height="902" alt="image" src="https://github.com/user-attachments/assets/257a1810-22a0-4372-8bfb-d8d67d87d10e" />
            
   * Do weekend admissions stay longer because of fewer specialists?
      * Findings: weekend admissions have the same length of stays with weekdays which does not confirm my hypothesis that weekend stays would be longer because of less specialists.
<img width="830" height="902" alt="image" src="https://github.com/user-attachments/assets/329ce1b0-72e8-4641-ae09-144910267d82" />

   * Which conditions affect length of stay?
      * Findings: Dialysis patients stay 2.14 days longer than patients without dialysis
        
| Condition | Absent | Present | Impact | 
| ---  | --- | --- | --- | 
| Dialysis_Renal_End_Stage_Flag | 3.92 | 6.06 | 2.14 | 
| Fibrosis_Flag | 3.99 | 6.11 | 2.12 | 
| Psychological_Disorder_Flag  | 3.90 | 5.99 | 2.09 | 
| Malnutrition_Flag    | 3.91 | 5.81 | 1.90 | 
| Blood_Disorder_Flag | 3.85 | 5.74 | 1.89 | 
| pneumonia_Flag | 3.94 | 5.58 | 1.64 | 
| Major_Psychological_Disorder_Flag  | 3.62 | 5.21 | 1.59 |
| Iron_Deficiency_Flag | 3.85 | 5.41 | 1.56 | 
| Substance_Dependence_Flag  | 3.91 | 5.35 | 1.44 | 
| Depression_Flag  | 3.93 | 5.23| 1.29 |
| Asthma_Flag  | 3.96 | 5.01 | 1.05 |
        
   * Does abnormal lab values affect length of stay?
      * Findings: Abnormal lab values do not affect length of stay
 <img width="796" height="908" alt="image" src="https://github.com/user-attachments/assets/becf02ec-c475-450d-81e6-8a3162cb7320" />

# Predictive Risk Scores: 
- Based on my previous analysis I created a weighted risk score to find out which patients will stay longer.
  
| Risk Level | Average Stay | Number of Patients | Percentage of Population | 
| ---  | --- | --- | --- |
| Low Risk | 3.63 | 79,400 | 79.4% |
| Medium Risk | 5.14 | 12,596 | 12.6% |
| High Risk  | 5.93 | 8,004 | 8.0% |

| Risk Category | Risk Distribution |
| :---: | :---: |
| <img width="892" height="908" alt="image" src="https://github.com/user-attachments/assets/a8b8b7d5-ec6d-4d58-8537-a64a1c2001aa" /> | <img width="892" height="908" alt="image" src="https://github.com/user-attachments/assets/75a1034d-5c42-48d5-841e-ddf128a2cc82" /> |

# Business Impact
**Realistic Goal (High Risk → Medium Risk):**
- 8,004 patients × 0.79 extra days = **6,323 bed-days annually**
- At $3,000 per bed-day = **$19 million in potential savings**

**Best Case (High Risk → Low Risk):**
- 8,004 patients × 2.3 extra days = **18,409 bed-days annually**
- At $3,000 per bed-day = **$55.2 million in potential savings**

# Recommendations
- Dialysis Patient Protocol: Early interventions for Dialysis patients to reduce number of days.
- Nutrition Support: Nutrition screening within 24 hours of admission.
- Mental Health Integration: Integrate mental health providers in medical units.

# Conclusions
This analysis successfully identified key drivers of length of stay in a community hospital setting:

- **Consistent baseline:** 4-day average stay with no seasonal variation
- **Top risk factors:** Dialysis (+2.14 days), Fibrosis (+2.12 days), Psychological disorders (+2.09 days)
- **Validated risk score:** Clear separation between Low (3.6 days), Medium (5.1 days), and High Risk (5.9 days) patients
- **Business impact:** Targeting High Risk patients could save 6,300+ bed-days ($19M) annually

**Next Steps:** Implement early intervention protocols for High Risk patients and track impact on length of stay.

# Limitations 
- **Dataset:** Synthetic data may not reflect real-world complexity
- **Causation vs Correlation:** Conditions are associated with longer stays but don't prove causation
- **Missing factors:** No data on procedures, medications, or insurance type
     

