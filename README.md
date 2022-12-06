# Speed Dating

## Abstract (Complete Introduction)

We will be exploring the [Speed Dating dataset](https://www.kaggle.com/datasets/whenamancodes/speed-dating) provided on Kaggle. The dataset contains data from a speed dating experiment where participants answered questions relating to dating behavior and qualities of a partner, and whether there was a match between the partners. We are interested in exploring if different attributes are more important in decision making for each gender. Using the attributes for ranking hobbies, we also want to look at shared interest between partners and see if having more shared interests increases a person's decision making. We would also like to see if a participant’s rating of themselves on attractiveness, intelligence, humor, ect. affects match probability. The data set consists of over 190 different attributes relating to 2 subjects (people), indicated as self and partner. The types of attributes range from binary, continuous, scaler, and categorical. The attributes cover the subjects’ hobbies, demographics, personal information, and interest in each other. Our target attributes are whether or not the two subjects are a match and if one subject chose the other subject. With this data set we will start out by encoding many of the categorical features, for example, yes or no questions will be converted to 1 for yes and 0 for no. From there if the data is not normal we will scale it from zero to one using the MinMax method. Furthermore, we will combine features, drop features and create new features to isolate and analyze the specific data needed to answer our hypotheses. With the preprocessed data, we will explore supervised learning models like linear regression, logarithmic regression and SVM to explore which factors make someone more likely to be a match. We will take a close look at correlation matrices and coefficients produced by these models to evaluate which features were the most influential or if they did not have any influence at all. Our goal in evaluating the dataset is to determine whether or not a confident person is more likely to find a match, whether a person chooses a potential partner based on shared interest, and how preferences differ by gender.



## Introduction
Dating is a complex subject, as most preferences in a partner are subjective. This makes predicting a match between two people basically impossible. However, our group wants to attempt the impossible. Our interest in the subject of dating shouldn't be a suprise, as relationships are a main aspect of life itself. Our goal with our exploration into dating is to find which attributes affect a person's decision making the most, and which attributes have the highest influence in predicting a match. With the side goal of creating an accurate model to predict decision making and matching.

Before you venture into our exploration, one key destinction needs to be made, and that is between decision and match. Decision is the attribute depicting one subject choosing another (Ie. Swiping right or left on Tinder). Match is the attribute depicting if two subjects matched each other. (Ie. Both subjects swiped right on Tinder). 

One final disclaimer that the data only accounted for subjects who identified as male and female, so in this case we chose to make gender a binary variable.



## Methods
### **Data Exploration**
The columns we are focusing on are: percieved interest, sharedinterestso, sharedinterestpartner, interestscorrelate, attractive, sincere, intelligence, funny, and ambition. Of these columns, the ones relating to assessing oneself are skewed low as a result of people overvaluing themselves we will normalize features and drop columns to evaluate our hypotheses.

We displayed a [correlation heatmap](https://colab.research.google.com/drive/1u627U9eaXVYpmNcxioSJax0oVLrmV6P7#scrollTo=AuGS2nfzbDHy&line=1&uniqifier=1) on our chosen columns: 

Most notably, there appears to be a positive correlation between a person's ranking of their own qualities.

### **Model 1: Evaluating Personal Perception**
#### **_Notebook_**
https://colab.research.google.com/drive/1u627U9eaXVYpmNcxioSJax0oVLrmV6P7#scrollTo=NU895PVUbYLq&line=13&uniqifier=1
#### **_Hypothesis_**
We hypothesize that a person's perception of themselves along with their expectations of a partner play a key role in creating a match in speed dating.
#### **_Preprocessings_**
Features relating to personal perception like personal ratings of one's own attractiveness, sincerity, intelligence, fun, ambition and shared interest and personal ratings of expectations of a partner are kept for evaluation of our hypothesis. Some demographic information like age, race and gender are also kept. Then observations containing null or empty data values are dropped from the dataset, which is not a huge issue because our dataset is very big. Lastly the data is normalized in preperation of running the logistic regression model.
#### **_Logistic Regression Model_**
The data is split train:test in 75:25 and then run through a logistic regression model. A classification report and model coefficients are produced. Finally, mean-squared-error was calculated.
#### **_Artificial Neural Net Model_**
An artificial neural net (ANN) was run for comparision with the accuracy results of our logistic regression model. The ANN used two layers with a relu and then sigmoid activation function and it was run for eleven epochs.



### **Model 2: Exploring Shared Interests**
#### **_Notebook_**
https://colab.research.google.com/drive/1uPjPb_UVmOe4U9IjOXxzJ1T5Y1xSZmcT
#### **_Hypothesis_**
We hypothesize that percieved shared interests and overlap in reported interests will both have a significant positive impact on a person's decision.
#### **_Preprocessing_**
We kept features related to shared interests such as percieved shared interest, reported interest correlation, and shared interest importance as well as decision and gender. We dropped any rows that had an invalid value in any of those columns and normalized the data. We created a [correlation map](https://colab.research.google.com/drive/1uPjPb_UVmOe4U9IjOXxzJ1T5Y1xSZmcT#scrollTo=AuGS2nfzbDHy&line=2&uniqifier=1) of the remaining variables.
#### **_Model_**
The data is split train:test in 75:25 and then run through a logistic regression model. A classification report and model coefficients are produced. Finally, mean-squared-error was calculated. 


### **Model 3: Exploring Gender Differences**
#### **_Hypothesis_**
We hypothesize that there will be significant differences in the attributes that are more important between men and women.
#### **_Preprocessing_**
We split the dataframe in half, one with only male data and one with only female data. We also scaled the features so that their coefficients would be on the same scale, and compared more easily. The dependent variable for this analysis was dec (one's decision on whether to match or not) rather than match, since we were only interested in what the subject thought of their partner, not vice versa.
#### **_Model_**
Both male and female data were fit to logistic regression models, with the coefficients of these models then being graphed on a scatter plot for comparison.





## **Results**
### **Model 1: Evaluating Personal Perception**
The classification report shows the model's accuracy to be around 83%-85% which is quite good. The mean-square-error results shows no signs of overfitting or underfitting. We achieved a precision of 0.53 and recall 0.27, indicating that the model was less successful with identifying the true matches. Our ANN had a similar accuracy, but it had better recall at 0.50 and similar precision at 0.48 for identifiying true matches.

[Classification Report](https://colab.research.google.com/drive/1u627U9eaXVYpmNcxioSJax0oVLrmV6P7#scrollTo=p4SHA0Gqi5dA&line=2&uniqifier=1)
|        |  precision  |   recall    |  f1-score   |   support   |
| ------ | ----------- | ----------- | ----------- | ----------- |
| 0.0    |     0.87    |     0.95    |    0.91     |   1213      |
| 1.0    |     0.53    |     0.27    |    0.36     |    241      |
|accuracy|             |             |    0.84     |   1454      |


### **Model 2: Exploring Shared Interests**
The classification report shows the model's accuracy to be around 69% which is passable given the small number of columns we are analyzing. The mean-square-error results shows no signs of overfitting or underfitting. Our precisions and recall were comparable to the accuracy for both responses which means our model does not heavily favor one response over the other. [Coefficient analysis](https://colab.research.google.com/drive/1uPjPb_UVmOe4U9IjOXxzJ1T5Y1xSZmcT#scrollTo=zEMZpQ9Xc3v_&line=2&uniqifier=1) showed that percieved shared interests had the highest impact on the model predictions.

[Classification report](https://colab.research.google.com/drive/1uPjPb_UVmOe4U9IjOXxzJ1T5Y1xSZmcT#scrollTo=p4SHA0Gqi5dA&line=3&uniqifier=1)
|        |  precision  |   recall    |  f1-score   |   support   |
| ------ | ----------- | ----------- | ----------- | ----------- |
| 0.0    |     0.71    |     0.75    |    0.73     |    895      |
| 1.0    |     0.66    |     0.61    |    0.64     |     711     |
|accuracy|             |             |    0.69     |   1606      |


### **Model 3: Exploring difference in preference by gender**
The coefficients of this model indicate that attractiveness is more important to males compared to features like sincerity, fun, and intelligence than it was for women. However, the differences were not as drastic as we hypothesized. Error is high enough to indicate that further testing is required to make any real claims about these features.



## **Discussion**
### **Model 1: Evaluating Personal Perception**
A logistical regression model was chosen because we are evaluating how personal perception features influence the occurance of a match which is a yes/no binary variable. MSE was calculated to evaluate testing and training error which showed no evidence for overfitting or underfitting. The classification report was produced to evaluate the accuracy of the model, and the model coefficients were produced to evaluate the importance of specific personal perception features in determining match. As stated in results, the model's accuracy hovered around 83%-85%. As for specific features, A person's decision (the 'dec' feature) regarding a match was the strongest indicator of match which is not surprising. However, how much the person rated themselves in terms of fun and how they guessed how much the partner liked them also contributed significantly to the match value. When not considering 'dec' the importance of the other features can be more readily analyzed. Personal perception of fun and how much the person thought the partner liked them still contributed significantly to match value. Additionally, how much the person liked the partner and how they percieved their own attractiveness become more important. It should be noted that there is more data for a no-match compared to a yes-match and the no-match had a greater accuracy. The imbalance in the dataset may also explain the low recall score, which indicates that the model had rather poor perfomance with correctly predicting yes-matches. Futhermore, if we want to use personal perception to predict a match it would be beneficial to explore an artifical neural net compared to a simple logistic regression because our ANN had better recall in predicting matches compared to our logistic regression. An interesting next step after this evaluation would be to see if different genders, ages or races are more or less impacted by their personal perception based on the value of "match".



### **Model 2: Exploring Shared Interests**
We chose to use a logistical regression model as our target variable was decision which is a boolean variable. We used decision over match in this case as this would allow us to look at whether a given person is more likely to respond yes given whether they percieve their interests as matching their partner's without having to account for their partner's response. Our model achieved around 69% accuracy with percieved interests matching being weighted far above the other variables. Interestingly, we saw very little correlation between percieved interests matching and how closely their reported interests matched their partner's as well as very little correlation between similarity of reported interests and decision. This is likely due to how the data was generated as each person was asked to rate their interest in a number of activities and those numbers were compared which is a very inaccurate way to gauge how similar two peoples interests are. The precision and recall scores were close to the overall accuracy of the model, indicating that the ability of the model to predict the participant's decision was not disproportionate. We also split the data up by gender to see if either gender was more swayed by similar interests than the other. We observed very similar coefficients in the two models but slightly higher accuracy for women than men; However, that does not necessarily mean that women participants were more swayed by similar interests, as the improvement was reflected in the precision and recall of 'no' responses. This could also mean that the model simply performed better if women were more likely to decide 'no', and so the model was able to improve simply by returning 'no' more often. As such, we can not say whether the genders care more or less about similar interests. A possible next step for further investigation could be to compare the importance of shared interests in predicting a match decision across different hobbies/activities that participants are involved in.


### **Model 3: Exploring differences in preference by gender**
We chose to use logistic regression for this task as well because the dependent variable was boolean. The dependent variable, like in model 2, was one's decision on whether or not to match so that we could gauge one person's interest independent of whether the other said yes. The male model scored 75% accuracy, while the female model scored 78%. Our hypothesis that there would be differences was true; however, not as significant as we thought. We found that physical attraction played a more significant role in a male's decision compared to factors like intelligence or sincerity than it did for females. Further training data would likely be required to draw a more definitive correlation between this relationship. As one might expect, because there were more "no" decisions that "yes", the mode's recall on no was better than yes. However, it was close enough to conclude that it wasn't guessing "no" a disproportionate amount of the time. It would be interesting to see more objective data, as one's rating of their own opinions can be skewed. More objective data would allow for more concrete comparisons between males and females. Also, more relationships could be observed if we had data on who was partnered up, rather than just isolated data on what someone thought of a partner that we know nothing about.


### **Overall Exploration and Shortcomings**
Although our models for the most part were inaccurate, that doesn't mean they didn't provide valuable information in what our group was exploring. Remember from the introduction, that we wanted to understand what makes two people match, and what attributes influence a person's decision. Model 1 gave us data implying a person's confidence (self perception), or more specifically how fun and attractive one views themselves, to be the leading attribute in matching people. This model could also allow us to rank the attributes from most impactful to least impactful on matching. One fun fact regarding this ranking is that a person's ambition had the largest negative correlation for match, meaning you are less likely to match with anyone if you have low ambition. For model 3, it provided information regarding a person's decision, or more accurately which attributes are more important by gender. Finding, by no suprise, men look at attractiveness in a partner more than women (not by much), and women look at intelligence and sincerity more than men. Model 3 also highlighted a nice little fact that race was the least important attribute for both men and women when it came to decision. Overall, our biggest shortcoming was model 2. It provided very little information regarding someone's decision making due to lack of data and lack of accuracy. However, it allows us to improve our methodology for any future asperations. Mainly, rather than trying to predict decision making, we could test if shared interest has any influence on match. One final shortcoming of the data is in regard to the gender attribute, which did not include non-binary and others as an option.




## **Conclusion**
Our project shows that attributes such as self-confidence, common interests, and subconscious distinctions in how we perceive others dependent on gender, influence the likelihood of receiving a match when speed dating. One future direction would be to include more features in the models, such as 'expectednuminterestedinme' and 'expectednummatches' in model 1 and 'match' in model 3. Another future direction would be to work on increasing precision and recall for matches (1) in all three models. This could possibly be done by balancing the dataset to include an equal distribution of match and nonmatch data. We could also try implementing different models for binary classification to each hypothesis, such as k-Nearest Neighbors or Naive Bayes. A deeper dive into the dataset would also be beneficial, for there are still some ambiguous unused features such as 'attr1_1' and 'sinc1_1'. In addition, 'race' was previously encoded into integers, but it's unclear what race correlates to what number. If speed-dating companies considered the correlations we found between these features, they could see an increase in success rates. Although this project involves speed dating data, it may give us important insights into how we socialize and are attracted to others in varying contexts. Overall, it is incredible that we were able to quickly come to these conclusions using simple implementations of machine learning models. 




## **Collaboration**
As a whole, the team worked well together. We communicated entirely through discord, both call and direct message. The work was split relatively evenly; however, some team members took more responsability than others. Almost everyone was a coder who either individually or in a pair did their own model, but everybody would provide feedback and peer-review when needed. Everybody took part in writing, some more than others; However, everybody looked over each other's work to ensure correctness and readability. Below is a list of individual names and their contributions to the project:

Ashton Coates:
    Uploading the data, assisting with data exploration, built and analyzed the models for the question of whether there were differeces in preference by gender, and made sure all results were reproducible.

Thomas Guelker: 
    Worked on abstract, made edits to model 1 code, wrote code and writeups for model 2.

Shobha Khanna: 
    Worked on the abstract, created the correlation matricies for data exploration and coded the logistic regression model for evaluating the personal perception hypothesis. Wrote the analysis and conclusion of model 1 and helped facilitate and direct communication within the group.

Sydney Moseley: 
    Worked on the abstract, created pairplots for data visualization, assisted in preprocessing data, coded and evaluated the ANN model, and wrote conclusion.

Rishika Roy: 
    Worked on abstract, assisting construction of hypotheses, assisting data exploration, writing parts of methods, results, and discussion for model 1 and 2

Garrett Sandzimier: 
    I wrote a portion of the abstract. I provided feedback to team members regarding important attributes and what needed to get done. I created a skeleton/outline for the README.md to make it easier for my team members to simply write the needed information in each section. I wrote the Introduction, Overall Exploration and Shortcomings, and Collaborative statement for the write-up. I also took an already written paragraph for model1 (not written by me) and seperated it into the apppropriate locations in the write-up. I also proof read the document for grammatical and spelling errors. 
