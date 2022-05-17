# Heart-failure
Este projeto tem um objetivo explorar e aplicar algoritmos de machine learning em um modelo para prever ataque cardiaco com base em um dataset obtido no kaggle

Foi utilizado o dataset que pode ser obtido nesse [link](https://www.kaggle.com/datasets/andrewmvd/heart-failure-clinical-data)

Dada a complexidade desde projeto, o mesmo foi dividido em partes

**ML**= Machine Learning

## Indice
* [Visualização dos dados](#visualização-dos-dados)
* [Aplicando ML sem hiperparemtros](#aplicando-ml-Hiperparametros) 
* [Aplicando ML com Hiperparametros](#aplicando-ml-com-Hiperparametros)
* [Referências](#referencias)

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

# Aplicando ML sem hiperparemtro

:construction: Em construção :construction:

# Aplicando ML com Hiperparametros

:construction: Em construção :construction:

# Referências

1 - Modelos de Machine Learning para tomada de decisão no sistema de saúde público brasileiro, Autores : Guilherme Ferreira da Silva e Daielly Melina Nassif Mantovani, 2020 (ano de publicação) pode ser acessado nesse [link](https://login.semead.com.br/23semead/anais/arquivos/1117.pdf?)

**Obs**: A medida que for sendo novos materiais, eles vão sendo adicionados.
