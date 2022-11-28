# Speed Dating

## Abstract

We will be exploring the [Speed Dating dataset](https://www.kaggle.com/datasets/whenamancodes/speed-dating) provided on Kaggle. The dataset contains data from a speed dating experiment where participants answered questions relating to dating behavior and qualities of a partner, and whether there was a match between the partners. We are interested in exploring if perceived interest from a partner increases the likelihood of matching with them. Using the attributes for ranking hobbies, we also want to look at shared interest between partners and see if having more shared interests increases the chance of a match. We would also like to see if a participant’s rating of themselves on attractiveness, intelligence, humor, ect. affects match probability.The data set consists of over 190 different attributes relating to 2 subjects (people), indicated as self and partner. The types of attributes range from binary, continuous, scaler, and categorical. The attributes cover the subjects’ hobbies, demographics, personal information, and interest in each other. Our target attribute is whether or not the two subjects are a match. With this data set we will start out by encoding many of the categorical features, for example, yes or no questions will be converted to 1 for yes and 0 for no. From there if the data is not normal we will scale it from zero to one using the MinMax method. Furthermore, we will combine features, drop features and create new features to isolate and analyze the specific data needed to answer our hypotheses. With the preprocessed data, we will explore supervised learning models like linear regression, logarithmic regression and SVM to explore which factors make someone more likely to be a match. We will take a close look at correlation matrices and coefficients produced by these models to evaluate which features were the most influential or if they did not have any influence at all. Our goal in evaluating the dataset is to determine whether or not a confident person is more likely to find a match, whether a match is more likely if both parties share interests, and how good people are at judging what the other person thinks of the

## Data Exploration
The columns we are focusing on are: percieved interest, sharedinterestso, sharedinterestpartner, interestscorrelate, attractive, sincere, intelligence, funny, and ambition. Of these columns, the ones relating to assessing oneself are skewed low as a result of people overvaluing themselves we will normalize features and drop columns to evaluate our hypotheses.

## Model 1: Evaluating Personal Perception
### Preprocessing
Features relating to personal perception like personal ratings of an indvidual's own rating of their attractiveness, sincerity, intelligence, fun, ambition and shared interest and personal ratings of expectations out of speed dating is kept for evaluation of our hypothesis that personal perception plays a role in making a match. Some demographic information like age, race and gender are also kept. Then observations containing null or empty data values are dropped from the dataset, which is not a huge issue because our dataset is very big. Lastly the data is normalized is preperation for running the logistic regression model.
### Logistic Regression Model
A logistic regression model is used here to evaluate personal perception. This model was chosen because we are evaluating how personal perception features influence the occurance of a match which is a yes/no binary variable. The data is split train:test in 75:25 and then run through a logistic regression model. Mean-squared-error is used to evaluate testing and training error and there is no evidence for overfitting or underfitting. A classification report is produced to evaluate the accuracy of the model which hovers around 83%-85% which is quite good. Lastly model coefficients are produced to evaluate the importance of specific personal perception features in determining match.
### Model Conclusions
A person's decision (the 'dec' feature) regarding a match was the strongest indicator of match which is not surprising. However, how much the person rated themselves in terms of fun and how they guessed how much the partner liked them also contributed significantly to the match value. When not considering 'dec' the importance of the other features can be more readily analyzed. Personal perception of fun and how much the person thought the partner liked them still contributed significantly to match value. Additionally, how much the person liked the partner and how they percieved their own attractiveness become more important. Interestingly for both models the personal perception of ambition was paried with a negative coefficient which seems to indicate a higher personal perception ambition score reduces the probability of making a match. It should be noted that there is more data for a no-match compared to a yes-match and the no-match had a greater accuracy. This indicates that it is more likely that a low personal preception of attractiveness and fun results in a no-match then a high personal preception of attractiveness and fun results in a yes-match.
### Further Exploration
An interesting next step after this evaluation would be to see if different genders, ages or races are more or less impacted by their personal perception based on the value of "match".
