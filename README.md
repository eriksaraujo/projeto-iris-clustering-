# Projeto de Clustering — Iris com K-means

## 1. Objetivo
Aplicar um modelo de **aprendizado não supervisionado (clustering)** para agrupar flores com base em suas características físicas, sem utilizar os rótulos das espécies durante o treinamento.

## 2. Dados
Utilizei o dataset **Iris** (sklearn), que contém **150 registros** e **4 variáveis numéricas**:
- sepal length (cm)
- sepal width (cm)
- petal length (cm)
- petal width (cm)

A variável de espécie existe no dataset, mas **não foi utilizada** no pré-processamento e no treinamento do modelo (conforme orientação do exercício).

## 3. Metodologia

### 3.1 Análise exploratória
Foi utilizado um **pairplot** para observar as relações entre as variáveis.  
As variáveis relacionadas às pétalas (petal length e petal width) mostram melhor separação visual entre grupos.

### 3.2 Pré-processamento
- Verificação de valores nulos: a base não apresenta valores faltantes.
- Padronização: as variáveis foram padronizadas com **StandardScaler** (média 0 e desvio padrão 1), pois o K-means é baseado em distância e pode ser influenciado por escalas diferentes.

### 3.3 Modelagem (K-means)
Foram treinados modelos variando **k de 1 a 10** e o **WCSS (inertia)** foi armazenado para aplicação do **método do cotovelo**.

### 3.4 Avaliação
O gráfico WCSS x k foi utilizado para identificar o ponto de “cotovelo”, sugerindo **k=3** como número adequado de clusters.

### 3.5 Cluster final e visualização
Com **k=3**, o modelo foi treinado e uma coluna `cluster` foi adicionada ao dataframe.  
A visualização com pairplot usando `hue="cluster"` indica boa separação principalmente nas variáveis das pétalas.

## 4. Predição (Nova flor)
Após aplicar o mesmo pré-processamento (padronização), foi realizada a predição do cluster para uma nova flor com valores:
- 5.1, 3.5, 1.4, 0.2

O modelo retornou o cluster correspondente a esse padrão de medidas.

## 5. Conclusão
O K-means conseguiu identificar agrupamentos naturais no dataset Iris, com separação mais evidente ao utilizar variáveis das pétalas.  
O método do cotovelo indicou **k=3**, coerente com a estrutura esperada dos dados.
