# Golden State Warriors: Ticket-Timing Prediction & Fan Segmentation

Machine learning models that predict how far in advance a fan buys a ticket and classify fans by purchase timing. Built to beat the team's existing linear regression and decision tree models, and paired with revenue analysis to guide marketing.

*Texas A&M University, DAEN 400, Case Study 2, Fall 2025. Individual project.*

## Problem
The Warriors' business analytics team built a "Ticket Timing Model" to replace mass emails about unsold tickets. Market research identified three fan types: **Planners** (buy more than 2 weeks ahead), **In-Between**, and **Last-Minute** buyers. Objectives:
1. Predict the number of days before a game a fan will buy a ticket (regression).
2. Classify each fan's purchase type (classification).

## Data
Fan-level ticket data: age, fan mailing list membership, number of tickets, seat location (deck), ticket price, and concession spend. *Case data was provided for coursework and is not included in this repo.*

## Approach
- Reproduced the team's baselines: simple and multiple linear regression, plus their decision tree classifier.
- **Random Forest Regressor** in a scikit-learn `Pipeline` with `ColumnTransformer` encoding, for days-before-game.
- **Gradient Boosting Classifier** for fan type.
- Revenue segmentation by fan type, seating deck, and mailing-list status.

## Results
**Regression (days before game)**
- Random Forest: **MAE 3.88 days, R² 0.67** on the test set.
- On the team's five sample fans, average error was about 2.2 days, vs. 3.8 days (their multiple regression) and 8.4 days (simple regression).

**Classification (fan type), 200 test fans, 81% accuracy**
| Fan Type | Precision | Recall | F1 |
|---|---|---|---|
| Last-Minute | 0.93 | 0.88 | 0.90 |
| In-Between | 0.71 | 0.74 | 0.72 |
| Planner | 0.81 | 0.82 | 0.81 |

**Business insights**
- Planners generated about $403K in ticket revenue vs. $147K for Last-Minute buyers. A 10% increase in Planners is worth **$40K+** in added revenue.
- 75% of Planners sit in the lower deck (vs. 20% of Last-Minute buyers), and lower-deck fans bring in about $590 more each.
- Mailing-list fans spend about $1,076 on average vs. $778 for non-members.

## Recommendations
Target Planner-type fans (who skew older) through the mailing list and Facebook campaigns, add game date and other fields to data collection, and retrain the models after the move from Oracle Arena to Chase Center.

## Tech Stack
Python, pandas, NumPy, scikit-learn, matplotlib, seaborn, Jupyter

## Repository Contents
- `notebooks/warriors_ticket_timing.ipynb`: baselines, models, evaluation, and figures
- `reports/Warriors_Ticket_Timing_Report.pdf`: technical report
- `reports/Warriors_Ticket_Timing_Presentation.pdf`: slide deck
