# LengthOfStay Predictive Dasboard

# Project OVerview: 
This project analyzes hospital admission data to predict patient length of stay (LoS). By identifying key risk factors at admission, the dashboard enables proactive resource allocation and improved patient flow management.

###### Dataset: Microsoft Hospital Length of Stay dataset (100,000+ admissions, 28 clinical features)

# Data Cleaning:

###  Data Preparation
- Renamed columns for consistency and readability:
  * Original names are now clear and descriptive names
  * Ensured consistent naming convention (ex: all flags end with "_Flag")
  * This standardization allows for seamless analysis across Excel, SQL, R, and Tableau

### Data Optimization
- Reorganized fields to prioritize unique identifiers moved Facility_ID to the front of the dataset. This improves:
  * Data navigation efficiency
  * Lookup performance when joining tables
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
  * The consistent 4 day length of stay indicates this is a patient population with routine medical or surgical needs, not complex tertiary care cases. This allows for hospitals to be confident in staffing and bed allocation planning.

Next Question: Does this pattern hold across all admission types and months, or are there subgroups with different distributions?
