# **Distributed Machine Learning for Large-Scale Road Collision Severity Prediction**

---

## **Project Overview**

* Implements a fully distributed machine learning pipeline using Apache Spark.
* Predicts road collision severity using UK traffic collision data.
* Evaluates multiple regression models within a distributed computing architecture.
* Analyzes scalability, computational efficiency, and performance trade-offs.
* Demonstrates the effectiveness of ensemble models for structured big data applications.

---

## **Technologies Used**

* Apache Spark (Distributed Processing Engine)
* PySpark MLlib (Machine Learning Library)
* Parquet (Columnar Storage Format)
* Pandas & Matplotlib (Visualization)
* Scikit-learn (Single-node ML comparison)
* Tableau (Interactive Dashboards)

---

## **Dataset Description**

* Source: UK Department for Transport – Road Collision Statistics
* Multi-decade structured national collision records
* Features include:

  * Collision year
  * Severity
  * Number of vehicles involved
  * Number of casualties
  * Speed limit
  * Weather conditions
  * Road surface conditions
  * Lighting conditions
  * Time of collision
* Large temporal coverage suitable for distributed big data processing

---

## **Distributed Architecture & Configuration**

* 4 Executors
* 4 Cores per Executor
* 6GB Executor Memory
* 4GB Driver Memory
* 400 Shuffle Partitions
* Kryo Serialization enabled
* Repartitioning by collision year
* Partitioned Parquet storage
* DataFrame API optimization (Catalyst & Tungsten engines)

---

## **Data Engineering Pipeline**

* CSV ingestion in PERMISSIVE mode
* Safe casting using `try_cast`
* Null handling and validation
* Repartitioning for parallel processing
* Conversion to partitioned Parquet format
* Custom feature engineering (hour_of_day extraction)
* Vector assembly for ML feature creation

---

## **Machine Learning Models Evaluated**

* Linear Regression
* Decision Tree Regressor
* Random Forest Regressor
* Gradient Boosted Trees Regressor
* Evaluation Metric: Root Mean Squared Error (RMSE)
* 3-fold distributed cross-validation (parallelism = 4)

---

## **Model Performance Comparison**

* Linear Regression – RMSE: 0.4388 – Training Time: 15.10s
* Decision Tree – RMSE: 0.4355 – Training Time: 17.45s
* Random Forest – RMSE: 0.4323 – Training Time: 98.79s
* Gradient Boosted Trees – RMSE: 0.4329 – Training Time: 63.87s

**Best Performing Model:** Random Forest (Lowest RMSE)

---

## **Feature Importance Insights**

* Number of casualties identified as dominant predictor
* Number of vehicles involved strongly influences severity
* Speed limit shows nonlinear impact on severity
* Supports the use of ensemble tree-based methods

---

## **Scalability & Big Data Insights**

* Strong scaling: Increasing executors reduced training time
* Weak scaling: Training time increased proportionally with dataset size
* Partitioning reduced shuffle overhead
* Parquet enabled predicate pushdown optimization
* Caching reduced recomputation during cross-validation
* Kryo serialization improved memory efficiency

---

## **Exploratory Data Analysis Findings**

* Slight collisions dominate dataset distribution
* Long-term decline in total collisions since early 2000s
* Urban low-speed zones show higher collision frequency
* Weather has moderate influence on severity
* Weak linear correlations support nonlinear modeling approaches

---

## **Distributed vs Single-Node Comparison**

* 50,000-row sample evaluated using Scikit-learn Random Forest
* Distributed Spark efficiently processed full dataset
* Single-node approach limited by memory and computational constraints

---

## **Conclusion**

* Successfully developed a scalable distributed ML pipeline
* Random Forest achieved the lowest RMSE
* Ensemble models outperformed linear models
* Distributed training significantly improves scalability
* Demonstrates trade-off between computational cost and predictive accuracy

---

## **Future Work**

* Implement ordinal classification approach
* Integrate geospatial clustering
* Extend hyperparameter optimization
* Deploy in cloud environments (AWS / Azure Spark)
* Conduct statistical significance testing of model differences

---
