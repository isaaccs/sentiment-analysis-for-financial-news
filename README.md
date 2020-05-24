# Sentiment analysis for financial news

Data is available on [Kaggle](https://www.kaggle.com/ankurzing/sentiment-analysis-for-financial-news).

You can find a Google Colab Notebook on this repo.

## Table of contents
* [Motivation](#Motivation)
* [Communications](#Communications)
* [Tools](#Tools)
* [Technologies](#technologies)
* [Help and Support](#Help)


## Motivation
Create tools for Text Analysis and project for Udacity Data Scientist Nanodegree

As a data scientist for an insurance company, I found myself working on text data.

Text is an unstructured data which can provide a lot of information. And doing a statistical analysis on it allows to draw some information.

That's why I decide to create tools for Text Analysis.

## Communications 
[Medium post here](https://medium.com/@isaaccohensabban/exploratory-data-analysis-for-natural-language-processing-2d5a98dfd12d?sk=116eb6bc304a3732b216bae7507437ca)

## Tools

### Wordcloud
A Wordcloud function is available by using [Wordcloud's package](https://github.com/amueller/word_cloud)
`
def plot_word_cloud(data,text='text',label=None,save=True):
  """ Inputs : Dataset, text colums,labels column
  Output : Word cloud for all the corpus and for each label"""
  word_cloud_data = " ".join([post for post in data[text] ])
  word_cloud_data = WordCloud(stopwords=STOPWORDS).generate(word_cloud_data)
  plt.figure()
  plt.imshow(word_cloud_data)
  plt.title('All corpus')
  plt.axis("off")
  plt.show()
  if save:
    plt.savefig('wordcloud.png', dpi=300)
  if label !=None:
    labels=data[label].unique()
    for i in range(len(labels)):
          word_cloud_data = " ".join([post for (post,label) in zip(data[text],data[label]) if label==labels[i]])
          word_cloud_data = WordCloud(stopwords=STOPWORDS).generate(word_cloud_data)
          plt.figure(i)
          plt.imshow(word_cloud_data)
          plt.title('{}'.format(labels[i]))
          plt.axis("off")
          `

![wordcloud for negative feelings](images/negative.png)

### Word Frequencies
A Word Frequencies function is available.
It prints the most commun word for each labels and remove the most commun word in some case.
`
def word_frequencies(data,word):

  c_unique = Counter()
  for ind in data.index:
      c_unique.update(Counter(set(data.loc[ind][word])))

  print('First 20 common words:\n')
  for word in c_unique.most_common(20):
      print(word[0],'-->', 'appeared in',word[1],'documents out of {} documents i.e.'.format(len(data)),np.round(100*word[1]/len(data),2),'%')
      `
      
![most commun word](images/word_frequencies.png)


![label frequencies](images/label_frequencies.png)
## Technologies
### Languages
Project is created with Python 3.6.9.

### Dependencies


* [NumPy](https://numpy.org)
* [Matplotlib](https://matplotlib.org)
* [pandas](https://pandas.pydata.org)
* [Wordcloud](https://github.com/amueller/word_cloud)
* [NLTK](https://www.nltk.org/)
* [re](https://docs.python.org/3/library/re.html)
* [collections](https://docs.python.org/2/library/collections.html)


## Help and Support

### Communication

* Mail: isaaccohensabban_at_gmail_dot_com
