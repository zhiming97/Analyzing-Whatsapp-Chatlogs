from chatminer.chatparsers import WhatsAppParser
import nltk
nltk.download('stopwords')
from nltk.corpus import stopwords


parser_user2 = WhatsAppParser('WhatsApp Chat with xxx.txt')



parser_user2.parse_file_into_df()


import chatminer.visualizations as vis
import matplotlib.pyplot as plt


def displaychatdata(x):
    fig, ax = plt.subplots(8, 1, figsize=(10, 13))
    ax[0] = vis.calendar_heatmap(x, year=2015, cmap='Blues', monthly_border=True,ax=ax[0])
    ax[1] = vis.calendar_heatmap(x, year=2016, linewidth=0, monthly_border=True, ax=ax[1])
    ax[2] = vis.calendar_heatmap(x, year=2017, linewidth=0, monthly_border=True, ax=ax[2])
    ax[3] = vis.calendar_heatmap(x, year=2018, linewidth=0, monthly_border=True, ax=ax[3])
    ax[4] = vis.calendar_heatmap(x, year=2019, linewidth=0, monthly_border=True, ax=ax[4])
    ax[5] = vis.calendar_heatmap(x, year=2020, linewidth=0, monthly_border=True, ax=ax[5])
    ax[6] = vis.calendar_heatmap(x, year=2021, linewidth=0, monthly_border=True, ax=ax[6])
    ax[7] = vis.calendar_heatmap(x, year=2022, linewidth=0, monthly_border=True, ax=ax[7])
    plt.show()

def showwordcloud(x):
    fig, ax = plt.subplots(figsize=(15, 4))
    stop_words = set(stopwords.words('english'))
    irrelevantwords = ['these', 'are', 'stopwords', 'Media', 'omitted','need','got','liao','one','u','dont','de','hahaha','haha','hahah','ok','go','bro','wan','ya','wtf','lol','le','dun']
    irrelevantwords += stop_words
    kwargs={"background_color": "white", "width": 800, "height": 300, "max_words": 500}
    ax = vis.wordcloud(x, ax=ax, stopwords=irrelevantwords, **kwargs)
    plt.show()


#second person
displaychatdata(parser_user2.df)
showwordcloud(parser_user2.df)

#displaying the wordcloud on specific days
df = parser_user2.df
x = df.loc[df['datetime'] >= '2022-09']

#Generating Word Cloud For particular year 2022
from wordcloud import WordCloud
text = ''

stop_words = set(stopwords.words('english'))
irrelevantwords = ['first','say','see', 'come','these', 'are', 'stopwords', 'Media', 'omitted','need','got','liao','one','u','dont','de','hahaha','haha','hahah','ok','go','bro','wan','ya','wtf','lol','le','dun']
irrelevantwords += stop_words

for words in x.message.values:
    text += f" {words}"
wordcloud = WordCloud(
    width = 3000,
    height = 2000,
    background_color = 'white',
    max_words = 50,
    stopwords = irrelevantwords).generate(text)
fig = plt.figure(
    figsize = (13, 10),
    facecolor = 'k',
    edgecolor = 'k')
plt.imshow(wordcloud, interpolation = 'bilinear')
plt.axis('off')
plt.tight_layout(pad=0)
plt.show()
