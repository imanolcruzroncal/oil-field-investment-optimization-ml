# Oil Field Investment Optimization Using Machine Learning

Machine learning model to optimize $100M oil well investment using linear regression and bootstrap risk simulation.

## Project Overview

This project evaluates capital allocation decisions under uncertainty for oil field development. The objective is to determine which of three regions should receive a $100M investment to develop 200 new oil wells.

Rather than focusing solely on production predictions, this analysis integrates:

Predictive modeling

Financial evaluation

Risk simulation

Confidence interval estimation

The final decision is based on risk-adjusted return, not just expected profit.

## Business Objective

OilyGiant must:

Invest $100,000,000

Develop exactly 200 wells

Select wells from 3 available regions

Ensure the probability of financial loss is below 2.5%

Each well must generate at least 111.1 thousand barrels (break-even threshold) to avoid losses.

Revenue:

$4.5 per barrel

Production expressed in thousands of barrels

Goal:
Select the region with the highest expected profit while maintaining acceptable risk.

## Data Description

Each region contains 100,000 wells with the following features:

f0, f1, f2: geological characteristics

product: reserve volume (thousands of barrels)

Data preparation included:

Duplicate verification

Removal of non-informative ID column

Validation of numeric data types

75/25 train-validation split with fixed random state for reproducibility

## Methodology
### 1. Predictive Modeling

Model: Linear Regression

Train/Validation Split: 75/25

Evaluation Metric: RMSE

Baseline comparison using mean prediction

### 2. Well Selection Strategy

For each region:

Predict production on validation set

Select top 200 wells with highest predicted reserves

Estimate total projected revenue

### 3. Financial Modeling

Profit formula:

Profit = (Total Production × $4.5) − $100,000,000

Break-even threshold:
111.1 thousand barrels per well

### 4. Risk Simulation (Bootstrapping)

To evaluate uncertainty:

1000 bootstrap resamples

Randomly select 500 wells

Choose top 200 predicted wells

Compute profit distribution

Calculate:

Mean profit

95% confidence interval

Probability of loss

## Model Performance

RMSE by Region:

Region 0: ~37.6

Region 1: ~0.89

Region 2: ~40.0

Region 1 demonstrated significantly lower prediction error, indicating a more stable linear relationship between features and production.

## Financial Results

Expected Profit (Millions USD Approximation):

Region 0: ~3.96M

Region 1: ~4.61M

Region 2: ~3.93M

95% Confidence Interval:

Region 1 showed the narrowest interval

Regions 0 and 2 had wider variability

Probability of Loss:

Region 0: ~2.3%

Region 1: ~0.23%

Region 2: ~2.16%

## Final Recommendation

Region 1 is selected for development because:

Highest expected profit

Lowest RMSE

Narrowest confidence interval

Lowest probability of financial loss (well below 2.5%)

Although Region 0 initially appeared attractive due to higher raw production values, risk-adjusted evaluation revealed Region 1 as the optimal choice.

This demonstrates the importance of uncertainty modeling in capital investment decisions.

## Tech Stack

Python

Pandas

NumPy

Scikit-Learn

Bootstrapping Simulation

## What This Project Demonstrates

Capital allocation under uncertainty

Predictive modeling with constrained algorithms

Risk-adjusted decision-making

Bootstrapping for financial simulation

Business-oriented data science
