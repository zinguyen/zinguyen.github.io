# Association Rules

determining relations among variables in large databases

## 1. Market Basket Analysis

### Support

The support of an itemset 𝑋, 𝑠𝑢𝑝𝑝(𝑋) is the proportion of transaction in the database in which the item X appears. It signifies the popularity of an itemset.

$$ 𝑠𝑢𝑝𝑝(𝑋) = Number of transaction in which 𝑋 appears / Total number of transactions $$

If the sales of a particular product (item) above a certain proportion have a meaningful effect on profits, that proportion can be considered as the support threshold. Furthermore, we can identify itemsets that have support values beyond this threshold as significant itemsets.

### Confidence

$$ conf(X \rightarrow Y) = \frac{supp(X \cup Y)}{supp(X)} $$

## 2. The Apriori Algorithm

It assumes that

* All subsets of a frequent itemset must be frequent
* Similarly, for any infrequent itemset, all its supersets must be infrequent too
