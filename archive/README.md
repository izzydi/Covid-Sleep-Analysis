# Legacy exploration

`legacy_exploration.Rmd` preserves the original experimental coursework.

The audited source is [`../covid_sleep_analysis.Rmd`](../covid_sleep_analysis.Rmd). The legacy workflow fitted KNN imputation separately on the test set, made some filtering/outlier decisions before the train/test split, and used an `mtry` value as a row index when extracting tuned Ranger parameters. It also took the square root of Ranger's classification error and labelled the result RMSE.

Those issues are intentionally removed from the current baseline. More advanced class-imbalance or outlier techniques should only be reintroduced inside training resamples.
