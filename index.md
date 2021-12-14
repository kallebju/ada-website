# A study of quote similarity among politicians

## Introduction
In this project we investigate similarity among American politicians in different aspects. First, we perform a time correlation study to find politicians that tend to be quoted at the same time. This could for example suggest that these politicians focus on the same subject. Second, we expand the study by also comparing the actual content of the quotes made by the politicians, and compare the politicians by their quotes that they've made. Here we find interesting clusters of politicians that make similar quotes. Lastly, we study how both the time correlation and quote similarity have varied over the last three years in the QuoteBank dataset for an interesting pair of politicians, namely the former Secretary of State John Kerry and the current President Joe Biden.

## QuoteBank
Before we begin, let's gain some more insight into the data we use for the project.
In 2019, 3005 US policians were quoted. In total these were quoted 1'306'702 nr of times.
**Let's see the distribution of gender and party among the politicians in the dataset**

### Gender distribution in QuoteBank in 2019
{% include piechart.html %}
### Party distribution in QuoteBank in 2019
{% include piechart_party_2019.html %}

### Top words in the quotes in 2019
![Top words in 2019](/assets/wordcloud_2019.png)

## Quote similarity
In this part we cluster the concatenated quotes of single politicians in the 2019 partition of QuoteBank. The bag-of-words representation was reduced in dimensionality using NMF, to 50 dimensions.
The following figure shows the most heavily weighted words in the most important dimension for centroids in respective cluster.

<h3 style="text-align: center;">Heavily weighted words in clusters</h3>

![Top words in clusters](/assets/cluster_words_2019.png)

### Characteristics of the clusters
To see if the content of the quotes may tell us something about the gender and party of the quoted politician, we decided to plot the distribution of these two speaker properties in the following two figures.
<h3 style="text-align: center;">Gender distribution in clusters</h3>
![Gender in clusters](/assets/gender_hist_2019.png)
Here it is important to mention that the gender distribution of the entire dataset is heavily skewed before the clustering, as 82 % of the politicians are male. However, we can still note that some clusters have a greater share of males than others. One observation is that cluster 13 have a greater share of women compared to many other clusters, and this cluster is heavlily dependent on words relating to education, as can be seen in the word cloud figure above.
<h3 style="text-align: center;">Party distribution in clusters</h3>
![Party in clusters](/assets/party_hist_2019.png)
While the distribution of gender in the dataset was heavily skewed, the distribution of party is much more balanced, where Democratic, Republican and Other make up roughly a third of the quotes each, as can be seen in the pie chart in the Introduction section. Despite of this, the distribution within the clusters vary quite a lot. Cluster 13, which was mentioned above, include a majority of Democratic politicians. This differs from cluster 10 for example, which includes a majority of Republican speakers. This cluster is heavily dependent on words such as "president", "impeachment", "administration" etc.

## Time correlation
In this part, we focus on quotes as time series indicating the number of weekly quotes by US politicians.
#### 50 Clusters distribution per year
![50 Clusters distribution per year](/assets/kshapeperyear.png)

### Methods
We have therefore extracted from the database the different aliases by American politicians in order to search and extract, for a given year, all the dates of the quotations. We thus create annual time series associated to each politician.
#### K-Shape
In order to cluster all these time series, we quickly noticed that the use of K-means was inadequate. The algorithm systematically put the vast majority of time series in a single cluster.
We then looked at a clustering method adapted to time series, based on the concept of cross-correlation between signals: K-Shape.
The cross-correlation is itself based on a convolution between signals and allows to analyze the similarity between time signals ( as a distance), despite a temporal shift between them.
#### Choice of the number of cluster
![Cluster Kshape Curve](/assets/clusterkshapecurve.png)

According to this curve, we should take a number of clusters in the range of 40~50. We have chosen the number of 50 clusters arbitrarily in this range.
### Characteristics of the clusters
We begin by analyzing the gender distributions by cluster each year : 
![Gender distribution by years and cluster](/assets/gender.png)

82% of the politicians in the database are men, this inequality can be found within the clusters, a large part of which is exclusively male.

Then, we analyse the US politican party distributions by cluster each year : 
![Party distribution by years and cluster](/assets/party.png)

The proportion of Democrats and Republicans in the clusters each year seems to remain stable. However, there has been an increase in the number of party categorized as "other" here

#### Analysis of recurring politicians in the Joe Biden cluster
We put the year 2020 as a reference for Joe Biden and we looked to compare politicians belonging to the same cluster as him :
![Number of recurrent politicians with Biden](/assets/number_of_recurrent_politicians_with_Biden.png)

Note that the curve representing the number of politicians in Joe Biden's cluster common to his 2020 cluster is clearly increasing.
Upon further analysis, the number of politicians in Joe Biden's cluster each year is actually increasing as well. This explains the shape of the curve.
Even so, upon analysis, we find a certain stability in the population of Joe Biden's cluster in recent years.

We noticed that Joe Biden and John Kerry never belong to the same cluster. However, we analyzed the cross-correlation of Joe Biden and Kerry over the years and compared to their auto-correlation as references :
![Crosscorrelation between Biden and Kerry](/assets/crosscorrelation.png)

The cross-correlation of the two time series shows that they are not very far apart.
