# Data Science Project 1: Advanced EDA & Feature Engineering

## 📌 Project Overview

This project focuses on transforming raw e-commerce order data into a clean, structured, and analysis-ready dataset. It involves Exploratory Data Analysis (EDA), missing-value treatment, outlier detection, and feature engineering using Python.

The goal is to improve data quality, identify meaningful patterns, and prepare the dataset for potential downstream machine learning applications.

## 🎯 Objectives

- Perform Exploratory Data Analysis (EDA) to understand the dataset.
- Identify and handle missing values using appropriate techniques.
- Detect potential outliers using the Interquartile Range (IQR) method.
- Apply outlier treatment while preserving original transaction values.
- Create meaningful features from existing columns.
- Validate the cleaned dataset and export it for further analysis.

## 📂 Dataset Description

The dataset contains e-commerce order information, including:

| Column | Description |
|---|---|
| `OrderID` | Unique order identifier |
| `Date` | Order date |
| `CustomerID` | Customer identifier |
| `Product` | Product purchased |
| `Quantity` | Number of units ordered |
| `UnitPrice` | Price per unit |
| `ShippingAddress` | Shipping address |
| `PaymentMethod` | Payment method used |
| `OrderStatus` | Current order status |
| `TrackingNumber` | Shipment tracking identifier |
| `ItemsInCart` | Number of items in the cart |
| `CouponCode` | Coupon code associated with the order |
| `ReferralSource` | Source through which the customer arrived |
| `TotalPrice` | Total order price |

The dataset contains 1,200 records and 14 original columns.

## 🛠️ Technologies Used

- **Python** — Programming language
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical computations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Jupyter Notebook** — Interactive development environment

## 🔍 Project Workflow

### 1. Exploratory Data Analysis (EDA)

- Inspected dataset dimensions, column names, and data types.
- Generated descriptive statistics.
- Examined numerical and categorical variables.
- Analyzed distributions using histograms and boxplots.
- Visualized missing values and numerical correlations.
- Investigated order trends over time.

### 2. Missing-Value Treatment

The initial analysis identified missing values in the `CouponCode` column.

Since this is a categorical variable, mean and median imputation are not appropriate. Missing entries can be labeled as `No Coupon` if the dataset's business rules confirm that they represent orders without a coupon.

### 3. Outlier Detection and Treatment

The Interquartile Range (IQR) method was used to identify potential outliers in numerical columns.

The IQR is calculated as:

`IQR = Q3 - Q1`

Outlier boundaries are calculated using:

- Lower Bound = Q1 − 1.5 × IQR
- Upper Bound = Q3 + 1.5 × IQR

Potential outliers were inspected before treatment. A separate capped order-price column was created using clipping to support statistical analysis while preserving the original `TotalPrice` values.

### 4. Feature Engineering

The following features were derived from existing columns:

| New Feature | Description |
|---|---|
| `OrderYear` | Year in which the order was placed |
| `OrderMonth` | Month in which the order was placed |
| `OrderQuarter` | Calendar quarter of the order |
| `IsWeekend` | Indicates whether the order was placed on a weekend |
| `CustomerOrderCount` | Number of order records associated with each customer in the dataset |

These features can support temporal analysis, customer behavior analysis, and future predictive modeling.

### 5. Data Validation

The final dataset is checked for:

- Remaining missing values
- Duplicate records
- Appropriate data types
- Consistency between `TotalPrice` and `Quantity × UnitPrice`
- Correct generation of engineered features

### 6. Exporting the Processed Dataset

The processed dataset is exported as a CSV file for future analysis.

## 📁 Project Structure

```text
Data-Science-Project-1/
│
├── data/
│   ├── raw/
│   │   └── Dataset for Data Analytics - Sheet1.csv
│   │
│   └── processed/
│       └── cleaned_dataset.csv
│
├── notebooks/
│   └── Data_Science_Project_1.ipynb
│
├── README.md
└── requirements.txt
```

*Note: The folder structure above is a recommended organization. Adjust filenames and folders to match your actual project.*

## ⚙️ Installation and Setup

### Prerequisites

Install Python 3.10 or later and Jupyter Notebook, or use Anaconda.

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
cd Data-Science-Project-1
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

Alternatively, install the dependencies listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `Data_Science_Project_1.ipynb` and run the notebook cells in order.

Ensure the dataset path in the notebook matches your local folder structure.

## 📊 Key Findings

The initial dataset inspection identified the following observations:

- The dataset contains 1,200 order records and 14 original columns.
- Missing values were identified in `CouponCode`.
- No completely duplicated rows were identified in the initial inspection.
- `TotalPrice` is mathematically consistent with `Quantity × UnitPrice`, subject to floating-point precision.
- The IQR method identified potential high-value orders that required inspection.
- Date-derived and customer-level features were created to support further analysis.

## 🚀 Future Improvements

- Compare different imputation strategies on suitable numerical features.
- Add automated data-quality checks.
- Investigate seasonal patterns in order volume.
- Analyze order status and product-level trends.
- Explore categorical encoding and multicollinearity.
- Develop a machine learning model if a suitable prediction objective is defined.
- Add reproducible preprocessing pipelines and unit tests.

## 📝 Conclusion

This project demonstrates a structured approach to data preprocessing through exploratory analysis, missing-value treatment, outlier detection, and feature engineering. It emphasizes understanding the data and justifying preprocessing decisions instead of applying transformations blindly.

The resulting dataset can serve as a foundation for further business analysis and future machine learning experiments.

---

**Project:** Data Science Project 1 — Advanced EDA & Feature Engineering  
**Focus Areas:** Python, Pandas, NumPy, EDA, Data Cleaning, Statistical Analysis, Feature Engineering  
**Environment:** Jupyter Notebook
