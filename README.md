🚦 Distributed Machine Learning for Road Collision Severity Prediction
1. Project Summary

This project develops a scalable distributed machine learning pipeline to predict road collision severity using large-scale UK road safety data.

Built with Apache Spark (PySpark MLlib), the system processes multi-decade national traffic records and evaluates multiple regression models in a distributed environment.

The solution demonstrates how big data engineering and distributed analytics can support:

Data-driven road safety policy

Emergency response optimization

Infrastructure risk assessment

National-scale transportation analytics

2. Problem Statement

Road traffic collisions create significant social and economic impact. However, traditional statistical approaches face limitations when applied to large national datasets:

Inability to efficiently process large-scale historical data

Poor modeling of nonlinear feature interactions

Limited scalability in centralized environments

This project addresses these issues by designing a distributed machine learning architecture capable of scalable and accurate severity prediction.

3. Research Objectives

Identify the model with the highest predictive accuracy.

Evaluate computational efficiency of distributed training.

Analyse scalability trade-offs (strong vs weak scaling).

Investigate nonlinear patterns affecting collision severity.

Assess performance vs infrastructure cost trade-offs.

4. Dataset Description

Source: UK Department for Transport – Road Safety Data
Coverage: 1979 – Latest available year
Original Format: CSV
Optimized Format: Partitioned Parquet

4.1 Dataset Characteristics

Multi-decade national collision records

Millions of structured observations

Numerical and categorical variables

Year-wise partitioned storage

4.2 Key Features

Collision year

Severity (Target Variable)

Number of vehicles involved

Number of casualties

Speed limit

Weather conditions

Light conditions

Road type

Urban / Rural classification

5. Data Engineering Pipeline

To ensure scalability and performance, the following optimizations were implemented:

5.1 Data Validation & Cleaning

Explicit schema enforcement

Type casting and validation

Missing value handling

Null filtering

5.2 Storage Optimization

Conversion from CSV → Parquet

Columnar compression

Year-based partitioning

5.3 Performance Optimization

Kryo serialization

Optimized shuffle partitions

Memory configuration tuning

Catalyst optimizer

Tungsten execution engine

These improvements significantly reduced I/O overhead and improved distributed processing efficiency.

6. System Architecture

6.1 High-Level Pipeline
Raw CSV Data
      ↓
Spark Data Ingestion
      ↓
Data Cleaning & Validation
      ↓
Feature Engineering
      ↓
Vector Assembler
      ↓
Distributed Model Training
      ↓
Cross-Validation
      ↓
Evaluation (RMSE)
      ↓
Tableau Visualization

6.2 Machine Learning Workflow

Data ingestion using Spark DataFrame API

Feature preprocessing & encoding

Feature vector assembly

Distributed model training

k-fold cross-validation

RMSE evaluation

Feature importance extraction

Dashboard visualization

7. Models Implemented

Four regression models were evaluated using Spark MLlib:

7.1 Linear Regression

Baseline model

Assumes linear relationships

Fastest training

7.2 Decision Tree Regressor

Captures nonlinear splits

Interpretable structure

7.3 Random Forest Regressor ⭐

Ensemble of decision trees

Reduces overfitting

Best overall accuracy

7.4 Gradient Boosted Trees

Sequential boosting approach

Improved bias reduction

Higher computational cost

8. Model Performance

Primary Metric: Root Mean Squared Error (RMSE)

Model	RMSE	Training Time
Linear Regression	0.4388	15.10 s
Decision Tree	0.4355	17.45 s
Random Forest	0.4323	98.79 s
Gradient Boosted Trees	0.4329	63.87 s
🏆 Best Model: Random Forest Regressor

Random Forest achieved the lowest RMSE, demonstrating superior handling of nonlinear relationships.

9. Scalability Analysis
9.1 Strong Scaling

Fixed dataset size

Increased cluster resources

Diminishing returns due to shuffle overhead

9.2 Weak Scaling

Dataset size increased with cluster size

Acceptable performance scaling observed

9.3 Bottleneck Identified

Shuffle operations remain the primary performance constraint in distributed Spark ML workflows.

10. Tableau Dashboards

🔹 Dashboard 1 – Data Quality & Pipeline Monitoring

Missing value analysis

Annual collision trends

Partition balance

Ingestion health monitoring

🔗 https://prod-in-a.online.tableau.com/t/ashsish2345-3816dbd389/authoring/ashish/Dashboard1

🔹 Dashboard 2 – Model Performance & Feature Importance

RMSE comparison

Training time comparison

Random Forest feature importance

Interactive model exploration

🔗 https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/seconddashboard/Dashboard1

🔹 Dashboard 3 – Business Insights & Recommendations

Urban collision hotspots

Peak risk hours

Weather-based risk analysis

Policy recommendations

🔗 https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/thirddashboard_17719403723090/Dashboard1

🔹 Dashboard 4 – Scalability & Cost Analysis

Strong vs weak scaling

Training cost comparison

Spark efficiency metrics

Infrastructure trade-offs

🔗 https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/dashboardfour/Dashboard1

11. Technologies Used

Apache Spark

PySpark

Spark MLlib

Parquet

Tableau

Python

Distributed Computing

12. Key Findings

Ensemble models outperform linear models

Random Forest achieved the best predictive accuracy

Collision severity exhibits strong nonlinear patterns

Distributed Spark processing successfully scales to large datasets

Shuffle operations limit full scalability

13. Future Work

Hyperparameter optimization

Geospatial feature integration

Real-time streaming prediction (Spark Structured Streaming)

Deep learning model comparison

REST API deployment for real-time inference

14. Conclusion

This project demonstrates how distributed machine learning frameworks can effectively process and model national-scale traffic data.

By combining optimized data engineering techniques with ensemble learning models, the system achieves:

High predictive accuracy

Scalable distributed processing

Practical policy insights

The results highlight the importance of distributed analytics in modern transportation safety research.
