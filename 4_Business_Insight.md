4. Business Insight (30 poin)
Selain EDA, lakukan juga beberapa analisis dan visualisasi untuk menemukan suatu
business insight. Tuliskan minimal 3 insight, dan berdasarkan insight tersebut jelaskan
rekomendasinya untuk bisnis.


```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from textwrap import wrap
import numpy as np
```


```python
import pandas as pd
from google.colab import files
import io
```


```python
uploaded = files.upload()
```
 


    Saving E-Commerce-Dataset.csv to E-Commerce-Dataset.csv
    


```python
df = pd.read_csv('E-Commerce-Dataset.csv')
df
```





  <div id="df-8d69d17a-2d0b-4cd7-9d51-ffbb5917b04e" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CustomerID</th>
      <th>Churn</th>
      <th>Tenure</th>
      <th>PreferredLoginDevice</th>
      <th>CityTier</th>
      <th>WarehouseToHome</th>
      <th>PreferredPaymentMode</th>
      <th>Gender</th>
      <th>HourSpendOnApp</th>
      <th>NumberOfDeviceRegistered</th>
      <th>PreferedOrderCat</th>
      <th>SatisfactionScore</th>
      <th>MaritalStatus</th>
      <th>NumberOfAddress</th>
      <th>Complain</th>
      <th>OrderAmountHikeFromlastYear</th>
      <th>CouponUsed</th>
      <th>OrderCount</th>
      <th>DaySinceLastOrder</th>
      <th>CashbackAmount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>50001</td>
      <td>1</td>
      <td>4.0</td>
      <td>Mobile Phone</td>
      <td>3</td>
      <td>6.0</td>
      <td>Debit Card</td>
      <td>Female</td>
      <td>3.0</td>
      <td>3</td>
      <td>Laptop &amp; Accessory</td>
      <td>2</td>
      <td>Single</td>
      <td>9</td>
      <td>1</td>
      <td>11.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>5.0</td>
      <td>160</td>
    </tr>
    <tr>
      <th>1</th>
      <td>50002</td>
      <td>1</td>
      <td>NaN</td>
      <td>Phone</td>
      <td>1</td>
      <td>8.0</td>
      <td>UPI</td>
      <td>Male</td>
      <td>3.0</td>
      <td>4</td>
      <td>Mobile</td>
      <td>3</td>
      <td>Single</td>
      <td>7</td>
      <td>1</td>
      <td>15.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>121</td>
    </tr>
    <tr>
      <th>2</th>
      <td>50003</td>
      <td>1</td>
      <td>NaN</td>
      <td>Phone</td>
      <td>1</td>
      <td>30.0</td>
      <td>Debit Card</td>
      <td>Male</td>
      <td>2.0</td>
      <td>4</td>
      <td>Mobile</td>
      <td>3</td>
      <td>Single</td>
      <td>6</td>
      <td>1</td>
      <td>14.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>120</td>
    </tr>
    <tr>
      <th>3</th>
      <td>50004</td>
      <td>1</td>
      <td>0.0</td>
      <td>Phone</td>
      <td>3</td>
      <td>15.0</td>
      <td>Debit Card</td>
      <td>Male</td>
      <td>2.0</td>
      <td>4</td>
      <td>Laptop &amp; Accessory</td>
      <td>5</td>
      <td>Single</td>
      <td>8</td>
      <td>0</td>
      <td>23.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>134</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50005</td>
      <td>1</td>
      <td>0.0</td>
      <td>Phone</td>
      <td>1</td>
      <td>12.0</td>
      <td>CC</td>
      <td>Male</td>
      <td>NaN</td>
      <td>3</td>
      <td>Mobile</td>
      <td>5</td>
      <td>Single</td>
      <td>3</td>
      <td>0</td>
      <td>11.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>130</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>5625</th>
      <td>55626</td>
      <td>0</td>
      <td>10.0</td>
      <td>Computer</td>
      <td>1</td>
      <td>30.0</td>
      <td>Credit Card</td>
      <td>Male</td>
      <td>3.0</td>
      <td>2</td>
      <td>Laptop &amp; Accessory</td>
      <td>1</td>
      <td>Married</td>
      <td>6</td>
      <td>0</td>
      <td>18.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>151</td>
    </tr>
    <tr>
      <th>5626</th>
      <td>55627</td>
      <td>0</td>
      <td>13.0</td>
      <td>Mobile Phone</td>
      <td>1</td>
      <td>13.0</td>
      <td>Credit Card</td>
      <td>Male</td>
      <td>3.0</td>
      <td>5</td>
      <td>Fashion</td>
      <td>5</td>
      <td>Married</td>
      <td>6</td>
      <td>0</td>
      <td>16.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>225</td>
    </tr>
    <tr>
      <th>5627</th>
      <td>55628</td>
      <td>0</td>
      <td>1.0</td>
      <td>Mobile Phone</td>
      <td>1</td>
      <td>11.0</td>
      <td>Debit Card</td>
      <td>Male</td>
      <td>3.0</td>
      <td>2</td>
      <td>Laptop &amp; Accessory</td>
      <td>4</td>
      <td>Married</td>
      <td>3</td>
      <td>1</td>
      <td>21.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>186</td>
    </tr>
    <tr>
      <th>5628</th>
      <td>55629</td>
      <td>0</td>
      <td>23.0</td>
      <td>Computer</td>
      <td>3</td>
      <td>9.0</td>
      <td>Credit Card</td>
      <td>Male</td>
      <td>4.0</td>
      <td>5</td>
      <td>Laptop &amp; Accessory</td>
      <td>4</td>
      <td>Married</td>
      <td>4</td>
      <td>0</td>
      <td>15.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>9.0</td>
      <td>179</td>
    </tr>
    <tr>
      <th>5629</th>
      <td>55630</td>
      <td>0</td>
      <td>8.0</td>
      <td>Mobile Phone</td>
      <td>1</td>
      <td>15.0</td>
      <td>Credit Card</td>
      <td>Male</td>
      <td>3.0</td>
      <td>2</td>
      <td>Laptop &amp; Accessory</td>
      <td>3</td>
      <td>Married</td>
      <td>4</td>
      <td>0</td>
      <td>13.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>169</td>
    </tr>
  </tbody>
