# 17-The-determinants-of-cyberattack-costs-An-event-study

## Goal
This study aims to compute the impact of different types of cyber attacks on firms' stock prices.

------

## Abstract
Along with the increasing frequency and severity of cyber incidents, understanding their economic implications is paramount. In this context, listed firms' reactions to cyber incidents are compelling to study since they (i) are a good proxy to estimate the costs borne by other organizations, (ii) have a critical position in the economy, and (iii) have their financial information publicly available. We extract listed firms' cyber incident dates and characteristics from newswire headlines. We use an event study over 2012--2022, using a three-day window around events and standard benchmarks. We find that the magnitude of abnormal returns around cyber incidents is on par with previous studies using newswire or alternative data to identify cyber incidents. Conversely, as we adjust the standard errors accounting for event-induced variance and residual cross-correlation, we find that the previously claimed significance of abnormal returns vanishes. Given these results, we run a horse race of specifications, in which we test for the marginal effects of type of cyber incidents, target firm sector, periods, and their interactions. Data breaches are the most detrimental incident type with an average loss of -1.3\% or (USD -1.9 billion) over the last decade. The health sector is the most sensitive to cyber incidents, with an average loss of -5.21\% (or USD -1.2 billion), and even more so when these are data breaches. Instead, we cannot show any time-varying effect of cyber incidents or a specific effect of the type of news as had previously been advocated.

------

## Documents
For more information please refer to the manuscript associated with this repository.

------

## Code

The code is a mix of notebooks and a `py` file:
- the **py file** contains the functions needed in the notebooks;
- the **notebooks** explain all the steps of the analysis.

Stock market data are obtained from [WRDS](https://wrds-www.wharton.upenn.edu/).

------

## Data description and sample construction

This repository contains all data and code required to replicate the empirical analysis in the paper.

### Datasets

The repository includes two main datasets:

1. **refinitiv_data.csv**  
   This file contains the full universe of 270 validated cyber-incident headlines identified through an
   NLP-based filtering procedure applied to Refinitiv news data, followed by manual verification.
   Each row corresponds to a validated cyber incident and includes firm identifiers (CUSIP, ticker, RIC),
   event dates, sector classifications, incident-type indicators, news sources, and headline text.
   This dataset represents the complete set of cyber incidents identified in the study.

2. **event_df.csv**  
   This file contains the final dataset used in the event-study analysis.
   It includes the subset of cyber incidents affecting publicly listed firms that satisfy all
   data-availability and sample-selection criteria, including availability of stock return data,
   market capitalization thresholds, and valid event windows.

### Mapping between datasets

An event is considered to be used in the event-study analysis if and only if it appears in `event_df.csv`.
The mapping between the full incident universe and the final empirical sample can be reconstructed
by matching events across the two datasets using firm identifiers (e.g., CUSIP) and event dates.

All empirical results reported in the paper are based exclusively on the events contained in `event_df.csv`.

------

## Files description

Short description of the files:

| File name | Short Description |
| --------- | ---------------- |
| function_definitions.py | Defines all the functions used in the other files |
| event_study_prc.py | Processes and analyzes the cyber breach dataset from the Privacy Rights Clearinghouse |
| event_study_refinitiv.py | Merges the Refinitiv news data with stock market information |
| event_study_CAR_OLS.py | Estimates CARs with OLS and the associated test statistics |
| event_study_CAR_SURE.py | Estimates CARs with SURE and the associated test statistics |
| event_study_analysis.py | Runs regressions of CARs on firm and breach characteristics and computes descriptive statistics |

Each file contains additional details and comments explaining the individual steps.

------

## Replication note

Due to licensing restrictions on WRDS data, users will need appropriate access credentials to fully
reproduce the return-based calculations.
