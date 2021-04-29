# covid_vaccination_data

import pandas as pd
import numpy as np
import csv
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
sns.set(color_codes=True)

df = pd.read_csv("country.csv")
df.head(5)

df.tail(5)

df.dtypes

df = df.drop(['iso_code', 'daily_vaccinations_raw', 'people_vaccinated', 'source_website'] , axis= 1)
df.head(5)

df = df.rename(columns={"total_vaccinations":"Vaccinations", "people_fully_vaccinated":"Completely vaccinatied", "daily_vaccinations":"Per day vaccinations", "total_vaccinations_per_hundred":"Vaccination per hundred", "people_vaccinated_per_hundred":"Average vaccinated per hundred", "people_fully_vaccinated_per_hundred":"Completely Vaccinated per hundred", "daily_vaccinations_per_million":"Average vaccination per million", "vaccines":"Vaccine type", "source_name":"Organization"})
df.head(5)

df.tail(5)

df.shape

duplicate_rows_df = df[df.duplicated()]
print(" Number of duplicate rows:", duplicate_rows_df.shape)

df.count()

df = df.drop_duplicates()
df.head(5)

df.count()

print(df.isnull().sum())

df = df.dropna()
df.count()

sns.boxplot(x=df['Completely vaccinatied'])
