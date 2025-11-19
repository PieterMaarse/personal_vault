---
MOC:
  - "[[$Scriptie]]"
tags:
  - clippings
  - bron
source: https://academic.oup.com/bib/article/24/2/bbad002/6991123?utm_source=chatgpt.com
published: 2023-01-18
created: 2025-11-19
description: Abstract. In longitudinal studies variables are measured repeatedly over time, leading to clustered and correlated observations. If the goal of the study i
about:
relevant_for:
type: paper
PDF: "[[Hu_Szymczak_2023.pdf]]"
---
## Abstract

In longitudinal studies variables are measured repeatedly over time, leading to clustered and correlated observations. If the goal of the study is to develop prediction models, machine learning approaches such as the powerful random forest (RF) are often promising alternatives to standard statistical methods, especially in the context of high-dimensional data. In this paper, we review extensions of the standard RF method for the purpose of longitudinal data analysis. Extension methods are categorized according to the data structures for which they are designed. We consider both univariate and multivariate response longitudinal data and further categorize the repeated measurements according to whether the time effect is relevant. Even though most extensions are proposed for low-dimensional data, some can be applied to high-dimensional data. Information of available software implementations of the reviewed extensions is also given. We conclude with discussions on the limitations of our review and some future research directions.

## Introduction

In many scientific fields including medicine, life sciences and economics, the analysis of longitudinal data plays a vital role. Take precision medicine as an example. The goal of precision medicine is to provide customized treatments to patients based on their characteristics and thus to improve treatment efficiency while avoiding serious side effects \[[1–3](https://academic.oup.com/bib/article/24/2/bbad002/)\]. With recent technological advances, large-scale genetic and other molecular data can now be collected. Along with demographic and clinical profiles they characterize each patient under different aspects. Many of these measurements, however, change over time, often depending on disease activity, treatment, comorbidities and other environmental factors. Consequently, it is important to measure them for the same patient repeatedly over time, and this leads to longitudinal data, where a single observation captures the measurements at a specific time point for a patient.

Depending on the research question, the study design and the outcome of interest, multiple longitudinal data formats can be envisioned. Predictors might be available for a single time point only, such as at baseline visit, or are time-invariant, which is the case for genetic variants. Alternatively, predictors are measured multiple times during a study. Similarly, the outcome can be determined at a single time point. Examples include response to treatment at the end of therapy or after a prespecified follow-up time. But it might also be of interest to predict the outcome over time such as disease activity or severity. Furthermore, the data format is related to the study design where the same number of measurements at fixed time points is taken for each subject or data from a varying number of irregularly spaced time points are available; the latter is often encountered in observational studies.

In general, a longitudinal data set can be formatted as in Table [1](https://academic.oup.com/bib/article/24/2/bbad002/). Here in total, there are $N$ subjects, for each of them, $ni$ ⁠, $i=1,…,N$ observations are measured, and each observation consists of measurements on $m$ responses and $p$ predictors.

Table 1

[Open in new tab](https://academic.oup.com/view-large/398982835)

General structure of longitudinal data

<table><thead><tr><th>Subject</th><th>Time</th><th colspan="3">Responses</th><th colspan="3">Predictors</th></tr></thead><tbody><tr><td>1</td><td>1</td><td><span><math><msub><mi>y</mi> <mrow><mn>111</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mn>11</mn> <mi>m</mi></mrow></msub></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mn>111</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mn>11</mn> <mi>p</mi></mrow></msub></math></span></td></tr><tr><td>1</td><td>2</td><td><span><math><msub><mi>y</mi> <mrow><mn>121</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mn>12</mn> <mi>m</mi></mrow></msub></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mn>121</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mn>12</mn> <mi>p</mi></mrow></msub></math></span></td></tr><tr><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td></tr><tr><td>1</td><td><span><math><msub><mi>n</mi> <mn>1</mn></msub></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mn>1</mn> <msub><mi>n</mi> <mn>1</mn></msub> <mn>1</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mn>1</mn> <msub><mi>n</mi> <mn>1</mn></msub> <mi>m</mi></mrow></msub></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mn>1</mn> <msub><mi>n</mi> <mn>1</mn></msub> <mn>1</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mn>1</mn> <msub><mi>n</mi> <mn>1</mn></msub> <mi>p</mi></mrow></msub></math></span></td></tr><tr><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td><td><span><math><mrow><mo>⋮</mo></mrow></math></span></td></tr><tr><td>N</td><td>1</td><td><span><math><msub><mi>y</mi> <mrow><mi>N</mi> <mn>11</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mi>N</mi> <mn>1</mn> <mi>m</mi></mrow></msub></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mi>N</mi> <mn>11</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mi>N</mi> <mn>1</mn> <mi>p</mi></mrow></msub></math></span></td></tr><tr><td>N</td><td>2</td><td><span><math><msub><mi>y</mi> <mrow><mi>N</mi> <mn>21</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mi>N</mi> <mn>2</mn> <mi>m</mi></mrow></msub></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mi>N</mi> <mn>21</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mi>N</mi> <mn>2</mn> <mi>p</mi></mrow></msub></math></span></td></tr><tr><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td><td><span><math><mo>⋅</mo></math></span></td></tr><tr><td>N</td><td><span><math><msub><mi>n</mi> <mi>N</mi></msub></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mi>N</mi> <msub><mi>n</mi> <mi>N</mi></msub> <mn>1</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>y</mi> <mrow><mi>N</mi> <msub><mi>n</mi> <mi>N</mi></msub> <mi>m</mi></mrow></msub></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mi>N</mi> <msub><mi>n</mi> <mn>1</mn></msub> <mn>1</mn></mrow></msub></math></span></td><td><span><math><mo>…</mo></math></span></td><td><span><math><msub><mi>x</mi> <mrow><mi>N</mi> <msub><mi>n</mi> <mn>1</mn></msub> <mi>p</mi></mrow></msub></math></span></td></tr></tbody></table>

Analyzing longitudinal data is not an easy task. The most distinct feature of longitudinal data is the repeated measurements from the same subject. This inevitably leads to clustered and correlated observations. The clustering effect is due to individual characteristics. For instance, average response to a drug could vary from patient to patient. In the meantime, if repeated measurements are collected over a period of time, then there could be serial correlation among measurements.

Furthermore the observation time for the longitudinal data can be either equally spaced or irregularly spaced, which may affect the approach that can be used for the analysis. Visits at every other month would lead to equally spaced observations, while following up at 6 months, 1 year and 2 years after the treatment provides an example of irregularly spaced observations. Additionally, irregular spacing can also occur in observational studies when there are no prespecified follow-up times. Apart from that, missing values can pose great challenges as they can turn an equally spaced observation schedule into irregular. More importantly, they may carry vital information when the missingness could be related to the value of the variable. More discussions on the characteristics of longitudinal data can be found in the classic textbooks \[[4](https://academic.oup.com/bib/article/24/2/bbad002/), [5](https://academic.oup.com/bib/article/24/2/bbad002/)\].

Despite the difficulties introduced by longitudinal data, they bring rich information. In the context of precision medicine, with longitudinal data, clinicians can better understand disease progression, especially of chronic diseases, so that patients can be properly stratified and treatment plans can be tailored accordingly \[[6–8](https://academic.oup.com/bib/article/24/2/bbad002/)\]. Furthermore, repeated measurements allow the patients’ treatment responses to be captured more accurately, so that effective therapies can be implemented and evaluated.

The development of prediction models with longitudinal data using statistical or machine learning (ML) approaches is also crucial \[[9](https://academic.oup.com/bib/article/24/2/bbad002/)\]. One of the state-of-the-art ML methods for the development of prediction models is the random forest (RF) algorithm \[[10](https://academic.oup.com/bib/article/24/2/bbad002/)\]. It is a nonparametric approach that can accommodate different types of responses such as categorical or quantitative outcomes and survival times \[[11](https://academic.oup.com/bib/article/24/2/bbad002/)\]. Moreover, it can work with predictors of various scales or distributions and is suited for applications in high-dimensional settings where the number of predictors can be larger than the number of observations \[[12](https://academic.oup.com/bib/article/24/2/bbad002/), [13](https://academic.oup.com/bib/article/24/2/bbad002/)\]. Thus, it is very suitable for analyzing complex data such as omics data, which are often high-dimensional, plus metabolite and protein levels are usually skewed and left censored by limits of detection, and microbiome abundances often exhibit an excess of zeros. Furthermore, tree-based methods form data-driven subgroups of samples, which can be beneficial for patient stratification. Via the so-called variable importance measures, the method can also highlight the relevance of each predictor \[[10](https://academic.oup.com/bib/article/24/2/bbad002/)\]. This could be especially handy for pharmacogenomics \[[14](https://academic.oup.com/bib/article/24/2/bbad002/), [15](https://academic.oup.com/bib/article/24/2/bbad002/)\], where potential genetic variants associated with drug response phenotypes can be identified. Svetnik *et al*. (2004) \[[16](https://academic.oup.com/bib/article/24/2/bbad002/)\], for example, demonstrate that RF provides comparable or better prediction for compound’s biological activity in drug discovery process compared with conventional methods such as partial least square and support vector machine.

However, as with other ML methods, the RF algorithm assumes that observations are independently sampled from a population. Conducting statistical analysis on longitudinal data without considering the dependency among observations could lead to biased inference due to underestimated standard errors in linear models \[[17](https://academic.oup.com/bib/article/24/2/bbad002/)\] and spurious subgroup identification and inaccurate variable selection in tree-based methods \[[18](https://academic.oup.com/bib/article/24/2/bbad002/), [19](https://academic.oup.com/bib/article/24/2/bbad002/)\]. Furthermore, classification methods that match the data structure and thus properly handle the correlation due to repeated measurements have better prediction performance \[[20](https://academic.oup.com/bib/article/24/2/bbad002/)\].

Therefore, in this review, we will present a range of extensions of the standard RF algorithm for the analysis of longitudinal data. Even though we mention the applications of these methods within the context of precision medicine, our review is not a summary on studies analyzing longitudinal data, but rather provides an overview of available methods and their implementations. We limit our attention to RF based on the classification and regression tree (CART, \[[21](https://academic.oup.com/bib/article/24/2/bbad002/)\]) with a focus on prediction of categorical and quantitative outcomes. In section we consider the univariate response longitudinal scenario. We start with a short review on the standard RF in subsection . Following that, in subsection the case of repeated measurements or clustered data is investigated. Subsection then presents methods that incorporate time effect into modeling. Section focuses on extensions of RF algorithm suitable for multivariate responses. We provide information on the currently available implementations of the reviewed methods in section . We conclude with a discussion in section .

## Univariate response longitudinal data

We start with the simple scenario where we have univariate response longitudinal data; that is $m=1$ in Table [1](https://academic.oup.com/bib/article/24/2/bbad002/). We first briefly review the standard RF algorithm as a prediction model. Several RF extension methods are then presented and discussed, which are categorized by their ways of incorporating the time effect.

### Standard RF algorithm

RF is an ensemble of decision trees where each tree is built from a bootstrapped version of the training data set. Each tree is grown via the principle of repetitive partition where starting from the root node, the same node splitting procedure is applied repetitively until certain stopping rules are met. Its power in prediction comes from the aggregation of many weaker learners (decision trees). The performance is especially good if the correlations between trees in the forest are low. More detailed descriptions and discussions on RF can be found in \[[10](https://academic.oup.com/bib/article/24/2/bbad002/), [22](https://academic.oup.com/bib/article/24/2/bbad002/)\].

For a binary decision tree such as CART, the node splitting process consists of selecting a splitting variable and determining the splitting rule. The guiding principle for node splitting is to minimize the impurity of response values in each node, which is often measured by the Gini index if the response variable is categorical or by the variance if it is quantitative. The growth of each decision tree ends if the nodes to split are already pure (all samples within the node come from the same class or have the same response value) or other predetermined stopping rules are met. The nodes in the final layer of a tree are called leaves and are used for prediction of new observations. More detailed discussions on CART can be found in \[[21](https://academic.oup.com/bib/article/24/2/bbad002/)\].

To make prediction with RF, an observation goes through every decision tree in the forest. The final prediction for the observation from the RF is made either by majority voting or averaging, based on results from all decision trees in the forest. Because the RF algorithm uses bootstrap samples to grow each decision tree, some observations are left out in the construction of a given tree. By treating these out-of-bag (OOB) samples as observations needed to be predicted, it can, therefore, provide an estimate of prediction error of the constructed forest.

In addition, the so-called variable importance measure can be obtained for each predictor, which measures its relevance to prediction. Thus, for high-dimensional dataset such as omics data, variable selection procedures based on variable importance measure are possible (see \[[23](https://academic.oup.com/bib/article/24/2/bbad002/)\] and the reference therein for a description and comparison of various variable selection procedures based on variable importance measure).

Although it is possible to directly utilize the standard RF algorithm for longitudinal data analysis, it may suffer from several problems. As shown in Figure [1](https://academic.oup.com/bib/article/24/2/bbad002/), bootstrapped samples for different decision trees may have a high chance to include observations from every subject. This may cause correlated or even homogeneous trees to deteriorate the prediction performance. In addition, the estimated prediction error based on OOB samples is often too optimistic due to the high similarity between the observations from the same subject \[[24](https://academic.oup.com/bib/article/24/2/bbad002/)\]. Therefore, there is a need to build extensions of standard RF for longitudinal data analysis.

![Illustration of bootstrap samples used to construct decision trees in standard RF when it is applied to clustered data.](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/m_bbad002f1.jpeg?Expires=1766162541&Signature=o~Dp4rpqEcJuLLhAki-azXOm0I0-kXMaEUzMYnjbBf6zewHm3qsCexAKgy-ussE4Nb-bJaHkWdgvtKEFgpzQ2ClAQPUi82-1vMleTcYmz52BnmiVZktzZlZ12Pet4UwpDTCFCXdnRKsifgHkE8zwGgIlyRCwytpnJSHZmg9hEBb88vQYx~tt~4GGa0l14~aCw0ueEEoBn9jIQCXn0nLTA5Yg6ha8yHglgLwC8Gvgu8XZnDfmr4DUCA9W10lDBA--2ekbWyua9bGgCQpVsFNvu4zWvq3QCvcYcYsV2Oh0Szd2OH~NRp6PbOlRKmirixsXotlQN-oELVqrLRuxFVayXA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 1

Illustration of bootstrap samples used to construct decision trees in standard RF when it is applied to clustered data.

[Open in new tab](https://academic.oup.com/view-large/figure/398982850/bbad002f1.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/bbad002f1.jpeg?Expires=1766162541&Signature=YI9mBUUjK7Zn4zJYrfqsjaPCdMA05gEFe3iAqYSrd~zriQABsBZ63HZS7PVqlaxlmJ4wx-zo~xEzx5MSL83AW8NFKNWk5OuBKRi4gb9C~xLDFCNSBeTuNZpNze0V1Id3jDKBSvFQ3iIlAOOt~5FGGeI28Q616IkAsOA480PFwYoBrwj8vSSK4VXnTsjFjoqOSWHcnhCHGZPWv59p2YUg59ksRtB8jy6EEvmFZPCGNRiWM1qYCA-O6hUCL3LbB88ALoINZ-ETsZL-dg3eEx5NF-OduJZimVnHO5BC~1Zc1PfRTdcHm5iaIErRSiO6w17kYvRlCOLFVfUm5~LDOouncg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=398982850&ar=6991123&xsltPath=~/UI/app/XSLT&imagename=&siteId=5143)

### Clustered data

In some applications, the observations are made repetitively on the same subject as duplications. This results in clustered data setting. In such setting, the data still follow the general format shown in Table [1](https://academic.oup.com/bib/article/24/2/bbad002/), but there is hardly any time effect. In other words, the ordering of the observations from the same subject can be ignored and is not considered in training the prediction model. Hence, one model for clustered data can be written as follows.

(1)

where $μi$ reflects the mean value of subject $i$ ⁠, and $εij$ are random fluctuations with mean $0$ and independent from each other for all $j=1,…,ni$ and across all $i=1,…,N$ ⁠. The clustering effect, therefore, is the consequence of the shared mean value for observations from the same subject.

#### Averaging

One intuitive approach to deal with the aforementioned clustering effect of repeated measurements is to take the average of replicated data for each subject. This then brings the data structure back to the usual one-subject-one-observation scenario and retain the needed independence for standard RF algorithm. Vlahou *et al*. (2004) \[[25](https://academic.oup.com/bib/article/24/2/bbad002/)\] takes this approach to analyze mass spectrometry data for protein profiling in urine.

Despite the simplicity, this approach suffers from a loss of information. The intrasubject variation is averaged out. Moreover, this approach also masks the imbalance design. Different subjects could contribute different numbers of observations in the original data set, as in Table [1](https://academic.oup.com/bib/article/24/2/bbad002/), $ni$ could be different for $i=1,…,N$ ⁠, which may be due to some characteristics of the subjects and may carry underlying distributional information. However, after averaging out the repeated measurements, each subject now makes equal contribution to the training data set. This can have potential effects on the prediction efficiency and variable selection. Karpievitch *et al*. (2009) \[[24](https://academic.oup.com/bib/article/24/2/bbad002/)\] showed that this approach, when compared with the standard RF, is more sensitive to the total number of subjects $N$ ⁠; reduction in $N$ leads to poorer prediction and variable selection. The averaging approach may also be difficult to use when classification and categorical predictors are concerned. For a given patient, his/her cholesterol level based on different blood samples may vary that could lead to different categorization; one observation falls into normal level and another belongs to high level. The averaging approach needs to average all observations of this patient to end up with a subject-level measurement for analysis. However, when different observation-level measurements from the same subject fall in different categories, this averaging would be impossible.

#### Subject-level bootstrapping

To overcome the disadvantages that averaging approach have, extensions that can utilize all observations are designed. Karpievity *et al*. (2009) \[[24](https://academic.oup.com/bib/article/24/2/bbad002/)\] proposed the subject-level bootstrapping strategy to replace the original one, and the resulting algorithm is named as RF++. Specifically, when drawing bootstrap samples to construct decision trees in an RF, instead of resampling at the observation level, as shown in Figure [2](https://academic.oup.com/bib/article/24/2/bbad002/), bootstrap resampling at the subject level is performed and all observations from the selected subjects are included as in-bag observations.

![Illustration of subject-level bootstrap samples used to construct decision trees in RF++.](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/m_bbad002f2.jpeg?Expires=1766162541&Signature=uYDmclEHA2gzHHULG9YawM7WGrKwsXsrQWeKumTZ1lBVGJgCd8kivP2jo07OWQqTwiLLJV5FjkCjZvPd~S6QeCAweoPqCeA1hGm7XhKbppSoLpeufaQOqdfCokaHpEzUAVw~Tl6GMdxx8YSG~v2gZ6kQzcj-EiT9DcZCQDPc2wN-clP-5h2fXFLDPOYLQNi53tk~65PCbt-1eDe52LV5JqmGLn7ZoEg3iDZ1XSv7SUcS8HfGcnGEX3wpGR9k5AtmHvqkxLn3CzBgcXu1BbeM0DdmFJ3PuU4YhAwjbXJYdALeaTz8y5efLdR6dcyO~JRGBpW74Nm5oIRhyalwoFvJiw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 2

Illustration of subject-level bootstrap samples used to construct decision trees in RF++.

[Open in new tab](https://academic.oup.com/view-large/figure/398982858/bbad002f2.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/bbad002f2.jpeg?Expires=1766162541&Signature=B-2ZMLRtOAeeme-hlEjr3lEtGuTJY0S2thLLxspcyIEMJ-1sRxqsx-7uABHWdI6qkaa8UmIg4AlUTo2GtNEh2AGFkBXKKZa98VJyZjdEwkLllAPFshXGqHq6oyXy3qutUZlQrFuu01sJgZJ1PuDoKkrwBt1E6ewQiWZwUvbj79~Pxj~QogA3ykujGGRpqwxmELdWAeRVo2aCKHTrYKTG9wr9fEy~~yfooUuoTEndCpGRn6thWcf8nnnoqMU~U9QD8T3PFlhuNDnsbgkIFRjCvA9jzXc4Smh8lf-oNtkBbjbcLe2Rofaaa4bOjrEXh1IC0-6R~hrmeTVGgjrAF18I2g__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=398982858&ar=6991123&xsltPath=~/UI/app/XSLT&imagename=&siteId=5143)

Adler *et al*. (2011a) and Adler *et al*. (2011b) \[[26](https://academic.oup.com/bib/article/24/2/bbad002/), [27](https://academic.oup.com/bib/article/24/2/bbad002/)\] further extended this idea to a two-stage bootstrapping strategy. Firstly, one subject $i$ is chosen randomly and all associated observations are in bag. Afterwards for each chosen subject $i$ the training samples are chosen by randomly selecting one observation from all $ni$ measurements. Adler et al. (2011b) \[[27](https://academic.oup.com/bib/article/24/2/bbad002/)\] showed in their simulation studies that subject-level resampling based on one observation per subject yields the best prediction results compared to the standard RF, averaging approach and RF++, although one should also notice that different settings may lead to different results and there could be cases where the other methods are more preferable.

The adoption of subject-level bootstrapping avoids the problem of potentially exposing individual trees to all subjects. The two-stage bootstrapping strategy could further mitigate the negative effect the intrasubject correlation casts on the prediction performance; when only one observation per subject is selected, even though the same subject might be used in construction of different trees, likely different observations are selected for the training of different trees, which further reduces the similarity between trees.

Besides the usual observation-level classification, Karpievitch *et al*. (2009) \[[24](https://academic.oup.com/bib/article/24/2/bbad002/)\] showed that classification at subject level is also possible. A majority vote can be performed across the observations belonging to the same subject to result in the subject classification. With such results, a subject-level misclassification rate estimate based on OOB samples is also made possible. This information may be more beneficial and easier to interpret in clinical trials.

However, as pointed out in Hajjem *et al*. (2014) \[[28](https://academic.oup.com/bib/article/24/2/bbad002/)\], the subject-level bootstrapping only adjusts the sampling method for clustering; thus, no random effects are incorporated in the modeling as well as prediction. Furthermore, for longitudinal studies where time plays a role, this strategy cannot fully utilize the information contained in the data set.

### Time effect considered

For many research questions, not only values of predictors at the current time point, but also from the past are helpful, sometimes even crucial, for a good prediction performance. A large value of a particular biomarker might be relevant if it had rather small values in the past, pointing to an early change on the molecular level. Therefore, in this section, we would like to review several RF extensions that take time effect into consideration.

#### Historical RF

The historical RF, proposed by Sexton and Laake (2018) \[[29](https://academic.oup.com/bib/article/24/2/bbad002/)\], is an approach that explicitly considers the history of predictors. Assume that we have training data ${yij,tij,Xij}$ ⁠, $i=1,…,N$ and $j=1,…,ni$ ⁠. Here $yij$ denotes the response, $Xij$ the vector of predictors and $tij$ the time of the $j$ -th observation on the $i$ -th subject. The method estimates a model for the response $yij$ using both $(tij;Xij)$ (the observations concurrent with $yij$ ⁠) and all preceding observations of the $i$ -th subject up to (but not including) time $tij$ ⁠. Thus, for a time-varying predictor, its historical information along with its current value are both used for modeling. For a time-invariant predictor, of course, only its current value is used as in the standard RF.

For time-invariant predictors the standard splitting procedure is adopted when constructing each decision tree. In case of a time-varying predictor, its historical information, i.e. values within a specific time interval before the time concurrent with $yij$ ⁠, is first represented by a summary function. One exemplary such function for subject $i$ at time point $j$ counts the number of past observation values, including both response and predictor variables, that are measured at a maximum of $η1$ units of time before the current time point $j$ and smaller than $η2$ ⁠, i.e.

(2)

where $z¯ij={zil=(yil,xil):til<tij}$ denotes the past observations of subject $i$ prior time $j$ ⁠, and $z¯ijk$ is its $k$ -th component. This aggregation results in a single number per observation and variable for a fixed value of $η=(η1,η2)$ ⁠. For each summary function, there is also a windowed version where the time interval considered is further limited by an upper bound, i.e. $til∈[tij−η1,tij−η3)$ in equation (). The different functions usually lead to similar prediction performance (personal communication). However, it should be noted that only the frequency based functions are scale invariant, which is one of the properties that make the standard RF algorithm robust. Finally, the partitioning at a particular node is performed using the predictor with the smallest Gini impurity or sum-of-squares error for categorical or quantitative response, respectively. However, determination of an optimal cut-off point for time-varying predictors includes optimization of the parameters in the summary function such as $η$ ⁠, which largely increases the computing expenses especially when the number of time-varying predictors is large such as in some omics datasets.

To mitigate the effects of additional optimization of the parameters in the summary function, Sexton and Laake (2018) \[[29](https://academic.oup.com/bib/article/24/2/bbad002/), [30](https://academic.oup.com/bib/article/24/2/bbad002/)\] incorporate an additional level of randomization where instead of using all observations within the specified time interval, only a sub-sample is randomly selected and used for optimizing the cut-off point. In addition, subject-level resampling strategy is also adopted in RF construction. This not only enjoys the advantages mentioned in Section , but also keeps the complete observation history of a subject.

This method also does not include random effects in the modeling, so the prediction is solely based on the estimated fixed effects.

#### Extensions from (generalized) linear mixed effects model

A different approach to adjust for the longitudinal structure is to combine (generalized) linear mixed models ((G)LMMs) with the decision tree or RF algorithm. The (G)LMM is a classic statistical methodology for the analysis of longitudinal or more general clustered data. As with (G)LMMs the predictors can be constant or varying over time and different time points are possible for each subject. One advantage of (G)LMM is its explicit modeling of intrasubject correlation structure as well as subject-level random effects besides the main fixed effects of interest. After properly adjusting for these random effects and correlation structure, the longitudinal data become conditionally independent; thus, the estimation of the fixed effect component of the model follows exactly the same way as if independent observations were observed. Moreover, prediction can now be generalized to a wider population. However, the drawbacks of this approach include its computational complexity to fit mixed effects models as well as the possibility to misspecify the intrasubject correlation structure. More detailed descriptions, discussions and applications on classical methods for longitudinal data analysis can be found in several textbooks \[[4](https://academic.oup.com/bib/article/24/2/bbad002/), [5](https://academic.oup.com/bib/article/24/2/bbad002/)\].

The general idea of the RF extension from (G)LMM is to replace the linear model of the fixed effect component by a tree or RF while keeping the modeling of the dependence structure with random effects. Multiple algorithms have been developed to incorporate the tree or RF into the (G)LMM and are summarized in Table [2](https://academic.oup.com/bib/article/24/2/bbad002/). As can be seen, most extensions are based on two approaches, namely, MERT and RE-EM trees. For binary response, a Bayesian approach called BiMM has also been proposed.

Table 2

[Open in new tab](https://academic.oup.com/view-large/398982873)

Overview of different RF extensions from (G)LMM

| Outcome | Tree | Forest |
| --- | --- | --- |
| Quantitative (Gaussian) | MERT | MERF |
|  | RE-EM tree | REEMforest |
|  | SMERT | SMERF |
|  | SREEM tree | SREEMforest |
| Exponential family | GMERT |  |
|  | GMET | GMERF |
| Binary | BiMM tree | BiMM forest |

We first describe approaches for a regression setting based on LMMs, followed by more general methods using GLMMs that can be employed in the context of classification but also for other types of outcomes such as count variables.

**Quantitative (Gaussian) response variable**

For a normally distributed quantitative outcome, the classic LMM model can be written as where $yi=(yi1,…,yini)′$ is the $ni×1$ vector of the outcome for the $ni$ observations of subject $i$ ⁠, $Xi=[xi1,…,xini]′$ is the $ni×p$ matrix of predictors considered as fixed effects, $Zi=[zi1,…,zini]′$ is the $ni×q$ matrix of predictors modeled as random effects, $ϵi=(ϵi1,…,ϵini)′$ is the $ni×1$ vector of random errors, $β$ is the $p×1$ unknown vector of parameters of the fixed effects, and $bi$ is the $q×1$ unknown vector of random effects of subject $i$ ⁠. Both $bi$ and $ϵi$ are assumed to follow a normal distribution with mean zero and covariance matrix $D$ and $Ri$ ⁠, respectively. It is further assumed that they are independent and that the observations between subjects are also independent. The parameters can be estimated by maximum likelihood (ML) or restricted maximum likelihood (REML) methods.

Two different strategies have been proposed in the literature to replace the linear dependency between the predictors and the outcome. The first approach is the mixed effects regression tree/forest (MERT by Hajjem *et al*. (2011) \[[31](https://academic.oup.com/bib/article/24/2/bbad002/)\] and MERF by Hajjem *et al*. (2014) \[[28](https://academic.oup.com/bib/article/24/2/bbad002/)\]) where the fixed effects are estimated using a regression tree or RF. Specifically, the modified model can be written as

(3)

where it is further assumed that $Ri=σ2Ini$ where $In$ denotes the identity matrix with size $n$ ⁠, and the function $f(Xi)$ is estimated by the regression tree or RF. For model fitting an expectation-maximization (EM) algorithm \[[32](https://academic.oup.com/bib/article/24/2/bbad002/)\] is used, which iterates between estimation of the fixed and random effects components. The general approach can be described as in Algorithm 1 (slightly modified from \[[31](https://academic.oup.com/bib/article/24/2/bbad002/)\] and \[[28](https://academic.oup.com/bib/article/24/2/bbad002/)\]).

![graphic](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/m_bbad002fx1.jpeg?Expires=1766162541&Signature=nyvieH3irFzGH2iAOngK90C-JRivSUMBkNo75K63EJrduag1z3gn5UFvWGbaqQM4cb7p3K~56NJMgw9Zs1GHP14zHj04d-j85gc8uBGTTPpaWWQHFDrPvildAFDDOWZfKGQ~ODxNxT~5gYMGMtrYsVif8piCk7jBd8a1JsqrsXyComFGfaHI2c2CcMB73NgN1CaUMWshmhCi7eFcvtTtvkQxk0ApUolG5vXVelYvVVaD66~cUVgou66XNx1QWcJGNMagyjiY75~E1RPzCWKUbhYdQa2Qa~~GBJDX2yvYZdT-vVLWT36pNT15fQhfKsJoVMkWFl9werN0Ezm2jfaMwg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

The convergence is based on a generalized log-likelihood criterion

This method assumes that the correlation is only due to between subject variation, i.e. the covariance matrix $Ri$ of the errors $ϵi$ is assumed to be diagonal. The MERT approach uses a decision tree to estimate $f(Xi)$ ⁠, whereas the MERF method improves prediction performance by considering a standard RF. It can be noticed that in MERF the bootstrap sample for each tree is drawn on the observation level and predictions are based on the OOB sample to reduce the risk of overfitting. Note that resampling of individual observations is possible in this setting since it is assumed that the correlation between observations can be completely modeled by the random effects. Thus, using the modified outcome variable $yi∗$ results in independent observations.

The second approach is independently proposed in Sela and Simonoff (2012) \[[19](https://academic.oup.com/bib/article/24/2/bbad002/)\], called random effects expectation-maximization (RE-EM) trees. It still considers the model (), but it does not directly use tree or RF algorithms to estimate the fixed effects. Instead it considers the partition of samples formed by the regression tree and estimates local fixed effects within each partition while estimating the random effects globally. The algorithm is similar to MERT in using the generalized log-likelihood as convergence criterion.

More specifically, for model fitting, the initialization is the same as for MERT, and the rest is modified as shown in Algorithm 2.

![graphic](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/m_bbad002fx2.jpeg?Expires=1766162541&Signature=cxbnZ9XkX3K0rFZ7ZCobNQT0-NdiEd2XeBuko8fF7aLxKYgLsWImxLnZBuMVTuZTAuKiqhtAUCKPzw9QSeff~wckz2Cxaky0zM8mkxBeaGnE8lpwvR31ld5EnwJmzVnNhS8s5LeYGsEosE1kf7MmaQv3~AMIR9cCvVuGe0hNh5UNEmwTc5QWVV5WXdf1Rwzi0t8b4i538Mi4ATHae6KKthtdo~jZSssQaxnLNHqfmtVCjokJxD7LQ3wq~XX93QtML~xwFurSKDvI-pnmnT76ttvRBQyvWWaRuI-8aU~PDprEygcP~qiYBu~y-geYPOrb1y7mRRwXmSskDp4VKHgwuA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

The tree is thus only used to define the partition of the sample space and a system of LMM models is fitted with global random effects and each partition having its own local fixed effects. The *lme* function in the R package *nlme* is employed for LMM model fitting which allows a general within-subject correlation structure; for instance, an autocorrelation structure within the errors is possible so that $Ri$ can be a nondiagonal matrix.

An extension of the RE-EM tree has recently been proposed by Capitaine *et al*. (2021) \[[33](https://academic.oup.com/bib/article/24/2/bbad002/)\] and is called REEMforest where an ensemble of RE-EM trees is generated for the fixed effects estimation. The function $f^(Xi)$ is estimated by the mean of the $K$ fitted RE-EM trees: where $Φi,k$ is the $ni×T$ indicator matrix based on the tree $k$ and $μ^k$ is the $T×1$ vector of fitted local fixed effects from tree $k$ ⁠.

To further consider serial correlation within the observations of the same subject, the MERT and RE-EM tree and their corresponding forest variants have also been extended to include an additional stochastic component in Capitaine *et al*. (2021) \[[33](https://academic.oup.com/bib/article/24/2/bbad002/)\]. The resulting approaches are correspondingly called SMERT, SREEMtree etc. The model with the additional stochastic component can be written as follows: where $ωi=(ωi(t1),…,ωi(tni))′$ is a centered Gaussian process with $Cov(ωi(s),ωi(t))=γ2Γ(s,t)$ ⁠. The $ωi(t)$ are independent for different subjects $i=1,…,N$ and $bi, ϵi$ and $ωi(t)$ are mutually independent. Again, a variant of the EM algorithm is used to estimate the parameters where the definition of the new variable $yi∗$ now includes the additional stochastic component: $yi∗=yi−Zib^i−ω^i$ ⁠. In their simulation studies, Capitaine *et al*. (2021) \[[33](https://academic.oup.com/bib/article/24/2/bbad002/)\] showed that both MERT and RE-EM based tree and RF algorithms are applicable to high-dimensional datasets and provide more accurate prediction than LMM and standard RF.

**Generalized response variable**

The approaches described so far in this section assume a quantitative outcome that is normally distributed. Further extensions have been proposed for other types of outcomes by using generalized linear mixed models (GLMMs) instead of LMMs.

The GLMM assumes that, conditional on the random effects, the outcome $yi$ follows a distribution from the exponential family. The GLMM model can be further specified as: where $μi=E(yi|bi)$ ⁠, $g(⋅)$ is a known link function, and $ηi$ is a $ni×1$ vector. Commonly used link functions include identity link, logit link and log link functions for quantitative, binary and count outcomes, respectively. Parameters of GLMMs are estimated by ML or REML methods using numerical optimization algorithms such as penalized quasi-likelihood (PQL) \[[34](https://academic.oup.com/bib/article/24/2/bbad002/)\], iteratively reweighted least squares or a Newton–Raphson method \[[35](https://academic.oup.com/bib/article/24/2/bbad002/)\].

Similar to the quantitative outcome case, the RF extensions from GLMM replace the linear relationship between outcome and fixed effects predictor variables by a nonparametric alternative such as a decision tree or RF. The essential estimation procedure is again using an iterative algorithm inspired by the EM algorithm \[[32](https://academic.oup.com/bib/article/24/2/bbad002/)\] to estimate the fixed and random effects separately and iteratively. Here, we only provide a brief summary of the approaches and mention their quantitative counterparts. For more details, we refer the reader to the original publications.

The MERT approach has been extended to the generalized mixed effects regression tree (GMERT) in Hajjem *et al*. (2017) \[[36](https://academic.oup.com/bib/article/24/2/bbad002/)\]. The PQL algorithm of the GLMM is modified so that a weighted MERT pseudo-model is used instead of the weighted linear mixed-effects pseudo-model. The fixed part is again estimated with CART. In this implementation it is necessary to specify initial estimates of the mean values $μ^i$ ⁠. In the simulation study with a binary outcome the authors used predetermined values $μ^ij=0.25$ if $yij=0$ and $μ^ij=0.75$ if $yij=1$ ⁠. Unfortunately, no further discussions on this initialization were presented.

Similarly, Fontana *et al*. (2018) \[[37](https://academic.oup.com/bib/article/24/2/bbad002/)\] extends the RE-EM tree to the generalized mixed effects tree (GMET). Again, a regression tree is used and the indicator variables for the terminal nodes are modeled as fixed effects in the mixed effects model. The modified outcome variable for the regression tree is $yi∗=ηi−Zibi$ ⁠. However, $ηi$ needs to be estimated that is usually achieved with a standard generalized linear model (GLM) using the predictors as fixed effects covariates (in \[[37](https://academic.oup.com/bib/article/24/2/bbad002/), [38](https://academic.oup.com/bib/article/24/2/bbad002/)\]). Note that this approach is not possible for high-dimensional data due to this need to estimate $ηi$ with GLM since the number of variables then cannot exceed the number of observations. To the best of our knowledge, no solutions for high-dimensional data have so far been proposed in the literature along this direction. GMET has further been extended to generalized mixed effects random forest (GMERF) in Pellagatti *et al*. (2021) \[[38](https://academic.oup.com/bib/article/24/2/bbad002/)\] where instead of growing only a single decision tree, an RF is trained.

#### A Bayesian approach

For binary outcomes, Binary Mixed Model (BiMM) tree proposed in Speiser *et al*. (2020) \[[39](https://academic.oup.com/bib/article/24/2/bbad002/)\] considers a Bayesian implementation of GLMM. The GLMM portion of the BiMM method has the form where $CART(Xit)$ are indicator variables reflecting membership of each longitudinal observation $t$ for subject $i$ in terminal nodes within the decision tree. Therefore, the use of the tree in this approach is again not to model the fixed effects directly, but rather to determine similar groups of observations after random effects have been properly adjusted.

For estimation the BiMM tree method again adopts the EM-like algorithm and iterates between developing CART models using all predictors and then using information from the CART model within a Bayesian GLMM to adjust for the clustered structure of the outcome.

This tree method is further extended to a forest-based method by Speiser *et al*. (2019) \[[40](https://academic.oup.com/bib/article/24/2/bbad002/)\] where all $CART(Xit)$ are replaced by $RF(Xit)$ ⁠. More details of the algorithms can be found in the corresponding paper.

Lin and Luo (2019) \[[41](https://academic.oup.com/bib/article/24/2/bbad002/)\] considers the same model for binary outcomes and proposed a multilevel CART (M-CART) for estimation. The only difference between their method and BiMM is that they fit a multilevel logistic model instead of a Bayesian GLMM in the EM-like iterations to adjust for the clustered structure of the outcome.

Compared with the M-CART and previously reviewed frequentist methods, the Bayesian approach, as pointed out by the authors, can avoid issues with model convergence, especially when data are high dimensional. In addition, when uninformative priors are used, frequentist GLMM results can be obtained. That is to say, the Bayesian approach provides a more general framework with frequentist approaches such as RE-EM tree/forest as special cases.

#### Prediction with RF extensions from (G)LMM model

When making predictions with aforementioned RF extensions from a (G)LMM model, two different settings have to be distinguished. The first case is prediction for a new subject $i$ for which no random effects $b^i$ are available. This happens when the subject does not belong to the training dataset. Thus, prediction is solely based on the fixed effect component, which is either given by the prediction of the tree or RF or the predicted effect associated with the terminal node in which the new observation lands (⁠ $Φjtiμ^t$ ⁠). The other case is to predict a new observation for a subject $i$ used in the training process. In this case, the estimated random effects are available, so the sum of the fixed component and the corresponding random effect of subject $i$ can be used together.

## Multivariate response longitudinal data

So far, the reviewed methods are designed for univariate response longitudinal data; however, we can also treat measurements at different time points together as multivariate responses or a discretized response curve. Therefore, in this section, we would like to shift our attention to extensions of the RF algorithm that can accommodate multivariate response variables.

Before we start, we would like to note that the algorithms in this section are directly applicable with time-invariant predictors such as genetic data. If predictors are also observed at multiple time points, techniques from the previous sections need to be used along with the modifications reviewed in this section for an adequate analysis.

### Repeatedly measured univariate longitudinal responses as multivariate response

Even though the within-subject correlation cannot be disregarded, at the subject level, the usual independency assumption is still reasonable. Therefore, one strategy for longitudinal data analysis is to consider observations at different time points jointly so that each subject has only one multi-dimensional response.

To accommodate multivariate responses, the common strategy to extend the RF algorithm largely focuses on modifying the split criterion in the construction of each decision tree, where impurity measures are modified so that multivariate responses can be handled properly. In addition the covariance structure needs to be considered when defining the impurity measure to account for the inter-dimensional correlation. The modifications can be roughly categorized into two classes, using either distance or likelihood based split criteria.

#### Distance-based impurity functions

Segal (1992) \[[42](https://academic.oup.com/bib/article/24/2/bbad002/)\] was among the first to extend CART to longitudinal data by using a distance based measure for node impurity. Specifically, the author considered a univariate quantitative response but treated measurements at different time points jointly as a multivariate response. It is further assumed that the observation times for all subjects are the same, so that the dimension of the multivariate response is fixed and not changing across subjects. For a given node $t$ ⁠, Segal (1992) \[[42](https://academic.oup.com/bib/article/24/2/bbad002/)\] considers the following generalized sum of square function:

(4)

where $yi, i=1…,N$ is a $n×1$ vector, $y¯t$ is the sample average of $yi$ ’s within node $t$ ⁠, $V(θ,t)$ denotes the $n×n$ covariance matrix of the responses within node $t$ and depends on unknown parameters $θ$ ⁠, which can be estimated within the node. In principle, the estimated parameters $θ^$ can differ for node $t$ and its daughters $tL$ and $tR$ ⁠, which as the author noticed may lead to impurity increase. Hence, the author further imposes the restriction that for each candidate split the covariance parameters are determined from the parent node $t$ so that Furthermore, the author provides several candidates for the covariance structure, namely, independence (i.e. diagonal matrix), 1st-order autoregression (AR1), compound symmetry (CS) and sample covariance matrix.

The independence structure leads to the sum of square about the mean: where $yij$ is the outcome for subject $i$ and component $j$ ⁠, and all subjects are assumed to have same number of $n$ components. This is a direct generalization from the univariate regression tree, and has been used by De’Ath (2002) \[[43](https://academic.oup.com/bib/article/24/2/bbad002/)\] for applications in ecology and by Segal and Xiao (2011) \[[44](https://academic.oup.com/bib/article/24/2/bbad002/)\] in the construction of the multivariate RF.

When the sample covariance matrix is adopted in Segal’s approach, the generalized sum of square function in equation () is closely related to the Mahalanobis distance where the Mahalanobis distance of an observation $yi$ from a set of observations with mean $μi$ and (nonsingular) covariance matrix $S$ is defined as Larsen and Speckman (2004) \[[45](https://academic.oup.com/bib/article/24/2/bbad002/)\] directly considered the Mahalanobis distance as node impurity measurement and split criterion. Instead of updating the covariance structure during the tree construction, they estimate the covariance matrix from the whole data set at the very beginning and use the estimate throughout the whole process. They still consider the simple average of observations in each node for $μi$ ⁠, but different estimators such as trimmed mean could also be adopted.

Besides the Mahalanobis distance based split criterion, De’Ath (2002) \[[43](https://academic.oup.com/bib/article/24/2/bbad002/)\] proposed the distance-based multivariate regression tree (db-MRT), where the impurity of a given node is measured based on the pairwise dissimilarities between observations within the node. Sim *et al*. (2013) \[[46](https://academic.oup.com/bib/article/24/2/bbad002/)\] put this approach into a more formal construction where the dissimilarities between observations are captured by a distance matrix $D={Dij}1≤i,j≤N$ with $Dij$ measuring the distances between $yi$ and $yj$ ⁠. Then, the impurity of each node $t$ is defined as

This approach is more general than the aforementioned extensions in that the distance matrix does not necessarily depend on the dimension of the original responses. In fact, it is possible to analyze longitudinal responses at irregular time points with this approach as long as an appropriate distance measure can be defined. However, how to make prediction with the resulting RF needs further consideration because now within a leaf, it is possible to have responses with different dimensions thus, usual sample average would not make sense in such cases.

Lastly, when the distance is measured by $l1$ -norm, given the well-known relationship that this distance matrix based approach is connected to Segal’s approach with an assumed independence covariance structure.

#### Likelihood based impurity function

Zhang (1998) \[[47](https://academic.oup.com/bib/article/24/2/bbad002/)\] extended CART to multiple binary response variables. For responses from an exponential family distribution, the author considered the log-likelihood as the node impurity that depends only on the linear terms and the sum of the 2nd-order products of the responses. Specifically, for subject $i$ ⁠, $yi$ is assumed to follow the joint probability distribution: where $Ψ$ and $θ$ are arrays of parameters, $A(Ψ,θ)$ is the normalization function depending only on $Ψ$ and $θ$ ⁠, and $wi=∑j<kyijyik$ ⁠. The node impurity is defined as the maximum of the log-likelihood derived from this distribution; that is, for node t, where $Ψ^$ and $θ^$ are the maximum likelihood estimates of $Ψ$ and $θ$ within the node. Zhang and Ye (2008) \[[48](https://academic.oup.com/bib/article/24/2/bbad002/)\] applied the same technique to ordinal responses by first transforming them to binary-valued indicator functions.

When multivariate normally distributed responses are considered, Abdolell *et al*. (2002) \[[49](https://academic.oup.com/bib/article/24/2/bbad002/)\] proposed a likelihood-ratio test statistic as impurity function. Specifically, suppose that $yi∼Nn(μi,Σ)$ ⁠, the authors define the deviance function for a single observation as where $ℓ(μi;yi)$ is the log-likelihood function. Assuming that $Σ$ is constant and given for all $i$ ⁠, they further define the deviance within a node $t$ as where $μ^$ is the restricted maximum likelihood estimate within the node. The impurity of a node is then measured by the negation of the deviance. As pointed out by the authors, this deviance function in the context of the multivariate normal distribution is the Mahalanobis distance between $μi$ and $yi$ ⁠. In addition, they also noticed that deviance assessed via the multivariate analysis of variance approach such as Hotelling’s $T2$ is again in a form of the Mahalanobis distance. These observations connects the likelihood-ratio test statistics-based impurity function with the aforementioned Mahalanobis distance based one.

The likelihood-ratio test statistics based impurity function is also considered by Segal (1992) \[[42](https://academic.oup.com/bib/article/24/2/bbad002/)\] for multivariate normally distributed responses. However, their splitting rule focuses on the intrasubject variation structure other than the mean structure of responses, which we think may be difficult to interpret and less of interest in terms of precision medicine.

#### Prediction with multivariate RF extensions

While the RF extensions for univariate response longitudinal data predict the outcome at a single time point, the multivariate models predict the outcome at each of the predefined time points simultaneously.

## Implementation

In Table [3](https://academic.oup.com/bib/article/24/2/bbad002/), we provide a summary of the software implementations of the RF extensions reviewed in previous sections. Briefly, almost all extensions are presented in an R package on CRAN or as an R program. The majority of RF extensions provides variable importance measures that rely on standard importance measures of the underlying basic RF implementations. For instance, R package LongitudiRF uses randomForest \[[50](https://academic.oup.com/bib/article/24/2/bbad002/)\] for RF construction, which provides both permutation and Gini importance measures. RF++ and Historical RF only give permutation importance measure and in the R package MultivariateRandomForest, the variable importance is based on the frequency of the variable being used as a splitting variable.

Table 3

[Open in new tab](https://academic.oup.com/view-large/398982922)

Overview of the implementations of the reviewed RF extensions

| Name | Implementation | Type | Response | VImp | References |
| --- | --- | --- | --- | --- | --- |
| RF++ | Stand-alone software (binary) | F | C, R | Yes | \[[24](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
|  | ([https://sourceforge.net/projects/rfpp](https://sourceforge.net/projects/rfpp)) |  |  |  |  |
| Historical RF | R package htree (CRAN) | F | C, R | Yes | \[[30](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
| MERT | R package LongituRF (CRAN) | T | R | No | \[[31](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
| MERF | R package LongituRF (CRAN) | F | R | Yes | \[[28](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
| RE-EM | R package REEMtree (CRAN) | T | R | No | \[[19](https://academic.oup.com/bib/article/24/2/bbad002/), [51](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
| SMERT, SMERF | R package LongituRF (CRAN) | T, F | R | Yes | \[[33](https://academic.oup.com/bib/article/24/2/bbad002/), [52](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
| (S)REEMforest |  |  |  |  |  |
| GMERT | R code (supplement to original paper) | T | C | No | \[[36](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
| BiMM forest | R code (supplement to original paper) | F | C | Yes | \[[39](https://academic.oup.com/bib/article/24/2/bbad002/), [40](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
| Multivariate RF | R package MultivariateRandomForest (CRAN) | F | R | Yes | \[[44](https://academic.oup.com/bib/article/24/2/bbad002/), [53](https://academic.oup.com/bib/article/24/2/bbad002/), [54](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
|  | R package mvpart (CRAN) | T | R | No | \[[43](https://academic.oup.com/bib/article/24/2/bbad002/), [55](https://academic.oup.com/bib/article/24/2/bbad002/)\] |
|  | R package randomForestSRC (CRAN) | F | C, R | Yes | \[[44](https://academic.oup.com/bib/article/24/2/bbad002/), [56](https://academic.oup.com/bib/article/24/2/bbad002/)\] |

VImp = Variable importance, T = tree, F = forest, R = regression, C = classification

## Discussion

In this paper, we review extensions of the CART-based RF algorithm for the analysis of longitudinal data. An overview of the concepts and methods reviewed is shown in Figure [3](https://academic.oup.com/bib/article/24/2/bbad002/).

![Summary of the concepts and methods reviewed in the paper.](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/m_bbad002f3.jpeg?Expires=1766162541&Signature=4m8qwDHtpJfakk6p57S6KtxE5vGW8LuHbYFRrT4rk4dh0AZrGQEWKHIwMovJFJcKgTtyWFQAoW1j15LAfwc4Qaq7OLTs5KJ3z-OhTyFS36lajGef6CLTNdDo8NaJ2RfUtceqXus2rXiJSbRkFi-QVUtBnI7gJj0DE9ktzrgH~gLYACPgpWRYps2A4EyxfF2HneDKg76ccshVmRBNWfrLayfD5F2ga-q3bO7uHvprDzX5kYBjjM~nOAPaWiAQvoako3XT31vUFt5DMNeBByvi9YEfdayV1MFHBWIQ2Ygp2Wq54cfvKVP9HyExsPhaywC0so17CEfEEySjRMmVKOEgrw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 3

Summary of the concepts and methods reviewed in the paper.

[Open in new tab](https://academic.oup.com/view-large/figure/398982925/bbad002f3.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/24/2/10.1093_bib_bbad002/1/bbad002f3.jpeg?Expires=1766162541&Signature=4BkaHQCGxnNlwyV3XZbZ0igYD5Tw0uJjqG0w~xj~Bk0h5sHBw5Ja5SQh74J~0ajJA2NvQPN14DU7WL1~vmJ-pC62SB9bqWTuM7be4r4wqOnatcixAjOWqjsHObTCBpngRKXQBFiwK4sTPRcRgxPunKi~BLu-L~qTacY60U7RnyluSJ-wzn071t-Q8u~0t1n1p0oxnDrfRiFmHcL0Q3dXmb4dbTZzINYdfWAu-6Xv88tP9px9T6biB0KEfgz2ZlqqTgcDYwc7CzZnFnYFFX2oXr2rocM0nUS4iVvioxKpKXX6OhgduB5LxEBPZjaKzAk8cgQQe3hz2ScDHf2Fw56wRQ__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=398982925&ar=6991123&xsltPath=~/UI/app/XSLT&imagename=&siteId=5143)

There are certainly other RF construction approaches that can be considered. Examples include GUIDE \[[57](https://academic.oup.com/bib/article/24/2/bbad002/)\] and conditional inference \[[58](https://academic.oup.com/bib/article/24/2/bbad002/)\] approaches. For longitudinal data, extensions of non-CART-based tree and RF have also been proposed such as repeated measures random forest \[[59](https://academic.oup.com/bib/article/24/2/bbad002/)\], mixed effect machine learning framework \[[60](https://academic.oup.com/bib/article/24/2/bbad002/)\] and partially additive linear model trees \[[61](https://academic.oup.com/bib/article/24/2/bbad002/)\]. See \[[62](https://academic.oup.com/bib/article/24/2/bbad002/)\] for a review on different tree construction approaches and related discussions on extensions for longitudinal data analysis. Some extensions reviewed here such as MERT and MERF can easily switch to other approaches for tree/forest construction. In fact, the EM-based mixed effects approaches can also be adapted to be used with not only tree-based methods, but also other ML algorithms such as support vector machines or neural networks. However, one advantage of RF algorithm is that the prediction error will not increase when the number of trees in the forest increases, reflecting that it is not very prone to overfitting \[[10](https://academic.oup.com/bib/article/24/2/bbad002/)\]. But it is unknown whether such property holds as well for the reviewed extensions.

As we pointed out in Section , missing values represent a major challenge. Segal (1992) \[[42](https://academic.oup.com/bib/article/24/2/bbad002/)\] considered the surrogate splitting variable approach, which is one of the standard solutions for missing values in the literature of tree and forest methods. However, different missing mechanisms may require different approaches to handle missing values. In general, this is still an important research area in the context of developing and applying statistical methods and ML approaches in general.

Variable importance measure is a unique feature that RF can offer to support variable selection. Some reviewed extensions consider permutation-based variable importance, which is easy to implement but computationally expensive. Other approaches such as the variable-delete approach may also considered, but correlation between predictors may negatively affect its performance. How to measure variable importance in a tailored fashion for longitudinal data warrants further study, because this could be beneficial in both understanding disease progression and searching for target biomarkers for drug design. In addition, as pointed out by Speiser *et al*. (2019) \[[40](https://academic.oup.com/bib/article/24/2/bbad002/)\], it is also interesting to investigate within-cluster variable importance measures.

Another direction for future methodology development is on the effective handling of high dimensional longitudinal data. Except for the BiMM and REEMforest methods, the other reviewed methods have so far not been evaluated on high-dimensional data sets. For instance, for the extensions from GLMM with nonquantitative outcomes, there is a need for an initial GLM fit, which would be very difficult, if not impossible, with the high-dimensional data sets. Having RF extensions being able to handle such data would provide fruitful insights on their effects on complex diseases.

Lastly, while many of the mentioned studies compare the proposed modifications with standard RF or statistical approaches, only a few of them include comparisons between different RF extensions. One example is the simulation study performed by Capitaine *et al*. (2021) \[[33](https://academic.oup.com/bib/article/24/2/bbad002/)\], which demonstrates that MERT and RE-EM-based RFs have similar prediction performance. However, comprehensive neutral comparison studies \[[63](https://academic.oup.com/bib/article/24/2/bbad002/)\] for specific research questions and different types of longitudinal data with realistic simulation studies are needed to systematically investigate prediction performance, variable selection and computational efficiency. We plan to conduct such a benchmarking study to further understand these RF extensions and to give recommendations to practitioners analyzing real data sets.

Key Points

- Extensions of standard random forest algorithm for longitudinal data have been comprehensively reviewed.
- For clustered data where there is no time effect, subject-level bootstrap sampling technique is the key to take care of the clustering effect, and when the time effect is relevant, extensions from (generalized) linear mixed effects model and historical RF can be considered.
- Extensions to handle multivariate response are also available.
- Only a limited number of methods can analyze high-dimensional data such as omics data.
- Variable importance measure, a unique and essential feature of standard random forest for variable selection, warrants further development in the context of longitudinal data analysis.

## Author contributions statement

J.H. and S.S. wrote and reviewed the manuscript.

## Funding

This work was supported by the German Federal Ministry of Education and Research (BMBF) funded e:Med Programme on Systems Medicine \[grant 01ZX1510 (ComorbSysMed) to S.S.\].

## Author Biographies

**Jian chang Hu** is a postdoctoral research fellow at the Institute of Medical Biometry and Statistics, University of Lübeck, Lübeck, Germany. He received his Ph.D. degree in Statistics from the University of Wisconsin-Madison. His current research focuses on random forest extensions with applications to multi-omics data.

**Silke Szymczak** is professor of Genetic Epidemiology at the Institute of Medical Biometry and Statistics, University of Lübeck, Lübeck, Germany. Her research interests include the development and systematic evaluation of machine learning methods, with a particular focus on random forests in the context of omics data.

## References

1.

Ashley

EA

. .

Nat Rev Genet

2016

;

17

(

9

):

507

–

22

.

2.

Larry Jameson

J

,

Longo

DL

. .

Obstet Gynecol Surv

2015

;

70

(

10

):

612

–

4

.

3.

Matchett

KB

,

Niamh Lynam-Lennon

R

,

Watson

W

, et al. .

Cancer

2017

;

9

(

11

):

146

.

4.

Fitzmaurice

GM

,

Laird

NM

,

Ware

JH

.

Applied Longitudinal Analysis

.

John Wiley & Sons

, Hoboken, New Jersey,

2012

.

5.

Hedeker

D

,

Gibbons

RD

.

Longitudinal Data Analysis

.

Wiley-Interscience

, Hoboken, New Jersey,

2006

.

6.

Krasniqi

E

,

Schramm

W

,

Reichenbach

A

. .

GMS Medizinische Informatik, Biometrie und Epidemiologie

2021

;

17

(

1

)

ISSN

:

1860

–

9171

.

7.

Latourelle

JC

,

Beste

MT

,

Hadzi

TC

, et al. .

Lancet Neurol

2017

;

16

(

11

):

908

–

16

.

8.

Zhang

X

,

Chou

J

,

Liang

J

, et al. .

Sci Rep

2019

;

9

(

1

):

1

–

12

.

9.

König

IR

,

Fuchs

O

,

Hansen

G

, et al.

Eur Respir J

2017

;

50

(

4

).

10.

Breiman

L

. .

Mach Learn

2001

;

45

(

1

):

5

–

32

.

11.

Ishwaran

H

,

Kogalur

UB

,

Blackstone

EH

, et al. .

Ann Appl Stat

2008

;

2

(

3

):

841

–

60

.

12.

Chen

X

,

Ishwaran

H

. .

Genomics

2012

;

99

(

6

):

323

–

9

.

13.

Richard Cutler

D

,

Edwards

TC

,

Beard

KH

, et al. .

Ecology

2007

.

Preprint

;

88

(

11

):

2783

–

92

. [https://esajournals.onlinelibrary.wiley.com/doi/pdf/10.1890/07-0539.1](https://esajournals.onlinelibrary.wiley.com/doi/pdf/10.1890/07-0539.1).

14.

Mooney

SD

. .

Hum Genet

2015

;

134

(

5

):

459

–

65

.

15.

Ritchie

MD

. .

Hum Genet

2012

;

131

(

10

):

1615

–

26

.

16.

Svetnik

V

,

Liaw

A

,

Tong

C

, et al. . In:

International Workshop on Multiple Classifier Systems

.

Springer

\-Verlag, Berlin Heidelberg,

2004

,

334

–

43

.

17.

Raudenbush

SW

,

Bryk

AS

.

Hierarchical Linear Models: Applications and Data Analysis Methods

, Vol.

1

.

Sage

, Thousand Oaks, California,

2002

.

18.

Fokkema

M

,

Smits

N

,

Zeileis

A

, et al. .

Behav Res Methods

2018

;

50

(

5

):

2016

–

34

.

19.

Sela

RJ

,

Simonoff

JS

. .

Mach Learn

2012

;

86

(

2

):

169

–

207

.

20.

Mangino

AA

,

Holmes Finch

W

. .

Educ Psychol Meas

2021

;

81

(

6

):

1118

–

42

.

21.

Breiman

L

,

Friedman

J

,

Stone

CJ

, et al.

Classification and Regression Trees

.

CRC Press

, Boca Raton, FL,

1984

.

22.

Zhang

H

,

Singer

BH

.

Recursive Partitioning and Applications

.

Springer Science & Business Media

, New York,

2010

.

23.

Degenhardt

F

,

Seifert

S

,

Szymczak

S

. .

Brief Bioinform

2019

;

20

(

2

):

492

–

503

.

24.

Karpievitch

YV

,

Hill

EG

,

Leclerc

AP

, et al. .

PLoS One

2009

;

4

(

9

):e7087.

25.

Vlahou

A

,

Giannopoulos

A

,

Gregory

BW

, et al. .

Clin Chem

2004

;

50

(

8

):

1438

–

41

.

26.

Adler

W

,

Brenning

A

,

Potapov

S

, et al. .

Comput Stat Data Analysis

2011

;

55

(

5

):

1933

–

41

.

27.

Adler

W

,

Potapov

S

,

Lausen

B

. .

Comput Stat

2011

;

26

(

2

):

355

.

28.

Hajjem

A

,

Bellavance

F

,

Larocque

D

. .

J Stat Comput Simulation

2014

;

84

(

6

):

1313

–

28

.

29.

Sexton

J

,

Laake

P

.

Historical random forests

Working paper

,

2018

.

30.

Sexton

J

.

htree: historical tree ensembles for longitudinal data

.

R package version 2.0.0

,

2018

.

31.

Hajjem

A

,

Bellavance

F

,

Larocque

D

. .

Stat Probability Lett

2011

;

81

(

4

):

451

–

9

.

32.

Laird

NM

,

Ware

JH

. .

Biometrics

1982

;

963

–

74

.

33.

Capitaine

L

,

Genuer

R

,

Thiébaut

R

. .

Stat Methods Med Res

2021

;

30

(

1

):

166

–

84

PMID: 32772626

.

34.

Rodríguez

G

. . In:

Handbook of Multilevel Analysis

.

Springer

, New York,

2008

,

335

–

76

.

35.

McCullagh

P

,

Nelder

JA

.

Generalized Linear Models

. CRC Press, Boca Raton, FL,

2019

.

36.

Hajjem

A

,

Larocque

D

,

Bellavance

F

. .

Stat Probability Lett

2017

;

126

:

114

–

8

.

37.

Fontana

L

,

Masci

C

,

Ieva

F

, et al. .

MOX-Modelling and Scientific Computing, Department of Mathematics, Politecnico di Milano, via Bonardi

2018

;

9

:

1

–

17

.

38.

Pellagatti

M

,

Masci

C

,

Ieva

F

, et al. .

Data Sci J

2021

.

\_eprint:

;

14

(

3

):

241

–

57

. [https://onlinelibrary.wiley.com/doi/pdf/10.1002/sam.11505](https://onlinelibrary.wiley.com/doi/pdf/10.1002/sam.11505).

39.

Speiser

JL

,

Wolf

BJ

,

Chung

D

, et al. .

Commun Stat Simul Comput

2020

;

49

(

4

):

1004

–

23

.

40.

Speiser

JL

,

Wolf

BJ

,

Chung

D

, et al. .

Chemom Intel Lab Syst

2019

;

185

:

122

–

34

.

41.

Lin

S

,

Luo

W

. .

Multivar Behav Res

2019

;

54

(

4

):

578

–

92

.

42.

Segal

MR

. .

J Am Stat Assoc

1992

;

87

(

418

):

407

–

18

.

43.

Glenn De’ath.

.

Ecology

2002

;

83

(

4

):

1105

–

17

.

44.

Segal

M

,

Xiao

Y

. .

Wiley Interdisciplinary Rev

2011

;

1

(

1

):

80

–

7

.

45.

Larsen

DR

,

Speckman

PL

. .

Biometrics

2004

;

60

(

2

):

543

–

9

.

46.

Sim

A

,

Tsagkrasoulis

D

,

Montana

G

. .

Stat Appl Genet Mol Biol

2013

;

12

(

6

):

757

–

86

.

48.

Zhang

H

,

Ye

Y

. .

Statistics Interface

2008

;

1

(

1

):

169

.

49.

Abdolell

M

,

LeBlanc

M

,

Stephens

D

, et al. .

Stat Med

2002

;

21

(

22

):

3395

–

409

.

50.

Liaw

A

,

Wiener

M

. .

R News

2002

;

2

(

3

):

18

–

22

.

51.

Sela

JSR

,

Jing

W

.

REEMtree: regression trees with random effects for longitudinal (panel) data

.

R package version 0.90.4

,

2021

.

52.

Capitaine

L

.

LongituRF: random forests for longitudinal data

.

R package version 0.9

,

2020

.

53.

Rahman

R

.

MultivariateRandomForest: models multivariate cases using random forests

.

R package version 1.1.5

,

2017

.

54.

Rahman

R

,

Otridge

J

,

Pal

R

. .

Bioinformatics

2017

;

33

(

9

):

1407

–

10

.

55.

De’ath

G

.

mvpart: multivariate partitioning

.

R package version 1.6–2

,

2014

.

56.

Kogalur Hemant Ishwaran

UB

.

randomForestSRC: fast unified random forests for survival, regression, and classification (RF-SRC)

.

R package version 3.1.0

,

2022

.

57.

Loh

W-Y

. .

Statistica Sinica

2002

;

12

(

2

):

361

–

86

.

Institute of Statistical Science, Academia Sinica

.

58.

Hothorn

T

,

Hornik

K

,

Zeileis

A

. .

J Comput Graph Stat

2006

;

15

(

3

):

651

–

74

.

59.

Calhoun

P

,

Levine

RA

,

Fan

J

. .

Biometrics

2021

;

77

(

1

):

343

–

51

.

60.

Ngufor

C

,

Van Houten

H

,

Caffo

BS

, et al. .

J Biomed Inform

2019

;

89

:

56

–

67

.

61.

Seibold

H

,

Hothorn

T

,

Zeileis

A

. .

Adv Data Anal Classification

2019

;

13

(

3

):

703

–

25

.

62.

Loh

W-Y

. .

Int Stat Rev

2014

;

82

(

3

):

329

–

48

.

63.

Boulesteix

A-L

,

Lauer

S

,

Eugster

MJA

. .

PLoS One

2013

;

8

(

4

):e61562.