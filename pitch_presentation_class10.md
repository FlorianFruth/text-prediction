Word Prediction - Pitch Presentation for Algorithm and ShinyApp for predicting the next word of a phrase
========================================================
author: F. Fruth
date: 2017/03/12
autosize: true

Introduction
========================================================

Today cell phones and also computers are expected to ease their users life by making suggestions for the next text entry.Moes specifically, based on the previous phrase, the next word shall be suggested based on intelligent and fast algorithms. This is already a prominent feature in the google search and when typing messages in smart phones. 

Here, we describe an app that does exactly that: It takes a phrase as input and returns the next most likely word. The app was built for the Coursera Capstone project of the Data Science Specialization and can be found here:

<https://dfdf.shinyapps.io/Text_Prediction_App/>. 

The app uses data from the provided data sources (twitter, news, and blogs). Due to the size of the data, we sampled 5% of it to reduce memory issues and make it run fast but also have a large enough data basis in order retain a strong predition accuracy. The model returns the most likely next word in real-time-response.

Approach
========================================================

The app 
- uses previously calculated n-grams (n equals 1 to 3) from text data stemming from news, twitter, and blogs.
- takes a phrase as input, homogenizes and tokenizes it (i.e., lowering the case, removing numbers, double blanks, stop words, etc.)
- returns a prediction of the most likely next word based on a Markovian approach.

In order to build a strong prediction algorithm, we have previously written a program that calculates the n-grams (n= 1,2, and 3) from the data sources, i.e. it takes the most frequent phrases of length 1 to 3. For each of the phrases, it denotes the frequency with which they occured. 

Algorithm description
========================================================

For our prediction algorithm, we check which of the last two words of the phrase match the first two words of our previously calculated 3-gram list (if there is no match, we use the 2-grams and compare the last word of the input with the first of the 2-grams). 

This gives us a list of 3-grams, where the two first words correspond to the input and the last word corresponds to the next possible word. Now, we randomly choose an item of that list, where the probability of each row corresponds to the frequency with which the phrase occurs. After cutting away the input words, this gives us the predicted next word. 

The above algorithm is a Markovian approach because it is memory-less and uses the previously calculated frequencies to determine the next outcome. 

Summary
========================================================
In this pitch, we presented the Text Prediction ShinyApp, which takes a phrase as input and returns the most likely next word, based on n-gram models together with a markovian approach.  

The code for this presentation file can be found here:
<https://github.com/FlorianFruth/text-prediction/blob/master/pitch_presentation_class10.Rpres>
