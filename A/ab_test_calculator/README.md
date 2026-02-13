
## **Project Overview: A/B Test Significance Calculator**

This project automates the calculation of statistical significance for A/B testing experiments using Python instead of manual online calculators. The solution enables consistent, scalable, and reproducible analysis across experiments and segments.

**Business Objective:**
To determine whether product changes introduced in the test group (B) lead to meaningful improvements in key conversion metrics compared to the control group (A), or whether observed differences are attributable to random variation.

---

## **Analyzed Metrics**

Each metric is expressed as a **conversion rate**, with the total number of sessions used as the denominator to ensure comparability across groups:

* **add_payment_info / session** – Number of sessions where payment information was added.
* **add_shipping_info / session** – Number of sessions where shipping information was added.
* **begin_checkout / session** – Number of sessions where checkout was initiated.
* **new_accounts / session** – Number of sessions resulting in account creation.

---

## **Tech Stack**

* **SQL (BigQuery)** – Data extraction and transformation
* **Python (Pandas, NumPy)** – Data processing and aggregation
* **SciPy (scipy.stats.norm)** – Statistical computations
* **Google Colab** – Execution environment and BigQuery authentication

---

## **Methodology**

### **Statistical Framework**

* **Null Hypothesis (H₀):**
  Conversion rates in the control and test groups are equal.

* **Alternative Hypothesis (H₁):**
  Conversion rates differ between groups.

* **Statistical Test:**
  Two-proportion Z-test

* **Significance Level (α):**
  0.05 (95% confidence level)

The Z-test evaluates whether the difference in conversion rates between groups exceeds what would be expected from sampling variability.

---

### **Segmentation Strategy**

The analysis is performed at two levels:

1. **Total Experiment Level** – Overall experiment impact
2. **Segment Level** – Performance differences across:

   * Country
   * Device
   * Channel
   * Continent

This segmentation helps identify heterogeneous effects that may be masked in aggregate results.

---

## **Key Features**

* **Scalable Architecture** –
  Metrics and dimensions are defined via configuration structures, enabling automatic expansion without modifying core logic.

* **Reusable Statistical Engine** –
  A centralized `proportion_z_test()` function encapsulates all statistical calculations and validation rules.

* **Edge Case Handling** –
  Prevents invalid computations (e.g., zero denominators, degenerate pooled proportions).

* **Decision-Oriented Output** –
  Results include conversion rates, uplift %, Z-statistics, p-values, and significance flags.

---

## **Output Structure**

Results are exported in `.csv` / `.xlsx` formats with the following fields:

* `test_number` – Experiment identifier
* `metric` – Conversion metric name
* `numerator_ev` / `denominator_ev` – Control group counts
* `conversion_rate_ev` – Control conversion rate
* `numerator_co` / `denominator_co` – Test group counts
* `conversion_rate_co` – Test conversion rate
* `metric_change_%` – Relative conversion change
* `z_stat` – Z-test statistic
* `p_value` – Statistical significance indicator
* `significant` – Boolean decision flag
* `dimension` – Segmentation dimension
* `dimension_value` – Segment value

---

## **Business Value**

This tool allows analysts and product teams to:

* Rapidly evaluate experiment outcomes
* Distinguish real effects from noise
* Detect segment-specific behavior
* Standardize experimentation workflows

---
## **Results**
* **[A/B Test Significance Calculator](./ab-test-significance-calculator)**
* **[View CSV FILE](https://drive.google.com/file/d/1dvBsvxt6zkhTb_me-jTMm9KrWe4KHzmr/view?usp=sharing)**
* **[View Excel File](https://docs.google.com/spreadsheets/d/19RVpOy3DeleAEH4L-0DVow7Xx5TnR80Z/edit?usp=sharing&ouid=111842347865975349280&rtpof=true&sd=true)**
* **[Tableau Dashboards](https://public.tableau.com/shared/9B2344D2T?:display_count=n&:origin=viz_share_link)**
