/*
Writer - Manisha - MCA 1st year
*/

# Sentiment Analysis

Overview
With the growing popularity of websites like Amazon.com and Epinion.com where people can state their opinion on different products and rate them, the internet is replete with reviews, comments and ratings. People have always had an interest in what people think, or what their opinion is. Since the inception of the internet, increasing numbers of people are using websites and services to express their opinion. Mining such data to determine how people feel about your product, brand, or service, is called Sentiment Analysis. Generally speaking, Sentiment Analysis aims to determine the attitude of a speaker, writer, or other subject with respect to some topic or the overall contextual polarity or emotional reaction to a document, interaction, or event. With social media channels such as Facebook, LinkedIn, and Twitter, it is becoming feasible to automate and gauge what public opinion is on a given topic, news story, product, or brand.

The sentiment or Opinion mining systems analyze unstructured data and observe which part can contribute to collect opinions, and who has written these reviews. Sentiment analysis analyzes each word of opinion or phrase and classify, whether it is positive or negative or neutral. It gives the classification of opinion of a user

## Levels:

### 1.Document Level:
It aims to classify an opinion document as expressing a positive or negative opinion or sentiment. It considers the whole document a basic information unit (talking about one topic). A document (e.g., a review) based on the overall sentiment expressed by opinion holder. It assumes each document focuses on a single object and contains opinions from a single opinion holder. It considers opinion on the object as a whole.
Example -
My XYZ CAR was delivered yesterday. It looks faboulous. We went on a long highway drive the very second day of getting the car. It was smooth, comfortable and wonderful drive. Had a wonderful experience with family. Its an awesome car. I am loving it..!
User Sentiment?

### 2.Sentence Level: 
It aims to classify sentiment expressed in each sentence. The first step is to identify whether the sentence is subjective or objective. If the sentence is subjective, it will determine whether the sentence expresses positive or negative opinions. Sentiment expressions are not necessarily subjective in nature.
Example - 
Processing Individual Sentences
•	( ) I bought an IPhone a few days ago.
•	(+) It was such a nice phone.
•	(+) The touch screen was really cool. 
•	(+) The voice quality was clear too. 
•	(-) Although the battery life was not long, that is ok for me.
•	( ) However, my mother was mad with me as I did not tell her  before I bought the phone. 
•	(-) She also thought the phone was too expensive, and wanted me to return it to the shop.
. However, there is no fundamental difference between document and sentence level classifications because sentences are just short documents. Classifying text at the document level or at the sentence level does not provide the necessary detail needed opinions on all aspects of the entity which is needed in many applications, to obtain these details; we need to go to the aspect level.

### 3. Aspect/ Feature Level: 
It aims to classify the sentiment with respect to the specific aspects of entities. The first step is to identify the entities and their aspects. The opinion holders can give different opinions for different aspects of the same entity .
Example:
IPhone- User Review: 
I bought an IPhone a few days ago. It was such a nice phone. The touch screen was really cool. The voice quality was clear too. Although the battery life was not long, that is ok for me. However, my mother was mad with me as I did not tell her before I bought the phone. She also thought the phone was too expensive, and wanted me to return it to the shop.
Quintuples: 
(Phone …. Positive) 
(Touchscreen …. Positive)
 (Voice Quality….. Positive) 
(Battery Life ….. Negative) 
(Price ….. Negative)
Approach:
Machine Learning Approach:
 Machine learning approach relies on the famous ML algorithms to solve the SA as a regular text classification problem that makes use of syntactic and/or linguistic features.
Lexicon-Based Approach:Opinion words are employed in many sentiment classification tasks. Positive opinion words are used to express some desired states, while negative opinion words are used to express some undesired states. There are also opinion phrases and idioms which together are called opinion lexicon             

## Challenges:
The human language can be complex for machine based learning systems to interpret. For example, opinions can be expressed with sarcasm or irony, and the order of words can add even more confusion.
Take the following example:
“I currently use the Nikon D90 and love it, but not as much as the Canon 40D/50D. I chose the D90 for the video feature. My mistake.”
In this example, the author is conveying sarcasm; this can be hard for classifiers to process:
“After a whole 5 hours away from work, I get to go back again, I’m so lucky!”
  
For a classifier to process data and provide more accurate results, it must be trained.  This can be achieved by collecting training data.  Various sources can be used; one popular means is to use a corpus of movie reviews labeled as positive or negative.
2. Grammatically Incorrect Words:  There are many approaches that analyze sentiments but hardly any work accomplished on grammatical errors. The results of sentiment analysis can be improved if these types of errors can be mapped to correct words.

3. Success or failure of one side w.r.t. another: Often sentences describe the success or failure of one side w.r.t. another side—for example,‘Yay! France beat Germany3–1’, ‘Supreme court judges in favor of gay marriage’, and ‘the coalition captured the rebels’. If one supports France, gay marriage, and the coalition, then these events are positive, but if one supports Germany, marriage as a union only between man and woman, and the rebels, then these events can be seen as negative.
4. Speaker’s emotional state: The speaker’s emotional state may or may not have the same polarity as the opinion expressed by the speaker. For example, a politician’s tweet can imply both a negative opinion about a rival’s past indiscretion, and a joyous mental state as the news will impact the rival adversely.
5.Neutral reporting of valenced information: If the speaker does not give any indication of her own emotional state but describes valenced events or situations, then it is unclear whether to consider these statements as neutral unemotional reporting of developments or whether to assume that the speaker is in a negative emotional state(sad, angry, etc.). Example:
“The war has created millions of refugees.”

6.Sarcasm and ridicule: Sarcasm and ridicule are tricky from the perspective of assigning a single label of sentiment because they can often indicate positive emotional state of the speaker (pleasure from mocking someone or something) even though they have a negative attitude  towards someone or something.



