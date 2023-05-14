# 2023 EY Open Science Data Challenge

## Dataset description
The dataset has 5 columns and 23705 rows, last column contains values of each pixel of 48x48 images in just one dimension. Fourth column is the image name in the original
UTKFace Dataset, but in purpose of this project it is not important and we can remove that
column from dataset. Rest of the columns are labels. First label is age and values of this
column are in range of (1; 116), from that we know that the youngest person is 1 year old
and the oldest person in the dataset is 116 years old. Second column contains information
about ethnicity of the person in the image, values in this columns are all integers and vary
from 0 to 4, where 0 - White, 1 - Black, 2 - Asian, 3 - Indian, and 4 - Others (like Hispanic,
Latino, Middle Eastern). The last label is gender, which is a binary label, where 0 - Male, 1 -
Female. 

Dataset link: [Kaggle](https://www.kaggle.com/datasets/nipunarora8/age-gender-and-ethnicity-face-data-csv)  

## Problem definiton:  
The problem is to build a model that will predict all three features mentioned in previous
section. Gender and Ethnicity predictions are a classification problem, where in case of
gender there are 2 possible outcomes and in case of ethnicity 5 possible outcomes. Age
prediction is more of a regression problem, because we are dealing with specific value of
age. There is no missing values in the dataset and we decided to not remove any of the data,
because of outliers, which the people with highest age(90+ years old) were detected as so,
for the reason that in real life this is also the smallest group in the society and we want to
train model as it would be able to predict their age too. One of the issues that may be a
reason of poor quality for predicting ethnicity is that, the images are in just 1 channel, which
doesn’t gives any information about peoples skin color, which is probably the biggest
difference between all races. Quality of the images may cause poor decisions of model as
well, because its only 48x48 quality.  
Model should take as an input batches of images and outputs 3 values, which are age,
ethnicity and gender of each person in the image. We decided to use TensorFlow library for
this problem.

Project contains: 
- Basic statistial analysis with visualization(Histogram, barplots)
- Data preprocessing
- Image augmentation

### Model structure: 
[Model structure](https://github.com/devipeer/Age-gender-origin-prediction/blob/main/model_structure.png)


### Model Performance: 
  
Ethnicity:
|        | Precision | Sensitivity | F1-Score |
|--------|-----------|-------------|----------|
| White  |    0.75   |    0.9      |   0.82   |
| Black  |    0.83   |    0.82     |   0.82   |
| Asian  |    0.82   |    0.78     |   0.80   |
| Indian |    0.72   |    0.65     |   0.68   |
| Others |    0.62   |    0.05     |   0.09   |

Accuracy = 0.76
### To check the results go to Jupyter Notebook file(.ipynb)