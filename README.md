# 365-Bayesian-Analysis-Final-Project

1. Project Overview

   The goal of this project is to apply Bayesian statistical methods to a wine quality dataset. The analysis is divided into two primary sections:

   Bayesian Estimation: Estimating proportions (discrete) and means (continuous) using conjugate priors and MCMC sampling.

   Bayesian Regression: Building and validating models to predict wine quality based on chemical properties.

2. Dependencies

   The analysis is performed in R using the following libraries:

     rstan & rstanarm: For MCMC estimation and Bayesian regression.

     tidybayes & bayesplot: For visualizing posterior distributions and diagnostics.

     bayesrules & loo: For model validation and cross-validation.

     tidyverse & dplyr: For data manipulation and plotting.

3. Key Analysis Sections
  
     1.1 Discrete Parameter Estimation (Wine Quality)

       Objective: Estimate theta, the proportion of "High Quality" wines (quality >= 7)
   
       Methodology:
   
        Prior: Non-informative Beta(1, 1) (Uniform).
   
        Likelihood: Binomial.
   
        Comparison: Validated MCMC results against the closed-form theoretical Beta posterior.

       Result: The MCMC estimation showed excellent convergence (R-hat = 1.00) and aligned perfectly with theoretical expectations.

     1.2 Continuous Parameter Estimation (Alcohol Content)

       Objective: Estimate $\mu$, the mean alcohol percentage.
   
       Methodology:

        Prior: Weakly informative Normal distribution (N(10, 2^2)).
   
        Likelihood: Normal (with known sigma based on sample SD).
   
        Diagnostics: Trace plots and autocorrelation plots confirmed well-mixed chains and high sampling efficiency.

     2. Bayesian Regression Models
     
       The project evaluates the relationship between wine quality (the response variable) and various chemical predictors.

       Full Model: Includes all available predictors in the dataset.

       Reduced Model: Focuses on the most significant predictors identified by the posterior intervals:
      
          Volatile
        
          Acidity
      
          Chlorides
      
          Sulphates
      
          Alcohol

       Model Comparison:

        Used LOO (Leave-One-Out Cross-Validation) to compare predictive power.

        Determined that the Reduced Model is preferable due to its simplicity and comparable predictive performance (the difference in ELPD was within 2 standard errors).

        Performance: Both models achieved a Mean Absolute Error (MAE) of approximately 0.4, indicating high accuracy in predicting the discrete quality scale.

4. Key Findings & Diagnostics
     
    Convergence: All models reached convergence with R-hat values of 1.00.

    Predictive Coverage: 95% Posterior Predictive Intervals (PPIs) captured the actual data effectively.

    Insights: Lower volatile acidity and higher alcohol/sulphate content are the strongest indicators of higher wine quality in this dataset.

5. How to Run
     
    Ensure WineQT.csv is in the working directory.

    Install the required packages listed in the setup chunk.

    Knit the .Rmd file to generate the HTML or Word report.
