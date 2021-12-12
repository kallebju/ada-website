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

## Time correlation


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


### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/kallebju/ada-website/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
