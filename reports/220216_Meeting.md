# Weekly Meeting - February 16 2022

# Updates
- I am now using data from Paolo that has not been previously standardized.
- I performed a more thorough hyperparameter search for the random forest. The results have been saved in a csv file, and I can now say I've found the hyperparameters which optimize ROC-AUC score.
    - DONE: Found an optimal RF, which can be included in a voting classifier. --> **NOPE, NEEDS TO BE REPEATED**
    - DONE: Found an optimal Balanced RF, which is slightly better than a regular RF. (0.647 vs 0.644 ROC-AUC)  
    
- I performed a basic optimization of logistic regression, though I omitted regularization because it often failed to converge after 500 iterations. 
    - DONE: Established (once again) that optimal LR uses class balancing.
    - MAYBE: Explore LR regularization.
- I created a notebook for the Gaussian Naive Bayes classifier, which (as far as I know) does not require any hyperparamter tuning.
- I performed a gridsearch of SVM hyperparameters. 
    - DONE: Found optimal SVM. Default C is best. Class balancing=yes. Shrinking set to false seems to result in faster training time.
- I calculated spearman correlations for our models. The gaussian naive bayes classifier makes predictions that are not very correlated with the rest.
    - DONE: Calculated spearman correlation between the predictions of each model. 
- I implemented a soft voting classifier which included all the above models. A hard voting classifier does not report its own probability measure and therefore cannot be evaluated on ROC-AUC, as far as i understand.
    - DONE: Implemented a soft voting classifier. 
    - DONE: Scored each model on 10-fold cross-validation. The difference between ROC-AUC scores of the soft voting classifier and the support vector machine is not significant (p-value=0.66) 
- I calculated feature importance for each of the four models using a permutation method. 

- **UPDATE.** Found an error: I did not consistently apply scaling before pca. 
- **QUESTION.** PCA to 100% explained variance??