<img alt="rossmann" title="#logo" src='https://cdn.worldvectorlogo.com/logos/logo-rossmann-signet.svg'/>



## 1.0. Introdução ao problema de negócio

A Rossmann é uma rede de drogarias com de 4.244 lojas ativas em 7 países europeus, com 2.233 na Alemanha. O CFO da empresa planeja fazer uma reforma em cada loja, e em reunião com todos os gerentes indivíduais solicitou uma previsão das próximas 6 semanas de vendas de cada loja, pois com base nessas informações seria definido o total destinado a cada uma.

Como Cientistas de Dados da Rossmann, fomos acionados para trabalhar em uma solução.

### 1.1. Questões do negócio

- Fazer uma predição das vendas de cada loja pelas próximas 6 semanas


## 2.0. Premissas do negócio

- A coluna "Costumers" foi dropada pois é uma informação que não podemos ter no momento em que estivermos fazendo o treinamento do nosso modelo, já que não sabemos quantos clientes teremos nas nossas lojas ao longo das próximas 6 semanas

- Os valores vazios da coluna "competition_distance" foram substituídos por 3 vezes o valor maximo do competidor mais distante. Estamos assumindo que se não temos essa informação, não temos competidores mais próximos e então estamos extrapolando no valor dos dados faltantes.

- Linhas dizendo que as lojas estão fechada foram retiradas.


## 3.0. Planejamento da Solução

### 3.1. Entrega Final

- A entrega será de um Bot no Telegram, que opere 24/7 e seja capaz de devolver a soma total da predição das próximas 6 semanas de vendas da loja requisitada

<h1 align="center"><img alt="rossmann" title="#logo" src="image/bot_imagem.png" /></h1>

### 3.2. Algumas das ferramentas ultilizadas

- [Python 3.9.15]
- [Jupyter Notebook]
- [Scikit Learn]
- Boruta
- [Git] e [Github]
- [Render]
- [Telegram Bot]
- [Flask]

### 3.3. Processo até a solução

Iremos utilizar o método CRISP-DS ao longo do projeto, seguindo todas as suas etapas e visando uma primeira entrega mais
rápida porem mantendo uma boa qualidade, posteriormente poderemos voltar para o inicio do ciclo novamente afim de implementar novas tecnicas e melhorias no projeto caso o resultado final ainda não esteja satisfatório.

- **Business Problem:** Etapa em que é feito um pedido ou pergunta por parte do dono do problema.

- **Business Understand:** Entender mais sobre a motivação do CFO por trás da solicitação da predição de vendas.