</table>
<p>5630 rows × 20 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-8d69d17a-2d0b-4cd7-9d51-ffbb5917b04e')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>


  </div>


<div id="df-2e1badcb-e1b6-4cb9-bd41-c080fcb519c2">
  <button class="colab-df-quickchart" onclick="quickchart('df-2e1badcb-e1b6-4cb9-bd41-c080fcb519c2')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-2e1badcb-e1b6-4cb9-bd41-c080fcb519c2 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




## Apakah hubungan status menikah dengan tingkat churn ?


```python
dfa = df.copy()
dfa['MaritalStatus'].value_counts()
dfat = dfa.groupby(['MaritalStatus', 'Churn'])['CustomerID'].nunique()

dfat_pr = dfat.groupby(level=0).apply(lambda x:100 * x / float(x.sum())).reset_index(name='percentage')

df_1 = dfat_pr.merge(dfat.reset_index(), how = 'inner', on = ['MaritalStatus', 'Churn'])
df_1
```

    <ipython-input-10-5e3a2bab5e13>:5: FutureWarning: Not prepending group keys to the result index of transform-like apply. In the future, the group keys will be included in the index, regardless of whether the applied function returns a like-indexed object.
    To preserve the previous behavior, use
    
    	>>> .groupby(..., group_keys=False)
    
    To adopt the future behavior and silence this warning, use 
    
    	>>> .groupby(..., group_keys=True)
      dfat_pr = dfat.groupby(level=0).apply(lambda x:100 * x / float(x.sum())).reset_index(name='percentage')
    





  <div id="df-5a578f68-313a-4c2d-a290-aa2299025d50" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MaritalStatus</th>
      <th>Churn</th>
      <th>percentage</th>
      <th>CustomerID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Divorced</td>
      <td>0</td>
      <td>85.377358</td>
      <td>724</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Divorced</td>
      <td>1</td>
      <td>14.622642</td>
      <td>124</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Married</td>
      <td>0</td>
      <td>88.479571</td>
      <td>2642</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Married</td>
      <td>1</td>
      <td>11.520429</td>
      <td>344</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Single</td>
      <td>0</td>
      <td>73.273942</td>
      <td>1316</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Single</td>
      <td>1</td>
      <td>26.726058</td>
      <td>480</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-5a578f68-313a-4c2d-a290-aa2299025d50')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

  </div>


<div id="df-19e06dff-c44f-4921-80ca-2c7c19e7ddb1">
  <button class="colab-df-quickchart" onclick="quickchart('df-19e06dff-c44f-4921-80ca-2c7c19e7ddb1')"
            title="Suggest charts."
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-19e06dff-c44f-4921-80ca-2c7c19e7ddb1 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>





```python
import matplotlib.ticker as mticker
plt.figure(figsize=(9,7))
axt = sns.barplot(x='MaritalStatus', y='percentage', hue='Churn', data=df_1)

plt.title('Users with Single have The Highest Churn Rate',color='cornflowerblue',fontsize=18,fontweight='bold')
plt.ylabel('Percentage of Total Customers in each Group', fontsize=15) # y axis label
plt.xlabel('MaritalStatus', fontsize=15) # x axis label
plt.tick_params(axis = 'both', which = 'major', labelsize = 14);

ticks_loc = axt.get_yticks()
axt.yaxis.set_major_locator(mticker.FixedLocator(ticks_loc))
axt.set_yticklabels(labels =  ['0   ', '20   ', '40   ', '60   ', '80%  ', 100])

plt.tight_layout()
```


    
![png](output_7_0.png)
    


## Insight:
* Jika dilihat dari visualisasi, tidak ada perbedaan presentase secara signifikan antara status menikah Bercerai (Divorced) dan Menikah (Married) pada jumlah churn. Hanya saja untuk status menikah Belum Menikah (Single) ada perbedaan presentase dengan status lainnya.

