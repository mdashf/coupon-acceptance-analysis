# Will the Customer Accept the Coupon?

**UC Berkeley Executive Education — Practical Application 1 (Module 5.1)**

[**Open the completed Jupyter notebook**](prompt.ipynb) · [Dataset](coupons.csv)

## The question

Which driving circumstances and customer characteristics are associated with accepting a mobile coupon? This exploratory analysis uses the UCI In-Vehicle Coupon Recommendation survey, comparing acceptance across coupon types, then investigating **bar** and **coffee-house** offers in more detail.

## Key findings (nontechnical summary)

- **Overall:** 7,210 of 12,684 hypothetical driving scenarios (56.84%) resulted in coupon acceptance.
- **Bar offers:** 827 of 2,017 bar coupons were accepted (41.00%). Among respondents who reported their bar-going frequency, those who visited bars **more than three times per month** accepted 76.9% of bar coupons, compared with 37.1% for those visiting three times per month or fewer.
- **Age and habits:** Among respondents with known bar frequency, drivers aged over 25 who visited bars more than once monthly accepted 69.5% of bar coupons (n=420), compared with 33.4% for other respondents (n=1,576).
- **Travel context:** Drivers who visited bars more than once monthly, had no child passenger and did not work in farming/fishing/forestry accepted 71.3% (n=551), versus 29.5% for other respondents (n=1,445).
- **Coffee-house offers (independent investigation):** 3,996 coffee-house scenarios had 49.92% acceptance. Acceptance was **64.1% at 10 AM** (n=899) versus **41.3% at 6 PM** (n=1,093). Drivers with friends accepted 59.7% of coffee-house coupons (n=1,228), compared with 43.8% for drivers alone (n=2,256).

These figures describe *associations in a hypothetical-scenario survey*, not proven effects of a marketing intervention.

## Practical recommendations

1. **Segment by relevant past behavior.** Test bar offers with customers who already visit bars regularly; the descriptive acceptance gap is large.
2. **Test coffee-house timing.** In a controlled campaign, compare late-morning offers with early-evening offers rather than assuming the observed 10 AM advantage is causal.
3. **Consider driving context.** Passenger type and travel conditions may help explain acceptance; avoid targeting decisions based solely on one demographic variable.
4. **Measure real redemption.** Conduct randomized tests with actual coupon redemption and opt-in consent before deploying a targeting rule.

## Analysis and visualizations

The [notebook](prompt.ipynb) contains:

- Dataset inspection, missing-value review, and a documented cleaning decision.
- Overall acceptance rate, coupon-category counts, and temperature distribution.
- All required bar-coupon comparisons, with acceptance rates and subgroup sample sizes.
- Coffee-house comparisons by time, passenger, weather, destination, expiration and travel-time indicators.
- Labeled bar charts and a heatmap, plus a self-contained findings section.

**Data cleaning:** The `car` field is almost entirely missing (12,576 of 12,684 records) and is dropped. Missing visit-frequency categories are retained as `Unknown`; comparisons requiring bar-frequency information exclude the unknown-frequency records. No survey rows are discarded simply for having missing optional frequency data. Exact duplicate scenarios are retained because respondent identifiers are not available to establish whether they are duplicate responses.

**Interpretation limitations:** The data come from stated preferences in hypothetical scenarios, not observed purchases. Repeated scenarios may be correlated. Subgroup comparisons are exploratory, and some categories are small. The grouped restaurant frequency `4~8` includes exactly four visits, so treating it as *more than four* is only an approximation. No causal or population-generalizable claim is made.

## How to run

1. Download `prompt.ipynb` and `coupons.csv` into the same directory (or clone this repository).
2. Open the notebook in Jupyter and select a Python 3 kernel.
3. Run all cells in order. The notebook also supports several Vocareum dataset paths.

Requires `pandas`, `numpy`, `matplotlib`, `seaborn`, `IPython`, and Jupyter. The committed notebook includes executed outputs so that the results and charts can be inspected directly on GitHub.

## Source and credit

Dataset: [UCI In-Vehicle Coupon Recommendation](https://doi.org/10.24432/C5GS4P), attributed to the dataset's original creators and distributed under the repository's stated dataset license. Educational analysis prepared for the Berkeley Executive Education practical application assignment.