- **Data Collect:** Fazer a coleta dos dados da Rossmann no [Kaggle](https://www.kaggle.com/c/rossmann-store-sales)

- **Data Cleaning:** Realizar o tratamento dos dados faltantes no nosso conjunto de dados.

- **Data Description:** Entender o quão desafiador é o problema que temos em mãos, conseguiremos responder se temos recursos para trabalhar, quais sãos os tipos de variaveis que temos , qual porcentagem de cada tipo, a quantidade de dados faltantes e a estatistica descritiva dos dados.

- **Feature Engineering:** Derivação de novas features através das originais, que irão nos ajudar na melhoria do modelo de ML, alem de ser parte importante para a validação das hipoteses levantadas e insights para o negócio.

- **EDA:** Entendimento de como as variáveis impactam no fenomeno de vendas, e qual a força desse impacto. Aqui ganhamos experiência do negócio, validaremos as hipoteses levantadas anteriormente e com isso iremos conseguir ter a percepção de quais variáveis são importantes para descrever nosso fenomeno.

- **Data Preparation:** Parte onde os dados são preparados para que possam ser recebidos pelo modelo de ML, dados categóricos e numéricos recebem diferentes tratamentos para que posssam ficar em uma escala numérica próxima.

- **Feature Selection:** Nesta etapa, devemos escolher as features que melhor descrevem o nosso fenomeno, dizemos que estas são as features mais relevantes para o aprendizado do nosso modelo. 

- **Machine Learning Modeling:** Neste projeto, escolhemos os principais algoritmos de Regressão para serem treinados com nossos dados. 

- **Hyperparameter Fine Tunning:** Utilizado a tecnica de Random Search para escolher os melhores parametros para performance do algoritmo escolhido.

- **Avaliação do modelo:** Utilizado as metricas de MAE, MAPE e RMSE para checar a performance do algoritmo.

- **Resultados financeiros:** Tradução do resultado do modelo para um resultado financeiro, tornando fácil o entendimento dos resultados.

- **Deploy para produção:** Criação de um Bot do Telegram que seja capaz de me dar o resultado da predição a partir do numero da loja escolhida. 


## 4.0. Os 5 principais insights do negócio

- ### **H1:** Lojas com maior sortimento, na média, vendem mais
<h1 align="center"><img alt="rossmann" title="#logo" src="image/sortimento.png" /></h1>

- ### **H2:** Lojas com competidores mais próximos vendem mais
<h1 align="center"><img alt="rossmann" title="#logo" src="image/competidores.png" /></h1>

- ### **H3:** Lojas com competidores por mais tempo vendem mais
<h1 align="center"><img alt="rossmann" title="#logo" src="image/temp_competidores.png" /></h1>

- ### **H4:** Lojas vendem mais durante os anos
<h1 align="center"><img alt="rossmann" title="#logo" src="image/anos.png" /></h1>

- ### **H5:** Lojas vendem mais no segundo semestre do ano, principalmente em dezembro
<h1 align="center"><img alt="rossmann" title="#logo" src="image/semestre.png" /></h1>


## 5.0. Modelo de Machine Learning

Com nossos dados já tratados e prontos para serem utilizados, escolhemos cinco algoritmos de Regressão
nesse primeiro ciclo do CRISP, onde iremos fazer o treinamento de cada um e o modelo que melhor performar será
escolhido para ter seus parametros tunados na etapa seguinte.

- Average Model (Baseline model)
- Linear Regression
- Linear Regression Regularized Model
- Random Forest Regressor
- XGBoost Regressor

### 5.1. Resultado singular

| MODEL NAME              | MAE         | MAPE     | RMSE        |
|-------------------------|-------------|----------|-------------|
| Random Forest Regressor | 673.891784  | 0.099192 | 1003.873578 |
| XGBoost Regressor       | 660.277741  | 0.095625 | 969.670432  |
| Average Model           | 1354.800353 | 0.206400 | 1835.135542 |
| Linear Regression       | 1858.712447 | 0.285170 | 2684.283301 |
| Lasso                   | 1864.159587 | 0.287184 | 2686.040626 |



### 5.2. Performance Real - Cross Validation Time Series

| MODEL NAME              | MAE               | MAPE          | RMSE               |
|-------------------------|-------------------|---------------|--------------------|
| Random Forest Regressor | 832.88 +/- 217.69 | 0.12 +/- 0.02 | 1250.45 +/- 317.81 |
| XGBoost Regressor       | 837.67 +/- 146.0  | 0.12 +/- 0.01 | 1210.7 +/- 209.0   |
| Linear Regression       | 2037.26 +/- 268.6 | 0.3 +/- 0.01  | 2908.23 +/- 399.53 |
| Lasso                   | 2085.52 +/- 327.3 | 0.29 +/- 0.01 | 2982.39 +/- 500.42 |

### 5.3. Seleção do modelo

O modelo foi o mais performatico, sendo assim, vamos escolhe-lo para seguir o nosso projeto,
pelos seguintes motivos:

- O treinamento do XGBoost é mais rápido
- Um modelo leve
- Melhor performace

### 5.4. Resultado após ajuste nos hyperparametros do modelo

Aplicado o metodo de **Random Search** para encontrar os melhores hyperparametros para serem usados no treinamento
do XGBoost, o resultado foi esse:

| MODEL NAME        | MAE               | MAPE          | RMSE               |
|-------------------|-------------------|---------------|--------------------|
| XGBoost Regressor |     637.56213     |     0.09288	  |      931.67939     |


## 6.0. Bussiness Results

A partir do resultado das predições do modelo, conseguimos montar uma tabela onde é possível ver os resultados
financeiros para o negócio. Nessa tabela, podemos enxergar qual foi a predição das vendas do modelo para determinada
loja e também quais são o pior e o melhor cenário dentro das previsões feitas.
De acordo com o resultado do modelo, a soma total de vendas de todas as farmácias ao longo de 6 semanas é:

| CENARIO         | 	VALORES         |
|-----------------|------------------|
| predições	      | R$283,314,877.05 |
| pior cenario	   | R$282,618,661.69 |
| melhor cenario	 | R$284,011,092.40 |

## 7.0 Conclusão

Conseguimos atender o pedido feito pelo CFO, entregando como resultado um bot do Telegram que pode ser acessível
por qualquer dispositivo conectado a rede. A principal funcionalidade do bot é de que ao passar o numero de uma
loja para ele, será devolvido como resposta a predição de quanto aquela loja irá faturar nas próximas seis semanas.

### Acesse o RossmanBot: [![image](https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/rossmann_prediction_bot)
 
#### Principal funcionalidade:

- Qualquer mensagem : Inicializa o bot
- Número da loja desejada: O bot devolve a predição das proximas seis semanas de vendas para aquela loja.

### Meu LinkedIn: [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gabrielsicari/)
