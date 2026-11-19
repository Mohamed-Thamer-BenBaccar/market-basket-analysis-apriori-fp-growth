# Market Basket Analysis with Apriori and FP-Growth

## Overview

This project applies **Market Basket Analysis** to supermarket transaction data. It uses the Apriori and FP-Growth algorithms to identify frequent product combinations, generates association rules, visualizes their metrics, and implements a basic product recommendation function.

The notebook is designed as an end-to-end introductory data mining project.

## Dataset

The dataset contains:

- **500 transactions**
- **20 unique products**
- **1,968 transaction-product records**
- Two columns: `Transaction_ID` and `Produit`
- No missing values or exact duplicate rows in the supplied file

The CSV file is stored in `data/transactions_supermarche.csv`.

## Objectives

- Explore and validate transaction data.
- Transform transaction records into a Boolean basket matrix.
- Discover frequent itemsets with Apriori.
- Compare Apriori and FP-Growth.
- Generate association rules using support, confidence, and lift.
- Visualize and interpret the rules.
- Build a simple product recommendation function.

## Methods

### Frequent itemset mining

The notebook uses a minimum support threshold of `0.05`. On 500 transactions, this corresponds to an itemset appearing in at least 25 transactions.

- **Apriori** generates candidate itemsets level by level and prunes candidates that cannot be frequent.
- **FP-Growth** mines patterns using an FP-Tree and avoids explicit candidate generation.

Both methods identify frequent itemsets; execution times depend on the dataset and computing environment.

### Association rules

Association rules are generated with a minimum confidence threshold of `0.50`. The notebook retains the following metrics:

| Metric     | Meaning                                                                          |
| ---------- | -------------------------------------------------------------------------------- |
| Support    | Share of all transactions containing both sides of the rule                      |
| Confidence | Share of transactions containing the antecedent that also contain the consequent |
| Lift       | Confidence divided by the overall support of the consequent                      |

A lift greater than 1 indicates a positive association according to this measure. It does not establish causation.

## Selected Results

Examples from the analysis:

| Association rule     | Support | Confidence | Lift |
| -------------------- | ------: | ---------: | ---: |
| Pates → Sauce_tomate |   13.0% |     73.03% | 4.87 |
| Sauce_tomate → Pates |   13.0% |     86.67% | 4.87 |
| Sucre → Cafe         |   12.4% |     91.18% | 4.51 |
| Biscuits → Lait      |   13.6% |     89.47% | 2.89 |
| Beurre → Pain        |   28.2% |     96.58% | 2.45 |

At a minimum support of `0.05`, the earlier analysis identified 73 frequent itemsets. The notebook re-runs the algorithms so that outputs and timings are generated in the current environment.

The number of association rules changes with the confidence threshold:

| Minimum confidence | Number of rules |
| -----------------: | --------------: |
|               0.30 |              73 |
|               0.50 |              26 |
|               0.70 |              23 |

Execution times are intentionally not hard-coded because they vary across machines and runs.

## Potential Applications

The patterns may help inform:

- Product-bundle ideas, such as pasta and tomato sauce.
- Product placement analysis, such as biscuits and milk.
- Inventory monitoring for products that are frequently associated.

These are potential applications, not guaranteed business outcomes. The analysis does not include product prices, profit margins, or customer characteristics.

## Repository Structure

```text
market-basket-analysis-apriori-fp-growth/
├── data/
│   ├── transactions_supermarche.csv
│   └── README.md
├── images/
├── market_basket_analysis.ipynb
├── requirements.txt
├── .gitignore
├── LICENSE
└── README.md
```

## Installation and Usage

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/market-basket-analysis-apriori-fp-growth.git
cd market-basket-analysis-apriori-fp-growth
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the notebook

```bash
jupyter notebook
```

Open `market_basket_analysis.ipynb` and run all cells from top to bottom.

The notebook expects the CSV file at `data/transactions_supermarche.csv`. If opened directly in Google Colab without the repository data folder, it will offer a file-upload option.

## Limitations

- The dataset contains 500 transactions and may not represent other stores or time periods.
- Association rules identify statistical relationships, not causal effects.
- Results depend on the chosen support and confidence thresholds.
- The analysis does not include prices, profit margins, promotions, or customer-level information.
- High confidence on a small support should be interpreted cautiously.

## Future Improvements

- Evaluate the methods on larger transaction datasets.
- Include price and profit-margin information.
- Explore time-based purchasing patterns.
- Extend recommendations to baskets containing multiple products.
- Build an interactive dashboard for exploring association rules.

## Author

**Mohamed Thamer BENBACCAR**

Introductory Data Mining Project — Market Basket Analysis

---

If you find this project useful, feel free to star the repository.
