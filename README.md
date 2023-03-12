# Case Study: OList Deliveries

This project will analyse a dataset from OList, an important brazilian e-commerce. Our primary objective is to analyse the data about possible late deliveries, their causes, their impacts, and what could be done about it.

## Requisites
This analysis uses the following libraries: pandas, sqlalchemy, numpy and seaborn. The dataset can be found in <a href=https://www.kaggle.com/olistbr/brazilian-ecommerce>Kaggle</a>.

## Setup of the Analysis
The analysis was made combining SQL queries with Python, using Jupyter Notebook. We extracted relevant data and used pandas and seaborn libraries for better understanding of the data.

## First Analysis: The influence of the distance
Our first question is: is the distance between seller and customer relevant in the late deliveries occurrences? To answer that using the data available, we created a binary column which verified if the seller and the customer lived in the same state. The results are the following:

<table>
 <tr>
  <th>Live in the Same State?</th>
  <th>Quantity of Late Deliveries</th>
 </tr>
 <tr>
  <td>Yes</td>
  <td>2384</td>
 </tr>
  <td>No</td>
  <td>6331</td>
 </tr>
</table>

This already shows us that there are almost three times more late deliveries when they don't live in the same state, which indicates the importance of the distance in the time of delivery. Note that this says more about the logistic chain of deliveries than of literal geographical distance, since it is possible that nearby cities in different states take time to receive their shipments because of the logistic of it.

We can see the specifics of each seller and customer state in the following pivot table:
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>customer_state</th>
      <th>AL</th>
      <th>AM</th>
      <th>BA</th>
      <th>CE</th>
      <th>DF</th>
      <th>ES</th>
      <th>GO</th>
      <th>MA</th>
      <th>MG</th>
      <th>MS</th>
      <th>MT</th>
      <th>PA</th>
      <th>PB</th>
      <th>PE</th>
      <th>PI</th>
      <th>PR</th>
      <th>RJ</th>
      <th>RN</th>
      <th>RO</th>
      <th>RS</th>
      <th>SC</th>
      <th>SE</th>
      <th>SP</th>
      <th>TO</th>
    </tr>
    <tr>
      <th>seller_state</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>BA</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>5.23</td>
      <td>----</td>
    </tr>
    <tr>
      <th>DF</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>0.93</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>8.18</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>2.68</td>
      <td>----</td>
    </tr>
    <tr>
      <th>ES</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>9.24</td>
      <td>----</td>
    </tr>
    <tr>
      <th>GO</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>3.55</td>
      <td>----</td>
    </tr>
    <tr>
      <th>MA</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>26.72</td>
      <td>----</td>
    </tr>
    <tr>
      <th>MG</th>
      <td>----</td>
      <td>----</td>
      <td>9.53</td>
      <td>----</td>
      <td>2.71</td>
      <td>6.31</td>
      <td>2.89</td>
      <td>----</td>
      <td>2.98</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>7.56</td>
      <td>----</td>
      <td>1.69</td>
      <td>8.73</td>
      <td>----</td>
      <td>----</td>
      <td>4.76</td>
      <td>8.68</td>
      <td>----</td>
      <td>3.98</td>
      <td>----</td>
    </tr>
    <tr>
      <th>PE</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>2.83</td>
      <td>----</td>
    </tr>
    <tr>
      <th>PR</th>
      <td>----</td>
      <td>----</td>
      <td>14.97</td>
      <td>----</td>
      <td>4.49</td>
      <td>8.55</td>
      <td>----</td>
      <td>----</td>
      <td>5.54</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>11.76</td>
      <td>----</td>
      <td>4.23</td>
      <td>12.73</td>
      <td>----</td>
      <td>----</td>
      <td>4.6</td>
      <td>7.54</td>
      <td>----</td>
      <td>3.58</td>
      <td>----</td>
    </tr>
    <tr>
      <th>RJ</th>
      <td>----</td>
      <td>----</td>
      <td>10.34</td>
      <td>----</td>
      <td>10.53</td>
      <td>1.8</td>
      <td>7.09</td>
      <td>----</td>
      <td>6.91</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>12.04</td>
      <td>----</td>
      <td>7.69</td>
      <td>5.97</td>
      <td>----</td>
      <td>----</td>
      <td>9.25</td>
      <td>9.42</td>
      <td>----</td>
      <td>8.23</td>
      <td>----</td>
    </tr>
    <tr>
      <th>RS</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>2.28</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>4.7</td>
      <td>8.99</td>
      <td>----</td>
      <td>----</td>
      <td>6.73</td>
      <td>0.0</td>
      <td>----</td>
      <td>2.10</td>
      <td>----</td>
    </tr>
    <tr>
      <th>SC</th>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>4.76</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>----</td>
      <td>3.09</td>
      <td>10.0</td>
      <td>----</td>
      <td>----</td>
      <td>5.74</td>
      <td>6.75</td>
      <td>----</td>
      <td>4.05</td>
      <td>----</td>
    </tr>
    <tr>
      <th>SP</th>
      <td>24.13</td>
      <td>4.55</td>
      <td>14.33</td>
      <td>14.81</td>
      <td>8.26</td>
      <td>13.78</td>
      <td>8.52</td>
      <td>21.55</td>
      <td>6.01</td>
      <td>13.37</td>
      <td>6.61</td>
      <td>12.61</td>
      <td>10.0</td>
      <td>9.78</td>
      <td>17.2</td>
      <td>5.07</td>
      <td>14.41</td>
      <td>11.47</td>
      <td>4.52</td>
      <td>7.13</td>
      <td>10.4</td>
      <td>17.84</td>
      <td>5.97</td>
      <td>12.23</td>
    </tr>
  </tbody>
</table>

The top five late deliveries by seller state and customer state are in the following table:
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>seller_state</th>
      <th>customer_state</th>
      <th>qtd_late_deliveries</th>
      <th>total_shipments</th>
      <th>late_rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MA</td>
      <td>SP</td>
      <td>35.0</td>
      <td>131</td>
      <td>26.72</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SP</td>
      <td>AL</td>
      <td>69.0</td>
      <td>286</td>
      <td>24.13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SP</td>
      <td>MA</td>
      <td>122.0</td>
      <td>566</td>
      <td>21.55</td>
    </tr>
    <tr>
      <th>3</th>
      <td>SP</td>
      <td>SE</td>
      <td>43.0</td>
      <td>241</td>
      <td>17.84</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SP</td>
      <td>PI</td>
      <td>65.0</td>
      <td>378</td>
      <td>17.20</td>
    </tr>
  </tbody>
</table>

These two tables show us that the distance is very relevant, since the worst situation is in the delivery of shipments from São Paulo, in southeast Brazil, to northeast states as Maranhão (MA) and Alagoas (AL). The following heatmap illustrates this:

![heatmap distancia atrasos](https://user-images.githubusercontent.com/110355804/224564559-1e07550e-ffde-4124-9f49-62d381efe0bc.png)



## Conclusion


