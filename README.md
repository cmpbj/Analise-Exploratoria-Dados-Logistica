# **Análise Exploratória de Dados de Logística**

*  **[Link para o notebook publicado no Kaggle](https://www.kaggle.com/code/carlosmagnopbjunior/an-lise-explorat-ria-de-dados-de-log-stica/notebook)**


## 1\. Contexto

A Loggi é uma empresa de logística que cobre o Brasil inteiro. Assim como outras empresas de logística, a Loggi enfrenta problemas como: otimização das rotas de entrega, alocação de entregas nos veículos da frota com capacidade limitada etc.

Os dados que serão utilizados abaixo são sintetizados de fontes públicas, como IBGE, IPEA etc., e representam os desafios que uma empresa como a Loggi enfrenta no dia a dia.

O Loggi Benckmark for Urban Deliveries (BUD) é [um repositório do Git Hub](https://github.com/loggi/loggibud) com dados e códigos que oferece a possibilidade de tornar novas soluções de pesquisa de operações mais próximas das aplicações do mundo real.

O dado bruto utilizado é um arquivo do tipo JSON que possui uma lista de instâncias de entregas. Cada instância representa um conjunto de entregas que devem ser realizadas pelos veículos do hub regional. Exemplo:

```json
[
  {
    "name": "cvrp-0-df-0",
    "region": "df-0",
    "origin": {"lng": -47.802664728268745, "lat": -15.657013854445248},
    "vehicle_capacity": 180,
    "deliveries": [
      {
        "id": "ed0993f8cc70d998342f38ee827176dc",
        "point": {"lng": -47.7496622016347, "lat": -15.65879313293694},
        "size": 10
      },
      {
        "id": "c7220154adc7a3def8f0b2b8a42677a9",
        "point": {"lng": -47.75887552060412, "lat": -15.651440380492554},
        "size": 10
      },
      ...
    ]
  }
]
...

```
Estes dados são um subconjunto dos ados originais presentes [no Git Hub da Loggi](https://github.com/loggi/loggibud/blob/master/docs/quickstart.md) e foi consolidado por André Perez. Ele consolidou em um único arquivo as instâncias de terino de cvrp da cidade de Brasília.

## Descrição dos dados: 

 - **name**: uma `string` com o nome único da instância;
 - **region**: uma `string` com o nome único da região do **hub**;
 - **origin**: um `dict` com a latitude e longitude da região do **hub**;
 - **vehicle_capacity**: um `int` com a soma da capacidade de carga dos **veículos** do **hub**;
 - **deliveries**: uma `list` de `dict` com as **entregas** que devem ser realizadas.

Sendo que:

 - **id**: uma `string` com o id único da **entrega**;
 - **point**: um `dict` com a latitude e longitude da **entrega**;
 - **size**: um `int` com o tamanho ou a carga que a **entrega** ocupa no **veículo**.

 ## Download da base de dados

O download do dado bruto pode ser feito neste [link](https://github.com/andre-marcos-perez/ebac-course-utils/blob/main/dataset/deliveries.json). O nome do arquivo é `deliveries.json`
