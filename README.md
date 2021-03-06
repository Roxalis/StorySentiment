# Short Story Sentiment Analysis (Syuzhet)
 
## Data Overview

The data was scraped from the web site ["The Short Storie Library"](https://americanliterature.com/short-story-library). On the date of ethical web scraping (October 2019) there were 4346 stories by 226 authors with a word count of between 8 and 51596 (size of a novella). Although the definition of a short story length is vague, in this analysis a short story is considered to be between 1000 and 10000 words long, resulting in a data set of 3573 stories and 209 authors (82 % of the total data). The median word count in this data subset is approx. 3500.

![distribution](images/distwordcount.jpeg)

## Data Exploration

### Authors and their stories 

When looking at the distribution of authors and their number of works, we find 17 authors with 50 or more written stories (table 1) and an overall distribution represented in the histogram (figure 2).

Table 1: Authors with 50 or more works in data set.

| author | works |
| ---- | ----|
|O. Henry | 	251 |
|Guy de Maupassant|	181|
|Anton Chekhov	|180|
|Jack London	|164|
|Rudyard Kipling	|161|
|W. W. Jacobs|	141|
|Mark Twain|	113|
|H.H. Munro (SAKI)|	111|
|Nathaniel Hawthorne|	80|
|Henry van Dyke|	69|
|William Dean Howells|	68|
|Ambrose Bierce|	66|
|Edgar Allan Poe|	64|
|Mary E. Wilkins Freeman|	58|
|Kate Chopin|	54|
|P. G. Wodehouse|	54|
|Charles Dickens|	52|
|H. P. Lovecraft	|50|

According to this data, most authors are represented with only one to fifty stories.

![distribution](images/distauthorworks.jpeg)

### Parameter analysis

When we look at the relationship between word count and the number of unique number of words used by an author, then we find a positive correlation (see figure 3) with a downward trend. That means that the number of unique words used by any author increases slower than the total number of words used by that author.

![distribution](images/relwcuw.jpeg)

Another relationship of interest: reading ease and sentence length (word count per sentence). The following formula was used to calculate the Flesch Reading Ease Score:

206.835 - 1.015 * ( words / sentences ) - 84.6 * ( syllable count / words )

Theoretically, the correlation between these two parameters is negative; the longer the average sentence written the more difficult the text is to read (see figure 4).

![distribution](images/reresl.jpeg)

A selection of authors, each having written 10 or more stories as part of the data set, and their corresponding reading ease score is given in table 2.

Table 2: A selection of authors and reading ease (re)

|author|min re|max re|mean re|re sd|
|----|----|----|----|----|
|Katherine Mansfield|	81.57	|93.61|	87.04|	3.21|
|	Philip K. Dick	|76.05|	91.91|	86.92|	4.24|
|	D. H. Lawrence|	81.88	|93.19|	86.73|	3.25|
|	Ellis Parker Butler	|66.79|	92.00|	84.22|	7.55|
|	W. W. Jacobs	|74.40|	93.24|	84.14|	4.17|
|...||||
|	William Butler Yeats|	38.67|	76.69|	63.35|	11.50|
|	H. P. Lovecraft	|41.12	|84.55|	60.81|	7.58|
|	Edgar Allan Poe|	42.69|	84.13|	60.35|	9.28|
|	Charlotte M. Yonge|	48.61|	76.80|	58.39|	5.96|
|	Washington Irving|	37.44|	70.41|	55.87|	8.84|

## Syuzhet Sentiment Analysis

The word *syuzhet* originated in Russian formalism and was coined by Vladimir Propp and Victor Shklovsky to describe one of two elements in narrative construction - the plot. The other element is the *fabula* (story). In other words, 
the fabula is the step by step narrative of the story ("the raw material of a story"), and syuzhet represents the organization of the story ("the way a story is organized").  
In the context of this analysis each short story was processed with the [syuzhet package](https://github.com/mjockers/syuzhet) developed by Matthew L. Jockers; this resulted in sentiment values of different lengths that were converted by discrete cosine transformation (DCT) into comparable data (X1 - X100 in the data sample).  

![Syuzhet sec cluster 1](images/seccluster_1.jpg)

The DCT-Values were then organized into groups by K-means clustering. The number of clusters (60) were determined with the Krzanowski-Lai Index out of a range of 2 to 400 clusters. 
The 60 clusters were organized into 8 parent-clusters (see figure above for parent-cluster 1).

Examples of sub-clusters are represented in the successive figures.

![Syuzhet sec cluster 1](images/cluster_35.jpeg)

![Syuzhet sec cluster 1](images/cluster_54.jpeg)

![Syuzhet sec cluster 1](images/cluster_23.jpeg)

![Syuzhet sec cluster 1](images/cluster_51.jpeg)

