
# Chocolate Factory – Customer Segmentation & Price Elasticity Analysis

Integrates demographic segmentation, behavioral analytics, and price-sensitivity modeling for five chocolate brands using customer attributes and purchase data.




## Introduction

This repository delivers a comprehensive analytical workflow that connects who the customers are, how they buy, and how price changes influence demand.
It unifies clustering, behavioral mapping, and price-elasticity estimation to guide data-driven pricing and marketing decisions.

Demographic Segmentation : discover clusters by age, income, and lifestyle.

Behavioral Linkage : relate segments to purchase incidence and brand choice.

Elasticity Modeling : quantify how demand reacts to price variation per brand and segment.

Actionable Insights : recommend optimal price points and promotion strategies.


## Customer Demographics & Income Analysis

This section presents the analysis of demographic, income, education, occupation, and settlement data, revealing key trends and socio-economic patterns across customer groups.

---

# Distribution of Age

-Age distribution is right-skewed; majority are between 20–40 years.

-A noticeable peak around 25–30 represents the most common customer group.

-Customers aged 50+ form a smaller proportion → younger consumer base.
---

# Distribution of Income
- Income is **right-skewed**, concentrated between **80 000 – 150 000 units**.  
- **High-income outliers (> 200 000)** raise the mean.  
- Median < mean ⇒ positively skewed distribution.  

---

# Average Income by Age (5-Year Bins)
Income generally **increases with age**, peaking between **60–70 years**.  
Younger customers earn less due to entry-level positions, while post-retirement levels stay high from pensions/investments.  

**Visual:**  
![Average Income by Age](screenshots/output.png)

---
# Average Income by Settlement Size
- Clear **urbanization effect:**  
  - **Large cities (Size 2)** → highest incomes  
  - **Medium towns (Size 1)** → moderate  
  - **Rural areas (Size 0)** → lowest  

**Visual:**  
![Average Income by Settlement Size](screenshots/output2.png)

---
# Average Income by Occupation Level
- Income rises sharply with occupation level.  
- **Occupation 2** ≈ 2× higher than **Occupation 0** → strong link between career level & income.  

**Visual:**  
![Average Income by Occupation Level](screenshots/output3.png)

---
# Average Age by Occupation Level
- Higher occupation levels correspond to **older averages**.  
- Reflects typical career progression with experience.  

**Visual:**  
![Average Age by Occupation Level](screenshots/output4.png)

---
# Marital Status Distribution by Occupation
- **Occupation 2:** more **single** individuals.  
- **Occupation 0–1:** mostly **married**.  
- Indicates delayed marriage or career-first priorities in higher roles.  

**Visual:**  
![Marital Status by Occupation](screenshots/output5.png)

---
# K-Means Clusters (PCA Projection)
Distinct color-coded groups confirm strong separation across clusters.  

**Visual:**  
![K-Means Clusters (PCA Projection)](screenshots/output6.png)

---

# Final Segmentation (k = 4)
| Cluster | Segment Description | Age (mean) | Income (mean) | Dominant Education | Occupation | Settlement | Gender | Marital Status |
|:--|:--|:--:|:--:|:--|:--|:--|:--|:--|
| **0** | Mid-Age Rural Low-Income (Low-Skill) | 34.6 | 90 807 | High School | Low | Rural | ♀ 64 % | Single 56 % |
| **1** | Mid-Age City High-Income (Mid-Skill) | 36.8 | 137 369 | High School | Mid | City | ♂ 100 % | Single 100 % |
| **2** | High-Age Town High-Income (Mid-Skill) | 54.6 | 163 925 | Graduate | Mid | Town | ♂ 50 % | Married Majority |
| **3** | Mid-Income Rural Married (Mid-Skill) | 42 | ≈ 140 000 | High School | Mid | Rural | ♀ 71 % | Married 100 % |

---

# Key Insights
1. **Cluster 0 →** Rural, low-skill, female-dominant, low income.  
2. **Cluster 1 →** Urban, high-income, single males.  
3. **Cluster 2 →** Older, educated, high-income families.  
4. **Cluster 3 →** Married rural mid-income segment.  

---

# Purchase Data Analysis & Price Elasticity  

Builds upon segmentation by exploring **purchase incidence**, **brand market share**, **promotion influence**, and **price sensitivity** across customer clusters.  


## **Data Understanding**

Upon inspection, several records showed `quantity = 0`.  
Further analysis revealed:
- Whenever `Incidence = 0` (no purchase), both **quantity** and **brand** are also `0`.  
- The value `brand = 0` **only appears** alongside `Incidence = 0`.  

Hence, `brand = 0` is simply a **placeholder** used when a customer does **not make a purchase**.  

---
# Purchase Incidence*
- **75.1 %** of records correspond to **no purchase (Incidence = 0)**.  
- Only **24.9 %** represent actual purchases (Incidence = 1).  
- Indicates that most interactions don’t convert into transactions.

