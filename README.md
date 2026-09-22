# **ECE 2112_PA4**
### **Coded by: Vince Fredrick C. Dela Cruz (2ECE-A)**
The Programming Assignment 4 for ECE2112 can be seen inside this repository as well as its required .csv file. The main goal of this assignment is to apply our knowledge in data wrangling and visualization by solving sets of problems that helps us learn how to filter tabular data, making data frames by selecting relevant features, summarize the relationship between categorical features and a numerical variable, and to compare data using a clear and correctly labeled plot

## Initial Instructions: 
### Make sure to download board2.csv so that the fourth programming assignment can be accomplished.
### • Derive all tables and plot values from the dataset. Do not manually type rows, category means, or plotted values.
### • When applying more than one condition, make every condition explicit in the filtering expression.
### • Keep the original DataFrame unchanged.
### • Every graph must have a title, axis labels, readable category labels, and a consistent scale appropriate to the data.

## **A. VISAYAS COMMUNICATION DATAFRAME**
Make a data frame named VisComm which will contain students whose hometown is Visayas and track of Communication. (Put it in the order: Name, Gender, Math, Electronics, Average)

**Requirement:**
Display the resulting DataFrame and its number of rows. Both filtering conditions must be applied to the source dataset before the columns are selected.

Example:
```python
df = pd.read_csv('board2.csv')
a =df[['Math','Electronics','GEAS','Communication']].mean(axis=1) #gets the average of all subjects
df['Average']=a #creates a new column
VisComm = df.loc[(df['Hometown']=='Visayas')&(df['Track']=='Communication')] #chooses from the list that has the specific values of the columns per row
VisComm = VisComm[['Name','Gender','Math','Electronics','Average']]
```
Expected Output:
```python
VisComm
```
<img width="332" height="202" alt="image" src="https://github.com/user-attachments/assets/fa7dda44-5fdf-4ca4-a918-233c7c921f18" />

```python
len(VisComm) #displays the amount of rows the data frame has
```
5

## **B. VISAYAS FEMALE DATAFRAME**
Create another data frame named VisFemale which only contains female students whose hometown is Visayas. (Retain only the Name, Track, GEAS, Electronics, and Average)

**Requirement:**
Display VisFemale and the one who have an average of at least 60. (Do NOT overwrite VisFemale when performing the second filter)

Example:
```python
VisFemale = df.loc[(df['Hometown']=='Visayas')&(df['Gender']=='Female'),['Name','Track','GEAS','Electronics','Average']]
```

Expected Output:
```python
VisFemale
```
<img width="391" height="217" alt="image" src="https://github.com/user-attachments/assets/a4c68c3b-c5b7-44a9-8e5b-bdb913e13dd8" />

```python
VisFemale[(VisFemale['Average']>=60)] #shows the students that only has an average greater than 60 without overwriting the VisFemale
```
<img width="387" height="151" alt="image" src="https://github.com/user-attachments/assets/e54f616f-eb0a-485c-9ee2-ed6f1769f434" />

## **C. CATEGORY-AVERAGE VISUALIZATION**
Examine how the recorded Average differs across the three categorical features Track, Gender, and
Hometown.
a. For each feature, compute the mean of Average for every category using Pandas.
b. Display the three summary tables.
c. Create one figure containing three bar charts: mean Average by Track, by Gender, and by Hometown.
d. Below the figure, write three concise statements identifying the category with the highest sample mean for each feature.

**Requirement:**
Describe the observed dataset only. A difference in group means does not, by itself, establish that a feature causes a higher board-exam score.

Example:
```python
track_mean = df.groupby('Track')['Average'].mean()
gender_mean = df.groupby('Gender')['Average'].mean()
hometown_mean = df.groupby('Hometown')['Average'].mean()

display(track_mean) #to check the values (mean)
display(gender_mean)
display(hometown_mean)

fig, axes = plt.subplots(1, 3,) #sets the space of the figures
df.groupby('Track')['Average'].mean().plot(kind='bar', ax=axes[0]) #these gets the mean of each of the categories that were chosem
axes[0].set_ylabel('Mean Average')
df.groupby('Gender')['Average'].mean().plot(kind='bar', ax=axes[1])
df.groupby('Hometown')['Average'].mean().plot(kind='bar', ax=axes[2])

plt.tight_layout()
plt.show()
```
Expected Output:
<img width="628" height="466" alt="image" src="https://github.com/user-attachments/assets/e1969c2c-f6a5-49b7-a501-c550a9c3970a" />

**Track**
- Checking the values in the graph for the Tracks, we can see that the highest sampled mean is the track communications, having a 67.975 mean.
  
**Gender**
- As for the gender, it can be observed that the males have the highest sample mean, having a value of 67.183333.
  
**Hometown**
- Finally, for the hometown, the highest observed sample mean is Luzon, having 68.083333 mean.

#Thank you!
