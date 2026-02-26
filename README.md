# LengthOfStay Predictive Dasboard

# Project OVerview: 
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
  * Admission_Month: Allows for seasonal pattern analysis (ex: higher LoS in winter months)
  * Day_of_Week: Identifies admission day patterns (ex: weekend admissions may have different LoS due to staffing)
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
  * The consistent 4 day length of stay shows that this is a comumunity hospital with routine medical or surgical needs, not a tertiary care center. This allows hospitals to be confident in staffing and bed allocation planning.

- Questions:
   * Does length of stay increase during winter months?
   * Is it 4 days for everyone, or do some groups stay longer?
   * Do weekend admissions stay longer because of fewer specialists?
   * Which conditions increase length of stay? 

- Findings:
   * Length of is the same accross every month which means staffing needs are predicable year round.

