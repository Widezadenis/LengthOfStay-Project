# LengthOfStay Predictive Dasboard

# Goal: 
Predict patient length of stay at admission to enable proactive hospital resource planning.

# Business Impact: 
Reducing average LoS by just 1 day can save hospitals millions annually while improving patient throughput and bed availability.

###### Dataset: Microsoft Hospital Length of Stay dataset (100,000+ admissions, 28 clinical features)

# Data Cleaning:

###  Data Preparation
- Renamed columns for consistency and readability:
  * Original cryptic names are now clear, descriptive headers
  * Ensured consistent naming convention (ex: all flags end with "_Flag")
  * This standardization enables seamless analysis across Excel, SQL, and Tableau

### Data Optimization
- Reorganized fields to prioritize unique identifiers (Facility_ID, Episode_ID) at the front of the dataset. This improves:
  * Data navigation efficiency
  * Lookup performance when joining tables
  * Quick identification of primary keys

### Feature Engineering
- Created new temporal features from Admission_Date:
  * Admission_Month: Allows for seasonal pattern analysis (ex: higher LoS in winter months)
  * Day_of_Week: Identifies admission day patterns (ex: weekend admissions may have different LoS due to staffing)
- These engineered features are critical for understanding how timing affects patient outcomes and resource needs.

### Data Quality Verification
- Confirmed no null values in key fields (Episode_ID, Facility_ID, Admission_Date)
- Validated that Length_Of_Stay is positive and reasonable (0-17 days)
- Verified clinical flags contain only binary values (0/1)

<img width="1438" height="683" alt="Screenshot 2026-02-24 at 8 58 14 PM" src="https://github.com/user-attachments/assets/74e6153e-4bf3-4a79-ad03-5a037b35f83d" />

# Exploratory Analysis: 
- Question: What factors most strongly correlate with longer length of stay?

## Length of Stay Distribution
- Mean: 4.0 days
- Median: 4.0 days
  * Key Insight: Unlike my ER wait times project (81 min mean, 60 min median), this dataset shows a perfectly symmetrical distribution. The equal mean and median indicate no extreme outliers skewing the average—hospital stays are consistently clustered around 4 days.

Clinical Interpretation: This pattern suggests the dataset likely represents general medical/surgical patients rather than complex tertiary care cases. Resource planning can be based on predictable 4-day stays across most patient populations.

Next Question: Does this pattern hold across all admission types and months, or are there subgroups with different distributions?
