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

### Problem definiton:  
Deep learning model for classification and regression problems based on face images.  
  
Competition link: [Kaggle](https://www.kaggle.com/datasets/nipunarora8/age-gender-and-ethnicity-face-data-csv)  

Project contains: 
- Basic statistial analysis with visualization(Histogram, barplots)
- 

F1 Score: 0.83 obtained by XGBoost technique
### To check the results go to Jupyter Notebook file(.ipynb)