# Previsão de preços de passagens aéreas

Este projeto usa aprendizado de máquina para tentar prever o preço de uma passagem aérea.

Os dados estão no arquivo `Clean_Dataset.csv` e possuem informações sobre voos na Índia, como companhia aérea, cidade de origem, destino, horário, quantidade de paradas, classe e duração da viagem.

## Objetivo

O objetivo é treinar um modelo que receba as informações de um voo e estime o seu preço.

O projeto usa o modelo **Random Forest Regressor**, que combina várias árvores de decisão para fazer a previsão.

## Arquivos do projeto

- `Main.ipynb`: notebook com toda a análise e o treinamento do modelo.
- `Clean_Dataset.csv`: base de dados utilizada no projeto.

## O que é feito no notebook

O notebook segue estas etapas:

1. Carrega os dados com o Pandas.
2. Explora informações como companhias aéreas, cidades, horários, paradas e classes.
3. Remove colunas que não são necessárias para o modelo.
4. Converte informações em texto para valores numéricos.
5. Separa os dados em treino e teste.
6. Treina um modelo `RandomForestRegressor`.
7. Avalia as previsões com diferentes métricas.
8. Compara os valores reais com os valores previstos em um gráfico.
9. Analisa quais informações tiveram mais importância para o modelo.
10. Testa combinações diferentes de parâmetros para o Random Forest.

## Informações usadas pelo modelo

Entre as principais informações estão:

- companhia aérea;
- cidade de origem;
- cidade de destino;
- horário de partida;
- horário de chegada;
- quantidade de paradas;
- classe econômica ou executiva;
- duração do voo;
- quantidade de dias até a viagem.

A informação que o modelo tenta prever é a coluna `price`.

## Resultados

O primeiro modelo treinado apresentou aproximadamente os seguintes resultados:

- **R²:** 0,986
- **MAE:** 1.055
- **RMSE:** 2.713

Um R² próximo de 1 indica que o modelo conseguiu explicar boa parte da variação dos preços na divisão de dados utilizada.

Os resultados podem mudar um pouco a cada execução, porque a separação entre treino e teste não utiliza uma semente fixa no notebook.

## Como executar

Primeiro, tenha o Python instalado. Depois, instale as bibliotecas necessárias:

```bash
pip install pandas scikit-learn matplotlib scipy jupyter
```

Mantenha os arquivos `Main.ipynb` e `Clean_Dataset.csv` na mesma pasta.

Abra o notebook com:

```bash
jupyter notebook Main.ipynb
```

Depois, execute as células na ordem, do início ao fim.

## Observações importantes

- O treinamento pode demorar, pois a base possui mais de 300 mil registros.
- A etapa com `GridSearchCV` testa muitas combinações e pode levar bastante tempo.
- Nas versões atuais do scikit-learn, o valor `max_features='auto'` não é aceito pelo `RandomForestRegressor`. Use `sqrt`, `log2` ou `None`.
- O modelo faz uma estimativa baseada nos dados disponíveis. Ele não garante o preço real de uma passagem futura.

## Tecnologias utilizadas

- Python
- Pandas
- Scikit-learn
- Matplotlib
- SciPy
- Jupyter Notebook
