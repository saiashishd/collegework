Distributed Machine Learning for Road Collision Severity Prediction
Project Overview
This project develops a scalable distributed machine learning pipeline to predict road collision severity using large-scale UK road safety data. The system leverages PySpark MLlib and big data engineering techniques to efficiently process multi-decade traffic records.
The solution demonstrates how distributed analytics can support data-driven road safety policy and emergency planning by accurately modelling collision severity patterns.
Problem Statement
Road traffic accidents create significant social and economic impacts. Traditional statistical methods struggle with:
● Large-scale traffic datasets
● Complex nonlinear relationships
● Scalability limitations
This project addresses these gaps by building a distributed ML pipeline capable of handling big traffic data efficiently.
Research Objectives
● Identify which ML model achieves the best predictive accuracy
● Evaluate the impact of distributed training on computational efficiency
● Analyse scalability trade-offs in large-scale traffic data processing
Dataset
● Source: UK Department for Transport road safety data
● Coverage: 1979 – latest available year
● Format: CSV → converted to partitioned Parquet
● Key Features:
○ Collision year
○ Severity
○ Number of vehicles
○ Number of casualties
○ Speed limit
○ Weather/environment conditions
Data Engineering Steps
● Schema validation
● Missing value handling
● Year-based partitioning
● Parquet columnar storage
● Feature vector assembly
System Architecture
Big Data Engineering
● PySpark DataFrame API
● Partitioned Parquet storage
● Kryo serialization
● Optimized shuffle partitions
● Catalyst & Tungsten optimization
Machine Learning Pipeline
1. Data ingestion
2. Preprocessing
3. Feature engineering
4. Model training
5. Cross-validation
6. Evaluation
7. Visualization in Tableau
Models Implemented
Four regression models were evaluated using PySpark MLlib:
● Linear Regression
● Decision Tree Regressor
● Random Forest Regressor
● Gradient Boosted Trees
Performance Metric
Primary Metric: Root Mean Squared Error (RMSE)
Model
RMSE
Training Time
Linear Regression
0.4388
15.10 s
Decision Tree
0.4355
17.45 s
Random Forest
0.4323
98.79 s
Gradient Boosted Trees
0.4329
63.87 s
Best Model: Random Forest Regressor
Key Findings
● Ensemble models outperform linear models
● Random Forest achieved the lowest RMSE
● Collision severity shows strong nonlinear relationships
● Distributed Spark processing successfully handled large datasets
● Shuffle overhead remains a scalability bottleneck
Tableau Dashboards
🔹 Dashboard 1: Data Quality & Pipeline Monitoring
● Missing value analysis
● Annual collision trends
● Partition balance
● Ingestion health monitoring
Link:
https://prod-in-a.online.tableau.com/t/ashsish2345-3816dbd389/authoring/ashish/Dashboard1
🔹 Dashboard 2: Model Performance & Feature Importance
● RMSE comparison
● Training time comparison
● Random Forest feature importance
● Interactive model exploration
Link:
https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/seconddashboard/Dashboard1
🔹 Dashboard 3: Business Insights & Recommendations
● Urban collision hotspots
● Peak time risk analysis
● Weather impact
● Policy recommendations
Link:
https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/thirddashboard_17719403723090/Dashboard1?:iid=1
Dashboard 4: Scalability & Cost Analysis
● Strong vs weak scaling
● Training cost comparison
● Spark efficiency analysis
● Infrastructure trade-offs
Link:
https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/dashboardfour/Dashboard1
 
