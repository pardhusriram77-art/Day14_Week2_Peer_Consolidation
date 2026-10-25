# Day 14 — Week-2 Consolidation Report

## 1. Work completed
- Audited the original water-potability dataset and documented missing values and the absence of timestamps.
- Generated synthetic timestamps to exercise temporal-quality checks, including missing timestamps, duplicate timestamps, and irregular intervals.
- Prepared an EDA/preprocessing review with distributions, feature correlations, IQR-based candidate-anomaly screening, chronological split summaries, and leakage checks.
- Prepared a feature-engineering workflow covering calendar features, lag features, rolling statistics based on prior rows, and exploratory cross-feature aggregates.
- Documented feature definitions, assumptions, and leakage risks.

## 2. Findings and limitations
- The original dataset is static tabular data, not genuine time-series sensor data.
- The temporal index is synthetic and can support software-pipeline testing only; it cannot demonstrate real underwater environmental trends.
- IQR flags are candidates for investigation, not confirmed sensor faults.
- Duplicate timestamp handling, split policy, and preprocessing decisions should be confirmed by the mentor before Dataset V1 is considered frozen.
- Rolling features use previous rows rather than fixed-duration windows, because timestamps are synthetic and irregular.
- Cross-feature mean and standard deviation combine variables with different units and are exploratory rather than physically interpretable.

## 3. Draft hypothesis to test
**H1:** A model using lag and rolling features may perform differently from a model using only raw sensor columns, but any apparent improvement on this dataset may be caused by the artificial timestamp ordering rather than genuine temporal signal.

### Proposed comparison
Compare a baseline using raw sensor features against a model using raw plus engineered features, using the same chronological split and training-only preprocessing. Report the selected metric and uncertainty/limitations. Do not describe the result as validated real-world forecasting.

## 4. Peer consolidation
Record one real peer insight after the discussion. Compare the observation or hypothesis, not code. The peer insight log is provided as a template; it must be completed with what the peer actually said.

## 5. Decisions needed from mentor
- Confirm the missing- and duplicate-timestamp policies.
- Confirm the chronological split and training-only imputation/scaling approach.
- Confirm whether engineered features should be retained for the next experiment.
- Clarify whether a genuine timestamped environmental dataset can be supplied for meaningful temporal analysis.

## 6. Next steps
1. Add the actual peer insight and discussion date to the log.
2. Apply mentor corrections and rerun quality/leakage checks.
3. Compare raw vs engineered features without changing the evaluation split between experiments.
4. Keep synthetic-timestamp limitations explicit in reports and presentations.
5. Freeze Dataset V1 only after mentor approval.
