### Laplace Smoothing

Reading the well-written article of [Monkey Learn on an application of Naive Bayes classifier](https://monkeylearn.com/blog/practical-explanation-naive-bayes-classifier/?utm_source=Email&utm_medium=Newsletter&utm_campaign=naive-bayes-classifier), I came across the notion of **Laplace Smoothing**. It's a mouth-filling name for a very intuitive idea.

When counting a word's rate of occurrance in a corpus, new words get a 0 rate. To apply further arithmetics, this 0-score may cause difficulties. So instead, everything is boosted by one unit. For instance, in calculating the rate of occurance, numerator is naturally increased by one. But to avoid rates > 1, the handling of denominator is important.     

Consider this extreme case: In the prior, we have only one sample of class, classA, with exactly one word, wordA, in it.     
P(wordA | classA) = (1+1)/1     
We need to boost the denominator such that it uniformly impacts all such probabilities and solves the problem of rates > 1.     
One way to get around it is to increase the denominator by the total number of unique words in the entire corpus.    
Let's examine this solution:       
1) it does ensure all rates be under 1, otherwise there's a word that has ocurred in a class more than the combination of all words in that class + count of unique words in all other classes. This is even impossible in a corpus consisting only of repeated copies of one word.      
2) It does uniformly impact all probability calculations. 


Other Use Cases: 
- In a project, due to magnitude of values, I had log-transformed every data point. But that meant data points with 0 value were not interpretable (log 0 = -inf). There I had to boost every value by one unit. This case didn't require any special handling of any denominators.
