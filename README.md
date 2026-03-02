# **Distributed Machine Learning for Large-Scale Road Collision Severity Prediction**

## **Project Overview**

This project develops a scalable distributed machine learning framework using Apache Spark to predict road collision severity from extensive UK traffic collision records. Various regression models are implemented and assessed within a parallel computing environment to evaluate predictive accuracy, scalability, and computational efficiency. The results highlight the advantages of ensemble techniques in handling structured big data, particularly in capturing complex nonlinear patterns present in transportation datasets.

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

* **Source:** UK Department for Transport – Road Collision Statistics
* Multi-decade structured national collision records

**Key Features:**

* Collision year
* Severity
* Number of vehicles involved
* Number of casualties
* Speed limit
* Weather conditions
* Road surface conditions
* Lighting conditions
* Time of collision

Large temporal coverage makes the dataset suitable for distributed big data processing.

---

# **Methodology**

## 1.Data Engineering & Preprocessing

* CSV ingestion in PERMISSIVE mode
* Safe casting using `try_cast`
* Null handling and validation
* Repartitioning by collision year for parallelism
* Conversion to partitioned Parquet format
* Feature engineering (hour_of_day extraction)
* VectorAssembler for ML feature creation

---

## 2.Distributed Architecture Configuration

* 4 Executors
* 4 Cores per Executor
* 6GB Executor Memory
* 4GB Driver Memory
* 400 Shuffle Partitions
* Kryo Serialization enabled
* DataFrame API optimization (Catalyst & Tungsten engines)

---

## 3.Model Training Strategy

* 80/20 Train-Test Split
* 3-fold Distributed Cross-Validation (parallelism = 4)
* Evaluation Metric: **Root Mean Squared Error (RMSE)**

### Models Evaluated:

* Linear Regression
* Decision Tree Regressor
* Random Forest Regressor
* Gradient Boosted Trees Regressor

---

# **Results**

## Model Performance Comparison

| Model                  | RMSE              | Training Time |
| ---------------------- | ----------------- | ------------- |
| Linear Regression      | 0.4388            | 15.10s        |
| Decision Tree          | 0.4355            | 17.45s        |
| Random Forest          | **0.4323 (Best)** | 98.79s        |
| Gradient Boosted Trees | 0.4329            | 63.87s        |

### Key Findings

* Random Forest achieved the lowest RMSE
* Ensemble models outperformed linear regression
* Tree-based models effectively captured nonlinear relationships
* Improved accuracy came with higher computational cost

---

# **Feature Importance Insights**

* Number of casualties is the strongest predictor
* Number of vehicles significantly influences severity
* Speed limit exhibits nonlinear impact
* Confirms suitability of ensemble tree-based methods

---

# **Exploratory Data Analysis Findings**

* Slight collisions dominate dataset distribution
* Long-term decline in total collisions since early 2000s
* Urban low-speed zones show higher collision frequency
* Weather moderately influences severity
* Weak linear correlations justify nonlinear modeling

---

# **Scalability & Big Data Insights**

* Strong scaling: Increasing executors reduced training time
* Weak scaling: Training time increased proportionally with dataset size
* Partitioning reduced shuffle overhead
* Parquet enabled predicate pushdown optimization
* Caching reduced recomputation during cross-validation
* Kryo serialization improved memory efficiency

---

# **Distributed vs Single-Node Comparison**

* 50,000-row sample evaluated using Scikit-learn Random Forest
* Distributed Spark efficiently processed full dataset
* Single-node approach limited by memory and computational constraints

---

# **Interactive Dashboards (Tableau)**

**[Dashboard 1 – Data Quality & Pipeline Monitoring](https://prod-in-a.online.tableau.com/t/ashsish2345-3816dbd389/authoring/ashish/Dashboard1)**

**[Dashboard 2 – Exploratory Data Analysis](https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/seconddashboard/Dashboard1)**

**[Dashboard 3 – Model Performance & Feature Importance](https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/thirddashboard_17719403723090/Dashboard1?:iid=1)**

**[Dashboard 4 – Scalability & Cost Analysis](https://prod-in-a.online.tableau.com/#/site/ashsish2345-3816dbd389/views/dashboardfour/Dashboard1)**

# **Conclusion**

The project demonstrates that distributed machine learning using Apache Spark significantly improves scalability and computational efficiency for large-scale transportation analytics. Random Forest achieved the best predictive performance, validating the effectiveness of ensemble methods for structured big data problems. The study highlights the trade-off between computational cost and predictive accuracy while confirming the value of distributed ML architectures.

---
