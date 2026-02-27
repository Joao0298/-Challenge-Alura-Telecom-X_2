# -Challenge-Alura-Telecom-X_2

# 📡 Telecom X – Modelo de Previsão de Churn (Parte 2)

🎯 **Objetivo do Projeto**  
Esta segunda fase do projeto tem como objetivo desenvolver e comparar modelos de Machine Learning para prever a evasão de clientes (*churn*) da Telecom X. A partir da análise exploratória realizada na Parte 1, construímos pipelines de classificação, avaliamos diferentes algoritmos e identificamos o modelo com melhor capacidade preditiva, fornecendo uma ferramenta para a equipe de Ciência de Dados priorizar ações de retenção.

🛠️ **Tecnologias e Bibliotecas**  

- **Linguagem:** Python 3  
- **Manipulação de Dados:** Pandas, NumPy  
- **Pré-processamento e Modelagem:** Scikit-learn (Pipelines, StandardScaler, OneHotEncoder, RandomForest, LogisticRegression)  
- **Modelo Avançado:** XGBoost  
- **Visualização:** Matplotlib, Seaborn  
- **Persistência:** Joblib  
- **Formato de Entrega:** Jupyter Notebook (`TelecomX_Modelo_Final.ipynb`)

🚀 **Estrutura do Projeto (Modelagem)**  

A modelagem seguiu uma abordagem estruturada e reprodutível:

1. **Preparação dos Dados**  
   - Carregamento e limpeza (mesmos passos da Parte 1).  
   - Transformação de variáveis categóricas com One-Hot Encoding.  
   - Padronização de variáveis numéricas.

2. **Seleção de Variáveis**  
   - Análise de correlação para variáveis numéricas.  
   - Teste Qui‑Quadrado para variáveis categóricas.  
   - Consolidação das features mais relevantes.

3. **Treinamento de Múltiplos Modelos**  
   - **Random Forest** (com balanceamento de classes).  
   - **Regressão Logística** (com balanceamento).  
   - **XGBoost** (com ajuste de `scale_pos_weight` para desbalanceamento).

4. **Avaliação e Comparação**  
   - Relatórios de classificação (Precision, Recall, F1).  
   - Matrizes de confusão.  
   - Curvas ROC e AUC.  
   - Tabela comparativa de desempenho.

5. **Análise de Importância de Variáveis**  
   - Importância para modelos baseados em árvores.  
   - Coeficientes da Regressão Logística.

6. **Salvando o Melhor Modelo**  
   - O modelo com maior AUC-ROC é persistido em formato `.pkl` para uso em produção.

💡 **Principais Insights da Modelagem**  

- O **XGBoost** apresentou o melhor desempenho geral, com AUC-ROC acima de 0,85, superando Random Forest e Regressão Logística.  
- As variáveis mais importantes para a predição foram:  
  - **Tempo de contrato (tenure)**  
  - **Tipo de contrato (mensal vs. anual)**  
  - **Cobrança mensal (monthly_charges)**  
  - **Serviços contratados** (ex.: segurança online, suporte técnico)  
- Clientes com contratos de curto prazo e faturas elevadas são os que apresentam maior probabilidade de churn, corroborando os achados da EDA.

📈 **Resultados dos Modelos**  

| Modelo               | Acurácia | Precision (Churn) | Recall (Churn) | F1 (Churn) | AUC-ROC |
|----------------------|----------|-------------------|----------------|------------|---------|
| **XGBoost**          | 0,80     | 0,68              | 0,55           | 0,61       | **0,86**|
| Random Forest        | 0,79     | 0,65              | 0,54           | 0,59       | 0,84    |
| Regressão Logística  | 0,79     | 0,62              | 0,60           | 0,61       | 0,85    |

> *Nota: Os valores podem variar ligeiramente conforme a semente aleatória.*

📁 **Como Executar**  

1. Certifique-se de ter o arquivo `TelecomX_Data.json` no mesmo diretório do notebook.  
2. Instale as dependências necessárias:  
   ```bash
   pip install pandas numpy scikit-learn joblib matplotlib seaborn xgboost
Abra o notebook TelecomX_Modelo_Final.ipynb em um ambiente Jupyter (JupyterLab, VS Code, Google Colab).

Execute todas as células sequencialmente.
