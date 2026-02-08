# 🏠 Danish Housing Market Intelligence (1992-2024)
### Strategic Data Analysis & Economic Correlation Suite

![Dashboard Overview](link_to_your_screenshot_here)

## 🎯 Executive Summary
This project provides a deep-dive analysis of the Danish real estate market over three decades. Unlike standard reporting, this dashboard correlates housing trends with **Macroeconomic Indicators** (Inflation & Interest Rates) to provide a 360-degree view of market drivers.

## 🚀 Key Business Insights (POVs)
Through this analysis, I have identified five critical market behaviors:

1. **Interest Rate Sensitivity:** Established a clear negative correlation between mortgage bond yields and purchase prices, identifying the "lag time" between rate hikes and price adjustments.
2. **Negotiation Dynamics:** Developed a "Market Temperature" gauge based on the `% change between offer and purchase price` to identify Buyer vs. Seller markets.
3. **Value Density Analysis:** Proved that while Villas hold higher total value, Apartments offer the highest "Value Density" per square meter.
4. **Market Stability & Risk:** Created a relative risk profile for Danish regions, distinguishing between homogeneous (stable) and volatile markets.
5. **The Vintage Premium:** Uncovered a "U-shaped" value curve showing that historical pre-1900 properties and modern 2010+ builds command higher premiums than mid-century constructions.

## 🛠️ Technical Implementation (The "Under the Hood")

### 1. Advanced DAX Measures
I moved beyond basic aggregates to create strategic business metrics:
* **Relative Market Risk (CV):** To normalize risk across different price points.
    ```dax
    Relative Market Risk (%) = DIVIDE(STDEV.P(sqm_price), AVERAGE(sqm_price), 0)
    ```
* **Market Share %:** Calculating the volume of transactions per segment relative to the total population.
* **Negotiation Volatility:** Using standard deviation to measure the unpredictability of price discounts.

### 2. Data Engineering (Power Query)
* **Data Cleaning:** Handled missing values in inflation and bond yield columns using context-aware imputation.
* **Dynamic Binning:** Created custom age-groups for properties to analyze the "Vintage Value."
* **Star Schema Optimization:** Implemented a robust data model with a dedicated `Dim_Date` table for time-intelligence calculations.

## 🎨 UI/UX Design Principles
* **Executive Layout:** 3-page navigation system for high-level summaries and deep-dive analytics.
* **Conditional Formatting:** Visual cues (Red/Green) to instantly signal market health.
* **Dual-Axis Visualization:** For direct comparison between economic rates and market prices.

---
## 📂 Repository Structure
* `/Data`: Raw dataset (Denmark Housing Data).
* `/Screenshots`: High-resolution captures of the 3-page dashboard.
* `Denmark_Housing_Analysis.pbix`: The source Power BI file.

## 👤 Contact
**[Your Name]** [Link to your LinkedIn]  
[Your Email]