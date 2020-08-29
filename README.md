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
  * a. It shows that the word ‘black’ comes around population quite often
  * b. Black population increase or decrease might be an important factor
3. Use N-gram to find contiguous sequence of n items from a given sample of text or speech
  * a. Help us to get the idea of the context
  * b. n=2, top 5: Public health, Cook County, Pritzker Said, New York, Health Care
    * i. Public health has been a hot topic for the past couple of months
    * ii. Governor Pritzker plays a very important rule
  * c. n=3, top 5: Depart public health, Mayor lori lightfoot, illinois department public, cook county jail, chicago mayor lori
    * i. Cook county jail rings an alert that maybe the criminal issues could be one of the reason people leave
  * d. Target N-gram by using population as the key word
    * i. n=3 Top 5: county population census, significant percentage population, percentage population underserved, population underserved christmas, jail population dropped
    * ii. It shows that Chicago is a city that have a diverse group of people,
    * iii. Due to covid the jail population has dropped

## Sentiment Analysis
1. Separate dataset to positive sentiment and negative sentiment
* a. Positive sentiment Analyse helps to demonstrate why people want to move in
  * i. For example:Illinois is a beautiful place, University of Chicago is the most
famous school in Chicago, St. Patrick's Day celebration is amazing, illinois
ranks the 26th best states for elderly Americans
* b. Negative sentiment Analysis helps to demonstrate why people want to move
out
  * i. For Example: Violence in the south side of chicago, Covid-19 is
destroying African American Community, Does not have enough covid
testing, progressive income tax, Chicago police
  * ii. One specific topic came out of the analysis is specifically talking about
population decline problem in Chicago(Article title: ‘Illinois saw nation’s
worst population loss during the decade’), after did similar word analysis
on the specific text, it turns out that people do not have confidence in the
economy and a lot of people have really high debt. Those could be of the
reason they move out of the city.

## Topic Analysis
1. To get a better idea on how to label the data for the future usage, it is import to check the general
topics of the articles
* a. Use LDA topic model
* b. For 3 topic model
  * i. First topic: The first topic is about the safety concern of the community(Crime and jail issues) It also
covered the tax issues and some university issues
  * ii. Second topic: The second topic is mostly about Covid_19 and different methods government use to
tackle these difficulties, that includes the testing and cases numbers as well as death numbers
  * iii. Third topic: The third topic is mostly about the politics including joe baden, different police to the
jewish community and also some articles is talking about the voters.
* c. For 5 topic model
  * i. First topic: The first topic is mostly about Covid_19 and different methods government use to tackle
these difficulties, that includes the testing and cases numbers as well as death numbers
  * ii. Second topic: The second topic is more about the tax issues in Chicago and IL
  * iii. Third topic: The third topic is about the inmate and jail issues, some part of the group is talking about
government officials release some of the inmates in IL because of Covid
  * iv. Fourth topic:The fourth topic is talking about the minority including black and jewish community in
Chicago, how they impact the election results
  * v. Fifth topic: The fifth topic does not seems like a topic more like some random words.
  
## How to label the unstructured news articles?
1. Snorkel could be the solution
* a. From the previous analysis, we already have a decent idea on the major topics
* b. For this step I conclude the major topic and group it to 5 different classes
  * i. Tax: This group include the articles talks about the tax issues in the illinois and chicago area
  * ii. Safety: Since Chicago is a diverse city, racism is a huge problem. Thus, the violence caused by
racism is a big part of the Chicago problem. This group talks about the crime and violence as
well as discriminations issues happens in Chicago.
  * iii. Investment: As a city with a huge population, the education, manufacture and infrastructure
are things that people also really care about. I classify it as investment
  * iv. Health: Covid-19 is definite the major topic people talks about in 2020,also virus in general
could be the reason that driving people leave the place. I group it as health.
  * v. Weather: Chicago is famous for this cold weather, with that being said, cold weather could
also be a factor
  * vi. Other: Any other reasons can all classify as Others
