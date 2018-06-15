import pandas as pd
import matplotlib.pyplot as plt


import numpy as np



#read csv into dataframe


df = pd.read_csv("sample.csv") 


print(df) 



#plot factor data graphically to identify outliers and compare values for both factors


df.plot(x='companyname', y='Factor_VALUE', style='o', label='Value')


df.plot(x='companyname', y='Factor_QUALITY', style='o', label='Quality')


plt.xlabel('Company/Data Date', fontsize=12)


plt.ylabel('Factor values', fontsize=12)


plt.legend(loc='best')


plt.show()



#isolate outlier


print(df['Factor_VALUE'].max())



#remove outlier


df['Factor_VALUE'] = df['Factor_VALUE'].replace('8000', np.nan)



#check outlier has been removed


print(df['Factor_VALUE'].max())



#build histograms to look for skewness or assymetry for quality


df.hist('Factor_QUALITY', bins = 100)


plt.show()



#build histograms to look for skewness or assymetry for value


df.hist('Factor_VALUE', bins = 100)


plt.show()



#isolating columns


v = df[['Factor_VALUE']]


q = df[['Factor_QUALITY']]



#printing the means to compare 


print(v.mean())


print(q.mean())



#printing the standard deviations to compare 


print(v.std())


print(q.std())
