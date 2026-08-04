# 📊 Executive Sales & API Analytics Pipeline
![Status: Em Andamento](https://img.shields.io/badge/Status-In_Progress-yellow?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker_Studio-4285F4?style=for-the-badge&logo=google&logoColor=white)

> **Desafio Empresarial Real:** Projeto fim a fim simulando uma demanda executiva de extração de dados via API REST, modelagem SQL e Business Intelligence para tomada de decisão estratégica.

---

## 🎯 1. O Problema de Negócio (Business Case)
*📧 Mensagem do seu chefe

Assunto: Limpeza da base de clientes

Bom dia, Calebe.

Recebemos uma lista de clientes da equipe de desenvolvimento através de uma API. Antes que esses dados possam ser utilizados pelo time de Business Intelligence, precisamos garantir que estejam organizados e fáceis de analisar.

Sua tarefa é importar os dados da API, realizar a limpeza necessária e entregar uma base pronta para análise.

Fonte de dados
https://jsonplaceholder.typicode.com/users
Objetivos

Queremos um arquivo chamado

clean_users.csv

que possa ser entregue para outro analista sem necessidade de tratamento adicional.

Requisitos

Você deverá:

Importar os dados da API.
Avaliar a qualidade dos dados.
Organizar a estrutura da tabela.
Remover informações desnecessárias.
Transformar os campos aninhados (JSON dentro de JSON) em colunas simples.
Garantir que todos os nomes das colunas sejam padronizados.
Entregar um DataFrame limpo.
Além da limpeza

Antes de finalizar, preciso que você me responda as seguintes perguntas.

Quantos usuários existem na base?
Quantas cidades diferentes existem?
Qual cidade possui mais usuários?
Quantas empresas diferentes aparecem?
Existe algum dado ausente?
Existem registros duplicados?
Quais colunas você decidiu remover e por quê?
Entregáveis

Quero receber:

O notebook Python.
O arquivo clean_users.csv.
Um pequeno relatório explicando todas as transformações realizadas.
Observações

Não existe uma única resposta correta para a limpeza. O mais importante é que suas decisões façam sentido e sejam justificadas.

💼 (Fim da mensagem do chefe)*

---

## ⚙️ 2. Pipeline de Dados & Arquitetura
1. **Extração (API REST):** Consumo de endpoint externo utilizando Python (`requests`).
2. **Transformação & Limpeza (Pandas):** Tratamento de valores nulos, padronização de tipos e regras de negócio.
3. **Análise Exploratória (SQL):** Consultas de agregação, window functions e validação de hipóteses.
4. **Visualização (BI):** Construção de painel gerencial no Looker Studio.

---

## 🐍 3. Amostra dos Dados Tratados (Pandas DataFrame)
*Em breve...*

---

## 🗄️ 4. Análise e Insight Gerado (SQL)
*Em breve...*

---

## 📈 5. Dashboard Gerencial (Looker Studio)
*Em breve...*
