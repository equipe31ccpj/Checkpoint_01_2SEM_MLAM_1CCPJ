# Checkpoint_01_2SEM_MLAM_1CCPJ

## Modelos de Classificação

# Checkpoint 01 — Modelagem Linear Para Aprendizado de Máquina

Avaliação prática de modelos de classificação, aplicando um fluxo completo de ciência de dados: carga, exploração, pré-processamento, modelagem e avaliação.

**Integrantes do grupo:**
Maria Eduarda Rocha Benjamim
Pedro Henrique Neves

**Turma:** 1CCPJ

**Data:** 02/09/2026

---

## Sobre o projeto

O notebook apresenta um fluxo completo de classificação utilizando diferentes conjuntos de dados e modelos de aprendizado de máquina.

O trabalho está dividido em três exercícios:

| Exercício | Tema                                                             | Status            |
| --------- | ---------------------------------------------------------------- | ----------------- |
| 1         | Saúde — classificação de tumores (Breast Cancer Wisconsin)       | Exemplo resolvido |
| 2         | Economia — classificação de faixa de renda (Adult Census Income) | Concluído         |
| 3         | Energia — classificação da estabilidade de uma rede elétrica     | Concluído         |

Cada exercício trabalha etapas importantes do processo de Ciência de Dados:

1. Carga dos dados a partir de um arquivo CSV.
2. Inspeção das dimensões, tipos e amostra dos dados.
3. Verificação de valores ausentes e duplicados.
4. Análise exploratória e distribuição das classes.
5. Separação entre variáveis preditoras (`X`) e variável-alvo (`y`).
6. Divisão dos dados em treino e teste.
7. Aplicação do pré-processamento necessário.
8. Treinamento de modelos de classificação.
9. Avaliação dos modelos por meio da acurácia.
10. Análise da matriz de confusão.
11. Comparação dos resultados.
12. Discussão das limitações e possíveis melhorias.

---

# Exercício 3 — Desafio real

## Tema escolhido

**Energia — Classificação da estabilidade de uma rede elétrica.**

O objetivo é utilizar técnicas de aprendizado de máquina para classificar uma rede elétrica simulada como **estável** ou **instável**, a partir de características relacionadas às condições de operação da rede.

O dataset utilizado possui **10.000 registros e 14 colunas**, sendo 13 variáveis numéricas e uma variável categórica (`stabf`).

### Fonte do dataset

**Electrical Grid Stability Simulated Data — UCI Machine Learning Repository**

https://archive.ics.uci.edu/dataset/471/electrical+grid+stability+simulated+data

O notebook utiliza o arquivo:

`Data_for_UCI_named.csv`

---

## Definição do problema

### Unidade representada por cada linha

Cada linha representa uma **simulação individual das condições operacionais de uma rede elétrica sintética**, composta por quatro nós: um gerador e três consumidores.

### Variável-alvo

A classificação utiliza a estabilidade da rede elétrica.

A base possui:

* `stab`: indicador numérico de estabilidade;
* `stabf`: classificação final da estabilidade, com as categorias `stable` e `unstable`.

A variável `stab` pode ser utilizada para representar o indicador contínuo de estabilidade, enquanto `stabf` representa diretamente as duas classes utilizadas no problema de classificação.

### Significado das classes

**Classe 0 — Estável (`stable`)**

Representa uma condição em que a rede elétrica permanece em equilíbrio dinâmico.

**Classe 1 — Instável (`unstable`)**

Representa uma condição em que a rede perde estabilidade e pode caminhar para uma situação de falha do sistema.

No conjunto analisado, a variável `stabf` apresenta exatamente duas classes: `stable` e `unstable`.

---

## Variáveis utilizadas

O dataset apresenta as seguintes variáveis:

* `tau1`, `tau2`, `tau3`, `tau4` — parâmetros relacionados às condições dos nós da rede;
* `p1`, `p2`, `p3`, `p4` — valores relacionados à potência;
* `g1`, `g2`, `g3`, `g4` — parâmetros relacionados à geração;
* `stab` — indicador numérico de estabilidade;
* `stabf` — classificação da estabilidade.

A base possui 10.000 registros e não apresenta valores ausentes ou linhas duplicadas na verificação realizada no notebook.

---

## Decisão que o modelo pretende apoiar

