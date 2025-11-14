# 🚴‍♂️ Seoul Bike Sharing – Power BI Analytics Dashboard

This project analyzes the **Seoul Bike Sharing dataset** and transforms it into an interactive **Power BI dashboard** to uncover rental trends across seasons, temperature, time, holidays, and weekdays/weekends.

---

## 📌 Project Highlights
- Built a fully structured **Power BI data model**
- Created a **Calendar table** with year-month-day hierarchy
- Added **DAX measures** to form a semantic layer
- Designed **two dashboards**:
  - 📊 Overview Dashboard
  - 📈 Advanced Analysis Dashboard
- Time intelligence, drill-downs, slicers, and custom KPIs included

---

## 🛠️ Data Transformation Steps

### 1️⃣ Data Cleaning
- Renamed columns for readability  
- Validated and assigned proper data types  
- Removed errors & blanks  
- Converted `Functioning Day` from Yes/No → Boolean (True/False)

### 2️⃣ Calendar Table (Date Table)
Created using:
Additional columns:

Year

Month

MonthName

Day

Weekday

The table was marked as a Date Table for accurate time intelligence.

🔗 Data Model

Calendar[Date] → SeoulBikeData[Date]

One-to-Many relationship enables proper filtering & drill-down

📐 Semantic Layer (DAX Measures)
Total Rentals = SUM(SeoulBikeData[Rented_Bike_Count])

Avg Rentals = AVERAGE(SeoulBikeData[Rented_Bike_Count])

Weekend Rentals = 
    CALCULATE([Total Rentals], SeoulBikeData[WeekType] = "Weekend")

Weekday Rentals = 
    CALCULATE([Total Rentals], SeoulBikeData[WeekType] = "Weekday")

Total Functioning Days = 
    COUNTROWS(FILTER(SeoulBikeData, SeoulBikeData[Functioning_Day] = TRUE()))

Avg Temp = AVERAGE(SeoulBikeData[Temperature])
Using measures ensures accuracy across all visuals.

📊 Dashboard Pages
🔹 1. Overview Dashboard

Includes:

Total Rentals

Avg Rentals

Total Functioning Days

Avg Temp

Avg Humidity

Rentals by:

Month

Season

Weekday / Weekend

Day

🔹 2. Analysis Dashboard

Includes:

Rentals vs Temperature (Scatter Plot)

Rentals by Hour

Rentals by Holiday

Slicers: Season, Month, WeekType, Functioning Day

📁 Repository Contents

SeoulBikeDashboard.pbix (Power BI file)

Cleaned Excel dataset

README documentation

🎯 Key Insights Extracted

Summer has the highest rental demand (2.3M+ rides)

Rentals drop significantly in winter

Strong positive correlation between temperature & rentals

Weekdays account for 73% of overall rentals

Evening hours show maximum activity

🚀 Tools Used

Power BI

DAX

Excel

👩‍💻 Author

Anushree Kashyap
Data Analytics | Power BI | SQL | Visualization

```DAX
Calendar = CALENDAR(MIN(SeoulBikeData[Date]), MAX(SeoulBikeData[Date]))
