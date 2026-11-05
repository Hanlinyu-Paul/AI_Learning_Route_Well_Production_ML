# Leakage traps in well data

## 1. Target leakage: gauge-derived features
- **Feature:** gauge-derived features (e.g., AVG_DP_TUBING);PI or drawdown calculated from gauge pressure
Rates allocated with a model calibrated on BHP
Centered rolling averages that use future values
- **Why it leaks:** because the AVG_DP_TUBING is determined directly from the BHP
- **How to detect:** nearly-1 correlation with the target
- **Fix:** Drop the feature

## 2. Train-test contamination: random splits across time
- **Split:** The same well appears in both train and test, so the model learns the well rather than the physics.
Scalers or imputers are fitted on the full dataset before the split.
- **Why it leaks:** Daily well data is strongly autocorrelated. A shuffled K-fold puts day t in training and day t+1 in validation. The model then just interpolates between neighboring days, and the CV score is inflated. Two related versions:
- **How to detect:** big gap between random-cv and grouped-cv error
- **Fix:** split forward in time (TimeSeriesSplit) and/or hold out whole wells (GroupKFold)