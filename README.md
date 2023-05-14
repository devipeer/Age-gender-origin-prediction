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
![Model structure](https://github.com/devipeer/Age-gender-origin-prediction/blob/main/model_structure.png)


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


Gender: 
|        | Precision | Sensitivity | F1-Score |
|--------|-----------|-------------|----------|
| Male   |    0.92   |    0.85     |   0.89   |
| Female |    0.85   |    0.92     |   0.89   |

Accuracy: 0.89


Age:  
$R^2$ score = 0.75

### Example of prediction: 
![ExamplePrediction](https://github.com/devipeer/Age-gender-origin-prediction/blob/main/example_prediction.png)

## Conlusions:
The hardest part and what took the most amount of time during the work on this project
was to prepare data. At first I was trying to use DataImageGenerator for the
preparing and augmentation, but it was working only for dataset with one label, in my
case there were 3 labels. That is why I had to do all the preparation manually. Second
hardest part was to build model that will obtain good results. I am only partially
satisfied with the results that I obtained. We can see that model is the best at
predicting Gender specially ‘Male’ class, where precision is at very high level of 0.92, the
overall accuracy here equals 0.89, which is a very good score. When we take Ethnicity
into consideration it does not look that good. The model is good at predicting ‘Black’ and
‘Asian’ classes, acceptable for predicting ‘White’ and ‘Indian’ class, but It is not doing so
well in predicting ‘Others’ class, which can be understandable, because there are
multiple ethnicities included there with not much in common. R-squared score in a
regression problem equals 0.75, which is acceptable, because even for human beings It is
sometimes very hard to predict someone’s age. 

### To check the results go to Jupyter Notebook file(.ipynb)