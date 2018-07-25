# Quasar Property Testing
These tests were done as part of a final project focusing on using statistical testing and ML techniques to explore potential conclusions that could come of datasets. *the basis for testing X-Ray properties versus color was simply to see if this relatonship existed, much like the exploration of testing radio-loud/quiet sources versus color.

## Regression:
The first test done was an attempt to create a photometric predictor for redshift. This entailed looking at our dataset in each of the four colors (u-g, g-r, r-i, i-z) in which the quasar was observed, and examining the dependency of color and the observed redshift of the quasar. Via regression, fits were made to the portion of the data with high redshifts, and were assessed in ‘goodness of fit’ tests.

Using polynomial regression, from the astroML package in python, fits were made for color versus redshift plots. The fits were done in the four colors: u-g, g-r, r-i, i-z and using redshifts above 2.5. This decision was made as the result of difficulty fitting the entire plot to a model, where the issues arose in redshifts below 2.5.

## Hypothesis Testing
The second test was a re-working of conclusions found in the Weinstein et al. (2004) paper, in which quasar reddening was confirmed. This was done by hypothesis testing, in attempt to rule out that these observations of redder colors could not have happened by chance.

By splitting the data into five redshift segments, I examined the positive z-scores of every data point in a given redshift range. This was done for u-g and g-r. Only positive z-scores were taken into account because this meant that the color value was shifted positively away from the mean, or in qualitative terms, ‘redder’. In this test we do not care about values that are ‘bluer’ than they should be.  

## Classification
Lastly, the third method used was classification. Using a linear support vector model (SVM), an attempt was made to classify quasars as X-Ray ‘bright’ or X-Ray ‘dim’ based on their colors. 

We create a classifier that assigns either a class of ‘bright’ or ‘dim’ to a given quasar. We fit our classifier model, using a Linear SVC support vector machine, to the quasar’s four color values. Running this classifier on our data, this results in an accuracy of 60.93% meaning an error of 39.06%. To cross-validate this classification, we split up our data into 20% test and 80% train. We then get an accuracy of 62.8% and an error of 37.2%. This indicates that our classifier is most likely classifying correctly at random. The classifier doesn’t have to work very hard to make a ‘correct’ classification, meaning including true positives and false positives, since it only has two options. This means that in theory we should have a much higher accuracy rate if this were a good classifier.

Using the K Nearest Neighbors method, the classification accuracy rate is 57.82% and its error is 42.18%, and after cross-validation to assess the ‘goodness’ of our classifier, we get an accuracy rate of 53.08% and an error of 46.92%. These rates are worse than the above for Linear SVC, therefore we can confidently say that the likelihood that there exists a relationship between X-Ray emission and color is very low. 


The aim in all of this is to find dependencies between quasar properties, which could give astronomers insight into the relationships between those properties in galaxies nearer to us. 
