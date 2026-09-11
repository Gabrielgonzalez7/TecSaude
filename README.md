# Predição de Glicemia com Machine Learning

Este projeto apresenta a avaliação de sete modelos de Machine Learning para prever níveis de glicemia.

O objetivo foi comparar o desempenho dos modelos utilizando **Acurácia**, **F1-Score Macro** e **Matrizes de Confusão**.

Durante a análise, foi identificado um problema importante de **desbalanceamento das classes**.

## Dataset

O conjunto de teste possui **217 amostras**, distribuídas entre três classes:

| Classe | Descrição | Quantidade |
|---|---|---:|
| 0 | Abaixo | 7 |
| 1 | Normal | 166 |
| 2 | Acima | 44 |

A classe **Normal** possui uma quantidade muito maior de exemplos do que as classes Abaixo e Acima.

## Modelos Avaliados

Foram utilizados sete algoritmos de classificação:

- Logistic Regression
- Decision Tree
- Random Forest
- KNN
- Naive Bayes
- SVM
- Gradient Boosting

## Comparação dos Resultados

![Comparação dos Modelos](resultados_modelos.png)

| Modelo | Acurácia | F1-Score Macro |
|---|---:|---:|
| **SVM** | **0.7696** | **0.3178** |
| Gradient Boosting | 0.7512 | 0.3116 |
| Logistic Regression | 0.7558 | 0.2870 |
| Naive Bayes | 0.7327 | 0.2819 |
| Random Forest | 0.7281 | 0.3049 |
| KNN | 0.7097 | 0.3116 |
| Decision Tree | 0.7005 | 0.2973 |

# Acurácia

A **acurácia** representa a porcentagem geral de previsões corretas realizadas pelo modelo.

O modelo com maior acurácia foi o **SVM**, com:

**0.7696 → 76,96%**

Em seguida aparecem:

1. SVM — 76,96%
2. Logistic Regression — 75,58%
3. Gradient Boosting — 75,12%
4. Naive Bayes — 73,27%
5. Random Forest — 72,81%
6. KNN — 70,97%
7. Decision Tree — 70,05%

Porém, a acurácia pode ser enganosa quando existe **desbalanceamento de classes**.

Como a classe Normal possui **166 dos 217 casos**, um modelo pode obter uma acurácia relativamente alta classificando a maioria dos exemplos como Normal.

# F1-Score Macro

O **F1-Score Macro** calcula o F1-Score individualmente para cada classe e depois realiza uma média, dando o mesmo peso para todas as classes.

Essa métrica é importante neste problema porque as classes possuem quantidades muito diferentes de exemplos.

Os resultados ficaram entre **0.2819** e **0.3178**.

Isso mostra que, apesar das acurácias estarem próximas de 70%–77%, os modelos apresentam dificuldades para reconhecer corretamente as classes minoritárias.

# Matrizes de Confusão

As matrizes de confusão permitem observar detalhadamente os acertos e erros de cada modelo.

Os valores da diagonal representam os acertos.

Os valores fora da diagonal representam erros de classificação.

## Logistic Regression

```text
[[  0   7   0]
 [  0 164   2]
 [  0  44   0]]
```

- Abaixo: 0/7 acertos
- Normal: 164/166 acertos
- Acima: 0/44 acertos

## Decision Tree

```text
[[  0   6   1]
 [  4 150  12]
 [  0  42   2]]
```

- Abaixo: 0/7 acertos
- Normal: 150/166 acertos
- Acima: 2/44 acertos

## Random Forest

```text
[[  0   6   1]
 [  1 156   9]
 [  0  42   2]]
```

- Abaixo: 0/7 acertos
- Normal: 156/166 acertos
- Acima: 2/44 acertos

## KNN

```text
[[  0   7   0]
 [  5 151  10]
 [  1  40   3]]
```

- Abaixo: 0/7 acertos
- Normal: 151/166 acertos
- Acima: 3/44 acertos

O KNN apresentou um dos maiores F1-Scores Macro, com **0.3116**.

## Naive Bayes

```text
[[  0   7   0]
 [  0 159   7]
 [  0  44   0]]
```

- Abaixo: 0/7 acertos
- Normal: 159/166 acertos
- Acima: 0/44 acertos

## SVM

```text
[[  0   7   0]
 [  0 165   1]
 [  0  42   2]]
```

O SVM apresentou a maior acurácia:

**76,96%**

Porém, identificou apenas:

- 0 dos 7 casos Abaixo
- 165 dos 166 casos Normal
- 2 dos 44 casos Acima

Isso demonstra que uma acurácia alta não significa necessariamente que o modelo consiga identificar corretamente todas as classes.

## Gradient Boosting

```text
[[  0   7   0]
 [  0 161   5]
 [  0  42   2]]
```

- Abaixo: 0/7 acertos
- Normal: 161/166 acertos
- Acima: 2/44 acertos

# Relatórios de Classificação

## Logistic Regression

