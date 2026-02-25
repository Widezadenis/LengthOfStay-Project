# LengthOfStay Predictive Dasboard

## Goal: 
Predict patient length of stay at admission to enable proactive hospital resource planning.

## Business Impact: 
Reducing average LoS by just 1 day can save hospitals millions annually while improving patient throughput and bed availability.

###### Dataset: Microsoft Hospital Length of Stay dataset (100,000+ admissions, 28 clinical features)

## Data Preparation
- Renamed columns for consistency and readability:
  * Original cryptic names are now clear, descriptive headers
  * Ensured consistent naming convention (ex: all flags end with "_Flag")
  * This standardization enables seamless analysis across Excel, SQL, and Tableau

## Data Structure Optimization
- Reorganized fields to prioritize unique identifiers (Facility_ID, Episode_ID) at the front of the dataset. This improves:
  * Data navigation efficiency
  * Lookup performance when joining tables
  * Quick identification of primary keys
