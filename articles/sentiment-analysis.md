---
Question ? | Answer ! |
--- | --- |
writer: Manisha - MCA 1st year
Editor: Jatin
Status: Review Complete
Plagiarism: Heavy 57% [Report link](./plag_reports/plag_sentiment.pdf)
Content: General Overview and challenges. content is good. 
Verdict: Relevance to CES is doubtful. Can add to magazine as last resort. Will need to remove plag before adding.
---

# Sentiment Analysis

## Overview

With the growing popularity of websites like Amazon.com and Epinion.com where people can state their opinion on different products and rate them, the internet is replete with reviews, comments, and ratings. People have always had an interest in what other people think, or what their opinion is. With more products to judge, increasing number of people are using these websites to express their opinion. 
Sentiment Analysis deals with mining such data and aims to determine the attitude of the public towards some topic or to determine the overall contextual polarity and emotional reaction to a product. With social media channels like Facebook, Twitter, and LinkedIn, it is becoming increasingly feasible to automate and gauge what the public opinion is on a given topic.

The Opinion mining systems analyze unstructured data and observe which part can contribute to collect opinions, and who has written these reviews. It analyzes each word of opinion and classifies whether it is positive, negative or neutral. 

## The Classification can be done at many levels.

### Document or Sentence Level: 
It aims to classify sentiment expressed in each sentence. The first step is to identify whether the sentence is subjective or objective. If the sentence is subjective, it will determine whether the sentence expresses positive or negative opinions. Example Processing Individual Sentences
•   ( ) I bought an iPhone a few days ago.
•   (+) The touchscreen was really cool. 
•   (+) The voice quality was clear too. 
•   (-) Although the battery life was not long.
•   (-) It was pretty expensive as well.

However, there is no fundamental difference between document and sentence level classifications because sentences are just short documents. Document Classification, however, assumes that each document focuses on a single object and contains opinions from a single opinion holder.
Classifying text at the document level or at the sentence level does not provide the necessary detail needed opinions on all aspects of the entity which is needed in many applications, to obtain these details; we need to go to the aspect level.

### Aspect or Feature Level: 
Aspect Level Analysis aims to classify the sentiment with respect to specific aspects of entities.  The first step is to identify the entities and their aspects. The opinion holders can give different opinions on different aspects of the same entity. Example, iPhone User Review from above.
Quintuples: 
(Touchscreen …. Positive)
 (Voice Quality….. Positive) 
(Battery Life ….. Negative) 
(Price ….. Negative)

## Approaches 

### Machine Learning Approach - 
Machine learning approach relies on famous ML algorithms to solve it as a regular text classification problem that makes use of syntactic and linguistic features.

### Lexicon-Based Approach - 
Opinion words are employed in many sentiment classification tasks. Positive opinion words are used to express some desired states, while negative opinion words are used to express some undesired states. There are also opinion phrases and idioms which together are called opinion lexicons.           

## Challenges 
The human language can be complex for ML systems to interpret. 

- Grammatically Incorrect Words:  There are many approaches that analyze sentiments but hardly any work accomplished on grammatical errors. The results of sentiment analysis can be improved if these types of errors can be mapped to correct words.

- The order of words can add even more confusion. Example,
“I currently use the Nikon D90 and love it, but not as much as the Canon 40D/50D. I chose the D90 for the video feature. My mistake.”

- Subjective to people - Often sentences describe the success or failure of one side relative to another side. for example,
‘Yay! France beat Germany', ‘Supreme court judges in favor of gay marriage’. If one supports France, gay marriage, then these events are positive, but if one supports Germany, and opposes gay marriage then these events can be seen as negative.

- Neutral reporting of valenced information: If the speaker does not give any indication of her own emotional state but describes valenced events or situations, then it is unclear whether to consider these statements as neutral reporting or whether to assume that the speaker is in a negative emotional state. Example: “The war has created millions of refugees.”

- Sarcasm and ridicule: Sarcasm and ridicule are tricky from the perspective of assigning a single label of sentiment because they can often indicate a positive emotional state of the speaker (pleasure from mocking someone or something) even though they have a negative attitude towards someone or something.

## Conclusion

Sentiment Analysis is being used in real time in chat assistant. Blah Blah.
