# Chicago-Residents-Relocation-Analysis
## Executive Summary
People are leaving Illinois in droves. For the past five
years, Illinois population has declined by 157,000
residents. Making it one of only two state(The other is
West Virginia) to lose people over the past decade.
For this project, I dive into all the news articles for the past
few month to see what is the reason of this and found
some interesting thoughts. During this horrible pandemic,
Chicago has became the new epic center for the past
month and the lack of testing is driving people leaving the
city. Also, state’s high taxes and its unfunded pension
liability, lack of investment in education and infrastructure
are also the major factors that make people leave Illinois.

So what can government to do to make people love to live
in Illinois again? I will walk you thought this project and
draw the conclusion at the end of the project.
## Data Preparation
1. Only extract the dataset
that related with the
population issues
2. Isolate the different
sentiment in the middle of
the analysis process
3. Convert to lower case,
remove stopwords,
punctuation, number by
using regex
## Detect Major topics
1. Use Lemmatization to get the most common words in the news

2. Use textList.concordance get the insight of some sample articles
  a. It shows that the word ‘black’ comes around population quite often
  b. Black population increase or decrease might be an important factor
3. Use N-gram to find contiguous sequence of n items from a given sample of text or speech
  a. Help us to get the idea of the context
  b. n=2, top 5: Public health, Cook County, Pritzker Said, New York, Health Care
    i. Public health has been a hot topic for the past couple of months
    ii. Governor Pritzker plays a very important rule
  c. n=3, top 5: Depart public health, Mayor lori lightfoot, illinois department public, cook county jail, chicago mayor lori
    i. Cook county jail rings an alert that maybe the criminal issues could be one of the reason people leave
  d. Target N-gram by using population as the key word
    i. n=3 Top 5: county population census, significant percentage population, percentage population underserved, population underserved christmas, jail population dropped
    ii. It shows that Chicago is a city that have a diverse group of people,
    iii. Due to covid the jail population has dropped



