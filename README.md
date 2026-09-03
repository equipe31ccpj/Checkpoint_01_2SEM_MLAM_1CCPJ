# Checkpoint 01 — Modelagem Linear para Aprendizado de Máquina


## Modelos de Classificação

Este projeto tem como objetivo aplicar conceitos de **Machine Learning** para resolver problemas de classificação utilizando Python e bibliotecas de aprendizado de máquina.

O trabalho apresenta um fluxo completo de Ciência de Dados, envolvendo:

* Carregamento dos dados;
* Exploração e análise do dataset;
* Pré-processamento;
* Separação entre dados de treinamento e teste;
* Treinamento dos modelos;
* Avaliação dos resultados;
* Comparação entre os algoritmos utilizados.

O projeto foi dividido em três exercícios:

1. **Saúde** — Breast Cancer Wisconsin;
2. **Economia** — Adult Census Income;
3. **Energia** — Classificação da estabilidade de uma rede elétrica.

---

## 2. Integrantes

* **Maria Eduarda Rocha Benjamim** — RM: **570554**
* **Pedro Henrique Neves** — RM: **571382**

**Turma:** 1CCPJ
**Data:** 02/09/2026

---

## 3. Tema e dataset escolhidos

Para o terceiro exercício, o grupo escolheu o tema **Energia**, utilizando um dataset relacionado à estabilidade de uma rede elétrica.

O dataset escolhido foi:

**Electrical Grid Stability Simulated Data**

O conjunto de dados apresenta informações obtidas por meio de simulações de uma rede elétrica, permitindo analisar diferentes condições de funcionamento e determinar se a rede está **estável ou instável**.

Cada registro representa uma simulação das condições operacionais de uma rede elétrica sintética composta por quatro nós: um gerador e três consumidores.

---

## 4. Fonte dos dados

Os dados foram obtidos no **UCI Machine Learning Repository**.

Dataset:

**Electrical Grid Stability Simulated Data**

Fonte:

https://archive.ics.uci.edu/dataset/471/electrical+grid+stability+simulated+data

Arquivo utilizado:

`Data_for_UCI_named.csv`

O dataset possui **10.000 registros e 14 colunas**, sendo variáveis numéricas relacionadas às condições da rede e a variável categórica utilizada como alvo.

---

## 5. Variável-alvo

A variável-alvo utilizada no problema de classificação é:

`stabf`

Essa variável representa a classificação da estabilidade da rede elétrica.

Ela possui duas classes:

* `stable` — rede estável;
* `unstable` — rede instável.

A variável `stab` também está presente no dataset como um indicador numérico de estabilidade. Porém, ela não foi utilizada como variável de entrada dos modelos, pois está diretamente relacionada à classificação `stabf`.

As principais variáveis utilizadas como entrada foram:

* `tau1`
* `tau2`
* `tau3`
* `tau4`
* `p1`
* `p2`
* `p3`
* `p4`
* `g1`
* `g2`
* `g3`
* `g4`

---

## 6. Etapas realizadas na implementação

O desenvolvimento do projeto foi realizado seguindo as principais etapas de um processo de Machine Learning.

### 6.1. Carregamento dos dados

Inicialmente, o arquivo CSV foi carregado utilizando a biblioteca **Pandas**.

Foi realizada uma análise inicial para verificar:

* quantidade de linhas e colunas;
* tipos das variáveis;
* existência de valores ausentes;
* existência de registros duplicados;
* distribuição das classes.

### 6.2. Exploração dos dados

Foram utilizados gráficos para compreender melhor o comportamento das variáveis.

Entre as análises realizadas estão:

* Histograma da variável `tau1`;
* Gráfico de dispersão entre `p1` e `g1`;
* Análise de correlação entre as variáveis.

Essas visualizações ajudaram a identificar padrões e relações entre as características do dataset.

### 6.3. Pré-processamento

Na etapa de preparação dos dados:

1. A variável `stabf` foi definida como variável-alvo;
2. A variável `stab` foi retirada das variáveis de entrada;
3. Os dados foram divididos em conjuntos de treinamento e teste;
4. Foi utilizado `random_state=42` para permitir a reprodução dos resultados;
5. Os dados utilizados pela Regressão Logística foram padronizados utilizando `StandardScaler`.

A divisão utilizada foi de:

* **80% para treinamento**
* **20% para teste**

### 6.4. Treinamento dos modelos

Foram utilizados dois algoritmos de classificação:

* **Regressão Logística**
* **Random Forest**

