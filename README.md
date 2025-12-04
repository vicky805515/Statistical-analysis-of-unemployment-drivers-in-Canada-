# Drivers of Unemployment in Canada: A Demographic and Economic Analysis

## Project Overview

This comprehensive statistical analysis examines the drivers of unemployment in Canada by leveraging data from Statistics Canada's Labour Force Survey (LFS). The project employs design-based statistical methodologies to investigate the complex relationships between unemployment and demographic characteristics including age, gender, education, and immigration status, while accounting for the LFS's sophisticated survey design.

## Problem Statement

Understanding unemployment trends at the population level requires rigorous statistical methods that account for complex survey designs. The Canadian Labour Force Survey uses stratified multi-stage sampling with clustering and weighting, necessitating appropriate analytical techniques that respect these design elements. This project demonstrates how neglecting survey design considerations can lead to biased estimates and misleading conclusions about employment patterns.

## Dataset

- **Source**: Statistics Canada Labour Force Survey (LFS)
- **Total Observations**: 111,645 records
- **Number of Variables**: 60
- **Geographic Coverage**: Canadian provinces (excludes territories and institutions)
- **Target Population**: Non-institutionalised population 15 years of age and over
- **Sampling Design**: Stratified multi-stage probability sample with rotating panel design
- **Survey Weights**: FINALWT variable accounts for design effects and non-response adjustments

### Key Variables Analyzed
- **LFSSTAT**: Labour Force Status (employed, unemployed, out of labour force)
- **SEX**: Gender (male, female)
- **AGE_12**: Age group categories
- **EDUC**: Education level
- **IMMIG**: Immigration status
- **HRLYEARN**: Hourly earnings
- **PROV/CMA**: Geographic location (province and census metropolitan area)
- **MARSTAT**: Marital status

## Technologies & Methods

### Statistical Software & Libraries
- **R** - Primary statistical programming language
- **Survey Package in R** - Specialized survey analysis package for complex designs
- **Base R & tidyverse** - Data manipulation and visualization

### Statistical Methods Employed
- **Weighted Descriptive Statistics** - Population-level estimates accounting for survey weights
- **Design-based Estimation** - Proper variance estimation accounting for stratification and clustering
- **Logistic Regression (Weighted)** - Modeling probability of unemployment with survey design adjustments
- **Chi-square Tests of Association** - Testing relationships between categorical variables
- **Survey Weighting Adjustments** - Accounting for non-response and coverage errors

## Methodology

### Survey Design Considerations

The analysis properly accounts for the LFS complex design:

1. **Stratification**: Each province divided into strata based on homogeneous labour market characteristics
2. **Clustering**: Two-stage sampling with ~6 clusters per stratum containing ~230 households
3. **Rotation Panel**: Six-month rotating design with five-sixths monthly overlap
4. **Weighting**: FINALWT variable adjusted for:
   - Selection probability (basic weight)
   - Sub-sampling adjustments
   - Non-response adjustments (~10% average)
   - Coverage errors via composite calibration

### Analytical Approach

1. **Data Preparation**
   - Loaded 111,645 observations with 60 variables
   - Identified and handled missing data strategically
   - Decoded categorical variables using Statistics Canada codebook

2. **Descriptive Analysis**
   - Computed weighted population estimates
   - Analyzed demographic distribution of employment status
   - Examined regional variations in unemployment rates

3. **Association Testing**
   - Chi-square test: Gender vs. Employment Status
   - Chi-square test: Education vs. Employment Status
   - Chi-square test: Age vs. Employment Status

4. **Regression Analysis**
   - Weighted logistic regression: Probability of unemployment
   - Weighted linear regression: Determinants of hourly earnings
   - Proper standard error calculation accounting for design effects

## Key Findings

### Gender Disparities in Employment Status
Chi-square test revealed a **significant association between gender and employment status**. Key observations:
- Higher proportion of men in employed category
- Women overrepresented in "out of labour force" category
- Suggests caregiving responsibilities and socio-economic factors affect women's participation
- Policy implication: Work-life balance initiatives could increase female workforce participation

### Education and Earnings
Regression analysis demonstrated **strong positive correlation between education level and hourly earnings**:
- Each additional education level associated with meaningful earnings increase
- Aligns with human capital theory
- Highest earners typically have tertiary education
- Policy implication: Investment in education yields significant economic returns

### Age and Income Profiles
Analysis revealed **positive association between age and hourly earnings**:
- Older workers command higher wages due to experience and seniority
- Typical age-income profile follows expected labour economics patterns
- Effect may plateau or reverse near retirement (requires further investigation)
- Reflects value of accumulated skills and work experience

### Immigration and Labour Outcomes
Study findings indicate **immigrants face different unemployment risks** based on years in Canada:
- Recent immigrants show higher unemployment rates initially
- Risk decreases with time in Canada
- Economic integration occurs progressively
- Important for immigration policy considerations

