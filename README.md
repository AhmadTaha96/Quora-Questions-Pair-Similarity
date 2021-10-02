# Quora-Questions-Pair-Similarity
### Predict Whether Two Quora Questions Are Duplicates or Not.

![1_R81CmTOWcYHzX4PO5n-q4g](https://user-images.githubusercontent.com/91129320/135132406-c8729fff-0ce7-4427-aa7a-567e3e1ee01f.jpeg)

# Real-world/Business

### Problem Statment

In this problem we will predict the similarity ratio between two Quora question, that so we shall identify which questions on Quora are duplicates of another previous questions so we don't need to re-publish the question again and this would help to deliver answers to immediately if their question was already been asked.

### objectives and constraints

**Objectives:**

Predict similarity between two questions as a probability using some threshold so that we can determine what question to accept and what question to declare as duplicate.


**Constraints:**

In this problem the cost of misclasification is very high, in order to explain that, if we have 2 question and we declare them as duplicate in case of they we not duplicate this would cause a big problem because Quora in this case will get answers to completey diffrent question, in contrast if they were duplicates and we say not that's not a big deal.

If we want to explain that in term of *Precesion & Recall* then we shall focus here on Precesion more than Recall.

Interpretability is not really important here because user care only about the results and only the results, so we shall not focus too much on this side.

Speed & Latency is not really strict here as well, as user would normally ask a question, after couple of minutes the question either published or the results will be delivered from another question [Here in case of both are duplicates].

### ML Problem Formulation

Given two candidate question to be duplicates, we should predict the ratio of similarity and upon that the our program should decide if those questions are duplicate or not.

### Performance metrics

1.   Log Loss: This is our main Key Performance Indicator (KPI).
   
   ![CodeCogsEqn](https://user-images.githubusercontent.com/91129320/135132512-d8603b24-fdcd-421d-838a-5dee35b5f436.png)
    
2.   Confusion Matrix ( For Precisoion and Recall ).

### Data Overview

The Data we have will be in one CSV file, it contains 404,351 rows and 5 columns as follow:



1.   qid1 : The ID of question 1

2.   qid2 : The ID of question 2

3.   question1 : Question 1 text.

4.   question2 : Question 2 text.

5.   is_duplicate : The label of the data, it's either 1 for duplicate or 0 for not duplicate, and that's the dependant variable we want to predict.


---


                                                     Example of data

qid1: 15

question1: How can I be a good geologist?

qid2: 16

question2 : What should I do to be a great geologist?

is_duplicate: 1

qid1: 1

question1: What is the step by step guide to invest in share market in india?

qid2: 2

question2 : What is the step by step guide to invest in share market?

is_duplicate: 0

The second example here explain that even one word can change the meaning of the question referring that some words are very important.


### Basic Features

1. question1_freq = Frequency of question1

2. question2_freq = Frequency of question2

3. quesiton1_len = Length of question1

4. quesiton2_len = Length of question2

5. question1_n_words = Number of words in question1

6. question2_n_words = Number of words in question2

7. len_diff = absoulte value of question1 length - question2 length

8. words_diff = absoulte value of question1 number of words - question2 number of words.

8. words_common = Number of common unique words in Question 1 and Question 2

9. words_share = word_common / (len(quesiton1) + len(question2))

10. frequency_sum = frequency of quesiton1 + frequency of quesiton2

11. frequency_diff = absolute value of frequency of quesiton1 - frequency of quesiton2

12. words_share_square = square root of words_share feature

13. words_share_log = log of words_share feature

14.  words_common_square = square root of words_common feature
