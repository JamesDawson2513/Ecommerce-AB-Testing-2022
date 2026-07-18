# Ecommerce-AB-Testing-2022
My first AB test project using the data from https://www.kaggle.com/datasets/putdejudomthai/ecommerce-ab-testing-2022-dataset1/data.

# E-Commerce A/B Testing: Old vs. New Webpage

## Introduction

The company has developed a new webpage and wants to determine if it has resulted in an increase in paying users. To do this, we conduct an AB test.

We have two equally-sized gropus:
* **Control Group (A):** Presented with the old webpage
* **Treatment Group (B):** Presented with the new webpage

Data was collected for both gropus to monitor conversion rates, and we apply hypothesis tests to arrive at a conclusion as to whether the change is statistically significant.

---

## About the Dataset
The dataset contains information regarding user interactions during the A/B test. 
* **`user_id`:** Unique user identifier
* **`timestamp`:** Time of the interaction
* **`group`:** Specifies whether the user is in the `treatment` or `control` group
* **`landing_page`:** Specifies whether the user saw the `old_page` or `new_page`
* **`converted`:** Sign-up status after viewing the page (0 for no, 1 for yes)



---

## A/B Test Steps & Methodology

### 1. Create the Hypothesis
We want to test if the new page increased the number of paying users.
* **$H_0$:** There is no statistically significant difference between the old page and the new page.
* **$H_1$:** There is a statistically significant difference between the old page and the new page.

### 2. Data Normality
To determine which statistical test to use, we check the distribution and variance of our data.

**Normality Assumption**
* **$H_0$:** The data is normally distributed
* **$H_1$:** The data isn't normally distributed




### 2. Exploratory Data Analysis (EDA) & Cleaning
Before testing, the data was cleaned and explored:
* Duplicate `user_id` records were dropped to ensure data integrity
* The mean conversion rate for the control group (`old_page`) was roughly 12.017%
* The mean conversion rate for the treatment group (`new_page`) was roughly 11.872%

### 3. Assumption Checks
To determine the correct statistical test, we must check the distribution and variance of our data.

**Normality Assumption**
* **$H_0$:** The assumption of normal distribution is provided.
* **$H_1$:** The assumption of normal distribution is not provided.
* **Result:** The Shapiro-Wilk test was utilized[cite: 1]. The control group yielded a p-value of $9.036 \times 10^{-178}$, and the treatment group yielded a p-value of $6.263 \times 10^{-178}$[cite: 1]. Because $p < 0.05$, the assumption of normality is not met[cite: 1]. 

**Variance Homogeneity**
* **$H_0$:** Variances are homogeneous.
* **$H_1$:** Variances are not homogeneous.
* **Result:** Levene's test was used to check for equal variance in both groups[cite: 1]. The variances were found to be homogeneous.

### 4. Hypothesis Testing
Because the normality assumption was not met, a non-parametric test (Mann-Whitney U test) was selected instead of a parametric t-test[cite: 1].

* **Test Statistic:** $10259026653.0000$[cite: 1].
* **P-Value:** $0.2323$[cite: 1].

---

## Conclusion
The hypothesis conclusion is based on the p-value obtained from the Mann-Whitney U test. 

Because the p-value ($0.2323$) is greater than $0.05$, **we fail to reject $H_0$**[cite: 1]. 

**Final Takeaway:** There is no statistically significant difference in conversions between the new page and the old page[cite: 1]. Based on this analysis, the new page does not bring a profitable increase in paying users, and a full rollout is not currently recommended[cite: 1].
