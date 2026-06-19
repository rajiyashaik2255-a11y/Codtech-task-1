NAME: SHAIK RAJIYA INTENSHIP ID:CITS5234 NO:OF:WEEKS:4 weeks PROJECT NAME: Data Analytics PROJECT SCOPE:sales Trends visualization 


 #code
 Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

2. Create Sample Dataset
data = {
 'Month': ['Jan','Feb','Mar','Apr','May','Jun',
 'Jul','Aug','Sep','Oct','Nov','Dec'],
 'Sales': [12000,13500,14000,15000,16500,18000,
 19000,21000,22000,23500,25000,27000]
}
df = pd.DataFrame(data)
print(df.head()

3)Data Cleaning
# Check missing values
print(df.isnull().sum())
# Remove duplicates
df = df.drop_duplicates()
# Check data types
print(df.dtypes)
# Convert month into numeric index
df['Month_Num'] = range(1, len(df)+1)
print(df)

4. Exploratory Data Analysis
Summary Statistics
print(df.describe())
Total Sales
total_sales = df['Sales'].sum()
print("Total Sales:", total_sales)
Average Sales
avg_sales = df['Sales'].mean()
print("Average Sales:", avg_sales)
Highest Sales Month
highest = df.loc[df['Sales'].idxmax()]
print("Highest Sales Month:")
print(highest)

5) Sales Trend Visualization
plt.figure(figsize=(10,5))
plt.plot(
 df['Month'],
 df['Sales'],
 marker='o',
 linewidth=2
)
plt.title("Monthly Sales Trend")
plt.xlabel("Month")
plt.ylabel("Sales")
plt.grid(True)
plt.show()

6. Bar Chart
plt.figure(figsize=(10,5))
sns.barplot(
 x='Month',
 y='Sales',
 data=df
)
plt.title("Monthly Sales Comparison")
plt.show()

8. Prediction Model (Linear Regression)
X = df[['Month_Num']]
y = df['Sales']
model = LinearRegression()
model.fit(X, y)
predictions = model.predict(X)
print("R2 Score:", r2_score(y, predictions
future_months = pd.DataFrame({
 'Month_Num':[13,14,15]
})
future_sales = model.predict(future_months)
forecast = pd.DataFrame({
 'Month':['Jan-2025','Feb-2025','Mar-2025'],
 'Predicted_Sales':future_sales

})
print(forecast)

9) Forecast Visualization
plt.figure(figsize=(10,5))
plt.plot(
 df['Month_Num'],
 df['Sales'],
 marker='o',
 label='Actual Sales'
)
future_x = [13,14,15]
plt.plot(
 future_x,
 future_sales,
 marker='o',
 linestyle='--',
 label='Forecast Sales'
)
plt.title("Sales Forecast")
plt.xlabel("Month Number")
plt.ylabel("Sales")
plt.legend()
plt.show()

10. Interactive Dashboard (Plotly)
import plotly.express as px
fig = px.line(
 df,
 Month',
 y='Sales',
 title='Sales Trend Dashboard',
 markers=True
)
fig.show()

12. KPI Dashboard Summary
print("========== SALES DASHBOARD ==========")
print("Total Sales:", df['Sales'].sum())
print("Average Sales:", round(df['Sales'].mean(),2))
print("Maximum Sales:", df['Sales'].max())
print("Minimum Sales:", df['Sales'].min())
growth = (
 (df['Sales'].iloc[-1] -
 df['Sales'].iloc[0])
 /
 df['Sales'].iloc[0]
) * 100
print("Growth Rate: {:.2f}%".format(growth))
