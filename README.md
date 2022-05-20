# Heart-failure
Este projeto tem um objetivo explorar e aplicar algoritmos de machine learning em um modelo para prever ataque cardiaco com base em um dataset obtido no kaggle

Foi utilizado o dataset que pode ser obtido nesse [link](https://www.kaggle.com/datasets/andrewmvd/heart-failure-clinical-data)

Dada a complexidade desde projeto, o mesmo foi dividido em partes

**ML**= Machine Learning

## Indice
* [Visualização dos dados](#visualização-dos-dados)
* [Aplicando ML sem hiperparemtros](#aplicando-ml-sem-hiperparametros) 
* [Aplicando ML com hiperparametros](#aplicando-ml-com-hiperparametros)
* [Referências](#referências)

# Visualização dos dados
- [Notebook dos códigos](https://github.com/gustavoramos82/Heart-failure/blob/main/heart_visualiza%C3%A7%C3%A3o.ipynb)

Para ficar mais fácil, aqui está o dicionário dos dados
- **age**: Idade
- **anaemia**: Diminuição de glóbulos vermelhos ou hemoglobina (booleano).
- **creatinine_phosphokinase**: nivel da enzima CPK no sangue (mcg/L)
- **diabetes**: Se o paciente ja teve diabetes (boleano).
- **ejection_fraction**: porcentagem do sangue que que está saindo do coração a cada contração (porcentagem).
- **high_blood_pressure**: se o paciente tem hipertensão (boleano).
- **platelets**: Platelets no sangue (kiloplatelets/mL).
- **serum_creatinine**: nivel de serum creatinine no sangue (mg/dL).
- **serum_sodium**: nivel de serum sodio no sangue (mg/dL).
- **sex**: homem ou mulher (boleano).
- **smoking**: se fuma (boleano)
- **time**: periodo de acompanhamento (dias).
- **DEATH_EVENT**: Paciente faleceu durante o periode de acompanhamento (boleano).

Podemos ter um overview dos dados vendo o histograma abaixo:

![image](https://user-images.githubusercontent.com/39843884/168858111-5d445d9f-174d-477c-bf67-59ef679c42d6.png)


  Podemos ver que temos 5 variaveis do tipo booleano, sem contar o target e que quanto a idade é a partir dos 40 anos até mais o menos 85 anos, e outros envolvendo casos que podem contribuir para o atque cardiaco como diz no trabalho de  Silva e Mantonani (2020) os fatores individuais que influenciam são: *idade, sexo, nível de instrução,composição genética, tabagismo, hábitos alimentares, sedentarismo, nivel de colesterol no sangue e obesidade* (As referencias estão ao final).
  
Podemos ver melhor pelo gráfico de pizza que o target tem mais pessoas que não sofreram ataque do que pessoas que sofreram ataque, o que pode causar um enviesamento dos dados(talvez utilizar o undersampling seja o mais indicado)

![image](https://user-images.githubusercontent.com/39843884/168860146-823da4be-3e24-48a1-a4b9-9ec8b1404aa4.png)

Podemos ver pelos grafico de histogramas a diferenças nos pesos das variaveis, sendo então que será necessária a normalização dos dados

Pela imagem abaixo, no dataset, quem tem mais de 80 anos em ambos os sexos pode sofrer o ataque cardiaco (desconsiderando un casos)

![image](https://user-images.githubusercontent.com/39843884/168916008-cce81f55-1f79-4ea9-b702-648e9c8ed598.png)

E uma coisa interessante que pode ser visto neste gráfico de dispersão e quem passou mais dias de acompnahmento em sua maioria não sofreu um ataque e quem passou menos em sua maioria sofreu um ataque.

![image](https://user-images.githubusercontent.com/39843884/168917103-2be0b385-6a8d-499f-adef-ec0f465347d6.png)

# Aplicando ML sem hiperparametros

- [Notebook dos códigos](https://github.com/gustavoramos82/Heart-failure/blob/main/heart_sem_oti.ipynb)

Com o objetivo de ter uma base antes de fazer uma otimização dos parâmetros, e com base nos trabalhos de Silva e Mantonani (2020), Santos et al (2019) e Gomes (2019), foi escolhido os seguintes algoritmos de classificação:
- random forest;
- regressão logística;
- árvore de decisão;
- naive bayes.

Usando o *cross validation* tivemos os seguintes resultados (também foi usado o *undersampling* para os modelos fiquem menos enviesados): 

![image](https://user-images.githubusercontent.com/39843884/169055606-55600dcd-ac97-47f7-aba2-b57358001b24.png)

Com esses resultados, temos que:

- A árvore de decisão foi o que teve melhor perfomace, muito próximo a ele foi o random forest;
- To os valores estão acima de 70%;
- Naive bayes foi o que teve a pior perfomace

Com isso veremos se com a otimização dos hiperparametros os modelos tem uma melhor perfomace.

# Aplicando ML com hiperparametros

## Com random forest

- [Link do noteboook](https://github.com/gustavoramos82/Heart-failure/blob/main/heart_oti_random.ipynb)

Foi utilizados o para otimização do hiperparametros o grid search e o random search e foi obtido os seguintes resultados q teve como melhores:

Com o *grid search*:
 {'bootstrap': False, 'class_weight': 'balanced', 'criterion': 'entropy', 'max_features': 'sqrt', 'n_estimators': 7, 'warm_start': True} 
 com score de 0.796221322537112

e com o *random search*:
{'warm_start': True, 'n_estimators': 6, 'max_features': 'log2', 'criterion': 'entropy', 'class_weight': 'balanced', 'bootstrap': True} 
com score de 0.769770580296896

Tivemos uma melhora nas metricas com segue abaixo:

![image](https://user-images.githubusercontent.com/39843884/169345192-c03fd432-ab67-4358-bcfe-9eb57bb0c4c1.png)

Podemos ver que com o grid search e o random search teve uma melhora, principalmente na precisão, embora que com o grid search teve uma maior melhora, mas é importante observar que o random search o processamento é mais rápido que com o grid search.

## Com regressão logística

- [Link do notebook](https://github.com/gustavoramos82/Heart-failure/blob/main/heart_oti_rg.ipynb)

Foi utilizados o para otimização do hiperparametros o grid search e o random search e foi obtido os seguintes resultados q teve como melhores:

Com o *grid search*:
{'dual': False, 'fit_intercept': True, 'max_iter': 5, 'multi_class': 'auto', 'penalty': 'l2'} 

com score de 0.7333333333333333

Com e com o *random search*:
{'penalty': 'none', 'multi_class': 'ovr', 'max_iter': 52, 'fit_intercept': True, 'dual': False}

com score de 0.7333333333333333

Assim foram obtidos os seguintes resultados, a partir das métricas:

![image](https://user-images.githubusercontent.com/39843884/169395999-e1d9d20c-bbb7-470c-9fda-06e8f7a29c9e.png)

Podemos ver que aplicando a otimização teve uma melhora, entretanto, com o grid search e o random search tiveram praticamente os mesmos resultados.

## Com árvore de decisão

-[Link do noteboo](https://github.com/gustavoramos82/Heart-failure/blob/main/arv_de_decis%C3%A3o_oti.ipynb)

Foi utilizados o para otimização do hiperparametros o grid search e o random search e foi obtido os seguintes resultados q teve como melhores:

Com o *grid search*:
{'criterion': 'gini', 'max_features': 'auto', 'max_leaf_nodes': 30, 'min_impurity_decrease': 1, 'min_samples_leaf': 1, 'splitter': 'best'}

com score de 0.4948717948717949

E com o *random search*:
{'splitter': 'best', 'min_samples_leaf': 59, 'min_impurity_decrease': 11, 'max_leaf_nodes': 45, 'max_features': 'log2', 'criterion': 'entropy'}
com score de 0.4948717948717949

Assim foram obtidos os seguintes resultados, a partir das métricas:

![image](https://user-images.githubusercontent.com/39843884/169555828-fe3dba83-f35f-4396-8fa3-f6829c26b98e.png)

Temos então, que não teve uma melhora com a otimização de parametros

:construction: Os outros algoritmos estão em processo de construção :construction:

# Referências

1 - Modelos de Machine Learning para tomada de decisão no sistema de saúde público brasileiro, Autores : Guilherme Ferreira da Silva e Daielly Melina Nassif Mantovani, 2020 (ano de publicação) pode ser acessado nesse [link](https://login.semead.com.br/23semead/anais/arquivos/1117.pdf?) .

2 - Machine learning para análises preditivas em saúde: exemplo de aplicação para predizer óbito em idosos de São Paulo, Brasil, Autores: Hellen Geremias dos Santos, Carla Ferreira do Nascimento, Rafael Izbicki,Yeda Aparecida de Oliveira Duarte e Alexandre Dias Porto Chiavegatto Filho, 2019 (ano de piblicação) pode ser acessado nesse [link](https://www.scielo.br/j/csp/a/jyhKL6G4dZhcbchMD6bcS8s/?format=pdf&lang=pt) .

3 - Classificação com Naive Bayes,  Pedro César Tebaldi Gomes, 2019 (ano de publicação), acessado em: 18/05/2022 as 10:36 (pode ser acessado nesse [aqui](https://www.datageeks.com.br/naive-bayes/)).

**Obs**: A medida que for sendo usado novos materiais, eles vão sendo adicionados.
