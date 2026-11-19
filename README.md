# Market Basket Analysis with Apriori and FP-Growth

## Project Overview

This project explores **Market Basket Analysis**, a data mining technique used to identify relationships between products frequently purchased together.

Using transactional data, this project applies two frequent itemset mining algorithms — **Apriori** and **FP-Growth** — to discover product combinations and generate association rules.

The objective is to extract meaningful purchasing patterns and demonstrate how these insights can support data-driven retail decisions.

## Dataset

The dataset contains transactional purchase records with the following structure:

- **500 transactions**
- **20 unique products**
- **1,968 transaction-product records**
- Two columns: `Transaction_ID` and `Produit`

Each row represents a product included in a particular transaction.

The data is transformed into a binary basket matrix, where each row represents a transaction and each column represents a product.

> Note: The dataset is not included in this repository. Add it only if you have permission to share it.

## Project Objectives

- Explore and understand transactional data.
- Transform transaction records into a basket matrix.
- Identify frequent itemsets using the Apriori algorithm.
- Compare Apriori with FP-Growth.
- Generate association rules using support, confidence, and lift.
- Visualize relationships between association rules.
- Build a simple product recommendation function.
- Interpret the results and discuss possible retail applications.

## Technologies and Libraries

- Python
- Pandas
- Matplotlib
- mlxtend
- Jupyter Notebook

## Methodology

### 1. Data Preparation

The dataset is loaded and inspected to identify its structure, missing values, duplicate records, and product distribution.

The transactional data is then transformed into a binary basket matrix using Pandas.

### 2. Frequent Itemset Mining

Two algorithms are implemented:

- **Apriori:** Generates candidate itemsets level by level and removes itemsets that do not satisfy the minimum support threshold.
- **FP-Growth:** Uses an FP-Tree structure to mine frequent itemsets without explicitly generating candidate itemsets.

Both algorithms are evaluated using a minimum support threshold of `0.05`.

### 3. Association Rule Mining

Association rules are generated using a minimum confidence threshold of `0.50`.

The following metrics are used:

| Metric | Description |
|---|---|
| Support | Proportion of transactions containing both the antecedent and consequent |
| Confidence | Probability of finding the consequent when the antecedent is present |
| Lift | Measures how much more frequently two itemsets occur together than expected under independence |

Rules with a lift greater than `1` are selected for further analysis.

### 4. Visualization

A scatter plot is created to visualize association rules:

- X-axis: Support
- Y-axis: Confidence
- Color: Lift

This visualization helps identify rules with interesting combinations of support, confidence, and lift.

### 5. Product Recommendations

A recommendation function is implemented to suggest products based on previously discovered association rules.

For example, the rule:

`Pates → Sauce_tomate`

can be used to suggest tomato sauce when pasta is present in a transaction.

## Key Results

### Apriori vs. FP-Growth

With a minimum support threshold of `0.05`, both algorithms identified **73 frequent itemsets**.

| Algorithm | Frequent Itemsets | Execution Time |
|---|---:|---:|
| Apriori | 73 | 0.038 seconds |
| FP-Growth | 73 | 0.308 seconds |

Apriori was faster in this particular experiment. However, execution time depends on dataset characteristics, implementation, and computing environment. FP-Growth can be advantageous on larger datasets.

### Association Rule Examples

| Association Rule | Support | Confidence | Lift |
|---|---:|---:|---:|
| Pates → Sauce_tomate | 13.0% | 73.03% | 4.87 |
| Sauce_tomate → Pates | 13.0% | 86.67% | 4.87 |
| Sucre → Cafe | 12.4% | 91.18% | 4.51 |
| Biscuits → Lait | 13.6% | 89.47% | 2.89 |
| Beurre → Pain | 28.2% | 96.58% | 2.45 |

These results illustrate positive associations between several product combinations.

### Confidence Threshold Analysis

The number of generated association rules changes depending on the minimum confidence threshold:

| Minimum Confidence | Number of Rules |
|---|---:|
| 0.30 | 73 |
| 0.50 | 26 |
| 0.70 | 23 |

Increasing the confidence threshold reduces the number of retained rules.

## Potential Business Applications

The discovered associations can support several retail decisions:

- Creating product bundles based on frequently associated items.
- Improving product placement in stores.
- Planning inventory for products that are frequently purchased together.
- Designing targeted promotions based on purchasing patterns.

These are potential applications, not guaranteed outcomes.

## Limitations

- The dataset contains only 500 transactions.
- Results may not represent purchasing behavior in other stores or periods.
- Association rules identify statistical relationships, not causal relationships.
- Support, confidence, and lift depend on the selected thresholds.
- The analysis does not include product prices, profit margins, or customer characteristics.

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/market-basket-analysis-apriori-fp-growth.git
```

Navigate to the project directory:

```bash
cd market-basket-analysis-apriori-fp-growth
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open:

`notebooks/market_basket_analysis.ipynb`

## Project Structure

```text
market-basket-analysis-apriori-fp-growth/
│
├── data/
├── notebooks/
│   └── market_basket_analysis.ipynb
├── images/
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

## Future Improvements

- Test the algorithms on larger transactional datasets.
- Optimize the recommendation function for transactions containing multiple products.
- Explore additional evaluation metrics.
- Include product prices and profit margins.
- Develop an interactive dashboard for exploring association rules.

## Author

**Mohamed Thamer BENBACCAR**

Data Mining Project — Market Basket Analysis

If you find this project useful, feel free to star the repository.

