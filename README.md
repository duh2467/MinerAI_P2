# Projeto de EDA — MinerAI — Análise de Crédito

Este repositório contém a Análise Exploratória de Dados (EDA) e um modelo simples de Machine Learning aplicados a um dataset de crédito. O objetivo do projeto é investigar padrões que diferenciam bons e maus pagadores, para auxiliar na tomada de decisões da empresa.

O trabalho foi dividido em 4 partes, cada uma atribuída a um integrante do grupo.
Todo o conteúdo final está consolidado em um notebook único, com seções claras, código comentado e gráficos explicativos.


* ### Estrutura do Repositório
* MinerAI_P2
   * data
     * 📄 credit.csv
     * 📄 credit_clean.csv
 * 📄 README.md
 * 📓 EDA_MinerAI_TrabalhoFinal.ipynb

\
credit_original.csv → dataset bruto

credit_clean.csv → dataset limpo após tratamento

notebook_eda_credit.ipynb → notebook principal com todo o EDA + ML

README.md → explicações gerais do projeto


### Divisão do Trabalho (Etapas)
#### 1. Preparação, Limpeza dos Dados e GitHub — Eduardo

Responsável por:

Criar o notebook e organizar o repositório

Importar e carregar o dataset

Tratar valores nulos

Corrigir inconsistências nas colunas

Padronizar categorias (maiúsculas/minúsculas, acentos, etc.)

Detecção e tratamento de outliers

Converter colunas para os tipos corretos

Gerar o dataset final credit_clean.csv


#### 2. Análise Demográfica — Maria

Investigou a relação entre a variável-alvo e:

Sexo

Estado civil

Número de dependentes

Escolaridade

Entregou:

Gráficos (countplot, barras empilhadas, tabelas cruzadas)

Interpretações após cada gráfico

Identificação de padrões relevantes (ex: concentração em categorias)


#### 3. Distribuição por Estado e Tipo de Residência — Thiago

Responsável por:

Analisar a distribuição de bons x maus pagadores por estado

Criar gráficos adequados (barras, barras empilhadas ou mapa)

Gerar boxplots e análises sobre o tipo de residência

Verificar categorias raras e lidar com problemas de distribuição


#### 4. Renda, Idade, Conclusões e Modelo de Machine Learning — Pedro

Desenvolveu:

Gráficos de dispersão, histogramas e boxplots para renda

Análise da influência da idade

Interpretação dos padrões observados

Conclusão geral da EDA

Modelo simples de Machine Learning:

Divisão treino/teste

Escolha do classificador

Métricas de avaliação (accuracy, matrix de confusão, classification report)


### Sobre o Notebook

O notebook está dividido em seções claras, todas documentadas com Markdown.
Cada etapa contém:

Explicações sobre o que está sendo feito

Comentários no código

Gráficos com títulos e legendas

Interpretações escritas pelo grupo

Principais seções do notebook:

Importação das bibliotecas e leitura do dataset

Limpeza e padronização dos dados

Análises demográficas

Distribuição por estado e tipo de residência

Renda, idade e análises complementares

Modelo de Machine Learning

Conclusões gerais


### Processo de Limpeza

Durante a limpeza foram realizados:

Remoção ou preenchimento adequado de valores nulos

Padronização de textos e categorias

Conversão de colunas para tipos adequados

Checagem de outliers e tratamento quando necessário

Criação do arquivo final credit_clean.csv

Esse arquivo será usado pelos outros integrantes nas análises.


### Modelo de Machine Learning

Um classificador simples foi implementado com o objetivo de:

Testar o comportamento dos dados após a limpeza

Avaliar a capacidade de prever bons/mau pagadores

O notebook apresenta:

Separação entre treino e teste

Treinamento do modelo

Predições

Accuracy

Matrix de confusão

Classification report


### Notas Importantes

Todos os gráficos possuem explicações logo abaixo.

O notebook é inteiramente comentado para facilitar o entendimento do professor.

O repositório está organizado para facilitar correção e reuso.

O arquivo final credit_clean.csv é o dataset utilizado nas análises.


### Integrantes

Eduardo Henrique Silva de Amorim \
Maria Eduarda Ferreira \
Pedro Henrique Bomfim Wolski \
Thiago Pereira de Jesus Souza

Caso qualquer trecho precise de revisão ou explicação extra, estamos à disposição.
