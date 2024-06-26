<h1 align="center"><string>Medical Data Visualizer</string></h1>

## **Assignment**

In this project, you will visualize and make calculations from medical examination data using matplotlib, seaborn, and pandas. The dataset values were collected during medical examinations.

## **Data description**

The rows in the dataset represent patients and the columns represent information like body measurements, results from various blood tests, and lifestyle choices. You will use the dataset to explore the relationship between cardiac disease, body measurements, blood markers, and lifestyle choices.

File name: medical_examination.csv

| Feature | Variable Type |	Variable | Value Type |
| :-------: | :-------------: | :--------------: | :----: |
| Age | Objective Feature | <code>age</code> | int (days) | 
| Height | Objective Feature | <code>height</code> |	int (cm) |
| Weight | Objective Feature | <code>weight</code> | float (kg) |
| Gender | Objective Feature | <code>gender</code> | categorical | code |
| Systolic blood pressure | Examination Feature | <code>ap_hi</code>	| int |
| Diastolic blood pressure	| Examination Feature | <code>ap_lo</code> | int |
| Cholesterol | Examination Feature | <code>cholesterol</code> | 1: normal, 2: above normal, 3: well above normal |
| Glucose | Examination Feature	| <code>gluc</code> | 1: normal, 2: above normal, 3: well above normal |
| Smoking | Subjective Feature | <code>smoke</code> | binary |
| Alcohol intake | Subjective Feature | <code>alco</code> | binary |
| Physical activity | Subjective Feature | <code>active</code> | binary |
Presence or absence of cardiovascular disease | Target Variable | <code>cardio</code> | binary |

## **Tasks**

Create a chart similar to <code>examples/Figure_1.png</code>, where we show the counts of good and bad outcomes for the <code>cholesterol</code>, <code>gluc</code>, <code>alco</code>, <code>active</code>, and <code>smoke</code> variables for patients with cardio=1 and cardio=0 in different panels.

Use the data to complete the following tasks in <code>medical_data_visualizer.py</code>:

- Add an <code>overweight</code> column to the data. To determine if a person is overweight, first calculate their BMI by dividing their weight in kilograms by the square of their height in meters. If that value is > 25 then the person is overweight. Use the value 0 for NOT overweight and the value 1 for overweight.
- Normalize the data by making 0 always good and 1 always bad. If the value of <code>cholesterol</code> or <code>gluc</code> is 1, make the value 0. If the value is more than 1, make the value 1.
- Convert the data into long format and create a chart that shows the value counts of the categorical features using seaborn's <code>catplot()</code>. The dataset should be split by 'Cardio' so there is one chart for each <code>cardio</code> value. The chart should look like <code>examples/Figure_1.png</code>.
- Clean the data. Filter out the following patient segments that represent incorrect data:
    - diastolic pressure is higher than systolic (Keep the correct data with <code>(df['ap_lo'] <= df['ap_hi'])</code>)
    - height is less than the 2.5th percentile (Keep the correct data with <code>(df['height'] >= df['height'].quantile(0.025))</code>)
    - height is more than the 97.5th percentile
    - weight is less than the 2.5th percentile
    - weight is more than the 97.5th percentile
- Create a correlation matrix using the dataset. Plot the correlation matrix using seaborn's <code>heatmap()</code>. Mask the upper triangle. The chart should look like <code>examples/Figure_2.png</code>.

Any time a variable is set to <code>None</code>, make sure to set it to the correct code.

Unit tests are written for you under <code>test_module.py</code>.

## **Development**

For development, you can use <code>main.py</code> to test your functions. Click the "run" button and <code>main.py</code> will run.

## **Testing**

We imported the tests from <code>test_module.py</code> to <code>main.py</code> for your convenience. The tests will run automatically whenever you hit the "run" button.