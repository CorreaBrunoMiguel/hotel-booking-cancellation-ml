# Hotel Booking Cancellation Analysis

Projeto de portfólio em **Análise de Dados e Machine Learning** para investigar padrões associados ao cancelamento de reservas hoteleiras e construir um modelo introdutório de classificação.

O trabalho foi desenvolvido em contexto educacional a partir do dataset público **Hotel Booking Demand**, disponível no Kaggle.

## Problema

Cancelamentos afetam previsibilidade de ocupação, planejamento operacional e gestão da demanda. A análise busca responder duas questões principais:

1. Quais características das reservas aparecem associadas a maiores taxas de cancelamento?
2. É possível construir um modelo capaz de identificar padrões relacionados a reservas canceladas?

## Dataset

**Hotel Booking Demand**  
Fonte: Kaggle — `jessemostipak/hotel-booking-demand`

O conjunto contém reservas de **City Hotel** e **Resort Hotel**. A variável alvo utilizada na modelagem é:

```text
is_canceled
```

O dataset não é versionado neste repositório. O notebook utiliza `kagglehub` para baixá-lo e copiá-lo para `data/raw/` na primeira execução.

## Etapas realizadas

- compreensão e validação estrutural dos dados;
- tratamento de valores ausentes e preparação das variáveis;
- análise exploratória e visualizações;
- investigação de padrões de cancelamento;
- feature engineering;
- remoção de variáveis com risco de vazamento de informação;
- codificação de variáveis categóricas;
- divisão estratificada entre treino e teste;
- treinamento de `RandomForestClassifier`;
- avaliação por Accuracy, Precision, Recall, F1-Score e matriz de confusão;
- análise de importância das features.

## Resultado do modelo

Após a preparação dos dados, o conjunto utilizado na modelagem possui **87.396 registros** e **85 features**.

O `RandomForestClassifier` apresentou no conjunto de teste:

| Métrica | Resultado |
|---|---:|
| Accuracy | 84,47% |
| Precision | 75,85% |
| Recall | 63,81% |
| F1-Score | 69,31% |

Matriz de confusão registrada no notebook:

```text
[[11699,  976],
 [ 1739, 3066]]
```

O modelo apresentou melhor desempenho na identificação de reservas não canceladas. O recall da classe de cancelamento mostra que ainda há cancelamentos não identificados pelo modelo, deixando espaço para evolução futura.

## Principais sinais identificados

Entre as features com maior importância no modelo estão:

- `lead_time`;
- `adr`;
- `arrival_date_day_of_month`;
- `arrival_date_week_number`;
- `total_of_special_requests`;
- `stays_in_week_nights`;
- `country_PRT`;
- `stays_in_weekend_nights`;
- `required_car_parking_spaces`.

A análise exploratória também investiga sazonalidade, tipo de hotel, segmento de mercado e outras características operacionais das reservas.

## Tecnologias

- Python
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- KaggleHub
- Jupyter Notebook

## Estrutura

```text
hotel-booking-cancellation-ml/
├── README.md
├── requirements.txt
├── .gitignore
└── notebook/
    ├── hotel_booking_cancellation_analysis.ipynb
    └── data_dictionary.py
```

A pasta `data/raw/` é criada durante a execução e permanece fora do versionamento.

## Como executar

Clone o repositório e crie um ambiente virtual:

```bash
python -m venv .venv
```

Ative o ambiente e instale as dependências:

```bash
pip install -r requirements.txt
```

Depois, inicie o Jupyter a partir da pasta `notebook`:

```bash
cd notebook
jupyter notebook
```

Abra:

```text
hotel_booking_cancellation_analysis.ipynb
```

Na primeira execução, o notebook baixa o dataset por meio do KaggleHub.

## Contexto

Este é um **projeto educacional de portfólio**. O objetivo é demonstrar um fluxo completo de trabalho em dados: investigação exploratória, tratamento, preparação para modelagem, Machine Learning e avaliação de resultados.

## Autor

**Bruno Miguel Corrêa**  
GitHub: [CorreaBrunoMiguel](https://github.com/CorreaBrunoMiguel)