### Non-response and Data Quality
- Average non-response rate: ~10% of eligible households
- Weight adjustments applied to account for non-response
- Some employment-related variables missing (FTPTLAST, EVERWORK)
- Sensitivity to non-response bias acknowledged

## Results & Statistics

### Survey Design Effects
- Proper variance estimation critical due to clustering and stratification
- Design effects (DEFF) typically >1.0, indicating efficiency gains from survey design
- Failure to account for design leads to underestimated standard errors

### Key Statistical Findings
- Significant associations found: Gender × Employment Status, Education × Earnings
- Weighted population estimates properly represent Canadian labour force
- Design-adjusted confidence intervals appropriately wider than SRS equivalents
- Non-response adjustments validated through post-stratification

## Files in Repository

- `unemployment_analysis.R` - Complete R analysis script
- `unemployment_report.pdf` - Full written report with detailed findings
- `data_description.csv` - Data dictionary and variable descriptions
- `visualizations/` - Charts and graphs from analysis
- `README.md` - Project documentation (this file)

## Installation & Usage

### Requirements
```
R >= 4.0.0
survey >= 4.1
tidyverse >= 1.3.0
ggplot2 >= 3.3.0
```

### Installation Steps

1. Clone the repository:
```bash
git clone https://github.com/vicky805515/canada-unemployment-analysis.git
cd canada-unemployment-analysis
```

2. Install required R packages:
```r
install.packages(c("survey", "tidyverse", "ggplot2"))
```

3. Download Statistics Canada LFS data:
- Access: https://www150.statcan.gc.ca/n1/en/start
- Dataset: Table 14-10-0011-01 (Labour force characteristics by census division)

4. Run the analysis:
```r
source("unemployment_analysis.R")
```

## Key Learnings & Insights

### Methodological Insights
1. **Survey Design Matters**: Ignoring complex survey design leads to incorrect variance estimates
2. **Weighting is Essential**: Population-level inferences require proper weight application
3. **Design Effects Are Real**: Multi-stage sampling typically produces design effects >1
4. **Non-response Handling**: Weight adjustments effectively mitigate non-response bias

### Substantive Insights
1. **Demographic Factors**: Age, gender, and education significantly influence employment outcomes
2. **Immigration Integration**: Labour market integration of immigrants is progressive
3. **Gender Disparities**: Persistent gender gaps in labour force participation warrant policy attention
4. **Education Premium**: Strong education-earnings relationship supports human capital investment

## Limitations & Future Work

### Current Limitations
- Territorial data excluded due to methodological differences
- Cross-sectional design limits causal inference
- Missing data in some employment variables
- Excludes institutionalised population and armed forces

### Future Research Directions
- Time-series analysis examining unemployment trends across years
- Sector-specific analysis (industry variation in employment)
- Intersectionality analysis (combined effects of multiple demographic factors)
- Sensitivity analyses for missing data impact
- Survival analysis of unemployment duration
- Regional labour market dynamics and migration patterns

## Policy Implications

### Recommendations
1. **Education Policy**: Expand access to higher education; supports earnings growth and reduces unemployment
2. **Gender Equity**: Implement work-life balance policies; flexible arrangements increase female participation
3. **Immigration Support**: Targeted integration programs for recent immigrants; accelerates economic contribution
4. **Regional Development**: Consider geographic disparities in unemployment; tailor regional policies accordingly

## How to Cite This Project

```
Arvind, V., Zhang, L., Padiya, P. N., & Janampet, D. (2024). 
"Drivers of Unemployment in Canada: A Focus on Demographic and Economic Factors." 
STAT 8101 Group Project, Macquarie University.
```

## References

- Statistics Canada. (2020). Guide to the Labour Force Survey. Statistics Canada, Catalogue no. 71-543-G. Retrieved from https://www150.statcan.gc.ca/n1/en/catalogue/71-543-G
- Statistics Canada. (2017). Methodology of the Canadian Labour Force Survey. Statistics Canada, Catalogue no. 71-526-X. Retrieved from https://www150.statcan.gc.ca/n1/en/catalogue/71-526-X
- Statistics Canada. (2015). Chapter 6: Weighting and Estimation in Methodology of the Canadian Labour Force Survey. Retrieved from https://www150.statcan.gc.ca/n1/en/catalogue/71-526-X
- Lumley, T. (2010). Complex Surveys: A Guide to Analysis Using R. John Wiley & Sons.

## Contact & Collaboration

- **Email**: vignesh.arvind@students.mq.edu.au
- **LinkedIn**: [linkedin.com/in/vignesh-arvind](https://linkedin.com/in/vignesh-arvind)
- **GitHub**: [@vicky805515](https://github.com/vicky805515)

Questions about methodology, findings, or collaboration opportunities? Feel free to reach out!

## License

This project is open source and available under the MIT License.

---

**Project Date**: October 2024  
**Course**: STAT 8101 - Sampling Design and Analysis  
**Institution**: Macquarie University  
**Status**: Completed
