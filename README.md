# MARKET BASKET ANALYSIS

Market Basket term is a collection of items added to a cart (for online order) or basket at a supermarket. Market basket analysis is to find a set of items that appear together in many transactions.

We're using "Association Rule" for this, and familiarity with few terms is important before jumping to algorithm and its implementation.

## Support:

This tells how often a combination of products appeared in all transactions. 
For example: # records with X and Y / Total number of transactions (or records)

## Confidence:

It tells you how confident are we in saying "X" product to "Y" product.
This is a conditional probability of a rule of getting the second element given the first.
For example: # records with both X and Y / # records with X

Note:- Association Rule is "strong" if it has minimum support and confidence, which is predefined by you.

## Example:

Transactions:
* T1: Diaper, milk, candy
* T2: Milk, eggs
* T3: Milk, beer
* T4: Diaper, milk, egg

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

* Inefficient Method:
  - As finding all combinations and then imputing their frequency is a long process and time-consuming.

* Efficient Method - Using APRIORI ALGORITHM:
  - IF A -> X doesn't occur frequently.
  - THEN A & B -> X doesn't occur frequently either.

Apriori Pruing Principle: If there is any itemset which is infrequent, its superset should not be generated/tested! 

## Apriori Algorithm (Working):
### Stage I - Rules generation based on SUPPORT
1. First Decide the minimum support.
2. Find all frequent k-item sets (k=1 for start i.e. frequency of each product i.e. X1, X2, X3..).
3. Keep the one with meet the minimum support threshold
4. PRUNING - Generate new sets with (k+1) items (i.e. (X1, X2), (X2, X3), (X1, X3)....) from items which exists in upper level.
5. Again Limit the list to frequent items based on min support value
6. Repeat 2-5 until we have no frequent item set.
7. Final combinations will be used to generate strong association rules.

### Stage II - Filtering of Rules based on CONFIDENCE
1. Not all rules are acceptable.
2. Limit the set of rules that meet the minimum confidence requirements. It answers - Can we rely on that rule or not? If so, how confident are we?

## Apriroi Algo (Pseudo-Code)
Set minimum required support
<br>C<sub>k</sub>: Candidate item set of size k
<br>L<sub>k</sub>: frequent item set of size k (from C<sub>k</sub>) with min_support

<br>L<sub>1</sub>: {frequent items};
<br>for (k=1; L<sub>k</sub> $\neq$; k++)
<br>  <b>Begin:</b>
    C<sub>k+1</sub>: candidates generated from L<sub>k</sub>;
    <b>for each</b> transaction t in database <b>do</b>:
      Increment the count of all candidates in C<sub>k+1</sub> that are contained in t
    L<sub>k+1</sub>: candidates in C<sub>k+1</sub> with min_support
  <b>END</b>

  <b>return</b> L<sub>1</sub> U L<sub>2</sub> U ... L<sub>k</sub>;


    
