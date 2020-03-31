MARKET BASKET ANALYSIS

Market Basket - a collection of items added to a cart (for online order) or basket at a supermarket.

Market basket analysis is to find a set of items that appear together in many transactions.

We're using "Association Rule" for this, and familiarity with few terms is important.
Support:
This tells how often a combination of products appeared in all transactions. 
For example: # records with X and Y / Total number of transactions (or records)

Confidence: It tells you how confident are we in saying "X" product to "Y" product.
This is a conditional probability of a rule of getting the second element given the first.
For example: # records with both X and Y / # records with X

Note:- Association Rule is "strong" if it has minimum support and confidence, which is predefined by you.

APRIORI ALGORITHM.
Let's see how it works:

For example we have data like below:
Transactions:
T1: Diaper, milk, candy
T2: Milk, eggs
T3: Milk, beer
T4: Diaper, milk, egg

To find the association rule -> we need to count occurences of all combinations.
* 1 to 1 rules like:
  - diaper -> milk
  - diaper > candy
  - milk -> beer
  - egg -> milk

* 2 to 1 rules be like:
  - diaper & milk -> eggs
  - daiper & candy -> milk
Too many combinations


