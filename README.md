# **ECE 2112_PA4**
### **Coded by: Vince Fredrick C. Dela Cruz (2ECE-A)**
The Programming Assignment 4 for ECE2112 can be seen inside this repository as well as its required .csv file. The main goal of this assignment is to apply our knowledge in data wrangling and visualization by solving sets of problems that helps us learn how to filter tabular data, making data frames by selecting relevant features, summarize the relationship between categorical features and a numerical variable, and to compare data using a clear and correctly labeled plot

##Initial Instructions: 
### Make sure to download board2.csv so that the fourth programming assignment can be accomplished.
### • Derive all tables and plot values from the dataset. Do not manually type rows, category means, or plotted values.
### • When applying more than one condition, make every condition explicit in the filtering expression.
### • Keep the original DataFrame unchanged.
### • Every graph must have a title, axis labels, readable category labels, and a consistent scale appropriate to the data.

##A. VISAYAS COMMUNICATION DATAFRAME
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
