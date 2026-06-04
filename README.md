
# Navigating Supply Chain Volatility: A Predictive 3-Class Model for Stockout

### Executive  Summary & Strategic Value
This project transforms high-dimensional supply chain data into a predictive classification system designed to mitigate the financial risks of inventory imbalance. By categorizing orders into **No Stockout**, **Potential Stockout**, and **Stockout** (Class 2), the model acts as an early-warning radar for supply chain managers.

Using the DataCo Smart Supply Chain dataset, the project employs advanced data cleaning, feature engineering, and cost-sensitive modeling to minimize lost revenue and optimize capital allocation.

-   **Technical Performance:** Through rigorous data cleaning, `SMOTETomek` resampling to handle class imbalance, and hyperparameter optimization, the project identifies key predictive indicators. The **K-Nearest Neighbors (KNN)** model was selected as the optimal tool for Class 2 detection, achieving the highest F1-Score (0.36) for the critical minority category.
    
-   **Business Impact:** The system prioritizes **Recall (Sensitivity)** for stockout events, ensuring that critical failures are rarely missed—a strategic choice to prioritize operational continuity over the lower costs of investigating "false alarm" flags.
    
-   **Next Steps:** Future iterations will focus on **precision optimization** via threshold tuning, the integration of **Explainable AI (SHAP)** to reveal hidden drivers of stockouts, and the development of a **Human-in-the-Loop triage dashboard** to streamline procurement responses.

### Rationale

Supply chain disruptions lead to significant financial losses and decreased customer satisfaction. Conversely, overstocking traps capital and increases holding costs. A prescriptive tool that anticipates these states allows businesses to move from reactive troubleshooting to proactive strategy, effectively balancing inventory health against operational risk.

### Research Question

How can we transform high-dimensional supply chain data into a predictive classification system that categorizes inventory into actionable risk states, effectively managing class imbalance to prioritize critical stockout events?

### Data Sources

-   **Dataset**: DataCo Smart Supply Chain for Big Data Analysis (Available on [Kaggle](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis)).
    
-   **Scope**: 180,519 entries with 53 initial attributes covering production, sales, and commercial distribution.
    

### Methodology

-   **Exploratory Data Analysis (EDA):** Analyzed variable distributions and correlations to identify key predictors of delivery delays and cancellations.
    
-   **Target Engineering:** Categorized inventory into three classes:
    
    -   **Class 0:** No Stockout.
        
    -   **Class 1:** Potential Stockout (Late delivery risk).
        
    -   **Class 2:** Stockout (Cancelled orders or shipping canceled).
        
-   **Preprocessing:** Handled missing values, removed redundant features, and applied dimensionality reduction to reduce noise.
    
-   **Modeling Pipeline:**
    
    -   Evaluated multiple classifiers: Logistic Regression (Baseline), KNN, SVM, Decision Trees, Hist Gradient Boosting, and Random Forest.
        
    -   **Class Imbalance Strategy:** Implemented resampling techniques (`SMOTETomek`) to ensure robust learning for the minority "Stockout" class.
        
    -   **Optimization:** Executed comprehensive hyperparameter tuning for all models.
        

### Results

The project successfully moved beyond baseline performance.

-   **Performance Metrics:** While accuracy is generally high, our primary metric—the **F1-Score for Class 2 (Stockout)**—was the target for optimization. In supply chain, the cost of missing a stockout (a false negative) far outweighs the cost of investigating a false alarm (a false positive).
    
-   **Best Performing Model:** **K-Nearest Neighbors (KNN)** emerged as the most effective model for Class 2 identification, achieving an F1-Score of **0.36**.
    
-   **Key Insight:** While tree-based ensemble methods (like Random Forest) provided superior overall accuracy, the **KNN** model demonstrated the best balance of targeted class identification and computational speed for the specific objective of detecting "Stockout" events.
    


| Model | Train Time (s) | Train Accuracy | Test Accuracy | F1-Score (Class 2) |
| :--- | :--- | :--- | :--- | :--- |
| **KNN** | 0.13 | 1.00 | 0.69 | **0.36** |
| **SVC** | 7.15 | 0.71 | 0.55 | 0.27 |
| **Logistic Regression** | 5.99 | 0.67 | 0.57 | 0.27 |
| **Random Forest** | 7.29 | 0.76 | 0.61 | 0.27 |
| **Decision Tree (DT)** | 5.69 | 0.80 | 0.66 | 0.24 |
| **Hist Gradient Boosting** | 4.23 | 0.81 | 0.69 | 0.17 |


### Next Steps

-   **Threshold Tuning:** Implement probability threshold moving to further improve Class 2 Precision without compromising Recall.
    
-   **SHAP Analysis:** Integrate explainable AI techniques (SHAP) to interpret which specific supply chain features are driving the model's predictions.
    
-   **Operational Integration:** Prototype an automated dashboard that flags "Class 2" items for immediate review by procurement managers.
    

### How to use this project

1.  Clone this repository.
    
2.  Ensure you have the `DataCoSupplyChainDataset.csv` in the appropriate directory.
    
3.  Open `stockout_prediction.ipynb` in Jupyter Lab or Google Colab.
    
4.  Run the cells sequentially to reproduce the preprocessing, modeling, and evaluation pipeline.
