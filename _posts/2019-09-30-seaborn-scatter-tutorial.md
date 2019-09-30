---
layout: post
published: true
title: Seaborn scatter tutorial
subtitle: Seaborn을 이용한 데이터 분포 시각화
---
# 필요 라이브러리 import



```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
#배경스타일 지정
sns.set(style="darkgrid")
```

## 데이터셋 로드 및 조회


```python
tips = sns.load_dataset("tips")
tips
```




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
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <td>1</td>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <td>2</td>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <td>3</td>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <td>4</td>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
    <tr>
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
      <td>239</td>
      <td>29.03</td>
      <td>5.92</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <td>240</td>
      <td>27.18</td>
      <td>2.00</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <td>241</td>
      <td>22.67</td>
      <td>2.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <td>242</td>
      <td>17.82</td>
      <td>1.75</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <td>243</td>
      <td>18.78</td>
      <td>3.00</td>
      <td>Female</td>
      <td>No</td>
      <td>Thur</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 7 columns</p>
</div>




```python
sns.relplot(x="total_bill", y="tip", data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x1c6133009b0>




![output_4_1](https://user-images.githubusercontent.com/50393277/65853382-468fb980-e394-11e9-9678-7506626f8e94.png)


## hue :  marker의 색상으로 구분


```python
sns.relplot(x="total_bill", y="tip", hue="smoker", data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x1c61360a630>




![output_6_1](https://user-images.githubusercontent.com/50393277/65853383-47285000-e394-11e9-9ac3-765d9e75adde.png)


## style : marker의 모양 구분


```python
sns.relplot(x="total_bill", y="tip", hue="smoker", style="time", data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x1c61360aeb8>




![output_8_1](https://user-images.githubusercontent.com/50393277/65853384-47285000-e394-11e9-8a4f-e5d8f34520b0.png)


## palette : marker 색상 변경 ([색상표](https://seaborn.pydata.org/tutorial/color_palettes.html))


```python
sns.relplot(x="total_bill", y="tip", hue="size", palette="jet", data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x1c6146f2860>




![output_10_1](https://user-images.githubusercontent.com/50393277/65853385-47285000-e394-11e9-8922-e9306500c767.png)


## size : marker의 size 변경
## sizes : size 범위


```python
sns.relplot(x="total_bill", y="tip", size="size", sizes=(15, 200), data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x1c6147ca860>




![output_12_1](https://user-images.githubusercontent.com/50393277/65853381-468fb980-e394-11e9-8be3-d1993a4eb790.png)