**Visual:**  
![Incidence: Count and Percentage](screenshots/output7.png)

---

# Brand Market Share
- **Brand 5** dominates with **34 %** of all purchases.  
- **Brand 3** trails with only **5.8 %**.  
- Brands 5 and 2 together capture **≈ 65 %** of the total market.

**Visual:**  
![Brand Market Share](screenshots/output8.png)

---

#Average Quantity Purchased per Brand
- Typical transaction size ranges **2 – 4 units**.  
- **Brands 1 & 3** see the largest average quantities, while **Brand 5**—despite market leadership—shows smaller quantities per purchase.

**Visual:**  
![Average Quantity per Brand](screenshots/output9.png)

---

# Promotion Analysis
- **66.1 %** of all purchases occur **under promotion**.  
- Promotions boost purchase probability but only modestly affect quantity.  
- Weekly promotion share consistently **> 50 %**, confirming strong marketing reliance.

**Visual:**  
![Percentage of Transactions with Promotions](screenshots/output10.png)

---

# Generation-wise Purchase Quantity
- **Boomers** purchase the largest average quantities.  
- **Gen Z / Millennials** buy smaller quantities but respond strongly to promotions.  

**Visual:**  
![Average Quantity per Generation](screenshots/output11.png)

---
# Purchase Rate by Cluster
- **Cluster 1** (premium spenders) leads with a **32.8 %** purchase rate.  
- **Cluster 2** (promotion-driven buyers) shows the lowest conversion at **19.8 %**.  

**Visual:**  
![Purchase Rate by Cluster](screenshots/output12.png)

---

# **Cluster-Level Purchase & Behavior Summary**

| Cluster | Customers | Avg Age | Avg Income | Avg Incidence | Preferred Brand | Promotion Usage | Segment |
|:--|:--:|:--:|:--:|:--:|:--:|:--:|:--|
| **0** | 12 746 | 29.4 | 103 703 | 0.21 | 2 | 60.7 % | Price-Sensitive / Budget |
| **1** | 13 010 | 37.9 | 140 263 | 0.33 | 5 | 60.6 % | Premium / VIP |
| **2** | 21 442 | 36.3 | 100 681 | 0.20 | 2 | 61.6 % | Mid-Tier / Deal-Seekers |
| **3** | 11 495 | 54.9 | 160 577 | 0.29 | 4 | 61.9 % | Affluent / Premium Loyalists |

---

## **Cluster Insights Summary**

### **Cluster 0 — Young Budget Shoppers**
- Youngest, low-income, lowest purchase rate (0.21).  
- Promotion-responsive, prefer mid-priced **Brand 2**.  
- Highly price-sensitive.  

---

### **Cluster 1 — Mid-Age High-Spending Loyalists**
- High income & highest incidence (0.33).  
- Prefer premium **Brand 5**.  
- Loyal, less price-sensitive, average promo usage.  

---

### **Cluster 2 — Large Mid-Tier Deal-Seekers**
- Largest group; low per-customer frequency.  
- Heavy promotion dependence (61.6 %).  
- Prefers **Brand 2**, buys mainly on discount.  

---

### **Cluster 3 — Older Affluent Customers**
- Wealthiest & oldest (avg age 55).  
- Loyal to premium **Brand 4**.  
- Moderate sensitivity to promotions; steady buyers.  

---
# Price Elasticity Analysis

To measure demand sensitivity, price elasticity was estimated for each **brand × cluster** combination.  
The elasticity metric indicates how much demand changes for a 1 % price change.
i made it with my team farida and omar through our internship at fixed solutions
**Visual Example (Cluster 3)**  
![Purchase Probability vs Price](screenshots/output13.png)

---

### **Elasticity Highlights by Cluster**

#### **Cluster 0 — Budget Customers**
- **Highly elastic** (E ≈ −7 to −4).  
- Small price hikes strongly reduce demand.  
- **Brand 3** anomalously positive (E ≈ +4) → possibly brand perception issue.

#### **Cluster 1 — Premium Loyalists**
- **Low elasticity** (E ≈ −5 to −1).  
- Stable demand; moderate tolerance for price shifts.  
- **Brand 5** nearly inelastic (E ≈ −1.0).

#### **Cluster 2 — Promotion-Driven Mid-Tiers**
- **Mixed elasticity**: some brands over-react (E ≈ −9), others positive outliers (E ≈ +18).  
- Heavily promotion-dependent — discounts drive spikes.

#### **Cluster 3 — Older Affluent**
- **Moderate elasticity** (E ≈ −7 to −2).  
- Premium focus (Brands 4 & 5) shows relatively stable demand.

---

# Key Takeaways
- **Premium segments (1 & 3)** show steady demand → ideal for **premium pricing**.  
- **Cluster 2** needs **discount strategy optimization**  heavy promo reliance reduces profit margins.  
- **Cluster 0** extremely **price-sensitive**  focus on **value packs** or **low-tier offers**.  

---

