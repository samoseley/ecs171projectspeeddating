# Speed Dating

## Abstract (Complete Introduction)

We will be exploring the [Speed Dating dataset](https://www.kaggle.com/datasets/whenamancodes/speed-dating) provided on Kaggle. The dataset contains data from a speed dating experiment where participants answered questions relating to dating behavior and qualities of a partner, and whether there was a match between the partners. We are interested in exploring if perceived interest from a partner increases the likelihood of matching with them. Using the attributes for ranking hobbies, we also want to look at shared interest between partners and see if having more shared interests increases the chance of a match. We would also like to see if a participant’s rating of themselves on attractiveness, intelligence, humor, ect. affects match probability. The data set consists of over 190 different attributes relating to 2 subjects (people), indicated as self and partner. The types of attributes range from binary, continuous, scaler, and categorical. The attributes cover the subjects’ hobbies, demographics, personal information, and interest in each other. Our target attribute is whether or not the two subjects are a match. With this data set we will start out by encoding many of the categorical features, for example, yes or no questions will be converted to 1 for yes and 0 for no. From there if the data is not normal we will scale it from zero to one using the MinMax method. Furthermore, we will combine features, drop features and create new features to isolate and analyze the specific data needed to answer our hypotheses. With the preprocessed data, we will explore supervised learning models like linear regression, logarithmic regression and SVM to explore which factors make someone more likely to be a match. We will take a close look at correlation matrices and coefficients produced by these models to evaluate which features were the most influential or if they did not have any influence at all. Our goal in evaluating the dataset is to determine whether or not a confident person is more likely to find a match, whether a match is more likely if both parties share interests, and how preferences differ by gender.




## introduction
Dating sites like Tinder, Bumble, EHarmony, etc. all have algorithms that are suppose to match two people as potential partners based soley on self-reported attributes. The importance of these algorithms' accuracy is at an all time high due to the fact online dating (speed dating) is the number one way adults are meeting in today's society.

Our group decided to analyze one of these algorithms to determine which attributes were most important when it comes to matching two potential people together. This topic was interesting to us because speed dating is a prominent aspect of most young adult lives today, and we wanted to understand more about what makes two people a match.

The importance of functional, accurate models that can analyze such algorithms cannot be overstated. By analyzing and determining important attributes in speed dating, companies such as Tinder, Bumble, EHarmony, etc. can more accurately match compatible partners together, and eliminate the excess uncompatible matches to create a more streamline process. 



## Methods
### **Data Exploration**
The columns we are focusing on are: percieved interest, sharedinterestso, sharedinterestpartner, interestscorrelate, attractive, sincere, intelligence, funny, and ambition. Of these columns, the ones relating to assessing oneself are skewed low as a result of people overvaluing themselves. We will normalize features and drop columns to evaluate our hypotheses.

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
We hypothesize that percieved shared interests and overlap in reported interests will both have a significant positive impact on a person's decision
#### **_Preprocessing_**
We kep features related to shared interests such as percieved shared interest, reported interest correlation, and shared interest importance as well as decision and gender. We dropped any rows that had an invalid value in any of those columns and normalized the data. We created a [correlation map](https://colab.research.google.com/drive/1uPjPb_UVmOe4U9IjOXxzJ1T5Y1xSZmcT#scrollTo=AuGS2nfzbDHy&line=2&uniqifier=1) of the remaining variables.
#### **_Model_**
The data is split train:test in 75:25 and then run through a logistic regression model. A classification report and model coefficients are produced. Finally, mean-squared-error was calculated. 


### **Model 3: [model_name]**
#### **_Hypothesis_**
%% TODO :: Write the hypothesis associated with this model
#### **_Preprocessing_**
%% TODO :: What preprocessing did we do for this model
#### **_Model_**
%% TODO :: The basic process of creating the model with important code blocks (Nothing about why, results, or conclusion)
``` print("hello world!") ```





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


### **Model 3: [model_name]**
%% TODO :: Your final model and final results summary (Figures, results, data) [NO exploration]



## **Discussion**
### **Model 1: Evaluating Personal Perception**
A logistical regression model was chosen because we are evaluating how personal perception features influence the occurance of a match which is a yes/no binary variable. MSE was calculated to evaluate testing and training error which showed no evidence for overfitting or underfitting. The classification report was produced to evaluate the accuracy of the model, and the model coefficients were produced to evaluate the importance of specific personal perception features in determining match. As stated in results, the model's accuracy hovered around 83%-85%. As for specific features, A person's decision (the 'dec' feature) regarding a match was the strongest indicator of match which is not surprising. However, how much the person rated themselves in terms of fun and how they guessed how much the partner liked them also contributed significantly to the match value. When not considering 'dec' the importance of the other features can be more readily analyzed. Personal perception of fun and how much the person thought the partner liked them still contributed significantly to match value. Additionally, how much the person liked the partner and how they percieved their own attractiveness become more important. It should be noted that there is more data for a no-match compared to a yes-match and the no-match had a greater accuracy. The imbalance in the dataset may also explain the low recall score, which indicates that the model had rather poor perfomance with correctly predicting yes-matches. Futhermore, if we want to use personal perception to predict a match it would be beneficial to explore an artifical neural net compared to a simple logistic regression because our ANN had better recall in predicting matches compared to our logistic regression.An interesting next step after this evaluation would be to see if different genders, ages or races are more or less impacted by their personal perception based on the value of "match".



### **Model 2: Exploring Shared Interests**
We chose to use a logistical regression model as our response variable was decision which is a boolean variable. We used decision over match in this case as we this would allow us to look at whether a given person is more likely to respond yes given whether they percieve their interests as matching their partners without having to account for their partners response. Our model achieved around 69% accuracy with percieved interests matching being weighted far above the other variables. Interestingly we saw very little correlation between percieved interests matching and how closely their reported interests matched their partners as well as very little correlation between similarity of reported interests and decision. This is likely due to how the data was generated as each person was asked to rate their interest in a number of activities and those numbers were compared which is a very inaccurate way to gauge how similar two peoples interests are. The precision and recall scores were close to the overall accuracy of the model, indicating that the ability of the model to predict the participant's decision was not siproportionate. We also split the data up by gender to see if either gender was more swayed by similar interests than the other. We observed very similar coefficients in the two models but slightly higher accuracy for women than men. However that does not necessarily mean the women participants were more swayed by similar interests, as the improvement was reflected in the precision and recall of 'no' responses. This could also mean that the model simply performed better if women were more likely to decide 'no', and so the model was able to improve simply by returning 'no' more often. As such, we can not say whether the genders care more or less about similar interests. A possible next step for further investigation could be to compare the importance of shared interests in predicting a match decision across different hobbies/activities that participants are involved in.


### **Model 3: __________**
%% TODO :: Discuss why you did what you did. Your thought process from beginning to end. Explore the results and what they infer. Discuss everything good about the model. Dicuss what is wrong with the model. What would you fix if you were to do it again.


### **Comparing Models**
%% TODO :: Compare the three models to each other. What are the similarities. What are their distinct differences. Does each model have a stength/weakness? Do some predict better than others. Why? Which model is the best.  




## **Conclusion**
%% TODO :: Concluding statements. Everything you want to say that isn't already in the other sections. 




## **Collaboration**
As a whole, the team worked well together. We communicated entirely through discord, both call and direct message. The work was split relatively evenly; however, some team members took more responsability than others. There were three coders who each worked on one model by themselves, but everybody would provide feedback and peer-review when needed. Everybody for the most part took part in writing, some more than others; However, everybody looked over each other's work to ensure correctness and readability. Below is a list of individual names and their contributions to the project:

Ashton Coates:
    Uploading the data, assisting with data exploration, building and evaluating the KNN model, making results reproducible.

Thomas Guelker: 
    Worked on abstract, made edits to model 1 code, wrote code and writeups for model 2.

Shobha Khanna: 
    Worked on the abstract, created the correlation matricies for data exploration and coded the logistic regression model for evaluating the personal perception hypothesis. Wrote the analysis and conclusion of model 1 and helped facilitate and direct communication within the group.

Sydney Moseley: 
    Worked on the abstract, created pairplots for data visualization, assisted in preprocessing data, and coded and evaluated the ANN model.

Rishika Roy: 
    Worked on abstract, assisting construction of hypotheses, assisting data exploration, writing parts of methods, results, and discussion for model 1 and 2

Garrett Sandzimier: 
    I wrote a portion of the abstract. I provided feedback to team members regarding important attributes and what needed to get done. I created a skeleton/outline for the README.md to make it easier for my team members to simply write the needed information in each section. I wrote the Introduction and Collaborative statement for the write-up. I also took an already written paragraph for model1 (not written by me) and seperated it into the apppropriate locations in the write-up. 
