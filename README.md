# Student Grade Predictions

## Govind Tanda

**Introduction and Background**

The purpose of this ML project was to see if it was possible to use a dataset that contains various information about students from numerical data such as their grades in previous tests, to demographic and socioeconomic factors such as their gender, familial relationships, alcohol consumption, parents&#39; education, travel time to reach school, etc... to predict their future grade at the end of their class. The link between socioeconomic factors and student performance would seem to be an obvious one and it was indicated that in Australia students from advantaged socioeconomic backgrounds could perform up to 3x higher than students from the most disadvantaged backgrounds [**2**]. Sirin, who had conducted a meta-analysis on socioeconomic status and academic achievement had found that there was a moderate to strong correlation between socioeconomic factors and academic achievement, but it was variable depending on school location, minority status, and the level of school they were in [**3**]. Even with the seemingly obvious stated, it remains relevant that it is difficult to generalize socioeconomic impact on student performance on a global scale because of what Sirin had found and how different each country&#39;s definition of socioeconomic factors can vary. This project consisted of making use of data provided by 2 schools in Portugal and using sklearn to see how accurately it was possible to predict a student&#39;s future grade based on various numerical and categorical data. To do this project, linear regression was used since the goal was to predict future grades based on previous grades and some other categorical data which was chosen from a model selection module offered by sklearn. Train, test, split was also used to help evaluate the model based on test data, R2 scores were also used to see how well the model would predict values.

**Project Details**

