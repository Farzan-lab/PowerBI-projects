# Housing Market Strategic Analysis  
*A Data-Driven Investment Intelligence Framework*

---

# 📊 Strategic Points of View (POVs) & Analysis

## 1. The Interest Rate Shockwave (Macro Correlation)

**Visualization:**  
Dual-axis Line and Stacked Column Chart comparing:
- Average Purchase Price  
- Nominal Interest Rates  

**Insight:**  
The analysis reveals high sensitivity to borrowing costs. Historically, periods with interest rates below **1.5%** saw rapid price acceleration.

The recent transition to a **3.5%+ interest rate environment** created a visible cooling effect, demonstrating the **lag-time between rate hikes and market valuation adjustments**.

---

## 2. Market Sentiment & Negotiation Power

**Visualization:**  
Area Chart tracking the % Change between Offer and Purchase Price with a baseline at 0.

**Insight:**  
Conditional formatting was implemented to identify Buyer vs. Seller Markets.

- A negotiation gap wider than **-3%** consistently signals a buyer’s market.
- This acts as a **Market Thermometer**, identifying cooling demand before total price declines appear.

---

## 3. Investment Efficiency (Value Density)

**Visualization:**  
Scatter Plot comparing:
- SQM (Size)  
- Purchase Price (Total Cost)

**Insight:**  
- Villas represent the highest total capital outlay.
- Apartments consistently show the highest **Price per SQM**.

Urban density therefore provides a **Liquidity Premium** and stronger value concentration.

---

## 4. Strategic Risk Profiling (The CV Metric)

**Visualization:**  
Matrix and Scatter Chart using the Coefficient of Variation (CV).

**Insight:**  
By normalizing volatility, regions can be categorized as:

- High Value + Low Risk → Stable  
- Low Value + High Volatility → Speculative  

This enables cross-district risk comparison despite different price levels.

---

## 5. The Vintage Premium (Architectural Value)

**Visualization:**  
Clustered Column Chart using decade-based binning.

**Insight:**  
A **U-shaped value curve** is observed:

- Pre-1900 properties → Premium  
- Post-2010 energy-efficient builds → Premium  
- 1960s–1980s housing → Market value floor  

---

# 🛠️ Technical Deep Dive

## Advanced DAX Measures

Custom measures were developed beyond basic aggregation.

### Relative Market Risk (CV Formula)

\[
CV = \frac{STDEV.P(Price)}{AVERAGE(Price)}
\]

### Market Share %

Calculated using ALL() and CALCULATE() to remove filter context.

### Year-over-Year (YoY) Growth

Time-intelligence functions used to track market momentum.

---

## Data Engineering (Power Query)

- Data Imputation for missing macroeconomic variables  
- Dynamic decade-based binning for building age  
- Star Schema design using:
  - Dim_Date
  - Dim_Geography  

---

# 📐 Formulas & Analytical Applications

---

## 1️⃣ Average Price per Square Meter

```DAX
Avg Sqm Price = AVERAGE('Housing Data'[sqm_price])
```

### 📌 Purpose

Calculates the average price per square meter across the selected filter context.

### 📊 Analytical Use

- Standardizes property comparison regardless of total size.
- Enables fair comparison between apartments, villas, and different districts.
- Useful for identifying value density and urban pricing premiums.
- Core metric for benchmarking regional competitiveness.

---

## 2️⃣ Average Negotiation Gap (Discount %)

```DAX
Avg Discount = AVERAGE('Housing Data'[%_change_between_offer_and_purchase])
```

### 📌 Purpose

Measures the average percentage difference between offer and final purchase price.

### 📊 Analytical Use

- Identifies Buyer vs. Seller Market conditions.
- A sustained negative gap below -3% signals weakening demand.
- Early indicator before total price declines.
- Supports sentiment tracking over time.

---

## 3️⃣ Relative Market Risk (Coefficient of Variation)

```DAX
Relative Market Risk =
DIVIDE(
    STDEV.P('Housing Data'[sqm_price]),
    AVERAGE('Housing Data'[sqm_price]),
    0
)
```

### 📌 Purpose

Calculates normalized volatility using the Coefficient of Variation (CV).

### 📊 Analytical Use

- Compares volatility across districts with different price levels.
- High Value + Low CV → Stable Investment Zones
- Low Value + High CV → Speculative Zones
- Enables risk-adjusted decision-making.
- Supports portfolio diversification strategy.

---

## 4️⃣ Market Share % (Transaction Volume Share)

```DAX
Market Share % =
DIVIDE(
    COUNT('Housing Data'[house_id]),
    CALCULATE(
        COUNT('Housing Data'[house_id]),
        ALL('Housing Data')
    )
)
```

### 📌 Purpose

Calculates each segment’s share of total market transactions.

### 📊 Analytical Use

- Identifies dominant districts or property types.
- Supports competitive landscape analysis.
- Detects shifts in buyer preferences.
- Useful for liquidity and demand concentration analysis.

---

# 🎯 Strategic Value

Together, these measures transform raw housing transaction data into:

- Comparative Market Intelligence  
- Risk-Adjusted Investment Profiling  
- Liquidity & Density Analysis  
- Early Sentiment Detection  
- Structural Market Segmentation  

This framework elevates the model from descriptive reporting to a **decision-support system for investors, analysts, and policymakers.**
