---
MOC:
  - "[[$SA]]"
tags:
  - clippings
source: https://ec.europa.eu/eurostat/cache/metadata/en/lfsi_long_esms.htm
published:
created: 2025-10-02
description:
about:
project: "[[Data Dismissal Rates Tim]]"
---
[

Back to top

](https://ec.europa.eu/eurostat/cache/metadata/en/#)

**Reference metadata**

Reference metadata describe statistical concepts and methodologies used for the collection and generation of data. They provide information on data quality and, since they are strongly content-oriented, assist users in interpreting the data. Reference metadata, unlike structural metadata, can be decoupled from the data.

For more information, please consult our [metadata website section](https://ec.europa.eu/eurostat/web/metadata/overview).

Close

![Graphic logo](https://ec.europa.eu/eurostat/cache/metadata/img/img111.png)

---

Labour market transitions - LFS longitudinal data (lfsi\_long)

Reference Metadata in Euro SDMX Metadata Structure (ESMS)

Compiling agency: Eurostat, the statistical office of the European Union

Need help? Contact the [Eurostat user support](https://ec.europa.eu/eurostat/contact-us/user-support)

---

Short metadata

Full metadata

Flow statistics are experimental statistics derived from the longitudinal component of the EU-LFS data. They identify the flows between different labour market statuses between consecutive quarters.

Flow statistics are published in the section 'LFS main indicators', which is a collection of the main statistics on the labour market derived from the EU-Labour Force Survey (EU-LFS). However, the flow indicators are calculated with special methods which justify the present page.

**Please note that countries may publish nationally slightly different results due to the use of more sophisticated methods**.

This page focuses on the particularities of the estimation of flow statistics. Other information on 'LFS main indicators' can be found in the respective ESMS page, see link in section 'related metadata'.

General information on the EU-LFS can be found in the ESMS page for 'Employment and unemployment (LFS)', see link in related metadata. Detailed information on the main features, the legal basis, the methodology and the data as well as on the historical development of the EU-LFS is available on the [EU-LFS (Statistics Explained) webpage](http://ec.europa.eu/eurostat/statistics-explained/index.php/EU_labour_force_survey).

13 June 2025

Flow statistics quantify the quarter-on-quarter transitions between the labour market states of unemployment, employment and out of labour force.

The definitions of employment and unemployment, as well as other survey characteristics follow the definitions and recommendations of the International Labour Organisation (ILO).

**Employed persons** are all persons who worked at least one hour for pay or profit during the reference week or were temporarily absent from such work or who found a job to start later, i.e. within a period of at most three months from the end of the reference week. Figures show the number of persons unemployed in thousands.

**Unemployed persons** are all persons 15 to 74 years of age (16 to 74 years in ES, IT and the UK) who were not employed during the reference week, had actively sought work during the past four weeks and were ready to begin working immediately or within two weeks. Figures show the number of persons unemployed in thousands. The duration of unemployment is defined as the duration of a search for a job or as the length of the period since the last job was held (if this period is shorter than the duration of search for a job).

**Out of labour force (previously: inactive persons)** are all persons who were neither unemployed nor employed during the reference week. Figures show the number of persons unemployed in thousandsFor flow statistics, 9 different transitions between the labour market status of unemployment, employment and inactivity between any two consecutive quarters (referred to as initial and final quarter respectively) are calculated; each transition is published under the heading of the final quarter. Individuals used for the calculation of these transitions were surveyed in two consecutive quarters and 15-74 years old in both these quarters.

| **Transition** | **Labour market status in initial quarter** | **Labour market status in final quarter** | **Code in database** |
| --- | --- | --- | --- |
| Employment to employment | Employed | Employed | E\_E |
| Employment to unemployment | Employed | Unemployed | E\_U |
| Employment to out of the labour force | Employed | Out of the labour force | E\_I |
| Unemployment to employment | Unemployed | Employed | U\_E |
| Unemployment to unemployment | Unemployed | Unemployed | U\_U |
| Unemployment to out of the labour force | Unemployed | Out of the labour force | U\_I |
| Out of the labour force to employment | Out of the labour force | Employed | I\_E |
| Out of the labour force to unemployment | Out of the labour force | Unemployed | I\_U |
| Out of the labour force to out of labour force | Out of the labour force | Out of the labour force | I\_I |

**Transition rates** between two labour market states are calculated as the share of a transition in % of the labour market status in the initial quarter, e.g. the transition rate for the flow between unemployment to employment is calculated as:

100\*U\_E/(U\_E+U\_U+U\_I), which is equivalent to 100\*U\_E/(Unemployemt of initial quarter).

The relevant codes for transition rates are

| PC\_UNE | Percentage of unemployment in initial quarter | To be used for transitions out of unemployment |
| --- | --- | --- |
| PC\_EMP | Percentage of employment in initial quarter | To be used for transitions out of employment |
| PC\_INAC | Percentage of out of the labour force in initial quarter | To be used for transitions out of the labour force |

For the **experimental tables on flows** of specific transitions, the following, additional, principles apply:

- All tables are published with the label " **experimental statistics** ". The dedicated page on experimental statistics published by Eurostat in general, and for labour market flows in particular, can be found at this [website](https://ec.europa.eu/eurostat/web/experimental-statistics/labour-market-transitions).
- All results are **estimates performed by Eurostat, derived from a simple regression model.** Information on the methodology used can be found at this [website](https://ec.europa.eu/eurostat/documents/7894008/8033722/20170519-111211_Q2016_paper_flows_-_final.docx.pdf/c09d9c33-4d8c-43bd-a2b0-80926fd4ac1e).
- Breakdowns published by countries on their national website may differ due to differences in methodology. National statistical institutes are usually better placed to tailor the methodology to the data situation in their county.
- The data refer to **annual averages of quarterly transitions;** the pooling of quarterly data is necessary due to the relatively small relevant sample sizes in most countries.
- **Small discrepancies for the same breakdown found in different tables may arise,** depending on the covariaties used in the regression as well as due to rounding of results.
- All results refer to **transition probabilities,** and are rounded to full percentage points **\-** estimates of levels are not available. Estimates which are statistically insignificantly different from zero (at 99% probability) are not shown.

While the flow statistics are produced by using EU-LFS samples, providing breakdowns of this data cannot always be achieved with the same method. For multiple countries, the samples would be too small to provide reliable data, even if annual averages of the quarterly transitions would be used. Instead, in cases such as these, Eurostat utilises a simple regression-based method. [The resulting type of data produced is called experimental statistics](https://ec.europa.eu/eurostat/web/experimental-statistics). This means that the estimated coefficients of the variables in such models are used to find the predicted probabilities. From the latter, the experimental datasets are built – see table codes (lfsi\_long\_e01 to lfsi\_long\_e04 and lfsi\_long\_e06 to lfsi\_long\_e09).

The development of this experimental data follows the same procedure as that for the individual countries’ experimental data: first, Eurostat developed non-pooled longitudinal microdata files, meaning that each file includes just the data of one quarterly transition. Secondly, the pooled longitudinal microdata procedure creates one file per country, including all quarters of the year. Then, the experimental data is calculated by using these files: the pooled data is put into regression models to find the annual averages for a specific country or the EU. From these, the eight aforementioned experimental datasets are created.

For more details on LFS data in general, please consult the [EU-LFS (Statistics Explained) - Methodology](http://ec.europa.eu/eurostat/statistics-explained/index.php/EU_labour_force_survey_-_methodology).

Persons.

The EU LFS results cover the total population usually residing in Member States, except for persons living in collective or institutional households. While demographic data are gathered for all age groups, questions relating to labour market status are restricted to persons in the age group of 15 years or older. For more details and exceptions, please consult please consult the [EU-LFS (Statistics Explained) - Methodology](http://ec.europa.eu/eurostat/statistics-explained/index.php/EU_labour_force_survey_-_methodology).

European Union, Euro area, EU Member States, Candidate Countries, EFTA Countries (except for Liechtenstein). Data for Cyprus refer only to the areas of Cyprus controlled by the Government of the Republic of Cyprus. Data for France do include the overseas departments (DOM) from 2014 on.

The reference periods are the calendar quarters and calendar years. They are defined based on the EU-LFS reference week. For details please refer to the ESMS page on 'Employment and unemployment (LFS)' (see link below in section 'related metadata').

Breakdowns of labour market flows of experimental tables refer to annual averages of quarterly transitions.

There are no measures of accuracy calculated at this point in time for flow statistics. However, the overall accuracy is considered as high, given the fact that the LFS was not set up as a panel. Unemployment is arguably the most important variable collected by EU-LFS, the survey design is optimized to measure unemployment.

For accuracy concerning the LFS as a whole, please refer to the ESMS page on 'Employment and unemployment (LFS)' (see link below in section 'related metadata').

Flow statistics are available as transition levels, indicating the number of persons (in 1000s) changing or remaining in a labour status between two quarters. Transition rates are expressed as share of initial labour market status.

Breakdowns of flow statistics are only available as transition probabilities (in %).

Due to the continuous update of SA (Seasonally Adjusted) estimates, it has to be noted that SA (Seasonally Adjusted) estimates may slightly differ between current data tables and historical vintages.

Eurostat calculates initial quarter-on-quarter flow estimates as 3x3 [ILO](http://ec.europa.eu/eurostat/statistics-explained/index.php/Glossary:International_Labour_Organization_\(ILO\) "Glossary:International Labour Organization (ILO)") labour status transition matrices, for the age group 15-74, by sex and for individual countries.

The following general criteria are applied for quarter-on-quarter flow calculations:

- All computations are restricted to persons who are aged 15-74 in the target period;
- For all quarters from the first quarter of 2010 to the current quarter, the quarterly longitudinal flow samples are defined as the overlapping sample of two consecutive quarters.
- For all years from the first year 2010, the annual longitudinal flow samples are defined as the annual average of the overlapping sample of the same quarters of two consecutive years.

The methodology below describes the production of quarter-on-quarter flows. Year-on-year flows are produced in the same way, described below in this section.

In anticipation of possible future consistency requirements for flow statistics and planned more detailed flow estimates, calculation of ILO labour status transitions starts by sex and age group, using 10-year age groups 15-24, 25-34…65-74. For each subgroup and each of the 9 possible quarter-on-quarter transitions between the 3 labour statuses, the respective final quarter sum of coefficients (weights) in the flow sample is computed. Final quarter weights are used as they lead to the correct [International Labour Organisation (ILO)](http://ec.europa.eu/eurostat/statistics-explained/index.php/Glossary:ILO "Glossary:ILO") labour status distribution in the most recent quarter. As those figures are based on a subset of the final quarter sample only, the resulting grossed-up weights obviously do not provide correct estimates for the underlying population subgroups. They have hence to be calibrated further to known marginal totals for the subgroups in question. In order to do this, the final quarter distribution of the 3 labour statuses in the respective subgroups is taken, and correction factors calculated.

The flow sample weights are then adapted accordingly to match the distribution in the final quarter, namely for each age group x sex x labour status in the final quarter combination. The steps described in the following could be applied to each intermediate matrix produced above. However, in order to avoid empty or poorly populated cells as far as possible and to get more robust results, calculation of the headline indicators for the age group 15-74 starts with a further aggregation of the previous results about age, i.e. all intermediate transition matrix results calculated so far for an individual country are combined into one single matrix, by sex. As for the final quarter, marginal ILO labour status distributions for the initial quarter are available as well. The next step tries to achieve consistency of the transition matrix with both marginal distributions. The procedure applied requires a common population in both quarters – for that, the probably least critical value (population outside the labour force in the initial quarter) is corrected in a way that the total population in both quarters matches that of the final quarter. Afterwards an iterative raking procedure is applied. It starts with the matrix consistent with the final quarter distribution and tries to find matrix values which are as close as possible to the start matrix while ensuring also consistency to the (partly corrected) initial quarter distribution. The iterative raking stops once the deviation of the row and column sums from the marginal distributions is less than 1,005. The results of the iterative raking are the flow estimates published. They are published separately for males and females.

Annual labour market flows between the labour market statuses of employment, unemployment and outside the labour force are derived from cross-sectional EU-Labour Force Survey data by matching microdata from all four quarters of a specific (initial) year to the same quarters of the following (target) year. This pseudo-longitudinal sample is used to derive transition matrices. Reweighting and raking mirrors the methodology used for quarterly labour market flows (see above). Across all countries, the share of individuals surveyed in the initial period but not present in the target period is higher for annual flows than for quarterly flows. This can be due to people moving away, dying, not being at home when surveyed, or refusing to answer the survey. There is some indication that this attrition is non-random and might therefore in some particular cases of significant population changes bias the annual flows estimates.

Estimates for Spain are sent to Eurostat by INE Spain, and make use of additional variables in the weighting (five year age groups, nationality, region). They are restricted to persons 16 to 74 years old in the target quarter due to the legal working age in Spain. Specificites for annual flows are given in the document annexed.

Estimates for the Netherlands are sent to Eurostat by the CBS. The methodology is explained in detail in the document annexed.

Estimates for Portugal (both annual and quarterly flows) are sent to Eurostat by INE Portugal. The methodology is explained in detail in the document annexed.

Annexes:  
[Methodology annual flows Portugal](https://ec.europa.eu/eurostat/cache/metadata/Annexes/lfsi_long_esms_an_1.docx "lfsi_long_esms_an_1.docx")  
[Methodology annual flows Netherlands](https://ec.europa.eu/eurostat/cache/metadata/Annexes/lfsi_long_esms_an_2.docx "lfsi_long_esms_an_2.docx")  
[Methodology annual flows Spain](https://ec.europa.eu/eurostat/cache/metadata/Annexes/lfsi_long_esms_an_3.docx "lfsi_long_esms_an_3.docx")  
[Methodology quarterly flows Portugal](https://ec.europa.eu/eurostat/cache/metadata/Annexes/lfsi_long_esms_an_4.docx "lfsi_long_esms_an_4.docx")

Quarterly for quarterly flows data.

Annual for annual flows data.

Annual for breakdowns of labour market flows.

The quarterly series are updated 4 times a year approximately 75 days after the end of the reference quarter.

The annual series are published along with quarter 4 data approximately 75 days after the end of the reference year.

No quarterly flows data is available for Germany before 2021 due to the missing overlap of the quarterly samples. No EU aggregates for levels are published before 2021. Rotational sampling designs were introduced in Luxembourg in 2015 and in Belgium in 2017.

The data published for **Spain, the Netherlands, Belgium and Portugal** are produced by the respective national institutes and sent to Eurostat. Small differences in the methodology for the derivation of longitudinal weights used are described in section 18.5.

Generally, geographical comparability of the EU-LFS has historically been very high, and has further improved with the implementation of IESS. However, some countries are still in the process of implementing the Regulation, or have other quality concerns that may impact geographical comparability. Please find details below:

**Spain**: Pre-IESS, and after the outbreak of the COVID crisis, Spain was including in employment also persons on lay-off paid by a governmental scheme and not directly from the employer. Under IESS, due to the COVID crisis, Spain continued to test for job attachment of employed persons on temporary lay-off as implemented in the pre-IESS situation.

**France:** Under IESS, and due to the COVID crisis, France continued to test for job attachment of employed persons on temporary lay-off as implemented in the pre-IESS situation.

**The Netherlands**: Data is collected using a rolling reference week instead of a fixed reference week, i.e. interviewed persons are asked about the situation of the week before the interview rather than a pre-selected week (irrespective of the interview time).

Flow statistics are published beginning with the transitions from Q1 to Q2 2010 for quarterly data, and with the transition from 2010 to 2011 for annual data. Breaks in series are indicated in the data.

![Close](https://ec.europa.eu/eurostat/cache/metadata/img/close.svg)