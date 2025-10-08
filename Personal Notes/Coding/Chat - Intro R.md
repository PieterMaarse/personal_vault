---
MOC:
  - "[[$Coding]]"
tags:
  - note
date: 2025-10-07
about:
  - Chat deep research about intro to R
gearchiveerd:
inhoudelijk:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---


# A Comprehensive Guide to Analyzing Survey Data on Early Retirement in R

## Introduction and Scope

Surveys are indispensable tools for social science and policy research. When studying a topic such as **early retirement**, researchers often collect survey data from individuals about their demographic characteristics, employment history, health status, financial readiness and retirement intentions. Analysing these data correctly is essential because survey designs often involve complex sampling strategies, differential probabilities of selection and adjustments for non‑response[stats.oarc.ucla.edu](https://stats.oarc.ucla.edu/r/seminars/survey-data-analysis-with-r/#:~:text=Sampling%20weights%3A%20There%20are%20several,will%20equal%20the%20population%20total). Failing to account for these complexities can lead to biased estimates and misleading conclusions about patterns of early retirement. This manual‑style guide is a comprehensive tutorial for a thesis student with minimal R experience who needs to wrangle, explore and model survey data on early retirement.

Throughout the manual we will adhere to clear structure and plain language. The guide uses the **tidyverse** set of packages for data wrangling—including `dplyr`, `tidyr`, `stringr` and `forcats`—and the **survey** and **srvyr** packages for design‑aware analyses. Code examples are kept simple and illustrate generic tasks rather than using a specific dataset. To ensure the manual is self‑contained, synthetic data examples will be generated as needed. Mathematical concepts are explained in intuitive terms, supplemented with LaTeX equations where necessary. Readers will also learn best practices for organising R projects and exporting tables and figures for academic reporting.

This manual is organised into several sections. We begin with an overview of early retirement research, highlighting key variables that might be collected in a survey. We then introduce the tidyverse and show how to import, clean, join, reshape and recode data. Next, we explain the concept of survey weighting and sampling design, and demonstrate how to create survey design objects using `survey` and `srvyr`. Subsequent sections cover exploratory analysis, descriptive statistics, hypothesis testing and regression models that account for survey design. The manual concludes with tips for writing clean R code, organising projects and communicating results effectively.

## Understanding Early Retirement and Survey Variables

Before delving into code, it is helpful to define **early retirement** and think about the variables typically included in surveys addressing this topic. Early retirement can be broadly described as the voluntary or involuntary exit from the workforce before the standard pension age. Motivation for early retirement may include poor health, caregiving responsibilities, job dissatisfaction, adequate savings or institutional incentives. When designing or analysing a survey on early retirement, researchers might collect variables such as:

- **Demographics**: age, gender, marital status, education, migration background.
    
- **Employment history**: current employment status, occupation, sector, tenure, contract type.
    
- **Health indicators**: self‑rated health, chronic conditions, mental well‑being.
    
- **Financial information**: income, assets, pension contributions, perceived financial preparedness.
    
- **Retirement preferences**: desired retirement age, expected retirement age, reasons for retiring early or late.
    
- **Work environment**: job satisfaction, workplace flexibility, physical demands.
    
- **Household context**: household size, caregiving responsibilities, partner’s employment status.
    

In your thesis, you may focus on how these factors influence the probability of retiring before a certain age (e.g., 60 or 62). In the examples below, we will assume you have a survey dataset where each row represents a respondent and columns represent the variables listed above. We will also assume the survey has a complex sampling design—e.g., stratification by region and clustering by household—with sampling weights provided.

## Setting Up the R Environment

### Installing packages and creating a project

R and RStudio are powerful tools for data analysis. Before working with any data, it is important to set up a clean and reproducible environment:

1. **Install necessary packages**: You should install the tidyverse (which loads `dplyr`, `tidyr`, `stringr`, `forcats`, `readr` and others) and the survey packages. Use `install.packages(c("tidyverse", "survey", "srvyr", "janitor", "ggplot2", "readxl"))` to install them.
    
2. **Load packages**: In your R script or R Markdown document, load the packages with `library()` calls. Loading the tidyverse packages grants access to a consistent grammar of data manipulation.
    
3. **Create a project**: Use RStudio Projects to organise your files. A project provides a working directory, making file paths reproducible and relative.
    
4. **Set seed for reproducibility**: When generating synthetic data or performing simulations, use `set.seed()` to ensure that results can be reproduced.
    

Here is example R code to get started:

`# install required packages (run only once) install.packages(c("tidyverse", "survey", "srvyr", "janitor"))  # load libraries library(tidyverse)  # loads dplyr, tidyr, stringr, forcats, ggplot2, etc. library(survey)     # functions for survey designs and analysis library(srvyr)      # dplyr-friendly wrapper around survey library(janitor)    # for cleaning column names and cross-tabulations  # set a seed for reproducibility set.seed(123)`


## Importing Data and Cleaning Variable Names

### Importing survey data

Survey data may be provided as CSV, Excel or SPSS files. The tidyverse provides `readr::read_csv()` and `readxl::read_excel()` functions to import such files. For example, suppose you receive a CSV file `early_retirement_survey.csv`. You can read it as follows:

`# read data from CSV file survey_raw <- read_csv("data/early_retirement_survey.csv")  # examine first few rows head(survey_raw)`

It is common for survey data to have messy column names with spaces, punctuation or inconsistent cases. The `janitor::clean_names()` function automatically standardises names to lower snake_case. For example:

`survey <- survey_raw %>%   clean_names()  # convert column names to snake_case  glimpse(survey)`

### Filtering rows

The `filter()` function in `dplyr` retains rows meeting certain conditions[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=without%20changing%20their%20order%2C%20and,also%20optionally%20modify%20the%20columns). For example, you may wish to keep only respondents aged 50 and above, or exclude those with missing weights. `filter()` takes the data frame as the first argument and a series of logical conditions thereafter:

`survey <- survey %>%   filter(age >= 50, !is.na(weight))`

You can combine conditions using `&` (and), `|` (or) and `%in%` (match any of a set). For instance, to keep only respondents who are either married or cohabiting:

`survey <- survey %>%   filter(marital_status %in% c("married", "cohabiting"))`

### Selecting and renaming columns

To focus on variables of interest, use `select()` to keep or drop columns[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=It%E2%80%99s%20not%20uncommon%20to%20get,the%20names%20of%20the%20variables). You can select by name, range or type. Negative selection (`!`) excludes variables. For example:

`survey <- survey %>%   select(age, gender, marital_status, employment_status, income, health_score,          retirement_intent, weight, strata, psu)`

If you need to rename variables for clarity, use `rename()`:

`survey <- survey %>%   rename(retire_age_intent = retirement_intent)`

### Creating new variables with mutate

The `mutate()` function adds new columns or transforms existing ones[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=the%20columns). Suppose we want to compute a binary variable `early_retire` indicating whether the respondent plans to retire before age 60. We can also calculate a weekly working hours variable from reported daily hours:

`survey <- survey %>%   mutate(     early_retire = if_else(retire_age_intent < 60, 1, 0),     weekly_hours = daily_hours * 5,     # Example of recoding employment_status to a factor with specific order     employment_status = factor(employment_status,                                levels = c("employed", "unemployed", "retired", "inactive"))   )`

The `.before` and `.after` arguments of `mutate()` can control where new variables appear[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=the%20columns); however, in practice, ordering variables is less important than clarity. It is good practice to avoid overwriting your original dataset inadvertently by assigning the result to a new object (e.g., `survey`), as the `mutate()` function prints the updated data but does not modify by default.

### Recoding factors with forcats

Factor variables often need reordering or recoding. The `forcats` package helps with these tasks. Use `fct_relevel()` to manually reorder factor levels, or `fct_recode()` and `fct_collapse()` to group or relabel categories. For instance, suppose the `health_status` factor has levels “excellent”, “good”, “fair” and “poor”, and we want to ensure “excellent” comes first and “poor” last:

`survey <- survey %>%   mutate(health_status = fct_relevel(health_status,                                      c("excellent", "good", "fair", "poor")))`

`fct_relevel()` allows moving levels to specific positions[forcats.tidyverse.org](https://forcats.tidyverse.org/articles/forcats.html#:~:text=Manually%20reordering). To recode some levels and drop others, use `fct_recode()`[forcats.tidyverse.org](https://forcats.tidyverse.org/reference/fct_recode.html#:~:text=Usage):

`survey <- survey %>%   mutate(     employment_status = fct_recode(employment_status,                                    unemployed = "job seeker",                                    retired    = "pensioner",                                    NULL       = "unknown")   )`

Here, any occurrence of “job seeker” will be recoded as “unemployed”, and “pensioner” as “retired”. The level “unknown” is removed from the factor. To collapse several categories into broader groups, use `fct_collapse()`[forcats.tidyverse.org](https://forcats.tidyverse.org/reference/fct_collapse.html#:~:text=Usage):

`survey <- survey %>%   mutate(     work_sector = fct_collapse(occupation,                                public  = c("teacher", "nurse", "civil servant"),                                private = c("manager", "engineer", "sales"),                                other   = c("farmer", "self-employed"))   )`

Lastly, to lump rare categories into an “Other” group, use `fct_lump()`[forcats.tidyverse.org](https://forcats.tidyverse.org/articles/forcats.html#:~:text=We%20see%20that%20there%E2%80%99s%2031,levels%20we%20want%20to%20keep). For example, to keep the five most common occupations and lump the rest:

`survey <- survey %>%   mutate(occupation_lumped = fct_lump(occupation, n = 5, other_level = "Other"))`

### Working with strings using stringr

Survey data often contain text responses that require cleaning. `stringr` offers consistent functions for manipulating strings. The introduction outlines four families of functions: character extraction, whitespace tools, locale-sensitive operations and pattern matching[stringr.tidyverse.org](https://stringr.tidyverse.org/articles/stringr.html#:~:text=There%20are%20four%20main%20families,of%20functions%20in%20stringr). Examples include:

- `str_length()` to compute string length.
    
- `str_sub()` to extract or replace substrings.
    
- `str_to_title()` or `str_to_upper()` to change case[stringr.tidyverse.org](https://stringr.tidyverse.org/articles/stringr.html#:~:text=Whitespace).
    
- `str_pad()` to pad strings to a fixed width[stringr.tidyverse.org](https://stringr.tidyverse.org/articles/stringr.html#:~:text=Whitespace).
    
- `str_trim()` to remove leading and trailing whitespace[stringr.tidyverse.org](https://stringr.tidyverse.org/articles/stringr.html#:~:text=Whitespace).
    

For pattern matching, `stringr` functions take a string vector and a pattern. For example, `str_detect()` tests whether the pattern is present, `str_extract()` extracts the first match, and `str_replace()` replaces matches[stringr.tidyverse.org](https://stringr.tidyverse.org/articles/stringr.html#:~:text=Each%20pattern%20matching%20function%20has,US%29%20phone%20numbers). Suppose we have a column `comments` containing responses with mentions of early retirement reasons. We can detect references to health issues or employer incentives:

`survey <- survey %>%   mutate(     mention_health = str_detect(comments, regex("health|medical", ignore_case = TRUE)),     mention_incentive = str_detect(comments, regex("incentive|buyout", ignore_case = TRUE))   )`

To split strings into multiple columns, such as a variable `gender_age` coded like “F-55”, use `separate()`[tidyr.tidyverse.org](https://tidyr.tidyverse.org/reference/separate.html#:~:text=Given%20either%20a%20regular%20expression,character%20column%20into%20multiple%20columns):

`survey <- survey %>%   separate(gender_age, into = c("gender", "age_group"), sep = "-")`

To combine multiple columns, use `unite()`[tidyr.tidyverse.org](https://tidyr.tidyverse.org/reference/unite.html#:~:text=unite%28data%2C%20col%2C%20,rm%20%3D%20FALSE):

`survey <- survey %>%   unite("contact", c(email, phone), sep = ";", remove = TRUE, na.rm = TRUE)`

`stringr` also provides functions for splitting strings by patterns (`str_split()`) and extracting multiple matches (`str_extract_all()`). For instance, splitting a semi‑colon delimited contact field:

`contact_list <- str_split_fixed(survey$contact, pattern = ";", n = 2) survey <- survey %>%   mutate(email = contact_list[, 1], phone = contact_list[, 2])`

## Joining and Merging Data

In many research projects, you need to combine information from different files. For example, a household file might contain household-level variables like household income and region, while a person file contains individual-level variables. The `dplyr` join functions help merge these datasets. There are two categories of joins: **mutating joins**, which add new variables by matching observations with keys, and **filtering joins**, which filter observations based on whether a match exists[r4ds.hadley.nz](https://r4ds.hadley.nz/joins.html#:~:text=It%E2%80%99s%20rare%20that%20a%20data,two%20important%20types%20of%20joins).

### Setting keys and understanding joins

A _primary key_ is a variable (or combination of variables) that uniquely identifies each row in a table. A _foreign key_ in one table references the primary key in another[r4ds.hadley.nz](https://r4ds.hadley.nz/joins.html#:~:text=19). For example, in a household survey, the household ID `hhid` might be the primary key in the household table and a foreign key in the person table.

The most common mutating join is `left_join()`, which keeps all rows from the left table and adds matching columns from the right table, filling `NA` when there is no match[r4ds.hadley.nz](https://r4ds.hadley.nz/joins.html#:~:text=A%20mutating%20join%20allows%20you,dataset%20with%20just%20six%20variables1). Other mutating joins include:

- `inner_join()`: keeps only rows with matches in both tables.
    
- `right_join()`: keeps all rows from the right table and matches from the left.
    
- `full_join()`: keeps all rows from both tables.
    

By default, `left_join()` uses all common column names as join keys (natural join)[r4ds.hadley.nz](https://r4ds.hadley.nz/joins.html#:~:text=By%20default%2C%20,dataset). If both tables share variables like `year`, this can produce unintended matches. To be explicit, use `join_by()` or specify `by = c("hhid" = "household_id")` to match different names. The difference between `inner_join`, `right_join` and `full_join` lies only in which rows are kept[r4ds.hadley.nz](https://r4ds.hadley.nz/joins.html#:~:text=,We%E2%80%99ll).

Suppose you have two synthetic data frames: `households` and `persons`. The households data contains `hhid`, `region` and `household_income`; the persons data contains `hhid`, `pid` (person ID), `age` and `retired`. You can merge them as follows:

`households <- tibble(   hhid = 1:3,   region = c("North", "South", "East"),   household_income = c(50000, 45000, 55000) )  persons <- tibble(   hhid = c(1, 1, 2, 3, 3),   pid  = 1:5,   age  = c(58, 62, 54, 60, 59),   retired = c(0, 1, 0, 1, 0) )  # left join: add household variables to persons persons_full <- persons %>%   left_join(households, by = "hhid")`

If you need to join more complex keys (e.g., region and year), supply a named vector to `by`. For filtering, `semi_join()` keeps rows in `x` that match `y`, and `anti_join()` keeps rows in `x` that do not have a match[r4ds.hadley.nz](https://r4ds.hadley.nz/joins.html#:~:text=As%20you%20might%20guess%20the,show%20just%20the%20origin%20airports). These are useful for identifying unmatched individuals or households.

### Pivoting data

Reshaping data between long and wide formats is a common task. The `tidyr` functions `pivot_longer()` and `pivot_wider()` handle these operations.

#### pivot_longer: making data longer

`pivot_longer()` increases the number of rows and decreases the number of columns by converting column names into a key-value pair[tidyr.tidyverse.org](https://tidyr.tidyverse.org/articles/pivot.html#:~:text=,cell%20values). It takes arguments `cols` (columns to reshape), `names_to` (name of the key column) and `values_to` (name of the value column). For example, suppose you have early retirement reasons for up to three possible reasons recorded as `reason1`, `reason2` and `reason3`. To convert them into a longer format:

`survey_long <- survey %>%   pivot_longer(cols = starts_with("reason"),                names_to = "reason_number",                values_to = "reason") %>%   filter(!is.na(reason))  # drop rows where reason is missing`

The `names_pattern` argument allows splitting complex column names into multiple variables[tidyr.tidyverse.org](https://tidyr.tidyverse.org/articles/pivot.html#:~:text=,four%20variables%20in%20their%20names). For instance, if we have variables like `income_2018`, `income_2019` and `income_2020`, we could extract the year:

`survey_income_long <- survey %>%   pivot_longer(     cols = starts_with("income_"),     names_to = "year",     names_prefix = "income_",     values_to = "income"   ) %>%   mutate(year = as.integer(year))`

#### pivot_wider: making data wider

`pivot_wider()` is the inverse operation, increasing the number of columns and decreasing rows[tidyr.tidyverse.org](https://tidyr.tidyverse.org/articles/pivot.html#:~:text=Wider). Suppose each respondent answers questions about satisfaction with life in various domains (health, finances, social connections). The data may be stored in long format with `domain` and `satisfaction` columns. To convert to a wide format where each domain becomes its own column:

`survey_wide <- survey %>%   select(pid, domain, satisfaction) %>%   pivot_wider(names_from = domain, values_from = satisfaction)`

If multiple rows per domain exist, specify `values_fn` to aggregate them (e.g., taking the mean)[tidyr.tidyverse.org](https://tidyr.tidyverse.org/articles/pivot.html#:~:text=,int). To replace `NA` with zeros or another value, use `values_fill`:

`survey_wide <- survey %>%   pivot_wider(names_from = domain,               values_from = satisfaction,               values_fn = list(satisfaction = mean),               values_fill = list(satisfaction = 0))`

### Example: combining household and person files

Putting these techniques together, suppose you have three separate files: a person‑level file with demographic variables, a household file with economic variables and a reason file listing reasons for early retirement. You can clean and combine them as follows:

`# read and clean persons <- read_csv("data/persons.csv") %>% clean_names() households <- read_csv("data/households.csv") %>% clean_names() reasons <- read_csv("data/retirement_reasons.csv") %>% clean_names()  # join household data to persons persons_full <- persons %>% left_join(households, by = "hhid")  # pivot reasons to longer format and join to persons reasons_long <- reasons %>%   pivot_longer(cols = starts_with("reason"),                names_to = "reason_number",                values_to = "reason",                values_drop_na = TRUE)  data_combined <- persons_full %>% left_join(reasons_long, by = "pid")  # view cleaned dataset glimpse(data_combined)`

## Survey Weighting and Design

### Why weighting matters

Surveys often use complex sampling designs involving unequal selection probabilities, stratification and clustering. To obtain unbiased population estimates and correct standard errors, analysts must incorporate sampling weights and design features[stats.oarc.ucla.edu](https://stats.oarc.ucla.edu/r/seminars/survey-data-analysis-with-r/#:~:text=Sampling%20weights%3A%20There%20are%20several,will%20equal%20the%20population%20total). The **sampling weight** for each unit is the inverse of its selection probability; it may also include adjustments for non‑response or calibration to known population totals[stats.oarc.ucla.edu](https://stats.oarc.ucla.edu/r/seminars/survey-data-analysis-with-r/#:~:text=Sampling%20weights%3A%20There%20are%20several,will%20equal%20the%20population%20total). Ignoring weights and design can bias point estimates and lead to under‑ or over‑estimated variances[stats.oarc.ucla.edu](https://stats.oarc.ucla.edu/r/seminars/survey-data-analysis-with-r/#:~:text=Strata%3A%20Stratification%20is%20a%20method,the%20sample%20as%20a%20whole).

### Types of sampling designs

Common sampling designs include:

1. **Simple random sampling (SRS)**: every unit has equal probability of selection. The sampling weight is wi=N/nw_i = N/nwi​=N/n, the inverse of the sampling fraction. When sampling without replacement, the variance estimator includes a finite population correction factor (FPC):
    

Var(yˉ)=(1−nN)S2n\text{Var}(\bar{y}) = \left(1 - \frac{n}{N}\right) \frac{S^2}{n}Var(yˉ​)=(1−Nn​)nS2​

where S2S^2S2 is the population variance[tidy-survey-r.github.io](https://tidy-survey-r.github.io/tidy-survey-book/c10-sample-designs-replicate-weights.html#:~:text=). If the sample is less than 10% of the population, the FPC is negligible.

2. **Stratified sampling**: the population is divided into strata (e.g., region, gender), and a sample is drawn within each stratum. Weights are proportional to the inverse selection probability within each stratum[stats.oarc.ucla.edu](https://stats.oarc.ucla.edu/r/seminars/survey-data-analysis-with-r/#:~:text=Strata%3A%20Stratification%20is%20a%20method,the%20sample%20as%20a%20whole). Stratification improves the precision of estimates when units within strata are more homogenous.
    
3. **Cluster sampling**: units are sampled in clusters (primary sampling units, PSUs) such as households or schools. Clustering affects variance; the design must account for intra‑cluster correlation.
    
4. **Multistage sampling**: combination of stratification and clustering, e.g., stratify by region and then sample households within each region.
    

### Creating weights and design objects

When you receive survey data, weights are often provided. If not, you may need to calculate them based on sample design information. The {survey} and {srvyr} packages include helper functions for adding weights and creating design objects. The Epi R Handbook emphasises dropping erroneous observations before adding weights and warns that weight and design variables cannot have missing values[epirhandbook.com](https://www.epirhandbook.com/en/new_pages/survey_analysis.html#:~:text=mutate%28obstime%20%3D%20as.numeric%28enddate%20). They show functions like `add_weights_strata` and `add_weights_cluster` to compute stratified and cluster weights[epirhandbook.com](https://www.epirhandbook.com/en/new_pages/survey_analysis.html#:~:text=,age_group%2C%20sex%2C%20health_district). For our synthetic data, we will assume weights are given.

The `svydesign()` function from the `survey` package creates a survey design object by specifying the cluster (PSU), strata, weights and finite population correction if needed[epirhandbook.com](https://www.epirhandbook.com/en/new_pages/survey_analysis.html#:~:text=26). For example:

`# assume survey data has variables: weight, strata, psu design <- svydesign(id = ~psu, strata = ~strata, weights = ~weight,                     data = survey, nest = TRUE)`

The `srvyr` package offers `as_survey_design()` for a tidyverse‑friendly syntax[epirhandbook.com](https://www.epirhandbook.com/en/new_pages/survey_analysis.html#:~:text=26):

`design_srvyr <- survey %>%   as_survey_design(ids = psu, strata = strata, weights = weight)`

If the survey uses a simple random sample without stratification or clustering, specify `id = ~1` and leave `strata` empty. For multistage designs, you may supply a vector of cluster IDs (e.g., `id = ~cluster1 + cluster2`).

### Checking weights and design

After creating the design, it is good practice to verify that weights sum to the population size (or the known total). You can use `svytotal()` to compute the total number of respondents and compare with the sum of weights. Additionally, check that there are no missing values in the weight, strata or PSU variables; any missing entries should be handled before constructing the design.

### Post‑stratification and calibration

In some cases, you may need to adjust weights to match known population totals (post‑stratification) or replicate frames (calibration). The `survey` package provides functions such as `postStratify()`, `rake()` and `calibrate()` for these tasks. For example, if you know the population proportion of men and women aged 50–64, you can adjust the weights accordingly. We will not detail these techniques here but note that they can improve the representativeness of your estimates.

## Exploratory Analysis and Descriptive Statistics

Once you have a survey design object, you can begin exploring your data. The `survey` and `srvyr` packages provide functions for design‑aware descriptive statistics. The `srvyr` package wraps these functions in a tidyverse syntax, making them easier to combine with pipes and group operations[epirhandbook.com](https://www.epirhandbook.com/en/new_pages/survey_analysis.html#:~:text=Most%20survey%20R%20packages%20rely,using%20a%20function%20from%20the). However, certain operations (like `arrange()` or `full_join()`) are not available on `srvyr` objects[cran.r-project.org](https://cran.r-project.org/web/packages/srvyr/vignettes/srvyr-vs-survey.html#:~:text=,pipes).

### Summary statistics using srvyr

The `srvyr` package offers functions `survey_mean()`, `survey_total()`, `survey_quantile()` and `survey_ratio()` to compute weighted means, totals, quantiles and ratios[cran.r-project.org](https://cran.r-project.org/web/packages/srvyr/vignettes/srvyr-vs-survey.html#:~:text=Summary%20statistics). These functions return tibbles with estimates and standard errors, optionally with confidence intervals. For example, to compute the mean age and proportion of early retirement intentions:

`library(srvyr)  # convert survey data to srvyr object design_srvyr <- survey %>%   as_survey_design(ids = psu, strata = strata, weights = weight)  # overall mean age and early retirement proportion design_srvyr %>%   summarise(     mean_age = survey_mean(age, vartype = "ci"),     prop_early = survey_mean(early_retire, vartype = "ci")   )`

Here `survey_mean()` automatically treats a 0/1 variable as a proportion. The `vartype = "ci"` argument requests confidence intervals[cran.r-project.org](https://cran.r-project.org/web/packages/srvyr/vignettes/srvyr-vs-survey.html#:~:text=Summary%20statistics). To compute weighted totals instead, use `survey_total()`; for example, the estimated number of respondents planning early retirement:

`design_srvyr %>%   summarise(     total_early = survey_total(early_retire)   )`

### Grouped summaries

To examine differences across groups (e.g., gender, education), use `group_by()` followed by `summarise()` with the survey functions. The `srvyr` package ensures that grouping variables are treated correctly. For instance, to compute the early retirement proportion by gender:

`design_srvyr %>%   group_by(gender) %>%   summarise(prop_early = survey_mean(early_retire, vartype = "ci"))`

You can compute weighted counts of observations meeting a condition using the fact that `survey_total()` can sum indicator variables. For example, the weighted number of respondents with positive and negative health scores:

`design_srvyr %>%   group_by(health_status) %>%   summarise(     count_nonmissing = survey_total(1),     count_good_health = survey_total(health_status == "good")   )`

Alternatively, summarise the distribution of a categorical variable by leaving out the variable argument. Doing so returns weighted proportions and totals for each level[cran.r-project.org](https://cran.r-project.org/web/packages/srvyr/vignettes/srvyr-vs-survey.html#:~:text=Proportions%20by%20group):

`design_srvyr %>%   group_by(education_level) %>%   summarise(survey_mean(vartype = "ci"))`

If you need unweighted counts as well, use the `unweighted()` helper[cran.r-project.org](https://cran.r-project.org/web/packages/srvyr/vignettes/srvyr-vs-survey.html#:~:text=Unweighted%20calculations):

`design_srvyr %>%   group_by(employment_status) %>%   summarise(     n_unw = unweighted(n()),     prop_early = survey_mean(early_retire),     total_early = survey_total(early_retire)   )`

### Tables and crosstabulations

Weighted cross‑tabulations can be computed using `svytable()` or `srvyr` functions. Suppose you want to examine the relationship between gender and early retirement intention. The `svytable()` function produces a contingency table with weights:

`svytable(~ gender + early_retire, design)  # design object from survey`

Alternatively, use `janitor::tabyl()` on the dataset, but this returns unweighted tables. To include weights, supply the weight variable and compute expected counts manually.

## Hypothesis Testing with Survey Data

Statistical tests such as t‑tests and chi‑square tests must be adapted for survey designs. The `survey` package provides design‑based versions of these tests.

### Design‑based t‑tests

The `svyttest()` function performs t‑tests for survey data. It can compare a sample mean to a hypothesised value (one‑sample test) or compare means between two groups (two‑sample test). The one‑sample version uses `svymean()` under the hood and the degrees of freedom are `degf(design)`[r-survey.r-forge.r-project.org](https://r-survey.r-forge.r-project.org/survey/html/svyttest.html#:~:text=One,sample%20case). For example, to test whether the average planned retirement age differs from 60:

`svyttest(retire_age_intent ~ 1, design = design, mu = 60)`

To compare average health scores between men and women:

`svyttest(health_score ~ gender, design = design)`

### Rao‑Scott chi‑square test

For categorical variables, the standard Pearson chi‑square test is not appropriate because of complex design. The `svychisq()` function computes the Rao‑Scott adjusted test[r-survey.r-forge.r-project.org](https://r-survey.r-forge.r-project.org/survey/html/svychisq.html#:~:text=%60svychisq%60%20computes%20first%20and%20second,type%20tests). Suppose we want to test the association between early retirement intention and marital status (binary variable). First, create a contingency table using `svytable()`, then call `svychisq()`:

`retire_marital_table <- svytable(~ early_retire + marital_status, design) svychisq(~ early_retire + marital_status, design)`

By default the statistic is the F statistic with a Satterthwaite approximation; other options include `statistic = "Chisq"` or `"Wald"`[r-survey.r-forge.r-project.org](https://r-survey.r-forge.r-project.org/survey/html/svychisq.html#:~:text=%60svychisq%60%20computes%20first%20and%20second,type%20tests). Note that `svychisq()` works only for two‑dimensional tables.

### Proportion tests

Testing differences in proportions between groups can be done using `svyciprop()` to compute confidence intervals for a proportion and `svyprop()` (alias for `svymean()` applied to an indicator variable). To test the difference in early retirement intention between men and women, compute the difference in proportions and examine whether the confidence intervals overlap. Alternatively, run a two‑sample t‑test on the indicator variable.

## Regression and Modeling

The final stage of analysis often involves modelling the relationship between early retirement and explanatory variables. Linear and logistic regression models can be fitted to survey data using `svyglm()`, which extends the usual `glm()` to handle complex designs[rdocumentation.org](https://www.rdocumentation.org/packages/survey/versions/4.4-8/topics/svyglm#:~:text=Fit%20a%20generalised%20linear%20model,based%20standard%20errors). While `svyglm()` can be used directly on survey design objects, the `srvyr` wrapper `survey_regression()` is not available; instead, convert to a design object or use `svyglm()`.

### Linear regression

Suppose we want to model planned retirement age as a function of health status, income and education. The dependent variable `retire_age_intent` is continuous. We fit a weighted linear regression:

`model_lin <- svyglm(retire_age_intent ~ health_status + income + education_level,                     design = design) summary(model_lin)`

`svyglm()` takes arguments similar to `glm()`, but the standard errors and test statistics are adjusted for survey design[rdocumentation.org](https://www.rdocumentation.org/packages/survey/versions/4.4-8/topics/svyglm#:~:text=Fit%20a%20generalised%20linear%20model,based%20standard%20errors). If the weights are extremely large or small, the `rescale` argument can rescale them internally for stability[rdocumentation.org](https://www.rdocumentation.org/packages/survey/versions/4.4-8/topics/svyglm#:~:text=Fit%20a%20generalised%20linear%20model,based%20standard%20errors). Use `predict()` on the model to obtain fitted values or predicted means for specific groups.

### Logistic regression

Early retirement intention is typically binary (1 if the respondent plans to retire early, 0 otherwise). Use logistic regression to model the log‑odds of planning early retirement. `svyglm()` with `family = quasibinomial()` or `family = binomial()` fits a survey‑weighted logistic regression[rdocumentation.org](https://www.rdocumentation.org/packages/survey/versions/4.4-8/topics/svyglm#:~:text=Fit%20a%20generalised%20linear%20model,based%20standard%20errors). Use `quasibinomial()` to avoid warnings for non‑integer responses or when modelling proportions.

`model_logit <- svyglm(early_retire ~ age + gender + health_status + income +                        employment_status + household_income + region,                       design = design,                       family = quasibinomial())  summary(model_logit)`

Interpretation follows standard logistic regression: exponentiating coefficients gives odds ratios. Use `confint()` to obtain confidence intervals. To compute predicted probabilities for different groups, create a new data frame with desired covariate values and use `predict()` with `type = "response"`.

### Interaction terms and model checks

Consider including interaction terms, for example between gender and health status, to test whether the effect of health differs between men and women. Model checks include examining residuals and influence measures; for survey data these diagnostics can be approximated but may not account fully for design. Consider replicating analyses with replicate weights if available (e.g., bootstrap weights) to assess robustness.

### Other models

The `survey` package supports other models such as Poisson regression for count outcomes, quantile regression (via `svyrq()`), survival analysis (`svykm()` for Kaplan–Meier curves) and generalized estimating equations. However, logistic regression is often the primary tool for binary outcomes like early retirement intention.

## Visualisation and Reporting Results

### Visualising survey data

When plotting survey data, you may want to reflect the weighting. For histograms and density plots, using weights can show the true distribution. For example, to plot the distribution of planned retirement age weighted by survey weights, use `ggplot2` with the `weight` aesthetic:

`ggplot(survey, aes(x = retire_age_intent)) +   geom_histogram(aes(weight = weight), bins = 20, fill = "steelblue") +   labs(title = "Distribution of Planned Retirement Age (Weighted)",        x = "Planned retirement age", y = "Weighted count")`

For bar plots of categorical variables, compute the weighted proportion via `survey_mean()` and then plot. Example: weighted proportion of early retirement by education level:

`library(ggplot2)  prop_education <- design_srvyr %>%   group_by(education_level) %>%   summarise(prop_early = survey_mean(early_retire)) %>%   mutate(prop_early = prop_early * 100)  # convert to percent  ggplot(prop_education, aes(x = education_level, y = prop_early)) +   geom_col(fill = "darkgreen") +   geom_text(aes(label = round(prop_early, 1)), vjust = -0.5) +   labs(title = "Weighted Percentage Planning Early Retirement by Education",        x = "Education level", y = "Percentage (%)")`

### Exporting tables and figures

For academic reporting, tables should be clear and reproducible. Use `knitr::kable()`, `gt`, or `flextable` to create well‑formatted tables. For example, to create a table of logistic regression results with odds ratios:

`library(broom) library(knitr) library(kableExtra)  model_results <- tidy(model_logit, exponentiate = TRUE) %>%   select(term, estimate, std.error, p.value) %>%   mutate(estimate = round(estimate, 2), std.error = round(std.error, 3),          p.value = round(p.value, 3))  model_results %>%   kable(col.names = c("Variable", "Odds ratio", "SE", "p-value"),         caption = "Survey-weighted logistic regression for early retirement intention") %>%   kable_styling(full_width = FALSE)`

Figures can be saved with `ggsave()` specifying width, height and resolution. In R Markdown, including code chunks with figures will automatically produce images. Ensure axes and legends are clearly labelled and footnote that estimates are weighted.

## Best Practices for R Programming and Project Organisation

To maintain clean and reproducible code in your thesis, adopt the following practices:

1. **Use scripts and R Markdown**: Keep your data processing, analysis and reporting in scripts or R Markdown documents. Use comments to explain steps and anchor code to the narrative.
    
2. **Keep data raw**: Store raw data in a `data/raw` folder and never modify it. Save cleaned data in `data/processed` with a script that documents how cleaning was done.
    
3. **Name objects meaningfully**: Use descriptive names for data frames and variables. Avoid abbreviations that are ambiguous.
    
4. **Modularise code**: Break analyses into functions or separate scripts for loading data, cleaning, analysis and plotting. This helps readability and debugging.
    
5. **Use version control**: Git and GitHub help track changes and collaborate. Commit small, meaningful changes with clear messages.
    
6. **Document your workflow**: Write a `README` file describing the project structure, how to reproduce the analysis and any dependencies.
    
7. **Write reproducible code**: Avoid interactive editing of data. Instead, write code to perform all transformations. Use relative file paths (e.g., `"data/raw"`) so the analysis runs on other machines.
    
8. **Handle missing values explicitly**: Decide how to treat missing data—whether to impute, drop or model them—and document your decisions. `dplyr` functions generally propagate `NA` values; use `na.rm = TRUE` in summarise functions when appropriate[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=3).
    

### Code styling

Follow a consistent style, such as the tidyverse style guide. Key points include:

- Use spaces around operators.
    
- Put each verb (`filter`, `mutate`, etc.) on a new line in pipelines, indenting arguments for readability[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=3).
    
- Avoid deeply nested code; use the pipe operator `%>%` to chain operations and emphasise sequential logic[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=3).
    
- Use `snake_case` for object names and function arguments.
    

### Checking assumptions and robustness

When presenting results, always discuss underlying assumptions. For survey analyses, these include the assumption that weights correctly reflect the inverse probability of selection and that responses are independent within clusters conditional on the design. Consider sensitivity analyses, such as excluding extreme weights or using replicate weights if available. Visualise residuals and predicted probabilities to identify outliers or influential observations.

## Conclusion

This manual has provided a step‑by‑step guide to analysing survey data on early retirement using R. Starting from importing and cleaning data, we introduced key `tidyverse` verbs—`filter()`, `mutate()`, `select()`, `pivot_longer()`, `pivot_wider()`—and functions from `stringr` and `forcats` for text and factor manipulations. We discussed how to join datasets correctly using mutating and filtering joins, emphasising the importance of primary and foreign keys[r4ds.hadley.nz](https://r4ds.hadley.nz/joins.html#:~:text=19). The guide explained the concept of survey weights and sampling designs, with formulas and rationale for weighting[tidy-survey-r.github.io](https://tidy-survey-r.github.io/tidy-survey-book/c10-sample-designs-replicate-weights.html#:~:text=). We created survey design objects using `svydesign()` and `as_survey_design()`, computed descriptive statistics and grouped summaries using `srvyr` functions[cran.r-project.org](https://cran.r-project.org/web/packages/srvyr/vignettes/srvyr-vs-survey.html#:~:text=Summary%20statistics), and performed design‑based hypothesis tests and regression models.

By following this manual, a thesis student can confidently handle complex survey data to investigate early retirement. The combination of tidyverse tools and survey‑specific functions ensures that analyses are both efficient and statistically appropriate. Keep practising with synthetic datasets, read documentation and always cross‑check your results. When in doubt, consult the original survey documentation to understand the sampling design and weight calculations. With careful planning, clear code and thoughtful interpretation, your survey analysis will provide valuable insights into the determinants of early retirement.

In summary, the guide begins by clarifying key concepts and variables related to early retirement and demonstrates how to set up a tidy R workflow. It explains importing and cleaning data, including filtering, selecting, and transforming variables with `dplyr`, and recoding and managing factors with `forcats`[r4ds.hadley.nz](https://r4ds.hadley.nz/data-transform.html#:~:text=the%20columns)[forcats.tidyverse.org](https://forcats.tidyverse.org/articles/forcats.html#:~:text=Manually%20reordering). The manual also covers string manipulation using `stringr` functions and reshaping data with `tidyr`’s `pivot_longer()` and `pivot_wider()`, providing clear code examples[stringr.tidyverse.org](https://stringr.tidyverse.org/articles/stringr.html#:~:text=There%20are%20four%20main%20families,of%20functions%20in%20stringr)[tidyr.tidyverse.org](https://tidyr.tidyverse.org/articles/pivot.html#:~:text=,cell%20values).

The guide then introduces survey weights and complex sampling designs, showing how to create survey objects with `svydesign()` and `as_survey_design()` and explaining the importance of weighting[stats.oarc.ucla.edu](https://stats.oarc.ucla.edu/r/seminars/survey-data-analysis-with-r/#:~:text=Sampling%20weights%3A%20There%20are%20several,will%20equal%20the%20population%20total)[epirhandbook.com](https://www.epirhandbook.com/en/new_pages/survey_analysis.html#:~:text=26). It illustrates descriptive analyses using `srvyr` functions like `survey_mean()` and `survey_total()` and demonstrates hypothesis testing with design-based t-tests and Rao-Scott chi-square tests[cran.r-project.org](https://cran.r-project.org/web/packages/srvyr/vignettes/srvyr-vs-survey.html#:~:text=Summary%20statistics)[r-survey.r-forge.r-project.org](https://r-survey.r-forge.r-project.org/survey/html/svychisq.html#:~:text=%60svychisq%60%20computes%20first%20and%20second,type%20tests). The manual concludes with modeling techniques such as survey-weighted linear and logistic regressions, guidance on visualization, best practices for project organization, and advice for communicating findings[rdocumentation.org](https://www.rdocumentation.org/packages/survey/versions/4.4-8/topics/svyglm#:~:text=Fit%20a%20generalised%20linear%20model,based%20standard%20errors). Overall, it provides a thorough, step-by-step roadmap for novice R users conducting survey research on early retirement.

Feel free to review the document and let me know if you need any more information or modifications.