```text
Acurácia: 0.7558
F1-Score Macro: 0.2870

              precision    recall  f1-score   support

           0       0.00      0.00      0.00         7
           1       0.76      0.99      0.86       166
           2       0.00      0.00      0.00        44

    accuracy                           0.76       217
   macro avg       0.25      0.33      0.29       217
weighted avg       0.58      0.76      0.66       217
```

## Decision Tree

```text
Acurácia: 0.7005
F1-Score Macro: 0.2973

              precision    recall  f1-score   support

           0       0.00      0.00      0.00         7
           1       0.76      0.90      0.82       166
           2       0.13      0.05      0.07        44

    accuracy                           0.70       217
   macro avg       0.30      0.32      0.30       217
weighted avg       0.61      0.70      0.64       217
```

## Random Forest

```text
Acurácia: 0.7281
F1-Score Macro: 0.3049

              precision    recall  f1-score   support

           0       0.00      0.00      0.00         7
           1       0.76      0.94      0.84       166
           2       0.17      0.05      0.07        44

    accuracy                           0.73       217
   macro avg       0.31      0.33      0.30       217
weighted avg       0.62      0.73      0.66       217
```

## KNN

```text
Acurácia: 0.7097
F1-Score Macro: 0.3116

              precision    recall  f1-score   support

           0       0.00      0.00      0.00         7
           1       0.76      0.91      0.83       166
           2       0.23      0.07      0.11        44

    accuracy                           0.71       217
   macro avg       0.33      0.33      0.31       217
weighted avg       0.63      0.71      0.66       217
```

## Naive Bayes

```text
Acurácia: 0.7327
F1-Score Macro: 0.2819

              precision    recall  f1-score   support

           0       0.00      0.00      0.00         7
           1       0.76      0.96      0.85       166
           2       0.00      0.00      0.00        44

    accuracy                           0.73       217
   macro avg       0.25      0.32      0.28       217
weighted avg       0.58      0.73      0.65       217
```

## SVM

```text
Acurácia: 0.7696
F1-Score Macro: 0.3178

              precision    recall  f1-score   support

           0       0.00      0.00      0.00         7
           1       0.77      0.99      0.87       166
           2       0.67      0.05      0.09        44

    accuracy                           0.77       217
   macro avg       0.48      0.35      0.32       217
weighted avg       0.72      0.77      0.68       217
```

## Gradient Boosting

```text
Acurácia: 0.7512
F1-Score Macro: 0.3116

              precision    recall  f1-score   support

           0       0.00      0.00      0.00         7
           1       0.77      0.97      0.86       166
           2       0.29      0.05      0.08        44

    accuracy                           0.75       217
   macro avg       0.35      0.34      0.31       217
weighted avg       0.64      0.75      0.67       217
```

# Ranking Final

| Posição | Modelo | Acurácia | F1-Score Macro |
|---:|---|---:|---:|
| 1 | **SVM** | **0.7696** | **0.3178** |
| 2 | KNN | 0.7097 | 0.3116 |
| 3 | Gradient Boosting | 0.7512 | 0.3116 |
| 4 | Random Forest | 0.7281 | 0.3049 |
| 5 | Decision Tree | 0.7005 | 0.2973 |
| 6 | Logistic Regression | 0.7558 | 0.2870 |
| 7 | Naive Bayes | 0.7327 | 0.2819 |

# Principal Problema Encontrado

O principal problema encontrado foi o **desbalanceamento das classes**.

```text
Abaixo  → 7 casos
Normal  → 166 casos
Acima   → 44 casos
```

A classe Normal representa aproximadamente **76,5% dos dados de teste**.

Isso faz com que os modelos tenham uma forte tendência a classificar os exemplos como Normal.

# Conclusão

O **SVM apresentou o melhor resultado geral**, alcançando:

- **76,96% de Acurácia**
- **0.3178 de F1-Score Macro**

Porém, a análise das matrizes de confusão mostrou que todos os modelos apresentaram dificuldades para identificar as classes minoritárias.

Portanto, **não é adequado avaliar este problema apenas pela acurácia**.

O F1-Score Macro e as Matrizes de Confusão mostraram que os modelos precisam ser aprimorados antes de qualquer aplicação prática.

# Próximos Passos

Como melhorias para o projeto, podem ser utilizadas técnicas para tratar o desbalanceamento dos dados:

- **SMOTE**
- Oversampling
- Undersampling
- `class_weight`
- Ajuste de hiperparâmetros
- Validação cruzada estratificada
- Análise de Precision, Recall e F1-Score por classe

O objetivo é desenvolver modelos capazes de identificar corretamente não apenas os casos **Normais**, mas também os casos de glicemia **Abaixo** e **Acima**.

## Tecnologias Utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Machine Learning
- Classificação Supervisionada

---

> **Machine Learning não é apenas sobre acertar o que é comum, mas também sobre conseguir identificar corretamente o que é raro.**
