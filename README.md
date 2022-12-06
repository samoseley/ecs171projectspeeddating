# Speed Dating

## Abstract (Complete Introduction)

We will be exploring the [Speed Dating dataset](https://www.kaggle.com/datasets/whenamancodes/speed-dating) provided on Kaggle. The dataset contains data from a speed dating experiment where participants answered questions relating to dating behavior and qualities of a partner, and whether there was a match between the partners. We are interested in exploring if perceived interest from a partner increases the likelihood of matching with them. Using the attributes for ranking hobbies, we also want to look at shared interest between partners and see if having more shared interests increases the chance of a match. We would also like to see if a participant’s rating of themselves on attractiveness, intelligence, humor, ect. affects match probability. The data set consists of over 190 different attributes relating to 2 subjects (people), indicated as self and partner. The types of attributes range from binary, continuous, scaler, and categorical. The attributes cover the subjects’ hobbies, demographics, personal information, and interest in each other. Our target attribute is whether or not the two subjects are a match. With this data set we will start out by encoding many of the categorical features, for example, yes or no questions will be converted to 1 for yes and 0 for no. From there if the data is not normal we will scale it from zero to one using the MinMax method. Furthermore, we will combine features, drop features and create new features to isolate and analyze the specific data needed to answer our hypotheses. With the preprocessed data, we will explore supervised learning models like linear regression, logarithmic regression and SVM to explore which factors make someone more likely to be a match. We will take a close look at correlation matrices and coefficients produced by these models to evaluate which features were the most influential or if they did not have any influence at all. Our goal in evaluating the dataset is to determine whether or not a confident person is more likely to find a match, whether a match is more likely if both parties share interests, and how good people are at judging what the other person thinks of them.




## introduction
%%TODO :: Create an intro paragraph just talking about why we chose our project? What was interesting about the topic? Why is it important to have an accurate model for this subject/data?



## Methods
### **Data Exploration**
The columns we are focusing on are: percieved interest, sharedinterestso, sharedinterestpartner, interestscorrelate, attractive, sincere, intelligence, funny, and ambition. Of these columns, the ones relating to assessing oneself are skewed low as a result of people overvaluing themselves we will normalize features and drop columns to evaluate our hypotheses.

### **Model 1: Evaluating Personal Perception**
#### **_Hypothesis_**
We hypothesize that a person's perception of themselves along with their expectations of a partner play a key role in creating a match in speed dating.
#### **_Preprocessings_**
Features relating to personal perception like personal ratings of one's own attractiveness, sincerity, intelligence, fun, ambition and shared interest and personal ratings of expectations of a partner are kept for evaluation of our hypothesis. Some demographic information like age, race and gender are also kept. Then observations containing null or empty data values are dropped from the dataset, which is not a huge issue because our dataset is very big. Lastly the data is normalized in preperation of running the logistic regression model.
#### **_Logistic Regression Model_**
The data is split train:test in 75:25 and then run through a logistic regression model. A classification report and model coefficients are produced. Finally, mean-squared-error was calculated. 

%% TODO :: Add some code blocks?
``` print("hello world!") ```


### **Model 2: [model_name]**
#### **_Hypothesis_**
%% TODO :: Write the hypothesis associated with this model
#### **_Preprocessing_**
%% TODO :: What preprocessing did we do for this model
#### **_Model_**
%% TODO :: The basic process of creating the model with important code blocks (Nothing about why, results, or conclusion)
``` print("hello world!") ```


### **Model 2: [model_name]**
#### **_Hypothesis_**
%% TODO :: Write the hypothesis associated with this model
#### **_Preprocessing_**
%% TODO :: What preprocessing did we do for this model
#### **_Model_**
%% TODO :: The basic process of creating the model with important code blocks (Nothing about why, results, or conclusion)
``` print("hello world!") ```



## **Results**
### **Model 1: Evaluating Personal Perception**
The classification report shows the model's accuracy to be around 83%-85% which is quite good. The mean-square-error results shows no signs of overfitting or underfitting. We achieved a precision of 0.57 and recall 0.33, indicating that the model was less successful with identifying the true matches.

%% TODO :: Add figures and little more about results [NO exploration]

Classification report: https://colab.research.google.com/drive/1u627U9eaXVYpmNcxioSJax0oVLrmV6P7#scrollTo=p4SHA0Gqi5dA&line=1&uniqifier=1
>Testing Precision & Recall
>              precision    recall  f1-score   support
>
>        0.0       0.88      0.95      0.91      1214
>        1.0       0.57      0.33      0.42       240
>
>   accuracy                           0.85      1454
>  macro avg       0.72      0.64      0.67      1454
>weighted avg       0.83      0.85      0.83      1454

### **Model 2: [model_name]**
%% TODO :: Your final model and final results summary (Figures, results, data) [NO exploration]


### **Model 2: [model_name]**
%% TODO :: Your final model and final results summary (Figures, results, data) [NO exploration]



## **Discussion**
### **Model 1: Evaluating Personal Perception**
A logistical regression model was chosen because we are evaluating how personal perception features influence the occurance of a match which is a yes/no binary variable. MSE was calculated to evaluate testing and training error which showed no evidence for overfitting or underfitting. The classification report was produced to evaluate the accuracy of the model, and the model coefficients were produced to evaluate the importance of specific personal perception features in determining match. As stated in results, the model's accuracy hovered around 83%-85%. As for specific features, A person's decision (the 'dec' feature) regarding a match was the strongest indicator of match which is not surprising. However, how much the person rated themselves in terms of fun and how they guessed how much the partner liked them also contributed significantly to the match value. When not considering 'dec' the importance of the other features can be more readily analyzed. Personal perception of fun and how much the person thought the partner liked them still contributed significantly to match value. Additionally, how much the person liked the partner and how they percieved their own attractiveness become more important. It should be noted that there is more data for a no-match compared to a yes-match and the no-match had a greater accuracy. An interesting next step after this evaluation would be to see if different genders, ages or races are more or less impacted by their personal perception based on the value of "match".

%% Stuff to add: Talk about the good and bad of the model. 


### **Model 2: __________**
%% TODO :: Discuss why you did what you did. Your thought process from beginning to end. Explore the results and what they infer. Discuss everything good about the model. Dicuss what is wrong with the model. What would you fix if you were to do it again.


### **Model 3: __________**
%% TODO :: Discuss why you did what you did. Your thought process from beginning to end. Explore the results and what they infer. Discuss everything good about the model. Dicuss what is wrong with the model. What would you fix if you were to do it again.


### **Comparing Models**
%% TODO :: Compare the three models to each other. What are the similarities. What are their distinct differences. Does each model have a stength/weakness? Do some predict better than others. Why? Which model is the best.  




## **Conclusion**
%% TODO :: Concluding statements. Everything you want to say that isn't already in the other sections. 




## **Collaboration**
%% TODO :: Write a collaboration statement saying did everyone collaborate well. Was there a leader? a Coder? a writer?

Example contributions:
    Coding, writing, providing feedback, setting up meetings/github/discord, submissions, helping other members, managing who works on what, etc.  
        Any non-participants write :: (Did not participate)

Ashton Coates:
    Uploading the data, assisting with data exploration, building and evaluating the KNN model, making results reproducible.

Thomas Guelker: 
    Contribution.

Shobha Khanna: 
    Contribution.

Sydney Moseley: 
    Contribution.

Rishika Roy: 
    Contribution.

Garrett Sandzimier: 
    Contribution.
