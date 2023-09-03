# Data-Analysis-Using-Python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns

ipl= pd.read_csv("C:\\Users\\sharm\\Downloads\\matches (1).csv")
print(ipl)

#It display the top 5 rows head() method
ipl.head()

#It display the info of the data use info()
ipl.info()

#Looking at the number of rows and columns
ipl.shape

#To print most man of the match player you use print(ipl["Column name"].value_counts())
print(ipl["player_of_match"].value_counts())

#Top five player man of the match you use print(ipl["columns name"].value_counts()[0:5])
print(ipl["player_of_match"].value_counts()[0:5])

#Only top 5 player name display use print(ipl["column name"].value_counts()[0:5].keys())
print(ipl["player_of_match"].value_counts()[0:5].keys())

#To print the bar graph use plt.bar((ipl["player_of_match"].value_counts()[0:5].keys()),(ipl['player_of_match'].value_counts()[0:5]))
plt.bar((ipl['player_of_match'].value_counts()[0:5].keys()),(ipl['player_of_match'].value_counts()[0:5]))
plt.show()

#To get the frequency of the result
print(ipl["result"].value_counts())

#To get the winner of top five teams
print(ipl["winner"].value_counts()[0:5])

#Tp draw the pie chart of the top five teams
print(ipl["winner"].value_counts()[0:5].keys())

#winner top 3 teams
plt.bar((ipl["winner"].value_counts()[0:3].keys()),(ipl["winner"].value_counts()[0:3]),color=["red","green","orange"])
plt.show()

#Find out the number of toss winner
print(ipl["toss_winner"].value_counts())

#Extract the record  where team choose batting first
batting_first=ipl[ipl['win_by_runs']!=0]

#First Five teams wining the record and batting first
batting_first.head()

#Making a histogram
plt.figure(figsize=(7,7))
plt.hist(batting_first["win_by_runs"])
plt.show()

#Showing the team wins after the batting first
print(batting_first["winner"].value_counts())


#Making a bar top 3 teams with most wins after batting first
plt.figure(figsize=(7,7))
plt.bar(list(batting_first["winner"].value_counts()[0:3].keys()),list(batting_first["winner"].value_counts()[0:3]),color=["red","green","yellow"])
plt.show()

#Draw Pie Char of batting first winner teams
plt.figure(figsize=(7,7))
plt.pie(list(batting_first["winner"].value_counts()),labels=list(batting_first["winner"].value_counts().keys()),autopct="%0.1f%%")
plt.show()

#Extract team where team won by watting second
batting_second=ipl[ipl["win_by_wickets"]!=0]

#First five teams
batting_second.head()

#Making a histogram
plt.figure(figsize=(7,7))
plt.hist(batting_second["win_by_wickets"].value_counts())
plt.show()

#Batting second wins who losses toss
batting_second["winner"].value_counts()

#Draw the bar plot of top 3 team
plt.figure(figsize=(7,7))
plt.bar(list(batting_second["winner"].value_counts()[0:3].keys()),list(batting_second["winner"].value_counts()[0:3]))
plt.show()