Rekomendasi:
* Tindakan Pencegahan: Pada visualisasi menunjukkan adanya pelanggan yang belum menikah (single) memiliki tingkat churn yang tinggi, dari sini mungkin bisa mengambil tindakan pencegahan khusus untuk segmen tersebut. Misalnya, menawarkan penawaran khusus atau layanan yang lebih baik kepada pelanggan yang belum menikah agar tidak churn

## Korelasi Tenure dan Churn rate


```python
churn_rate_by_tenure = df.groupby('Tenure')['Churn'].mean()

plt.figure(figsize=(10, 6))
churn_rate_by_tenure.plot(kind='line', marker='o', color='skyblue')
plt.title('Churn Rate by Tenure')
plt.xlabel('Tenure (Jangka Waktu Langganan)')
plt.ylabel('Churn Rate')
plt.xticks(rotation=45)
plt.grid(True)
plt.show()
```


    
![png](output_10_0.png)
    


## Insight dan Rekomendasi
Insight:
* Peningkatan Retensi: Insight menunjukkan bahwa ada tren yang menurun dalam churn rate seiring dengan meningkatnya jangka waktu langganan (Tenure). Pelanggan dengan jangka waktu langganan yang lebih lama cenderung memiliki churn rate yang lebih rendah.

Rekomendasi:
* Fokus pada Pelanggan Baru: Bisnis dapat memperkuat strategi retensi untuk pelanggan baru dengan jangka waktu langganan yang lebih pendek. Ini mungkin melibatkan insentif atau penawaran khusus untuk memotivasi mereka agar tetap menggunakan layanan lebih lama.
Analisis Segmen Pelanggan: Identifikasi segmen pelanggan dengan jangka waktu langganan yang lebih pendek dan coba pahami alasan di balik churn mereka. Dengan pemahaman yang lebih baik, bisnis dapat merancang strategi yang lebih efektif.

## Bussines insight lainnya


```python
churn_counts = df ['Churn'].value_counts()
labels = ['Churn', 'Not Churn']
colors = ['red', 'green']

plt.figure(figsize=(6, 6))
plt.pie(churn_counts, labels=labels, colors=colors, autopct='%1.1f%%', startangle=90)
plt.title('Distribution of Churn')
plt.show()

```


    
![png](output_13_0.png)
    


## Insight dan Rekomendasi
Insight:
*   Distribusi Churn: Item daftar Distribusi churn menunjukkan bahwa sebagian pelanggan telah melakukan churn

Rekomendasi:
*  Analisis Penyebab Churn: Identifikasi
penyebab utama churn dengan menganalisis data lebih mendalam. Apakah ada pola atau faktor-faktor tertentu yang menyebabkan pelanggan melakukan churn? Perlu dilakukan analisis penyebab untuk mengambil tindakan yang sesuai.
*  Program Loyalitas dan Insentif: Pertimbangkan untuk memperkenalkan program loyalitas atau insentif yang dapat memotivasi pelanggan untuk tetap menggunakan layanan. Insentif seperti cashback, diskon, atau penawaran eksklusif dapat membantu mempertahankan pelanggan.
*  Fokus pada Retensi: Meskipun sebagian besar pelanggan tetap aktif, bisnis perlu lebih memfokuskan upaya pada retensi pelanggan untuk mengurangi jumlah pelanggan yang melakukan churn.


```python
churn_rate_by_category = df.groupby('PreferedOrderCat')['Churn'].mean()

churn_rate_by_category = churn_rate_by_category.sort_values(ascending=False)

plt.figure(figsize=(10, 6))
churn_rate_by_category.plot(kind='bar', color='skyblue')
plt.title('Churn Rate by PreferredOrderCat')
plt.xlabel('PreferredOrderCat')
plt.ylabel('Churn Rate')
plt.xticks(rotation=0)
plt.show()

```


    
![png](output_15_0.png)
    


## Insight dan Rekomendasi
Insight:
*  Churn Rate Tertinggi: Kategori pesanan "Mobile Phone dan Mobile" memiliki churn rate tertinggi dibandingkan dengan kategori pesanan lainnya. Ini menunjukkan bahwa pelanggan yang memesan produk dalam kategori ini cenderung lebih mungkin untuk melakukan churn.

Rekomendasi:
* Analisis Mendalam: Bisnis perlu melakukan analisis lebih mendalam untuk memahami mengapa kategori pesanan "Mobile Phone dan Mobile" memiliki churn rate yang tinggi. Mungkin ada masalah dalam pengiriman, kualitas produk, atau pengalaman pelanggan yang perlu diidentifikasi.
* Pelacakan dan Umpan Balik Pelanggan: Bisnis dapat mengimplementasikan pelacakan dan umpan balik pelanggan yang aktif untuk kategori "Mobile Phone dan Mobile". Ini akan membantu dalam mengidentifikasi masalah dengan cepat dan mengambil tindakan yang sesuai.
* Promosi dan Diskon: Bisnis dapat mencoba menawarkan promosi khusus atau diskon dalam kategori "Mobile Phone dan Mobile" untuk memotivasi pelanggan agar tetap menggunakan layanan. Promosi ini dapat digunakan sebagai upaya untuk mengurangi churn rate.
