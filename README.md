# NBA Shooting Patterns and Defensive Performance Analysis

## Overview

This project investigates shooting patterns and defensive performance in NBA games during the 2014-2015 season. By analyzing shot logs, we aim to understand key aspects such as shooting efficiency, defensive impact, and the prevalence of outliers. Our analysis provides insights that could aid coaches and team management in strategic decision-making.

## Key Questions

1. **Shooting Efficiency**: 
    - How efficient were players in making their shots?
    - Were there trends based on shot distance, shot clock, or defender proximity?

2. **Defensive Impact**: 
    - What was the effect of the closest defender on shooting percentages?
    - What insights can be derived from defensive strategies employed by teams and players?

3. **Outlier Detection**: 
    - How prevalent were outliers and how did they affect the analysis?
    - How should outliers be addressed to ensure data integrity?

## Project Pipeline

### Data Loading

- Read data from `shot_logs.csv` into a pandas DataFrame.

### Data Preprocessing

- Handle null values using forward filling.
- Replace negative values in the `TOUCH_TIME` column with the mean of positive values.
- Remove unnecessary columns (e.g., `FGM` which duplicates `SHOT_RESULT`).
- Perform label encoding on categorical columns.
- Convert `GAME_CLOCK` to seconds.
- Optionally handle outliers by calculating and removing values outside the lower and upper bounds.

### Data Visualization

- Generate correlation heatmaps and correlation circle plots to explore relationships between features.
- Detect and visualize outliers using box plots.

### Prediction Models

- Split data into 75% training and 25% evaluation sets.
- Train and evaluate four different models: Logistic Regression, Random Forest, K-Nearest Neighbors (KNN), and Gradient Boosting.

### Map-Reduce Operations

- Implement two Map-Reduce tasks using PySpark:
  1. Identify the most scoring players in the last 30 seconds of the last quarter.
  2. Identify top shot players who scored 3 points with 0 dribbles.

## Analysis and Solutions

### Data Preprocessing

- **Handling Null Values**: Fill null values with forward filling.
- **Handling Negative Touch Time**: Replace negative values with the mean of positive values.
- **Removing Unnecessary Columns**: Drop the `FGM` column.
- **Label Encoding**: Encode the `W` column as binary (1 for W, 0 for L).
- **Time Conversion**: Convert `GAME_CLOCK` to seconds.
- **Outlier Handling**: Remove outliers based on calculated bounds.

### Visualization Insights

#### Correlation Heatmap

The heatmap uses color to represent the strength of correlations between features. Darker colors indicate weaker correlations.

#### Interesting Insight

Shots made from over 23.9 yards count as 3 points. If fouled and scored, players earn an extra free throw. This explains why about 8% of shots from less than 23.9 yards are recorded as 3 points.

#### Correlation Circle Plot

The plot visually represents relationships between features. Closer points indicate stronger correlations. The plot helps understand the interplay between different features.

### Outlier Detection

Visualize outliers using box plots to identify and handle anomalies in the data.

### Model Training

#### Logistic Regression

Train a logistic regression model and evaluate its performance.

#### Random Forest

Train a random forest model and evaluate its performance.

#### K-Nearest Neighbors (KNN)

Train a KNN model and evaluate its performance.

#### Gradient Boosting

Train a gradient boosting model and evaluate its performance.

### Map-Reduce

#### Task 1: Scoring in the Last 30 Seconds

Use PySpark to implement a Map-Reduce function to identify the top scoring players in the last 30 seconds of the last quarter.

#### Task 2: Top 3-Point Scorers with 0 Dribbles

Use PySpark to implement a Map-Reduce function to identify top players who scored 3 points with 0 dribbles.
