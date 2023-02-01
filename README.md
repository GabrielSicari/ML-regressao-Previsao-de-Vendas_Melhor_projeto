![image](https://user-images.githubusercontent.com/104724947/216117054-898e897b-998d-45aa-9f5a-d3ab9322a884.png)

## 1.0. Introdução ao problema de negócio
A Rossmann é uma rede de drogarias com mais de 3.000 lojas ativas em 7 países europeus. O CFO da empresa planeja fazer uma reforma em cada loja, e em reunião com todos os gerentes indivíduais solicitou uma previsão diaria das próximas 6 semanas de vendas de cada loja, pois com base nessas informações seria definido o total destinado a cada uma.

Como Cientistas de Dados da Rossmann, fomos acionados para trabalhar em uma solução.

#1.1. Questões do negócio
Fazer uma predição das vendas diarias de cada loja pelas próximas 6 semanas

##2.0. Premissas do negócio
A coluna "Costumers" foi dropada pois é uma informação que não podemos ter no momento em que estivermos fazendo o treinamento do nosso modelo, já que não sabemos quantos clientes teremos nas nossas lojas ao longo das próximas 6 semanas

Os valores vazios da coluna "competition_distance" foram substituídos por 3 vezes o valor maximo do competidor mais distante. Estamos assumindo que se não temos essa informação, não temos competidores mais próximos e então estamos extrapolando no valor dos dados faltantes.

##3.0. Planejamento da Solução
#3.1. Entrega Final
A entrega será de um Bot no Telegram, que opere 24/7 e seja capaz de devolver a soma total da predição das próximas 6 semanas de vendas da loja requisitada
