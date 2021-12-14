# A study of quote similarity among politicians

## Introduction
In this project, we investigate similarities among American politicians in different aspects. First, we perform a study by comparing the actual content of the quotes made by the politicians, and compare the politicians by the quotes that they've made. Here we find interesting clusters of politicians that make similar quotes.

Second, we extend the study by also a time correlation study to find politicians that tend to be quoted at the same time. This could for example suggest that these politicians focus on the same subject. 

Lastly, we study how both the time correlation and quote similarity have varied over the last three years in the QuoteBank dataset for an interesting pair of politicians, namely the former Secretary of State John Kerry and the current President Joe Biden.

## QuoteBank
The main dataset used in this project is QuoteBank, which contains 178 million quotations together with the name of the speaker [1]. The dataset has been collected from news articles in English on the internet, from August 2008 until April 2020. We also use Wikidata for gaining additional information about the quoted individuals.

Before we begin, let's gain some more insight into the data we use for the project.
In 2019, 3005 US policians were quoted. In total these were quoted 1'306'702 nr of times. Below you can find the distribution of gender and party among the politicians in the dataset.

### Gender distribution in QuoteBank in 2019
{% include piechart.html %}
### Party distribution in QuoteBank in 2019
{% include piechart_party_2019.html %}

## Quote similarity
In this part we cluster the concatenated quotes of single politicians in the 2019 partition of QuoteBank, into 14 clusters. The bag-of-words representation was reduced in dimensionality using NMF, to 50 dimensions.
The following figure shows the most heavily weighted words in the most important dimension for a sampled politician in respective cluster.

<h3 style="text-align: center;">Heavily weighted words in clusters</h3>

![Top words in clusters](/assets/cluster_words_2019.png)

Interestingly, for each cluster, the sampled politician have different dimensions as their strongest dimension. Also the strongest words in each dimension seem to be related in many cases, for instance cluster 2 contain words such as "law", "constitutional" and "court", while cluster 8 contain words relating to education, such as "students", "skills" etc.
### Characteristics of the clusters
To see if the content of the quotes may tell us something about the gender and party of the quoted politician, we decided to plot the distribution of these two speaker properties among the clusters in the following two figures.
<h3 style="text-align: center;">Gender distribution in clusters</h3>
![Gender in clusters](/assets/gender_hist_2019.png)
Here it is important to mention that the gender distribution of the entire dataset is heavily skewed before the clustering, as 82 % of the politicians are male. However, we can still note that some clusters have a greater share of males than others. One observation is that cluster 13 have a greater share of women compared to many other clusters, and this cluster is heavily dependent on words relating to education, as can be seen in the word cloud figure above.
<h3 style="text-align: center;">Party distribution in clusters</h3>
![Party in clusters](/assets/party_hist_2019.png)
While the distribution of gender in the dataset was heavily skewed, the distribution of party is much more balanced, where Democratic, Republican and Other make up roughly a third of the quotes each, as can be seen in the pie chart in the Introduction section. Despite of this, the distribution within the clusters vary quite a lot. Cluster 13, which was mentioned above, include a majority of Democratic politicians. This differs from cluster 10 for example, which includes a majority of Republican speakers. This cluster is heavily dependent on words such as "president", "impeachment", "administration" etc.

### Case study: Joe Biden and John Kerry
Two politicians that are in the same cluster for the 2019 data was John Kerry and Joe Biden, who ended up in Cluster 10. These two individuals have a strong connection in terms of many attributes. For instance, both are members of the Democratic party and work within the absolute top of US politics. During the Obama administration, Joe Biden serverd as Vice President while John Kerry was Secretary of State. Following the Presidential Election in 2020, Joe Biden was elected as President and appoinded John Kerry as U.S. Special Presidential Envoy for Climate in his administration.
#### Similarity over years
Let's investigate how the similarity between Biden and Kerry has evolved over some years.

![Biden Kerry Quote Similarity](/assets/sim_graph.png)

Judging by the plot above the similarity has steadily increased from 2018 until 2020.
## Time correlation
In this part, we focus on quotes as time series indicating the number of weekly quotes by US politicians. Each politician is hence represented as a time series of the number of quotes for each week of one year. Following this, we apply a clustering algorithm to find groups of politicians that have high correlation among their time series.

**Let's check how many individuals that are assigned to each of the 50 clusters:**

![50 Clusters distribution per year](/assets/kshapeperyear.png)

We notice a largely predominant cluster each year, despite the fact that the clusters are better distributed the last 3 years.
However, the number of politicians in the other clusters is generally still reasonably large enough to allow for further analysis.

### Characteristics of the clusters
We begin by analyzing the gender distributions by cluster each year : 
![Gender distribution by years and cluster](/assets/gender.png)

82% of the politicians in the database are men, this inequality can be found within the clusters, a large part of which is exclusively male.

Then, we analyse the distribution party among the clusters each year : 
![Party distribution by years and cluster](/assets/party.png)

The proportion of Democrats and Republicans in the clusters each year seems to remain stable. However, there has been an increase in the number of party categorized as "other" here

### Case study: Joe Biden and John Kerry
#### Analysis of recurring politicians in the Joe Biden cluster
We put the year 2020 as a reference for Joe Biden and we looked to compare politicians belonging to the same cluster as him. The curve represent the number of politicians in Joe Biden's cluster common to his 2020 cluster :

![Number of recurrent politicians with Biden](/assets/number_of_recurrent_politicians_with_Biden.png)

Note that the curve is clearly increasing.
Upon further analysis, the number of politicians in Joe Biden's cluster each year is actually increasing as well. This explains the shape of the curve.
Even so, upon analysis, we find a certain stability in the population of Joe Biden's cluster in recent years.

#### Similarity over years
We noticed that Joe Biden and John Kerry never belong to the same cluster. However, we analyzed the cross-correlation of Biden and Kerry over the years and compared to their auto-correlation as references. This tells us how the similarity has evolved over the years.

![Crosscorrelation between Biden and Kerry](/assets/crosscorrelation.png)

The cross-correlation of the two time series shows that they are not very far apart.

## Conclusion
By comparing politicians by their quote similarity, it's possible to get some interesting insights. The strongest topics are different for all of the 14 clusters, and the most heavily weighted words within those topics seem to tell us something about the politicians included in that cluster. As mentioned above, there is one cluster where the most heavily weighted words are relating to education. By further analyzing the composition of the clusters we can get insights about the politicians that are included in the clusters. Within the previously described "education"-cluster, there is a greater share of women compared to other clusters, and also a majority of Democratic politicians. This suggests that politicians who focus on these topics in their quotes are more probable to be women and Democratic, compared to many other focus areas.

Moving on, we extended the study by also measuring the time correlation for the time of quoting. An interesting insight from this is that cluster seems to be pretty stable; we see that Joe Biden ends up in a cluster with the same politicians from 2018 until 2020.

Finally, we note that for both of the similarity measures we identify an increasing trend of similarity between Joe Biden and John Kerry from 2018 until 2020. As this trend is identified by two measures, it should indicate that these two politicians have become more similar during these years.

## References
[1] T. Vaucher, A. Spitz, M. Catasta, and R. West, “Quotebank: A
corpus of quotations from a decade of news,” in Proceedings
of the 14th ACM International Conference on Web Search
and Data Mining, ser. WSDM ’21. New York, NY, USA:
Association for Computing Machinery, 2021, p. 328–336.
[Online]. Available: https://doi.org/10.1145/3437963.3441760

This project was created by Kalle Bjurek, Lucas Braz, Pierre-Alain Durand and Clément Nicolle
