# 📊 Análise Exploratória de Dados — MinerAI

<div align="center">

**Mineração de Dados - Trabalho Integrado Final**

Professora: Vagner S. Macedo  
Período: 2024

</div>

---

## 🎯 Objetivo

Realizar uma **Análise Exploratória de Dados (EDA)** completa e desenvolver um **modelo de Machine Learning** para identificar padrões que diferenciam **bons e maus pagadores** em um dataset de crédito, auxiliando na tomada de decisões sobre concessão de crédito.

---

## 📁 Estrutura do Repositório

```
MinerAI_P2/
├── 📓 EDA_MinerAI_TrabalhoFinal.ipynb    # Notebook principal com toda análise + ML
├── 📄 README.md                          # Este arquivo
└── data/
    ├── credit.csv                        # Dataset bruto (original)
    └── credit_clean.csv                  # Dataset limpo e processado
```

---

## 👥 Equipe

| Integrante | Responsabilidades |
|-----------|-----------------|
| **Eduardo Amorim** | Preparação, limpeza dos dados e GitHub |
| **Maria Eduarda** | Análise demográfica |
| **Thiago Souza** | Distribuição por estado e tipo de residência |
| **Pedro Wolski** | Renda, idade, conclusões e modelo ML |

---

## 📋 Divisão do Trabalho e Etapas

### 1️⃣ Preparação e Limpeza dos Dados — Eduardo

**Responsabilidades:**
- ✅ Importação e carregamento do dataset
- ✅ Tratamento de valores nulos e inconsistências
- ✅ Padronização de colunas (maiúsculas, espaços extras, caracteres especiais)
- ✅ Detecção e tratamento de outliers
- ✅ Conversão de variáveis binárias (Y/N → 1/0)
- ✅ Correção de tipos de dados
- ✅ Geração do arquivo `credit_clean.csv`

**Estratégias aplicadas:**
- Valores nulos em colunas categóricas → preenchidos com a **moda**
- Valores nulos em colunas numéricas → preenchidos com a **mediana**
- Outliers de renda → removidos para renda > R$ 50.000
- Conversão de tipos incorretos (ex: DDDs como texto → numéricos)

---

### 2️⃣ Análise Demográfica — Maria

**Variáveis analisadas:**
- 👤 `SEXO`
- 💍 `ESTADO_CIVIL`
- 👨‍👩‍👧‍👦 `QUANT_DEPENDENTES`
- 📚 `NIVEL_EDUCACIONAL`

**Metodologia:**
- Análise de proporções e distribuições
- Gráficos: countplot, barras empilhadas, tabelas cruzadas
- Cruzamento com `ROTULO_ALVO_MAU` (variável-alvo)

**Principais achados:**
- Concentração de categorias em alguns grupos
- Identificação de padrões demográficos associados a inadimplência
- Agregação de categorias raras para evitar ruído nos gráficos

---

### 3️⃣ Distribuição por Estado e Tipo de Residência — Thiago

**Variáveis analisadas:**
- 🗺️ `ESTADO_RESIDENCIAL`
- 🏠 `TIPO_RESIDENCIA`

**Metodologia:**
- Análise de distribuição geográfica
- Boxplots para relação renda vs. tipo de residência
- Gráficos de barras empilhadas (bons vs. maus pagadores)
- Cálculo de proporções por região

**Principais achados:**
- Variação significativa da inadimplência entre estados
- Estados com maior volume de clientes (SP, BA, CE, RS) impactam fortemente o risco total
- Tipo de residência correlacionado com níveis de renda
- Estados com maior proporção de inadimplentes exigem análise mais rigorosa

---

### 4️⃣ Renda, Idade, Conclusões e Modelo ML — Pedro

**Variáveis analisadas:**
- 💰 `RENDA_PESSOAL_MENSAL` e `OUTRAS_RENDAS`
- 📅 `IDADE`
- Estabilidade: `MESES_NO_TRABALHO`, `MESES_RESIDENCIA`
- Patrimônio e atributos financeiros

**Análises realizadas:**
- Dispersão, histogramas e boxplots da renda
- Influência da idade no comportamento de pagamento
- Correlação entre estabilidade financeira e inadimplência

**Modelo de Machine Learning:**
- **Algoritmo:** XGBoost
- **Divisão:** 70% treino, 30% teste (estratificado)
- **Tratamento:** Remoção de outliers via IQR (Interquartile Range)
- **Codificação:** One-Hot Encoding para variáveis categóricas
- **Balanceamento:** SMOTE (Synthetic Minority Over-sampling Technique)

---

## 📊 Principais Insights da EDA

### 🔍 Padrões Identificados

