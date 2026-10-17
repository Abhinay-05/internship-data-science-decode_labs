# Customer Segmentation Using Unsupervised Learning

## Project Overview

This project focuses on customer segmentation using **unsupervised machine learning**. The objective is to discover groups of customers with similar purchasing behaviours from retail transaction data and translate those groups into actionable business insights.

The project follows the DecodeLabs Data Science Project 3 brief, using feature scaling, Principal Component Analysis (PCA), K-Means clustering, the Elbow Method, and Silhouette Score.

## Objectives

- Explore and preprocess retail transaction data.
- Create customer-level features from individual order records.
- Standardize numerical features before distance-based clustering.
- Apply PCA to reduce dimensionality and visualize customer groups.
- Determine a suitable number of clusters using the Elbow Method and Silhouette Score.
- Develop customer personas and suggest data-driven business strategies.

## Dataset

The dataset contains e-commerce order information, including:

- `OrderID` — order identifier
- `Date` — order date
- `CustomerID` — customer identifier
- `Product` — product category or type
- `Quantity` — quantity purchased
- `UnitPrice` — price per unit
- `PaymentMethod` — payment method used
- `OrderStatus` — current or recorded order status
- `ItemsInCart` — number of items in the cart
- `CouponCode` — coupon associated with the order
- `ReferralSource` — source through which the customer arrived
- `TotalPrice` — total order price

**Dataset preparation:** Individual order records are aggregated by `CustomerID` to create customer-level profiles. Identifier fields are retained for interpretation but excluded from clustering features.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Project Workflow

### 1. Exploratory Data Analysis

- Inspected dataset dimensions, data types, and summary statistics.
- Checked missing values and duplicate records.
- Examined numerical and categorical features.
- Converted the order date into a datetime format.

### 2. Customer-Level Feature Engineering

Order records are aggregated to derive behavioural features such as:

- Total spending
- Total quantity purchased
- Number of orders
- Average order value
- Average items in cart
- Average unit price
- Number of unique products purchased
- Weekend order rate

Categorical purchasing information, including product, payment method, order status, referral source, and coupon usage, is also encoded to represent customer preferences.

### 3. Feature Scaling

`StandardScaler` is applied to standardize the feature matrix.

This is important because K-Means uses distance calculations, and features with larger numerical ranges could otherwise dominate the clustering process.

### 4. Principal Component Analysis (PCA)

PCA transforms the scaled features into principal components that capture variation in the data.

The project uses PCA to:

- Examine explained and cumulative explained variance.
- Understand how much information is retained by fewer components.
- Project customer profiles into two dimensions for visualization.

### 5. K-Means Clustering

K-Means groups customers based on similarities in their scaled feature values.

Different values of K are evaluated to identify a reasonable segmentation.

### 6. Selecting the Number of Clusters

Two evaluation techniques are used:

**Elbow Method**

Plots the within-cluster sum of squares (inertia) against the number of clusters. The elbow indicates where additional clusters produce diminishing improvements.

**Silhouette Score**

Measures how well-separated the clusters are. Scores closer to 1 generally indicate better separation, while values around 0 suggest overlapping clusters.

Both methods are considered when selecting the final number of clusters.

### 7. Cluster Visualization and Interpretation

The final cluster assignments are visualized using the first two principal components.

Cluster sizes and customer-level feature averages are examined to understand how the groups differ.

### 8. Customer Personas and Business Insights

Each cluster is interpreted using its observed purchasing behaviour.

Potential personas may include:

- High-Spending Customers
- Frequent Purchasers
- Budget-Conscious Customers
- Product-Variety Seekers

These names are examples only. Final persona labels and business recommendations should be based on the actual cluster profiles.

Possible applications include targeted marketing, customer loyalty initiatives, product recommendations, and personalized promotional campaigns.

## Evaluation

The project uses the following evaluation and diagnostic outputs:

- PCA explained variance
- Elbow Method plot
- Silhouette Scores across candidate cluster counts
- Cluster-size distribution
- Cluster-level feature summaries
- PCA-based cluster visualization

Since this is an unsupervised learning task, there is no predefined target label or classification accuracy score.

## Key Findings

Complete this section after running the notebook with the final dataset and model.

- **Number of customer profiles:** [Insert actual count]
- **Number of clusters selected:** [Insert selected K]
- **Variance retained by the first two principal components:** [Insert actual percentage]
- **Best Silhouette Score:** [Insert actual score and corresponding K]
- **Most distinctive customer segment:** [Describe using actual cluster statistics]
- **Business recommendation:** [Insert a recommendation supported by the results]

## Project Structure

```text
Project_3_Customer_Segmentation/
│
├── data/
│   └── Dataset for Data Analytics - Sheet1(1).csv
│
├── notebooks/
│   └── customer_segmentation.ipynb
│
├── outputs/
│   ├── customer_segments.csv
│   ├── cluster_profiles.csv
│   ├── cluster_comparison.csv
│   └── evaluation_plots/
│
├── README.md
└── requirements.txt
```

*The structure above is a recommended layout. Adjust the paths and filenames to match your actual repository.*

## Installation and Setup

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
cd Project_3_Customer_Segmentation
```

### 2. Install dependencies

Create a `requirements.txt` file containing:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

Install the packages:

```bash
pip install -r requirements.txt
```

### 3. Run the notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open `customer_segmentation.ipynb` and run the cells in order. Ensure that the dataset path matches your folder structure.

## Limitations

- Most customers have only one recorded order, limiting the ability to measure long-term purchasing behaviour.
- Clustering results depend on feature selection, scaling, and the chosen number of clusters.
- PCA visualization may hide information contained in dimensions beyond the first two components.
- Customer personas are interpretations of observed patterns, not verified demographic or psychological profiles.
- Business recommendations should be validated against additional data and business outcomes.

## Conclusion

This project demonstrates an end-to-end unsupervised learning workflow for customer segmentation. By combining customer-level feature engineering, feature scaling, PCA, and K-Means clustering, the analysis aims to identify meaningful purchasing patterns and translate them into practical business recommendations.

The project highlights how unsupervised learning can support customer understanding, targeted marketing, and data-driven business decisions.

---

**Project:** Data Science Project 3 — Customer Segmentation
**Training Program:** DecodeLabs Industrial Training Kit, Batch 2026
**Author:** Abhinay Anand