O modelo pretende apoiar a **identificação antecipada de situações de instabilidade na rede elétrica**, permitindo que ações preventivas de controle de carga e geração sejam consideradas antes que uma condição crítica provoque falhas operacionais.

A ideia é utilizar a classificação como uma ferramenta de apoio à tomada de decisão, e não como uma garantia de que uma falha ocorrerá.

---

## Possíveis consequências de falsos positivos

Um falso positivo ocorre quando o modelo classifica uma rede como **instável**, mas ela está realmente **estável**.

Isso pode provocar:

* ações preventivas desnecessárias;
* desligamento ou redução desnecessária de geração;
* corte preventivo de carga;
* custos operacionais evitáveis;
* interrupções desnecessárias no fornecimento de energia.

---

## Possíveis consequências de falsos negativos

Um falso negativo ocorre quando o modelo classifica a rede como **estável**, mas ela está realmente **instável**.

Esse tipo de erro é especialmente importante nesse problema, pois pode fazer com que uma situação de risco não seja identificada a tempo, aumentando a possibilidade de:

* falhas em equipamentos;
* falhas em cascata;
* interrupções no fornecimento;
* perda de estabilidade do sistema;
* ocorrência de um apagão.

---

# Análise exploratória

A análise inicial mostrou que o dataset possui **10.000 linhas e 14 colunas**, sendo a maior parte das variáveis do tipo numérico (`float64`). Não foram encontrados valores ausentes nem registros duplicados.

Foram realizadas visualizações para compreender melhor os dados, incluindo:

1. **Histograma da variável `tau1`**, permitindo observar sua distribuição.
2. **Gráfico de dispersão entre `p1` e `g1`**, buscando visualizar a relação entre essas variáveis.
3. **Mapa de correlação das variáveis**, permitindo observar relações entre os atributos utilizados na análise.

A variável `stab` apresenta valores tanto positivos quanto negativos, enquanto `stabf` transforma o resultado em duas categorias: `stable` e `unstable`.

---

# Pré-processamento

Antes do treinamento dos modelos, os dados foram preparados para que pudessem ser utilizados pelos algoritmos de aprendizado de máquina.

Foram realizadas etapas de:

* separação entre variáveis preditoras e variável-alvo;
* divisão dos dados em treino e teste;
* transformação das variáveis quando necessária;
* padronização dos dados para a Regressão Logística.

Foi utilizado `random_state=42` para permitir a reprodução dos resultados.

---

# Modelos utilizados

Foram comparados dois modelos de classificação:

### Regressão Logística

A Regressão Logística foi utilizada como modelo de referência. Ela busca estimar a probabilidade de cada registro pertencer a uma das classes.

### Random Forest

O segundo modelo utilizado foi o **Random Forest**, composto por várias árvores de decisão. O modelo foi configurado com `random_state=42` e 100 árvores (`n_estimators=100`).

A comparação dos dois modelos permite verificar qual apresentou melhor desempenho na mesma divisão dos dados.

---

# Resultados

Os resultados obtidos no notebook foram:

| Modelo              |   Acurácia |
| ------------------- | ---------: |
| Regressão Logística | **84,19%** |
| Random Forest       | **84,76%** |

O **Random Forest apresentou a maior acurácia**, com aproximadamente **0,57 ponto percentual** de vantagem sobre a Regressão Logística.

Portanto, considerando apenas a acurácia obtida nessa divisão dos dados, o Random Forest apresentou o melhor resultado.

---

# Matriz de confusão

### Regressão Logística

A matriz de confusão registrada no notebook foi:

```text
[[5739  436]
 [ 850 1110]]
```

A matriz permite identificar os acertos e erros do modelo em cada classe.

### Random Forest

A matriz de confusão registrada para o Random Forest foi:

```text
[[5715  460]
 [ 780 1180]]
```

O Random Forest apresentou uma quantidade maior de acertos na segunda classe e uma quantidade menor de erros nessa classe em comparação com a Regressão Logística.

A matriz de confusão é importante porque a acurácia sozinha não mostra como os erros estão distribuídos entre as classes.

---

# Principais conclusões

A análise mostrou que é possível utilizar modelos de classificação para identificar diferentes condições de estabilidade de uma rede elétrica simulada.

O dataset possui 10.000 registros e apresentou uma estrutura adequada para a aplicação dos modelos, sem valores ausentes ou registros duplicados. As visualizações permitiram observar a distribuição das variáveis e possíveis relações entre os atributos.