A Regressão Logística foi utilizada como um modelo de classificação linear.

O Random Forest foi utilizado como um modelo baseado em várias árvores de decisão, permitindo comparar seu desempenho com a Regressão Logística.

---

## 7. Algoritmos utilizados

### Regressão Logística

A **Regressão Logística** é um algoritmo utilizado para problemas de classificação.

Neste projeto, ela foi utilizada para classificar cada registro como:

* `stable`;
* `unstable`.

Antes do treinamento, os dados foram padronizados com `StandardScaler`.

### Random Forest

O **Random Forest** é um algoritmo que combina várias árvores de decisão para realizar a classificação.

No projeto foi utilizado um Random Forest com **100 árvores**, permitindo comparar seu desempenho com a Regressão Logística.

---

## 8. Avaliação dos modelos

Os modelos foram avaliados utilizando principalmente a **acurácia**, que representa a proporção de previsões realizadas corretamente pelo modelo.

Também foram utilizadas **matrizes de confusão** para observar a quantidade de classificações corretas e incorretas para cada classe.

### Resultados obtidos

**Regressão Logística:**

* Acurácia: **84,19%**

Matriz de confusão:

```text
[[5739  436]
 [ 850 1110]]
```

**Random Forest:**

* Acurácia: **84,76%**

Matriz de confusão:

```text
[[5715  460]
 [ 780 1180]]
```

### Comparação

O Random Forest apresentou o melhor resultado entre os dois modelos.

| Modelo              | Acurácia |
| ------------------- | -------: |
| Regressão Logística |   84,19% |
| Random Forest       |   84,76% |

A diferença entre os modelos foi de aproximadamente **0,57 ponto percentual**, com vantagem para o Random Forest.

---

## 9. Principais resultados

Os resultados mostram que os dois algoritmos conseguiram realizar a classificação da estabilidade da rede elétrica com desempenho semelhante.

A **Regressão Logística** apresentou uma acurácia de **84,19%**, enquanto o **Random Forest** apresentou **84,76%**.

Apesar da diferença ser pequena, o Random Forest apresentou o melhor desempenho no conjunto de teste.

A utilização das matrizes de confusão também permitiu observar os acertos e erros dos modelos em cada uma das classes.

---

## 10. Bibliotecas utilizadas

As principais bibliotecas utilizadas no projeto foram:

* **Pandas** — carregamento e manipulação dos dados;
* **NumPy** — operações numéricas;
* **Matplotlib** — criação de gráficos;
* **Seaborn** — visualização e análise de correlação;
* **Scikit-learn** — pré-processamento, treinamento e avaliação dos modelos.

---

## 11. Instruções para executar o notebook

Para executar o projeto, é necessário ter:

* Python 3.10 ou superior;
* Jupyter Notebook ou Google Colab;
* Arquivo `Data_for_UCI_named.csv`;
* Notebook `Checkpoint_01_2SEM_MLAM_1CCPKJ.ipynb`.

### Instalação das bibliotecas

Caso seja necessário instalar as bibliotecas, execute:

```python
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Execução

1. Baixe ou abra o notebook no **Google Colab** ou **Jupyter Notebook**.
2. Coloque o arquivo `Data_for_UCI_named.csv` no mesmo ambiente do notebook.
3. Instale as bibliotecas necessárias.
4. Execute as células do notebook na ordem.
5. Aguarde a execução das análises, gráficos, treinamento dos modelos e avaliações.
6. Verifique os resultados apresentados ao final do notebook.

---

## 12. Conclusão do grupo

O desenvolvimento deste projeto permitiu aplicar, na prática, diferentes etapas de um processo de Machine Learning, desde a exploração e preparação dos dados até o treinamento e avaliação dos modelos de classificação.

A análise do dataset de estabilidade de uma rede elétrica mostrou que é possível utilizar técnicas de aprendizado de máquina para identificar se determinadas condições de operação estão associadas a uma rede estável ou instável.

Entre os modelos avaliados, o **Random Forest apresentou o melhor resultado**, alcançando uma acurácia de **84,76%**, enquanto a Regressão Logística alcançou **84,19%**.

Apesar dos bons resultados, existem possibilidades de melhoria, como a utilização de validação cruzada, ajuste dos hiperparâmetros dos modelos e análise de outras métricas, como **precisão, recall e F1-score**.

Dessa forma, o projeto contribuiu para a compreensão prática de conceitos de classificação e mostrou como técnicas de Machine Learning podem ser aplicadas à análise de problemas relacionados à área de energia.
