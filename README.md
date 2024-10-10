# Student-Performance-Analysis

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df=pd.read_excel("/content/STUDENT.xlsx")

df

print(df.head())

df.describe

print(df.describe)

df.describe()

df.info()

df.isnull().sum()

df=df.drop("Unnamed: 0",axis=1)

#change weekly atudy hours

df["WklyStudyHours"]=df["WklyStudyHours"].str.replace("05-Oct","5-10")
df.head()

df=df.fillna({'WklyStudyHours':'5-10'})
df.head(5)

plt.figure(figsize= (4,4))
ax=sns.countplot(data=df,x="Gender")
ax.bar_label(ax.containers[0])
plt.show()

gb= df.groupby("ParentEduc").agg({"MathScore":'mean',"ReadingScore":'mean',"WritingScore":'mean'})

print(gb)

plt.figure(figsize= (4,4))
sns.heatmap(gb,annot= True)
plt.show

gb1= df.groupby("ParentMaritalStatus").agg({"MathScore":'mean',"ReadingScore":'mean',"WritingScore":'mean'})
print(gb1)

plt.figure(figsize= (4,4))
sns.heatmap(gb1,annot= True)
plt.show

sns.boxplot(data=df, x="MathScore")
plt.show()

sns.boxplot(data=df, x="ReadingScore")
plt.show()

sns.boxplot(data=df, x="WritingScore")
plt.show()

print(df["EthnicGroup"].unique())

groupA=df.loc[(df["EthnicGroup"]=="group A")].count()

print(groupA)

groupB=df.loc[(df["EthnicGroup"]=="group B")].count()
print(groupB)

groupC=df.loc[(df["EthnicGroup"]=="group C")].count()
print(groupC)

groupD=df.loc[(df["EthnicGroup"]=="group D")].count()
print(groupD)

groupE=df.loc[(df["EthnicGroup"]=="group E")].count()
print(groupE)

l=["group A", "group B","groupC","groupD","groupE"]
mlist=[groupA["EthnicGroup"],groupB["EthnicGroup"],groupC["EthnicGroup"],groupD["EthnicGroup"],groupE["EthnicGroup"]]
print(mlist)
plt.pie(mlist, labels=l, autopct="%1.2f%%")
plt.title("Distribution of Ethnic Group")
plt.show()


ax=sns.countplot(data=df,x="EthnicGroup")
ax.bar_label(ax.containers[0])