The chosen dataset was the [student performance dataset](https://www.kaggle.com/ishandutta/student-performance-data-set) which provides various numerical and categorical data about students in Portugal, ranging from the school they attend, to alcohol consumption, to whether or not they have access to internet and of course their grades in their current class. This dataset contained 33 different columns of data that were available for selection so the data needed to be trimmed to remove features that may not be relevant to the prediction and the categorical data needed to be converted into numerical data so that it could be fed into the linear regression model. To choose the features for the feature matrix the decided method was to make use of sklearns [feature selection module](https://scikit-learn.org/stable/modules/feature_selection.html), to avoid guessing and checking to see which features will be most relevant to predict future grades and pandas was used to convert the categorical data into usable numerical data.

**Fig 1**. Features Chosen through linearSVR

![Features Chosen Through linearSVR](C:\Users\Govin\Desktop\COMP\2021\COMP_3710\ML\StudentGrades\images\feature_chosen_frame.png)

The chosen features include data such as student age, family relationship, daily alcohol consumption, if the students receive extra support at school, if the student wants to pursue higher education, travel time to school, and if their parents work at home, as teacher or in other services, the reason they chose their school and of course their grades from previous tests in their class. The goal is to use these features to predict a student&#39;s future grade. To make this project possible, Jupyter labs was used to allow creating an easily documentable notebook that others can view to see the process of how this project was executed.

**Fig 2.** First 10 rows of dataset

![](RackMultipart20210706-4-8zhvfl_html_fdc8f99ca7ce6ac4.png)

**Method(s)**

To conduct this experiment, I made use of sklearns extensive modules for the bulk of the project and pandas, numpy and matplotlib for other smaller problems such as creating dataframes, converting numpy arrays, and to help visualize the outcome of the experiment.

To choose the feature which would be used for the predictions for the linear regression model, I made use of linear support vector regression as the classifier in the feature selection module to decide which features would be used for my final predictions since lsvr offers flexibility with tuning the regularization value. Train, test, split was also used to help estimate how well linear regression would work on the data, an 80/20 split was used for separating training/test data. After splitting the data, the training data was fit to the linear regression algorithm then the algorithm was used to predict on the X\_test data values and the R2 score provided by linear regression was used to see how well the model could predict final grades based on the chosen features and real values in the y\_test set.

**Figure 3.** Dataframe of chosen features

![](RackMultipart20210706-4-8zhvfl_html_31bb8a0fc4b27834.png)

**Experiments/Simulations**

To get some form of baseline before data was cleaned and features were selected, the numerical data was used with train, test, split, then fit and predicted with the linear regression model. Train, test, split was used with a random\_state value to ensure the same values are split to help see results of model, also made usage of train, test, split to see results made randomly without random\_state to see how different results would be to make sure that the random\_state value wasn&#39;t simply including results that were either over or underfit.

![](RackMultipart20210706-4-8zhvfl_html_cca205ca495a9add.png) **Figure 4.** R2 Score and results before usage of categorical data and feature selection, no random\_state parameter to make use of same data

![](RackMultipart20210706-4-8zhvfl_html_a5bccd36b3e2510.png) **Figure 5.** R2 Score and results after usage of categorical data and feature selection, no random\_state

**Steps to run project**

1. Drag the grade\_ipynb prediction file and the student.csv file into a folder together
2. Open up your preferred cli and go to the folder containing the grade\_prediction.ipynb file and students.csv file, and run the command &quot;jupyter lab grade\_prediction.ipynb&quot;

![](RackMultipart20210706-4-8zhvfl_html_82f8e8e2132d1a61.png)

1. After this step has occurred you should be redirected to the Jupyter labs notebook where you can select the &quot;Run&quot; dropdown and choose &quot;Run All Cells&quot; to get the output

![](RackMultipart20210706-4-8zhvfl_html_12d769e1a5ed5346.png)

**Results**

**Figure 6.** R2 model score before usage of categorical data and feature selection, and output of first 10 students in dataset

![](RackMultipart20210706-4-8zhvfl_html_34eb7720084a32cd.png)

**Figure 7.** R2 Model score after swapping categorical data to numerical data and usage of feature selection, output of first 10 students

![](RackMultipart20210706-4-8zhvfl_html_d657998f7a8b8d4c.png)

From the results we can clearly see that the model using numerical and categeorical data is producing better results but just barely, when random\_state parameter is used to make sure the same data is used for each model they produce nearly identical results with Figure 7 showing that the usage of categorical data and feature selection made a very small increase in how high the R2 score was at 87% vs the model that just made usage of the numerical data which produced results that reached 86%.

**Evaluation**

As stated in the results section the metric that I used to help evaluate how well my model could predict future student grades was the R2 score which returns a value between 0 and 1 and indicates the explained variation between the predicted value and mean value of our test set which allows us to draw some level of relationship between our X (feature matrix) and Y (target vector). In Figure 6 and 7 we can see there is a small difference between the R2 score that was returned, which indicated that in that specific instance where random\_state was set to 5 that the model that made usage of categorical and numerical data would outperform the model that only made usage of the numerical data. However, if we were to change the random\_state parameter to another value or even remove the random\_state value we can observe that the numerical only model can outperform the categorical and numerical data model depending on how the test/train data is split.

**Figure 8.** No random\_state parameter, only numerical values used

![](RackMultipart20210706-4-8zhvfl_html_4c98a35e350a4883.png)

**Figure 9.** No random\_state parameter, numerical and categorical data

![](RackMultipart20210706-4-8zhvfl_html_e9ea543e9d8222e7.png)

**Discussion and Conclusion**

I do not think that the model created was necessarily a good model since the model with only numerical data was able to outperform the model that included categorical data as well depending on how the test/train data was split, and when the model with categorical data did outperform the model without it seemed to only be by a few percent at best. I would estimate that the reason the model that included categorical data was not performing as well was because of the usage of get\_dummies which translates the string values into binary values but does not account for the context of the values provided in some cases, such as when looking at traveltime, or famrel, or any other features which are ordered in some sense based on their values from 1…N. I think making usage of OrdinalEncoder on these values may have been a better method to use and would have allowed modelselection to create a better features matrix. I noticed that in the matrix selected by modelselection that the features were not including data that would seem relevant because features like Mjob\_teacher or Fjob\_services were chosen but their counterparts, Fjob\_teacher or Mjob\_services were not selected so it seems as if the model would have some level of bias by not including these values to even out the selected features.

**Future Plans**

I think making usage of ordinalencoder and scaling the data beforehand may have helped create a better selected features matrix. Introducing usage of more metrics to get a better idea of how well the model is performing, such as using cross validation to help reduce overfitting instead of 1 iteration of train test split would also have been a good idea to see how well the model would perform when using different methods. Looking into how to optimize hyperparameters also seems to be worth looking into as they seem to have large impact on how the model will perform. As well as looking at how other similar studies have been conducted, in 2015 Asif et al investigated student grade prediction for 4th year students at university levels by only using marks before university, and during their 1st and second years but not including any socio-economic factors [**1**]. The same study by Asif et al also made usage of multiple models and algorithms such as multi-layer perceptron&#39;s to help classify their data and then made usage of linear regression later on, so it may be beneficial to make usage of multiple ML techniques for future projects [**1**]. In general, it seems that next time I attempt to create an ML model that it would be best to spend more time preprocessing the data before any train/testing or predictions happen and looking into making use of multiple algorithms and models to help create a better result.

**References**

[**1**] R. Asif, A. Merceron, and M. K. Pathan, &quot;Predicting Student Academic Performance at Degree Level: A Case Study,&quot; _International Journal of Intelligent Systems and Applications_, vol. 7, no. 1, pp. 49–61, 2014.

[**2**] &quot;&#39;Exploring Scientific Literacy: How Australia measures up. The PISA 200&#39; by Sue Thomson and Lisa De Bortoli,&quot; _Site_, 2015. [Online]. Available: https://research.acer.edu.au/ozpisa/2. [Accessed: 02-Apr-2021].

[**3**] S. R. Sirin, &quot;Socioeconomic Status and Academic Achievement: A Meta-Analytic Review of Research,&quot; _Review of Educational Research_, vol. 75, no. 3, pp. 417–453, 2005.
