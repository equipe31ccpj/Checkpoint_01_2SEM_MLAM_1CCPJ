# Checkpoint_01_2SEM_MLAM_1CCPJ
Modelos de classificação
# Checkpoint 01 — Modelagem Linear Para Aprendizado de Máquina

Avaliação prática de modelos de classificação, aplicando um fluxo completo de ciência de dados: carga, exploração, pré-processamento, modelagem e avaliação.

**Integrantes do grupo:** _preencher_
**Turma:** _1CCPJ_
**Data:** _02/09/2026_

---

## Sobre o projeto

O notebook está dividido em três exercícios:

| Exercício | Tema | Status |
|---|---|---|
| 1 | Saúde — classificação de tumores (Breast Cancer Wisconsin) | Exemplo resolvido (referência) |
| 2 | Economia — classificação de faixa de renda (Adult Census Income) | Concluído |
| 3 | Desafio real — tema escolhido pelo grupo | Concluído |

Cada exercício segue o mesmo fluxo:

1. Carga dos dados a partir de um CSV
2. Inspeção de dimensões, tipos e amostra
3. Verificação de valores ausentes, duplicados e inconsistências
4. Análise exploratória e distribuição das classes
5. Separação entre variáveis preditoras (`X`) e variável-alvo (`y`)
6. Divisão entre treino e teste (estratificada)
7. Pré-processamento adequado aos tipos de variáveis
8. Treinamento de uma Regressão Logística
9. Treinamento de um segundo algoritmo (Árvore de Decisão ou Random Forest)
10. Avaliação por acurácia e matriz de confusão
11. Conclusão com limitações e possíveis melhorias

---

## Exercício 3 — Desafio real

- **Tema escolhido:** _preencher (Saúde / Economia / Energia / Telecomunicações)_
- **Fonte e link do dataset:** _a preencher_
- **Unidade representada por cada linha:** _a preencher_
- **Variável-alvo:** _preencher_
- **Significado das classes:** _a preencher_
- **Decisão que o modelo pretende apoiar:** _a preencher_
- **Possíveis consequências de falsos positivos:** _a preencher_
- **Possíveis consequências de falsos negativos:** _a preencher_

### Resultados

| Modelo | Acurácia |
|---|---|
| Regressão Logística | _84.19%_ |
| Segundo modelo (Árvore/Random Forest) | _84.76%_ |

### Principais conclusões

- _Síntese dos padrões observados na análise exploratória_
- _Comparação entre os modelos treinados_
- _Leitura da matriz de confusão_
- _Limitações do conjunto de dados e da modelagem_
- _Melhorias que seriam testadas em uma próxima versão_

> O modelo não deve ser interpretado como prova ou garantia de um resultado — apenas como uma estimativa estatística sujeita a erros e limitações dos dados utilizados.

---

## Estrutura do notebook

Checkpoint_01_2SEM_MLAM.ipynb

├── Exercício 1 — Saúde (exemplo resolvido)
│
├── Exercício 2 — Economia (Adult Census Income)
│
├── Exercício 3 — Desafio real (tema do grupo)
│
└── Parte 2 — Roteiro de apresentação

---

## Como executar

1. Certifique-se de ter os arquivos CSV utilizados (`adult.csv` e o dataset do Exercício 3) na mesma pasta do notebook, ou ajuste os caminhos/URLs nas células de carga.
2. Instale as dependências:
```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
```
3. Execute o notebook do início ao fim (`Run All`), garantindo que os resultados e gráficos permaneçam visíveis na entrega.

## Bibliotecas utilizadas

- `pandas`, `numpy` — manipulação de dados
- `matplotlib`, `seaborn` — visualização
- `scikit-learn` — divisão treino/teste, modelos de classificação e métricas de avaliação

## Limitações gerais

- Os modelos foram treinados com hiperparâmetros padrão/simples, sem busca sistemática (ex.: `GridSearchCV`).
- A acurácia isolada pode mascarar desempenho fraco em classes minoritárias; métricas como precisão, recall e F1-score complementam a análise.
- Os resultados refletem apenas a divisão de treino/teste utilizada (`random_state=42`) e podem variar com outras divisões.
