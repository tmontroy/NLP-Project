<B><h2>Project Title: <i>WHAT DID YOU SAY?!</h2></B></i>

<B>Team Members:</B> Nathan Kotlyn, Taylor Montroy

<B>Competition:</B> Natural Language Processing with Disaster Tweets

<B>Project Link:</B> https://www.kaggle.com/c/nlp-getting-started/overview

# __Introduction__
<h3><B>Project Summary </B></h3>
The use of social media, specifically Twitter, has increasingly become widespread across the globe. Users hundreds of miles apart are connected to eachother, allowing for instant communication. In times of emergency, tweets/posts can be used to spread awareness and communicate the events taking place. With that, organizations are shifting their focuses to programmatically monitoring these sites. However, often times these posts can be ambiguous and it is difficult to interpret whether or not they are comminucating a real emergency. <br><br>

<br><h3><B>Project Objective</h3></B>
Our objective is to use text mining (regualr expressions and topic modeling) to build a Neural Net Classifier, Logistic Regression, and a Support Vector Machine. We will pre-process the data, build a term document matrix, and run it through our classifiers.

<br><h3><B>Data Summary</h3></B>
The data is 10,000 observations which include tweet information, such as: tweet id, tweet text, location, tweet keyword, and a target variable (a '0' or '1' and only included in train dataset). 

<B>train.csv <i>(file)</i></b>
- <b>id</b> - a unique identifier for each tweet
- <b>text</b> - the text of the tweet
- <b>location</b> - the location the tweet was sent from (may be blank)
- <b>keyword</b> - a particular keyword from the tweet (may be blank)
- <b>target</b> - in train.csv only, this denotes whether a tweet is about a real disaster (1) or not (0)

<b>train.csv <i>(file)</i></b>
- <b>id</b> - a unique identifier for each tweet
- <b>text</b> - the text of the tweet
- <b>location</b> - the location the tweet was sent from (may be blank)
- <b>keyword</b> - a particular keyword from the tweet (may be blank)


# __Exploratory Analysis Stage (EDA)__
### __Visualizations__

<h4><B> TOP 5 KEY WORDS CLASSIFICATION DISTRIBUTION</h4></B> 
 
 ![image](https://user-images.githubusercontent.com/65474326/157345237-90437695-5600-4263-bd2f-d13b47c591d8.png)

<h4><B> DISASTER TWEET CLASSIFICATION WORD CLOUD</h4></B> 
 
![image](https://user-images.githubusercontent.com/65474326/157345507-ef495b2e-46ad-4ca8-be31-749ebe91df11.png)

<h4><B> Non DISASTER CLASSIFICATION WORD CLOUD</h4></B> 
 
![image](https://user-images.githubusercontent.com/65474326/157345620-fed9f524-97e4-48cc-8ac3-92973328af1e.png)
 
 <h4><B> TOP 5 KEY WORDS CLASSIFICATION DISTRIBUTION</h4></B> 
  
![LOCATIONS](https://user-images.githubusercontent.com/65474326/157345869-4c2601f2-d34b-4057-bb98-63a25ec11578.png)

<h3><B>Interesting Findings</h3></B>

<h4><B>Distribution of Classification Labels:</h4></B> 
 
In the training dataset, we can see that there is a somewhat fair distribution of the target labels (i.e., classification of tweets). There are about 4300 tweets classified as 'non-distaster' and about 3200 tweets classified as 'disaster.' This distribution of training set labels shows that we can use the dataset for building out model(s) as it isn't heavily skewed. 

<h4><B>Findings on Locations:</h4></B> 
We can also see that the location of the tweet does not matter to use. There is a mixture of both cities, states, and nations in the location column. For example, some tweets are located in 'USA' while others are more specifically labelled in 'Los Angeles, CA.' Also, there is the duplication of country names like 'USA' and 'United States.'

<h4><B>Findings on Keywords:</h4></B> 
Looking at the distribution of the keywords, we find that some words such as armageddon, siren, harm, and fear are more commonly found in the tweets classified as 'non-distaster.' This could be considered opposite of what we think we should find.

 <h4><B></B></h4>
  
<p>With our basic exploratory findings, it is clear that we should not use location or keyword in our models. They provide no-real indication on whether a tweet would be classified as a disaster or not. Thinking ahead, we are planning to use a document term matrix in our models to quantify contextually valuable terms int the dataset, so the keywords and locations variables would be of no use to the analysis.</p>

# __Data Cleaning Stage__

Labels were addeed to training and testing sets first so that we can split them back up prior to modeling to ensure the feature space of the term document matrix was the same size between the training and testing sets. 

The location and keyword columns were dropped since they have no use to the analysis. 

Regular expressions were used to remove to special characters, numbers, and punctuationthese provide no contextual wieght in classyfying a tweet is realted to a disaster.  

Hyperlinks and usernames were also removed as they also provide no contexutal value to predicting a disaster. 

Following, words that provide little to no value by themselves were removed, such as conjunctions of 'of', 'or', and 'not'. In addition, we reduced each work to its stem since a word can be in a tense, yet represent the same concept. 

Once the data, was cleaned the TfidfVectorizer function from the Sci-Kit learn library was used to generate the term document matrix. Which generated a feature space of 2985 different possible terms.

# __Modeling Stage__
 The data was then re-split into prior training and testing sets and passed into three different Machine Learing algorithms to find which one would be the best in classfying disaster related tweets. 






