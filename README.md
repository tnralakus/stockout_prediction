
## Navigating Supply Chain Volatility: A Predictive 3-Class Model for Stockout

  

### Executive Summary

This project addresses the critical challenge of inventory imbalance within global supply chains. By transforming high-dimensional supply chain data into a predictive classification system, this model categorizes inventory into three actionable risk states: ***No Stockout***, ***Potential Stockout*** (Late Delivery Risk), and ***Stockout***.

Utilizing the DataCo Smart Supply Chain dataset, the project employs advanced data cleaning, feature engineering, and regularization techniques to minimize lost revenue and trapped capital, aiming for the "Goldilocks" balance of inventory management.
 

### Rationale

Supply chain disruptions and stockouts lead to significant financial losses and decreased customer satisfaction. Conversely, overstocking traps capital and increases holding costs. 

A prescriptive tool that can anticipate these states allows businesses to move from reactive troubleshooting to proactive strategy, mathematically pruning noise while focusing on key predictive indicators.

### Research Question

How can we transform high-dimensional supply chain data into a predictive classification system that categorizes inventory into actionable risk states while mathematically pruning redundant noise through regularization?
 

### Data Sources

The project utilizes the ***DataCo Smart Supply Chain for Big Data Analysis dataset (available on [Kaggle](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis?select=DataCoSupplyChainDataset.csv%C2%A0))*** . It consists of ***180,519*** entries with ***53*** initial attributes covering areas such as provisioning, production, sales, and commercial distribution.  
  

### Methodology

 - **Exploratory Data Analysis (EDA):** Conducted a comprehensive analysis of dataset distributions, variable relationships, and data quality to inform subsequent processing.

 - **Target Engineering:** Defined a new 3-class target variable (Stockout_Class):

					Class 0: No Stockout.

					Class 1: Potential Stockout (Orders with late delivery risk).

					Class 2: Stockout (Cancelled orders or shipping canceled).

 - **Data Cleaning & Feature Engineering:**  Performed cleaning to handle missing values and remove irrelevant or redundant columns.  Applied feature engineering and dimensionality reduction techniques to streamline the dataset and address multicollinearity.

 - **Modeling Approach:**  
	 - Established a classification pipeline incorporating necessary preprocessing, such as scaling and encoding.  
	 - Evaluated a suite of classification algorithms including:
		- Baseline: Logistic Regression
		- Advanced Models: K-Nearest Neighbors (KNN), SVM, Decision Trees, XGBoost, and Random Forest.
	- Implemented Cost-Sensitive Learning by applying a penalty matrix to weight misclassifications appropriately, prioritizing critical error mitigation.
	- Executed hyperparameter optimization to identify the most effective settings for every model.

 - **Handling Imbalance:**  Utilized resampling techniques like SMOTETomek to address class imbalance and ensure robust learning across all classes.

 - **Evaluation Metrics:** Assessed model performance using metrics beyond standard accuracy to ensure comprehensive evaluation based on the specific cost-sensitive requirements of the task.

  
### Results

The Logistic Regression model significantly outperformed the baseline, achieving an overall test accuracy of 80.32% compared to the 54.83% baseline.
 - **Performance Metrics:** The model shows robust performance for majority classes (Class 0 and 1) with high precision and recall.
 - **Minority Class Analysis (Class 2 - 'Stockout'):** While the implementation of SMOTETomek successfully addressed class imbalance and yielded a high recall of 0.86 for the minority 'Stockout' class, precision remains problematic at 0.16.
 - **Key Insight:** The current configuration is optimized for sensitivity, effectively capturing stockout events, but suffers from high false-positive rates due to the model's over-sensitivity resulting from the resampling technique.
 - **Reliability:** The model is highly accurate at identifying orders that are running smoothly or are only at minor risk.
 - **Primary Challenge:** The model is very good at flagging potential "Stockout" issues (the most critical category), ensuring that real problems are rarely missed. However, it is currently "overly cautious," meaning it often flags healthy orders as potential problems.
 - **Business Implication:** We are effectively catching real supply chain disruptions, but we are also generating a high volume of false alarms. Future adjustments should focus on balancing this "better safe than sorry" approach against the cost of investigating these false alerts.
 
 *To be completed*

### Next steps

*To be completed*
  
### Outline of project

[Stockout Prediction By Taner Alakus]([https://github.com/tnralakus/stockout_prediction](https://github.com/tnralakus/stockout_prediction/blob/main/stockout_prediction.ipynb))
