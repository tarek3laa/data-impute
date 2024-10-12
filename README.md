# Experiment Documentation

## System Specifications
- Machine Type: Google Cloud VM
- OS: Ubuntu 22
- Processor: 24 threads

## Experiment Details
- The purpose of this experiment is to evaluate different imputation techniques for motion data. Missing data is common in motion data and can negatively affect the accuracy of analysis results. The hypothesis is that using advanced imputation techniques can improve the accuracy of analysis results by filling in missing data with plausible values.

## Methodology
- 1. Load the motion data into the system.
- 2. Generate missing data points using (random points, transition points, intervals)
- 3. Apply the following imputation techniques 
  - gain (Missing Data Imputation using Generative Adversarial Nets)
  - bsi (Missing Data Imputation using Optimal Transport)
  - simplefill_mean
  - simplefill_median 
  - simplefill_random
  - knn 
  - soft_imputer
  - iterative_imputer
  - iterative_SVD 
- 4. Evaluate the performance of each imputation technique by comparing the imputed data with the original data using MAE and STD

## Additional Resources
 - 1. GAN
    - Authors: {Jinsung Yoon, James Jordon, Mihaela van der Schaar}
    - Paper Link: [Missing Data Imputation using Generative Adversarial Nets](http://proceedings.mlr.press/v80/yoon18a/yoon18a.pdf)
 - 2. OT Imputer 
    - Authors: {Muzellec, Boris and Josse, Julie and Boyer, Claire and Cuturi, Marco}
    - Paper Link: [Missing Data Imputation using Optimal Transport](https://arxiv.org/abs/2002.03860)  
 - 3. fancyimpute: An Imputation Library
    - author = {Alex Rubinsteyn and Sergey Feldman},
    - url = {https://github.com/iskandr/fancyimpute},


Experiment Documentation
System Specifications

    Machine Type: Google Cloud VM
    OS: Ubuntu 22
    Processor: 24 threads

Experiment Details

The objective of this experiment is to evaluate various imputation techniques for motion data. Missing data is often encountered in motion datasets, which can degrade the performance of subsequent analysis tasks. The hypothesis of this experiment is that applying advanced imputation techniques can yield more accurate analysis by imputing missing values with plausible alternatives.
Methodology

    Load the Motion Data: Start by loading the motion data into the system.
    Generate Missing Data:
        Missing data is artificially introduced by the following methods:
            Random Points: Missing values are generated randomly across the dataset.
            Transition Points: Missing values are introduced at transition points where rapid changes occur in the data.
            Intervals: Missing values are generated based on predefined intervals.
    Imputation Techniques:
        The following imputation methods are applied to the data:
            GAIN: Missing Data Imputation using Generative Adversarial Nets.
            BSI: Missing Data Imputation using Optimal Transport.
            SimpleFill (Mean, Median, Random).
            KNN Imputation.
            Soft Imputer.
            Iterative Imputer.
            Iterative SVD.
    Evaluation:
        The performance of each imputation technique is evaluated by comparing the imputed data with the original dataset.
        Metrics:
            Mean Absolute Error (MAE): Measures the average magnitude of errors between imputed and actual values.
            Standard Deviation (STD): Measures the variability of the imputed data in comparison to the original.

Additional Resources

    GAIN:
        Authors: Jinsung Yoon, James Jordon, Mihaela van der Schaar
        Paper: Missing Data Imputation using Generative Adversarial Nets
    BSI (Optimal Transport Imputer):
        Authors: Muzellec, Boris; Josse, Julie; Boyer, Claire; Cuturi, Marco
        Paper: Missing Data Imputation using Optimal Transport
    FancyImpute Library:
        Authors: Alex Rubinsteyn, Sergey Feldman
        GitHub: FancyImpute GitHub Repository

## How to Run the Experiment

You can use the following command to run the experiment, replacing the arguments as needed:

``` bash

python impute_firstexp.py \
    --missing <missing_count> \
    --type <data_generation_type> \
    --path <skill_name> \
    --impute_type <imputation_method> \
    --n_players <number_of_players> \
    --n_angles <number_of_angles> \
    --n_rows <number_of_rows> \
    --n_threads <number_of_threads>
```
### Argument Explanation:
* --missing: The number of missing data points to generate.
* --type: Type of missing data generation method. Accepts the following:
  + 1: Randomly generate missing data.
  + 2: Generate missing data based on transition points.
  + List: A list format to specify [total_ratio, number_of_intervals] for generating missing data over intervals.
* --path: Path to the data file or directory.
* --impute_type: The imputation method to use, based on the following options:
  + 1: Single variable imputer.
  + 2: Multivariable imputer across all players.
  + 3: Multivariable imputer across all angles.
* --n_players: Number of players in the dataset.
* --n_angles: Number of angles to consider for the motion data.
* --n_rows: Number of rows in the dataset.
* --n_threads: Number of threads to use for parallel processing.