* c. By setting up the labeling function, we can get a data set with 2524 Health Articles, 1846 Weather
Articles, 251 Safety Articles and 42 investment articles
* d. From this we are able to see that Health topic is the most popular topic for the past few week and the
weather comes at the second place, we can tell that weather plays a big role.
* e. The label data are also able to used in building a deep learning text classification model for the future
project.


## Entity Identification
1. Spacy is good for NER tasks
2. Separate Positive and Negative Articles to see the most common Entity for each group
3. Execute Entity on Organization(ORG), Nationalities or political groups(NORP) and Person
 * a. Most common Entity for For Health Issues :
  * i. Positive
1. ORG:Covid-19,Sanders, CNN, Pritzker, the Illinois Department of Public Health
2. NORP:Democratic, Americans, MeridianHealth( Government Healthcare Insurance Service)
3. Person: Lori Lightfoot, Prkitzker,Biden, Bernie Sanders
  * ii. Negative
1. ORG:Covid-19, State, Medicaid, CDC, PPE. It shows that people are disappoint on how local government handling this issues(Lack of PPE, CDC’s bad decisions
Etc.
2. NORP: African, American, Chicagoans, Illinoisans,
3. Person: Pritzker, Lori Lightfoot, Saint Anthony( Hospital Name), Rezin Garcia(Chicago Suntime Journalist)
 * b. Most common Entity for For Tax Issues :
  * i. Positive
1. ORG: Impact Advisors, Apple, Chicago Pacific Founders( Strategic Healthcare Investment Fund)
2. NORP: Democratic
3. Person: Allison Arwady( Chicago Public Health Commissioner), Lori Lightfoot, J.B. Pritzker(IL Governor)
  * ii. Negative
1. ORG:TW, AGI, Single-Family Homes,Congress, Labor Force Participation rate,
2. NORP: Trump
3. Person: John Kingner( policy analyst at the Illinois policy institute)
 * c. Most common Entity for For Safety Issues :
  * i. Positive
1. ORG:PediaStaff(full-service pediatric and school-based therapy staffing and recruitment specialist.)
2. NORP: Not Enough Data
3. Person: Not Enough Data
a. Lack of data shows the concern of the people to the Safety issue of IL
  * ii. Negative
1. ORG: CTA, CPD, FBI, the Democratic Party, McDonald, University
2. NORP: Americans, Democrates, Islamic,African American, Muslims, Trump
3. Person: Vam Dyke( Ex Police officer shoting Chicago teenager Laquan McDonald 16 times), Ramada (Hotel)
 * d. Most common Entity for For Investment Issues :
  * i. Positive
1. ORG: Associated Press ,Everstream( Internet Service Provider), The National Democratic Party
2. NORP: Democrats, Republican, American
3. Person: Merritt, Mao
  * ii. Negative
1. ORG: Navy, NYPD, FBI, NAACP, New York Times
2. NORP: American, African American, Jews, Hispanics
3. Person: Ilhan Omar(US Representative), D'Adrien Anderson and a lot of victim name of the local murder cases


## Conclusion
### Key reasons for the declining population
1. Public Health Issues during Pandemic(Lack of testing
for Covid-19)
2. Violence in the south side of chicago
3. Covid-19 is destroying African American Community
4. Progressive income tax
5. Some of the Chicago police are racist toward black
people
6. Cold weather
7. Declining birth rates
8. Long-standing Economic discrimination against black
residents
9. High Housing Costs
10. Lack of middle class jobs


## Recommendations
1. How the city / state can attract new businesses
* a. Lack of middle class jobs can be improved by bring
manufacturing company back to IL
* ab. Give more government funding for the south Chicago
to make it a safer place to attract business
* ac. Support family with more that 2 children
* ad. Decrease the business tax
2. Why businesses should stay in IL or move into IL?
* aa. They should stay in IL because Chicago is the world
famous financial harbor and there is a lot of
opportunities
3. Whey residents should stay in IL or move into IL?
* aa. Resident should stay in IL because the governor can
major have a good fame among local residents and
they are standing on the side of people
