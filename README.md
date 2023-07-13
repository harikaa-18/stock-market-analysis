# Stock Analysis
## should install requirements and  packages
$ pip3 install chart_studio

## importing libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import plotly
import chart_studio.plotly as py
import plotly.offline as plot
import plotly.graph_objs as go
from plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot
init_notebook_mode(connected=True)

# initialising training dataset
TSLV .csv from google drive


###Describing dataset
df.describe()

# plotting box plot
df[['Open','High','Low','Close','Adj Close']].plot(kind='box')

### Visualizing data plotting stock prices
iplot(plot)
#### importing sklearn library
 
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import MinMaxScaler
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import mean_squared_error as mse
from sklearn.metrics import r2_score

#### Setting layout for plot
trace0 = go.Scatter(
    x = X_train.T[0],
    y = Y_train,
    mode = 'markers',
    name = 'Actual'
)
trace1 = go.Scatter(
    x = X_train.T[0],
    y = lm.predict(X_train).T,
    mode = 'lines',
    name = 'Predicted'
)
df_data = [trace0,trace1]
layout.xaxis.title.text = 'Day'
plot2 = go.Figure(data=df_data, layout=layout)
### Train and test data
scores = f'''
{'Metric'.ljust(10)}{'Train'.center(20)}{'Test'.center(20)}
{'r2_score'.ljust(10)}{r2_score(Y_train, lm.predict(X_train))}\t{r2_score(Y_test, lm.predict(X_test))}
{'MSE'.ljust (10)}{mse(Y_train, lm.predict(X_train))}\t{mse(Y_test, lm.predict(X_test))}
'''

print(scores)


