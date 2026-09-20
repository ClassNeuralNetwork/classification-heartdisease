# 🫀 Projeto: Classificação de Doença Cardíaca com Rede Neural MLP 🫀

## 📝 Visão Geral

Este projeto foi desenvolvido para a atividade de Redes Neurais, utilizando uma **Rede Neural Perceptron Multicamadas (MLP)** para realizar a classificação de pacientes quanto à presença ou ausência de doença cardíaca.

A partir de características clínicas presentes no conjunto de dados, o modelo foi treinado para realizar uma **classificação binária**, identificando duas possibilidades:

- `0` → Sem doença cardíaca
- `1` → Com doença cardíaca

O projeto envolve o carregamento e tratamento dos dados, transformação das variáveis categóricas, padronização das características, construção e treinamento de uma rede neural MLP e avaliação do modelo por meio de métricas de classificação e matriz de confusão.

---

## 🎯 Problema

O problema abordado neste projeto é uma tarefa de **classificação binária**.

O objetivo é utilizar características presentes nos dados dos pacientes para que uma rede neural consiga classificar cada registro em uma das duas classes:

**Sem doença cardíaca** ou **Com doença cardíaca**.

O conjunto de dados original apresenta a variável `num` com valores de `0` a `4`, representando diferentes níveis relacionados à presença de doença cardíaca. Para transformar o problema em uma classificação binária, os valores foram agrupados da seguinte forma:

- `0` → Sem doença cardíaca
- Valores maiores que `0` → Com doença cardíaca

---

## 📊 Dataset

O conjunto de dados utilizado neste projeto é o **Heart Disease UCI**, obtido por meio da plataforma Kaggle.

Dataset utilizado:

- **Nome:** Heart Disease UCI
- **Fonte:** Kaggle
- **Identificador no KaggleHub:** `redwankarimsony/heart-disease-data`
- **Arquivo utilizado:** `heart_disease_uci.csv`

O conjunto de dados contém informações clínicas e características relacionadas aos pacientes, utilizadas para realizar a classificação.

Entre as características utilizadas pelo modelo estão:

| Característica | Descrição |
|---|---|
| `age` | Idade do paciente |
| `sex` | Sexo |
| `cp` | Tipo de dor no peito |
| `trestbps` | Pressão arterial em repouso |
| `chol` | Colesterol |
| `fbs` | Glicemia em jejum |
| `restecg` | Resultado do eletrocardiograma em repouso |
| `thalch` | Frequência cardíaca máxima atingida |
| `exang` | Angina induzida por exercício |
| `oldpeak` | Depressão do segmento ST |
| `slope` | Inclinação do segmento ST |
| `ca` | Número de vasos principais |
| `thal` | Resultado relacionado ao teste de tálio |

A coluna `id` foi removida por representar apenas um identificador dos registros. A coluna `dataset`, que representa a origem do registro, também foi removida para evitar que a origem dos dados fosse utilizada como característica na classificação.

---

## ⚙️ Pré-processamento dos dados

Antes do treinamento da rede neural, os dados passaram pelas seguintes etapas:

1. Remoção das colunas que não seriam utilizadas como características;
2. Transformação da variável `num` em uma variável binária;
3. Codificação das variáveis categóricas utilizando `LabelEncoder`;
4. Tratamento dos valores ausentes utilizando a mediana;
5. Separação dos dados em conjuntos de treinamento e teste;
6. Padronização das características utilizando `StandardScaler`.

Os dados foram divididos da seguinte maneira:

- **80%** para treinamento;
- **20%** para teste.

A padronização foi realizada utilizando apenas os dados de treinamento para calcular os parâmetros do `StandardScaler`, que posteriormente foram aplicados aos dados de teste.

---

## 🧠 Modelo de Rede Neural

Foi utilizada uma **Rede Neural Perceptron Multicamadas (MLP)** construída com TensorFlow/Keras.

A arquitetura utilizada foi:

```text
Entrada
   ↓
Dense (16 neurônios, ReLU)
   ↓
Dense (8 neurônios, ReLU)
   ↓
Dense (1 neurônio, Sigmoid)
   ↓
Classificação binária
```

### Configurações do treinamento

- **Otimizador:** Adam
- **Função de perda:** Binary Crossentropy
- **Métrica:** Accuracy
- **Épocas:** 30
- **Batch size:** 16
- **Validação:** 20% dos dados de treinamento

---

## 📈 Avaliação do modelo

Após o treinamento, o modelo foi avaliado utilizando o conjunto de teste.

Foram utilizadas as seguintes métricas:

- Acurácia
- Precisão
- Recall
- F1-Score
- Matriz de confusão

### Resultado

A acurácia obtida no conjunto de teste foi:

**82.61%**

Além das métricas numéricas, foi utilizada uma matriz de confusão para visualizar a quantidade de classificações corretas e incorretas realizadas pelo modelo.

---

## 📉 Histórico de Aprendizado

Durante o treinamento foram acompanhadas as perdas do conjunto de treinamento e de validação.

O gráfico permite observar a evolução da função de perda ao longo das épocas e verificar o comportamento do modelo durante o processo de aprendizado.

Também foi gerado um gráfico contendo a evolução da acurácia no treinamento e na validação.

---

## 🔎 Explicabilidade com SHAP

Para analisar a influência das características utilizadas pelo modelo, foi utilizada a biblioteca **SHAP (SHapley Additive exPlanations)**.

O gráfico SHAP permite observar quais características tiveram maior influência nas previsões realizadas pela rede neural.

No gráfico, valores SHAP positivos representam uma contribuição para aumentar a saída prevista pelo modelo, enquanto valores negativos representam uma contribuição para diminuir essa saída.

A análise SHAP foi realizada utilizando uma amostra dos dados de teste.

---

## 💾 Modelo

Após o treinamento, o modelo foi salvo no formato `.keras`:

```text
modelo_heart_disease.keras
```

## 🛠️ Tecnologias utilizadas

- **Python**
- **TensorFlow/Keras** — construção e treinamento da rede neural
- **Pandas** — manipulação dos dados
- **NumPy** — operações numéricas
- **Scikit-learn** — pré-processamento e métricas
- **Matplotlib** — geração dos gráficos
- **SHAP** — interpretação do modelo
- **KaggleHub** — obtenção do conjunto de dados

---

## 📁 Estrutura do projeto

```text
├── heart_disease_uci.csv
├── modelo_heart_disease.keras
├── notebook.ipynb
└── README.md
```

## 📚 Objetivo da atividade

Este projeto foi desenvolvido como parte da atividade de Redes Neurais, cujo objetivo é selecionar uma base de dados, definir um problema de aprendizado de máquina e desenvolver uma solução utilizando uma Rede Neural MLP.

Neste projeto:

```text
Base de dados: Heart Disease UCI
Problema: Classificação
Tipo: Classificação binária
Modelo: Perceptron Multicamadas (MLP)
Framework: TensorFlow/Keras
```