Na comparação dos modelos, a **Regressão Logística apresentou acurácia de 84,19%**, enquanto o **Random Forest apresentou 84,76%**. Dessa forma, o Random Forest foi o modelo com melhor desempenho nessa divisão dos dados.

A matriz de confusão mostrou que os dois modelos conseguem realizar uma quantidade significativa de classificações corretas, mas ainda apresentam erros entre as classes. Por isso, a acurácia não deve ser considerada a única métrica para avaliar o desempenho.

Uma das principais limitações é que os modelos foram avaliados utilizando uma única divisão entre treino e teste. Além disso, foram utilizados hiperparâmetros simples, sem uma busca sistemática por configurações melhores.

Em uma próxima versão, seria interessante utilizar métricas adicionais, como **precisão, recall e F1-score**, além de técnicas como validação cruzada e `GridSearchCV` para buscar melhores hiperparâmetros.

> O modelo não deve ser interpretado como prova ou garantia de estabilidade ou instabilidade da rede. Ele representa apenas uma estimativa estatística baseada nos dados utilizados e está sujeito a erros e limitações.

---

# Estrutura do notebook

```text
Checkpoint_01_2SEM_MLAM.ipynb

├── Exercício 1 — Saúde (exemplo resolvido)
│
├── Exercício 2 — Economia (Adult Census Income)
│
├── Exercício 3 — Desafio real (Energia)
│
└── Parte 2 — Roteiro de apresentação
```

---

# Roteiro da apresentação

A apresentação do grupo pode seguir a seguinte ordem:

1. **Problema e dados**

   * Tema: Energia
   * Dataset utilizado
   * Fonte
   * Unidade de análise
   * Variável-alvo
   * Classes

2. **Análise exploratória**

   * Quantidade de registros
   * Variáveis utilizadas
   * Ausentes e duplicados
   * Principais gráficos e padrões observados

3. **Pré-processamento**

   * Separação entre `X` e `y`
   * Divisão treino/teste
   * Padronização das variáveis

4. **Modelagem**

   * Regressão Logística
   * Random Forest
   * Motivo da comparação dos modelos

5. **Resultados**

   * Regressão Logística: 84,19%
   * Random Forest: 84,76%
   * Matrizes de confusão

6. **Conclusão**

   * Random Forest apresentou o melhor resultado
   * Limitações
   * Possíveis melhorias

---

# Como executar

1. Coloque o arquivo `Data_for_UCI_named.csv` na mesma pasta do notebook.
2. Abra o notebook no Google Colab ou Jupyter Notebook.
3. Instale as dependências, caso necessário:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

4. Execute o notebook do início ao fim utilizando **Run All**.
5. Verifique se os códigos executam sem erros.
6. Mantenha os resultados, tabelas, gráficos e matrizes de confusão visíveis na entrega.

---

# Bibliotecas utilizadas

* **pandas** — leitura e manipulação dos dados;
* **numpy** — operações numéricas;
* **matplotlib** — criação de gráficos;
* **seaborn** — visualização e análise exploratória;
* **scikit-learn** — pré-processamento, treinamento dos modelos e avaliação.

---

# Limitações gerais

* Os modelos utilizam configurações relativamente simples.
* Não foi realizada uma busca sistemática de hiperparâmetros.
* A avaliação foi realizada com uma divisão específica dos dados.
* A acurácia, analisada isoladamente, pode não representar completamente o desempenho do modelo em cada classe.
* A matriz de confusão deve ser considerada juntamente com outras métricas.
* O dataset é baseado em **simulações de uma rede elétrica**, portanto os resultados não devem ser interpretados automaticamente como desempenho em uma rede elétrica real.

---

# Considerações finais

O projeto permitiu aplicar, de forma prática, as principais etapas de um processo de aprendizado de máquina supervisionado: desde a leitura e exploração dos dados até o treinamento e comparação dos modelos.

No desafio de Energia, o **Random Forest obteve o melhor resultado entre os modelos avaliados**, alcançando **84,76% de acurácia**, contra **84,19% da Regressão Logística**.

Apesar do resultado, o modelo deve ser entendido como uma ferramenta de apoio baseada nos dados disponíveis, sendo necessário realizar análises adicionais, utilizar outras métricas e testar diferentes configurações antes de considerar uma aplicação mais avançada.