| Fator | Impacto | Observação |
|-------|--------|-----------|
| **Renda pessoal** | Alto | Rendas menores → maior inadimplência |
| **Outras rendas** | Moderado | Maus pagadores têm outras rendas menores |
| **Idade** | Moderado | Clientes mais jovens: proporção maior de inadimplência |
| **Estabilidade (emprego/residência)** | Moderado | Forte sobreposição entre grupos |
| **Patrimônio pessoal** | Fraco | Baixo poder discriminativo |
| **Atributos regionais** | Moderado | Variação significativa entre estados |

### ⚠️ Limitações Identificadas

- Variáveis demográficas sozinhas têm **poder discriminativo limitado**
- Forte sobreposição entre perfis de bons e maus pagadores
- Atributos disponíveis não contêm sinal estatístico suficiente para previsão confiável
- Faltam informações sobre histórico de crédito, inadimplência anterior e comportamento transacional

---

## 🤖 Desempenho do Modelo XGBoost

### Métricas Finais

| Métrica | Valor | Interpretação |
|---------|-------|---------------|
| **Acurácia** | ~70% | Moderada |
| **Recall (Bons Pagadores)** | 0.92 | Excelente - modelo identifica bem os bons |
| **Recall (Maus Pagadores)** | 0.11 | Insatisfatório - falha ao identificar maus |
| **Precisão (Maus Pagadores)** | 0.31 | Baixa - muitos falsos positivos |
| **ROC AUC** | 0.54 | Apenas ligeiramente melhor que acaso |

### 📝 Conclusão do Modelo

O modelo XGBoost desenvolvido apresenta **capacidade discriminativa limitada**, refletindo as limitações das variáveis disponíveis. Embora identifique bem os bons pagadores, **falha significativamente** na detecção de maus pagadores, o que inviabiliza seu uso prático em decisões de crédito.

**Recomendação:** Para melhorias significativas, seria necessário:
1. Incluir **histórico de crédito** e **inadimplência anterior**
2. Adicionar **dados transacionais** e **comportamento de pagamento**
3. Incorporar **score de crédito** de órgãos especializados
4. Expandir o conjunto de features relevantes

---

## 🛠️ Tecnologias Utilizadas

### Linguagem e Ambiente
- **Python 3.x**
- **Jupyter Notebook**

### Bibliotecas Principais

```python
# Manipulação de dados
pandas, numpy

# Visualização
matplotlib, seaborn

# Machine Learning
scikit-learn, xgboost, imbalanced-learn (SMOTE)

# Processamento
StandardScaler, OneHotEncoder, ColumnTransformer
```

---

## 📥 Como Executar

### 1. Instalação de Dependências

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn
```

### 2. Executar o Notebook

```bash
jupyter notebook EDA_MinerAI_TrabalhoFinal.ipynb
```

### 3. Fluxo de Execução

- **Seção 1-2:** Limpeza e preparação dos dados
- **Seção 3:** Análise demográfica
- **Seção 4:** Análise geográfica (estado e residência)
- **Seção 5:** Análise de renda e idade + modelo ML
- **Seção 6:** Conclusões finais

---

## 📚 Dataset

### Dimensões
- **Registros:** ~5.000 clientes
- **Features:** 51 variáveis (após limpeza)
- **Variável Alvo:** `ROTULO_ALVO_MAU` (0 = Bom, 1 = Mau Pagador)

### Características Principais

**Dados Pessoais:** Sexo, estado civil, dependentes, educação, nacionalidade  
**Localização:** Estado, cidade, bairro, CEP, tipo de residência  
**Financeiro:** Renda pessoal, outras rendas, patrimônio, contas bancárias, cartões  
**Profissional:** Tipo de funcionário, tempo no trabalho, profissão, código de profissão  
**Contato:** Telefones (residencial, móvel, profissional), email  
**Documentação:** Flags para CPF, RG, documentação, comprovante de renda

---

## 📖 Referências

- **Dataset:** [Credit Dataset](https://raw.githubusercontent.com/diogenesjusto/FIAP/master/dados/credit.csv)
- **Documentação:**
  - [Pandas Documentation](https://pandas.pydata.org/)
  - [XGBoost Documentation](https://xgboost.readthedocs.io/)
  - [Scikit-learn Documentation](https://scikit-learn.org/)
- **Instituição:** FIAP

---

## ✨ Conclusão Geral

Este projeto demonstrou o processo completo de análise de dados em crédito, desde a limpeza até a modelagem preditiva. Embora o modelo final tenha apresentado limitações, a **análise exploratória forneceu insights valiosos** sobre os fatores associados a inadimplência e as limitações dos dados disponíveis. O trabalho reforça a importância de dados de qualidade e variáveis adequadas para construção de modelos de crédito efetivos.

---

