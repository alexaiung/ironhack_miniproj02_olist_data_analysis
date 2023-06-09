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


## Second Analysis: The relevance of the product category
The late deliveries may be related not only to the distance, but to the type of product which is being sold. The following table illustrates that this hypothesis is correct:

Top-10 Categories by Quantity of Late Deliveries:
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>product_category_name</th>
      <th>qtd_total</th>
      <th>atraso</th>
      <th>taxa_atrasos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>audio</td>
      <td>364</td>
      <td>46.0</td>
      <td>0.1264</td>
    </tr>
    <tr>
      <td>fashion_underwear_e_moda_praia</td>
      <td>131</td>
      <td>16.0</td>
      <td>0.1221</td>
    </tr>
    <tr>
      <td>artigos_de_natal</td>
      <td>153</td>
      <td>18.0</td>
      <td>0.1176</td>
    </tr>
    <tr>
      <td>livros_tecnicos</td>
      <td>267</td>
      <td>29.0</td>
      <td>0.1086</td>
    </tr>
    <tr>
      <td>casa_conforto</td>
      <td>434</td>
      <td>44.0</td>
      <td>0.1014</td>
    </tr>
    <tr>
      <td>construcao_ferramentas_iluminacao</td>
      <td>304</td>
      <td>30.0</td>
      <td>0.0987</td>
    </tr>
    <tr>
      <td>alimentos</td>
      <td>510</td>
      <td>49.0</td>
      <td>0.0961</td>
    </tr>
    <tr>
      <td>eletronicos</td>
      <td>2767</td>
      <td>266.0</td>
      <td>0.0961</td>
    </tr>
    <tr>
      <td>beleza_saude</td>
      <td>9670</td>
      <td>858.0</td>
      <td>0.0887</td>
    </tr>
    <tr>
      <td>moveis_escritorio</td>
      <td>1691</td>
      <td>149.0</td>
      <td>0.0881</td>
    </tr>
  </tbody>
</table>

Top-5 Categories with the Better Late Deliveries Rates:
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>product_category_name</th>
      <th>qtd_total</th>
      <th>atraso</th>
      <th>taxa_atrasos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>moveis_cozinha_area_de_servico_jantar_e_jardim</td>
      <td>281</td>
      <td>12.0</td>
      <td>0.0427</td>
    </tr>
    <tr>
      <td>agro_industria_e_comercio</td>
      <td>212</td>
      <td>9.0</td>
      <td>0.0425</td>
    </tr>
    <tr>
      <td>market_place</td>
      <td>311</td>
      <td>13.0</td>
      <td>0.0418</td>
    </tr>
    <tr>
      <td>telefonia_fixa</td>
      <td>264</td>
      <td>11.0</td>
      <td>0.0417</td>
    </tr>
    <tr>
      <td>climatizacao</td>
      <td>297</td>
      <td>11.0</td>
      <td>0.0370</td>
    </tr>
  </tbody>
</table>

![barplot categorias atrasos](https://user-images.githubusercontent.com/110355804/224565019-6e59a01d-ef67-46a3-b3a0-f3e31f547b61.png)

The displayed data shows us that some product categories are more prone to late deliveries. Interestingly, this is not related with the dimensions of the product: some categories, such as 'fashion_underwear' and 'technical books', are relatively small products. On the other hand, in the list of the 5 categories with the least late deliveries rates, we have large products categories such as 'construction_tools_safety' and 'agro_industry_and_commerce'.

## Third Analysis: The customer satisfaction and the late deliveries
Our third analysis is about the impact of the late deliveries and the review that the customers gave. This allowed us to understand how much they value deliveries on time, allowing to think of the need for better date deliveries estimates. The following table shows us the mean score given if the product was delivered late or not, while the second table shows us the proportion of late deliveries according to each score given (from 1 to 5).

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>qtd</th>
      <th>late?</th>
      <th>mean_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>71916</td>
      <td>0</td>
      <td>4.2121</td>
    </tr>
    <tr>
      <td>6000</td>
      <td>1</td>
      <td>2.5578</td>
    </tr>
  </tbody>
</table>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>review_score</th>
      <th>total_reviews</th>
      <th>late?</th>
      <th>proportion</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>9001</td>
      <td>2786.0</td>
      <td>0.3095</td>
    </tr>
    <tr>
      <td>2</td>
      <td>2468</td>
      <td>462.0</td>
      <td>0.1872</td>
    </tr>
    <tr>
      <td>3</td>
      <td>6413</td>
      <td>689.0</td>
      <td>0.1074</td>
    </tr>
    <tr>
      <td>4</td>
      <td>15080</td>
      <td>745.0</td>
      <td>0.0494</td>
    </tr>
    <tr>
      <td>5</td>
      <td>44954</td>
      <td>1318.0</td>
      <td>0.0293</td>
    </tr>
  </tbody>
</table>

![barplot media reviews](https://user-images.githubusercontent.com/110355804/226129895-acffb6a4-59a8-440c-a73c-d2952777b554.png)

![barplot soma review proporcao](https://user-images.githubusercontent.com/110355804/226129902-cea3d983-10d9-4a0a-b1d7-351abfd06174.png)

With the intention of deepening the analysis, we calculated the impact that the scores would have with 50% less late deliveries. The estimated mean score are in the following table:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Current Mean</th>
      <th>Mean - 50% less late deliveries</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4.084709</td>
      <td>4.148404</td>
    </tr>
  </tbody>
</table>

## Conclusion
Our analysis showed how much the late deliveries impact in the overall experience of the customers. There are definitely certain correlations between the recurrence of delayed deliveries, the distance of seller and customer, and the category of the product; however, more analysis is needed so we can understand what of it is just a correlation and what is causality. It is interesting compare the data about distance and product categories, so we can see if the delays are somehow caused not by the product category but by the distance that they usually travel.

In more concrete terms, we already see that there is a huge amount of delays when the seller or the customer are in the northeast region of Brazil. This could lead to better decision-making, prioritizing the search for new sellers in the area, and a better delivery system. This will impact positively the customer experience.

