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

Queremos uma análise completa e bem estruturada desses dados!

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
*

|   id | name             | username   | email                     | phone                | website       | street            | suite     | city          | zipcode    |   geo.lat |   geo.lng | company_name       | company_catch_phrase                     | company_bs                           |
|-----:|:-----------------|:-----------|:--------------------------|:---------------------|:--------------|:------------------|:----------|:--------------|:-----------|----------:|----------:|:-------------------|:-----------------------------------------|:-------------------------------------|
|    1 | leanne graham    | bret       | sincere@april.biz         | 1-770-736-8031-56442 | hildegard.org | Kulas Light       | Apt. 556  | Gwenborough   | 92998-3874 |  -37.3159 |   81.1496 | Romaguera-Crona    | Multi-layered client-server neural-net   | harness real-time e-markets          |
|    2 | ervin howell     | antonette  | shanna@melissa.tv         | 010-692-6593-09125   | anastasia.net | Victor Plains     | Suite 879 | Wisokyburgh   | 90566-7771 |  -43.9509 |  -34.4618 | Deckow-Crist       | Proactive didactic contingency           | synergize scalable supply-chains     |
|    3 | clementine bauch | samantha   | nathan@yesenia.net        | 1-463-123-4447       | ramiro.info   | Douglas Extension | Suite 847 | McKenziehaven | 59590-4157 |  -68.6102 |  -47.0653 | Romaguera-Jacobson | Face to face bifurcated interface        | e-enable strategic applications      |
|    4 | patricia lebsack | karianne   | julianne.oconner@kory.org | 493-170-9623-156     | kale.biz      | Hoeger Mall       | Apt. 692  | South Elvis   | 53919-4257 |   29.4572 | -164.299  | Robel-Corkery      | Multi-tiered zero tolerance productivity | transition cutting-edge web services |
|    5 | chelsey dietrich | kamren     | lucio_hettinger@annie.ca  | (254)954-1289        | demarco.info  | Skiles Walks      | Suite 351 | Roscoeview    | 33263      |  -31.8129 |   62.5342 | Keebler LLC        | User-centric fault-tolerant solution     | revolutionize end-to-end systems     |
*
---

## 🗄️ 4. Análise e Insight Gerado (SQL)
*-----------------------------------------------
SELECT DISTINCT(id) FROM my_db.usuarios_limpos 
--Ha 10 usuarios existentes na base
-----------------------------------------------

------------------------------------------------
SELECT DISTINCT(city) FROM my_db.usuarios_limpos 
--Ha 10 diferentes cidades
------------------------------------------------

------------------------------------------------
SELECT city
       COUNT(*) AS numero de pessoas por cidade
FROM my_db.usuarios_limpos
--Cada usuario mora em uma Regiao diferente
------------------------------------------------

---------------------------------------------------------------------------------------------------------------
SELECT company_name FROM my_db.usuarios_limpos 
-- 10 empresas aparecem diferentes. Porem a empresa Romaguera aparece 2 vezes na primeira em Crona e na segunda em Jacobson!
----------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------------
SELECT * FROM my_db.usuarios_limpos
— NAO. Todos os dados foram tratados limpos e analisados antes de chegar aqui.
------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------
Não existe nenhum arquivo duplicado. Todos os arquivos duplicados ja foram analisados e tratados em python.
-----------------------------------------------------------------------------------------------------------
-----------------------------
Nenhuma coluna foi removida.
-----------------------------
*

---

## 📈 5. Dashboard Gerencial (Looker Studio)
*Em breve...*
