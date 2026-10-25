# Customer Age Group Segmentation Using K-Means and Decision Trees

## 1. Project Overview

This project creates a new feature called **Age Group** to categorize customers into meaningful age segments using machine learning techniques instead of predefined age ranges.

Two approaches are implemented:

- **K-Means Clustering:** Automatically identifies age groups based on customer age distributions.
- **Decision Tree Classification:** Creates age-based segments using customer recommendation behavior (`Recommended IND`).

The project uses the Women's Clothing E-Commerce Reviews dataset.

## 2. Objectives

- Analyze customer age data and missing values.
- Determine the optimal number of age clusters using the Silhouette Score.
- Generate age groups using K-Means clustering.
- Create age groups using a Decision Tree.
- Compare customer distributions across the generated groups.
- Analyze recommendation rates for each Decision Tree age group.
- Add the newly created age-group features to the original dataset.

## 3. Dataset

**Dataset file:** `Womens Clothing E-Commerce Reviews.csv`

### Features Used

| Feature | Description |
|---|---|
| `Age` | Customer's age |
| `Recommended IND` | Whether the customer recommended the product |
| `Age Group` | Age category generated using K-Means |
| `Age Group (Decision Tree)` | Age category generated using a Decision Tree |

## 4. Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## 5. Installation

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

## 6. Methodology

### Step 1: Data Loading and Inspection

Load the dataset using Pandas and inspect missing age values, minimum age, maximum age, and the number of valid records.

### Step 2: K-Means Clustering

K-Means groups customers according to their age values.

The code tests different cluster counts, from 2 up to 10 when enough distinct ages are available.

The Silhouette Score is calculated for each candidate number of clusters. The number with the highest score is selected as the optimal cluster count among the tested options.

### Step 3: Create Age Groups

After selecting the best cluster count, K-Means assigns each customer to a cluster.

The clusters are sorted by their average age and renamed as:

- Age Group 1
- Age Group 2
- Age Group 3
- Additional groups if selected by the algorithm

The generated `Age Group` feature is added to the original dataset.

### Step 4: Analyze K-Means Groups

The project calculates the following for each age group:

- Customer count
- Minimum age
- Maximum age
- Average age

Scatterplots and count plots visualize the age clusters and customer distribution.

### Step 5: Decision Tree Classification

A Decision Tree is trained using:

- Input feature: `Age`
- Target feature: `Recommended IND`

The data is split into training and testing sets using an 80:20 ratio, with stratification to preserve the target class proportions.

The tree uses `max_leaf_nodes=5` and `min_samples_leaf=100` to limit the number and size of its segments.

### Step 6: Evaluate the Decision Tree

The model is evaluated using:

- **Accuracy:** Overall proportion of correct predictions.
- **Precision:** Proportion of positive predictions that are correct.
- **Recall:** Proportion of actual positive cases identified.
- **F1-Score:** Harmonic mean of precision and recall.

### Step 7: Generate Decision Tree Age Groups

Each customer is assigned to a Decision Tree leaf using the trained model.

The leaf nodes are ordered by their average customer age and renamed as Age Group 1, Age Group 2, and so on.

The new feature `Age Group (Decision Tree)` is added to the dataset.

### Step 8: Analyze Decision Tree Groups

For each generated group, the project calculates:

- Customer count
- Minimum age
- Maximum age
- Recommendation rate

The recommendation rate is expressed as a percentage. A count plot visualizes the customer distribution across the groups.

## 7. Expected Outputs

The project generates:

- Dataset inspection and missing-age information.
- Silhouette Scores for candidate K-Means cluster counts.
- The selected number of clusters.
- K-Means age-group assignments.
- Age-group summary statistics.
- K-Means scatterplot and customer-distribution chart.
- Decision Tree evaluation metrics.
- Decision Tree age-group assignments.
- Recommendation rates for each Decision Tree age group.
- Decision Tree customer-distribution chart.

Actual cluster counts, group sizes, and evaluation scores depend on the dataset and are produced when the notebook is executed.

## 8. Advantages

- Creates data-driven age groups rather than relying on fixed age ranges.
- Helps identify patterns in customer age distributions.
- Enables comparison of recommendation behavior across age segments.
- Adds useful features for customer analytics and marketing analysis.
- Provides visual summaries of customer segments.

## 9. Important Considerations

- K-Means creates groups based on age similarity, while the Decision Tree creates segments based on recommendation behavior.
- Decision Tree segments are not purely age-distribution clusters; their boundaries depend on the target and training data.
- The Silhouette Score identifies compact, separated clusters among the tested options, but the highest score does not automatically guarantee the most useful business segments.
- The Decision Tree evaluation measures recommendation prediction, not the quality of the age-group segmentation itself.
- The code prints `"Random Forest model trained"` after training a Decision Tree. This message should be changed to `"Decision Tree model trained"` for accuracy.
- The notebook uses the same dataset to construct and analyze the age groups. For future predictive modeling, avoid data leakage by fitting preprocessing and segmentation rules on training data only.

## 10. Conclusion

This project demonstrates two machine learning approaches for creating customer age groups. K-Means discovers age-based clusters using the distribution of ages, while a Decision Tree identifies age segments associated with customer recommendation behavior.

The generated features can support customer segmentation, exploratory analysis, and future recommendation or marketing models. The most appropriate approach should be chosen based on the business objective and the usefulness of the resulting segments.
