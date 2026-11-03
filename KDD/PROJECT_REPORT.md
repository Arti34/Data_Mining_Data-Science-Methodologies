# KDD Project Report - Grocery Market Basket Analysis

**Student:** Arti Ramesh Nalawade  
**Student ID:** 02075713  
**Methodology:** Knowledge Discovery in Databases (KDD)

## 1. Project idea
I wanted to find out which grocery products customers commonly buy together. Shops can use these patterns to think about product placement or recommendations. I followed five KDD stages using a public Kaggle grocery dataset and Python in Google Colab.

## 2. Stage 1 - Selection
I used the Kaggle Groceries Dataset (heeraldedhia/groceries-dataset). It contains 38,765 records with a member number, date, and item name. Each member-date pair was treated as one shopping basket. I did not combine a customer's purchases from different dates.

## 3. Stage 2 - Preprocessing
I checked for missing values and duplicates. There were no missing values in the three required fields, and 759 exact duplicate records were found. I removed duplicate rows for basket-presence analysis and standardized product names. After cleaning, there were 14,963 baskets and 167 unique products.

## 4. Stage 3 - Transformation
I converted the grocery rows into a table where each row is a shopping basket and each column is a product. True means the basket contains that product. To make the Colab demonstration faster, I used only the 35 most common products for Apriori. This limits which patterns can be discovered.

## 5. Stage 4 - Data mining
I used the Apriori algorithm. With the original minimum support of 1.5%, the code found 35 frequent itemsets, all containing only one product. This was not useful for explaining which products are purchased together. Following a critique, I lowered the support threshold to 0.5%. This gave 72 frequent itemsets, including 37 multi-product itemsets. After applying a minimum confidence of 5% and lift greater than 1, five association rules remained.

### A rule in plain language
- **Frankfurter -> Other vegetables**
- Support: 0.005146, or about 0.51% of baskets.
- Confidence: 0.136283, or about 13.63% of baskets containing frankfurter also containing other vegetables.
- Lift: 1.116150, meaning this combination happened around 11.6% more often than expected under independent purchase behavior.

These numbers are associations, not cause-and-effect relationships. A higher lift does not automatically make a rule commercially useful.

## 6. Stage 5 - Interpretation and evaluation
I checked the first association rule myself by counting baskets containing the first product and both products. My manually calculated support (0.0051) and confidence (0.1363) matched the Apriori result. Whole milk was the most common item, appearing in about 15.79% of baskets.

The rules have fairly low support and modest lift, so I would treat them as starting points for discussion, not as strong evidence for expensive store changes. I would test any recommendations on fresh data before using them in a real shop.

## 7. AI critique and revision record
**First version:** Apriori used 1.5% minimum support and could not find multi-product itemsets.

**Critique:** The notebook ran, but it did not demonstrate meaningful multi-product patterns, which limited the data mining and interpretation stages. It also needed an independent check of its output.

**Revision:** I tried a lower support threshold of 0.5%, explained the choice, added positive-lift filtering, and manually checked support and confidence.

**After rerunning:** The notebook produced 72 frequent itemsets, 37 multi-product itemsets and five association rules. Its manual checks passed. The lower threshold is an exploratory choice, not proof the selected rules will be useful in the future.

## 8. Limitations and future work
The analysis includes only the 35 most frequent products. It also treats all baskets equally and does not check whether rules remain stable across different time periods. Some associations are weak. In future, I could expand to all 167 products, test pattern stability across dates, and consider business costs and margins.

## 9. Conclusion
This project helped me understand that KDD is more than running an algorithm. I selected data, cleaned it, changed it into basket format, discovered patterns, and checked whether the patterns made sense. I also learned that changing a parameter can change the findings, and I should explain why I changed it.

## 10. Reproducibility
Run `kdd_project_final.ipynb` in Google Colab using **Runtime -> Run all**. It downloads the Kaggle dataset using `kagglehub`, installs required libraries, produces rule tables, and writes CSV artifacts to the Colab runtime. The notebook output shows the actual completed run. Download `KDD_artifacts.zip` from the Colab Files sidebar if CSV outputs are needed separately.

**Dataset link:** https://www.kaggle.com/datasets/heeraldedhia/groceries-dataset
