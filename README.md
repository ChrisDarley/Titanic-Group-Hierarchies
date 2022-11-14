# Titanic-Group-Hierarchies
Classifying titanic passenger survival based on family and ticket survival hierarchies and passenger class

This repository is primarily focused on feature engineering, and does not necessarily demonstrate an efficient sklearn workflow of a problem.
For a more standard sklearn example, checkout the sample_sklearn_workflow repository https://github.com/ChrisDarley/sample_sklearn_workflow.

This notebook is inspired by the following kaggle notebook:
https://www.kaggle.com/cdeotte/titanic-using-name-only-0-81818

The above notebook achieves strong results by classifying women to survive and men to die, except it predicts boys to live 
when they are a part of a family group in which all women and other children live, and it predicts women to die when all 
other women and all other children in the group die.  

My notebook attempts to be more specific about predictions using a few strategies:
1) create an binary adult variable that helps seperate women and girls as well as adult children from their parents.
2) create a ticket variable that seeks to understand group information of passengers with no families on board.
3) splits the dataset into three main groups:
    1 - passengers traveling in families with children
    2 - passengers traveling in families without children
    3 - passengers traveling with no family but other passengers sharing the same ticket number
4) Predicting survival based on much smaller subsets of the data using family and ticket survival hierarchies
   and based on ticket class.  For example, how likely will a woman in passenger class 3 be to survive if her 
   boy dies but her daughter survives?
   
Overall, my model was slightly less accurate than the far simpler model it was inspired by.  It achieved just under 80%
accuracy when the other model achieves just under 82% accuracy.  I believe the process by which I classified adulthood may
contribute to poorer results.  Additionally, many of my survival rules were made based on segments of the passengers with 
too few examples to have the rules amount to anything other than educated guesses, so with a larger dataset this 
methodology may have been more effective.

I use sklearn pipeline functionality in the beginning of the notebook, but later abandon it in favor of using pandas only for 
simpler column name functionality.  In general, I could have been putting sequential operations into pandas pipelines, but this 
model was more focused on exploration of the dataset, so I was changing things around too much to want to do that.
