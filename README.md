# 📊 Executive Sales & API Analytics Pipeline
![Status: Concluído](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker_Studio-4285F4?style=for-the-badge&logo=google&logoColor=white)

> **Desafio Empresarial Real:** Projeto fim a fim simulando uma demanda executiva de extração de dados via API REST, modelagem SQL e Business Intelligence para tomada de decisão estratégica.

---

## 🎯 1. O Problema de Negócio (Business Case)
> **📧 Mensagem do seu chefe**  
> **Assunto:** Limpeza da base de clientes  
>  
> Bom dia, Calebe.  
>  
> Recebemos uma lista de clientes da equipe de desenvolvimento através de uma API. Antes que esses dados possam ser utilizados pelo time de Business Intelligence, precisamos garantir que estejam organizados e fáceis de analisar.  
>  
> Sua tarefa é importar os dados da API, realizar a limpeza necessária e entregar uma base pronta para análise.  
>  
> **Fonte de dados:** `https://jsonplaceholder.typicode.com/users`  
>  
> **Requisitos:**  
> 1. Importar os dados da API.  
> 2. Avaliar a qualidade dos dados.  
> 3. Organizar a estrutura da tabela.  
> 4. Remover informações desnecessárias.  
> 5. Transformar os campos aninhados (JSON dentro de JSON) em colunas simples.  
> 6. Garantir que todos os nomes das colunas sejam padronizados.  
> 7. Entregar um DataFrame limpo.  
>  
> **Além da limpeza, preciso que me responda:**  
> * Quantos usuários existem na base?  
> * Quantas cidades diferentes existem?  
> * Qual cidade possui mais usuários?  
> * Quantas empresas diferentes aparecem?  
> * Existe algum dado ausente?  
> * Existem registros duplicados?  
> * Quais colunas você decidiu remover e por quê?  

---

## ⚙️ 2. Pipeline de Dados & Arquitetura
1. **Extração (API REST):** Consumo de endpoint externo utilizando Python (`requests`).
2. **Transformação & Limpeza (Pandas):** Tratamento de valores nulos, padronização de tipos e regras de negócio.
3. **Análise Exploratória (SQL):** Consultas de agregação, window functions e validação de hipóteses no MotherDuck.
4. **Visualização (BI):** Construção de painel gerencial no Looker Studio.

---

## 🐍 3. Amostra dos Dados Tratados (Pandas DataFrame)

|   id | name             | username   | email                     | phone                | website       | street            | suite     | city          | zipcode    |   geo.lat |   geo.lng | company_name       | company_catch_phrase                     | company_bs                            |
|-----:|:-----------------|:-----------|:--------------------------|:---------------------|:--------------|:------------------|:----------|:--------------|:-----------|----------:|----------:|:-------------------|:-----------------------------------------|:-------------------------------------|
|    1 | leanne graham    | bret       | sincere@april.biz         | 1-770-736-8031-56442 | hildegard.org | Kulas Light       | Apt. 556  | Gwenborough   | 92998-3874 |  -37.3159 |   81.1496 | Romaguera-Crona    | Multi-layered client-server neural-net   | harness real-time e-markets          |
|    2 | ervin howell     | antonette  | shanna@melissa.tv         | 010-692-6593-09125   | anastasia.net | Victor Plains     | Suite 879 | Wisokyburgh   | 90566-7771 |  -43.9509 |  -34.4618 | Deckow-Crist       | Proactive didactic contingency           | synergize scalable supply-chains     |
|    3 | clementine bauch | samantha   | nathan@yesenia.net        | 1-463-123-4447       | ramiro.info   | Douglas Extension | Suite 847 | McKenziehaven | 59590-4157 |  -68.6102 |  -47.0653 | Romaguera-Jacobson | Face to face bifurcated interface        | e-enable strategic applications      |
|    4 | patricia lebsack | karianne   | julianne.oconner@kory.org | 493-170-9623-156     | kale.biz      | Hoeger Mall       | Apt. 692  | South Elvis   | 53919-4257 |   29.4572 | -164.299  | Robel-Corkery      | Multi-tiered zero tolerance productivity | transition cutting-edge web services |
|    5 | chelsey dietrich | kamren     | lucio_hettinger@annie.ca  | (254)954-1289        | demarco.info  | Skiles Walks      | Suite 351 | Roscoeview    | 33263      |  -31.8129 |   62.5342 | Keebler LLC        | User-centric fault-tolerant solution     | revolutionize end-to-end systems     |

---

## 🗄️ 4. Análise e Insight Gerado (SQL)


-- 1. Quantidade de usuários na base
SELECT COUNT(DISTINCT id) FROM my_db.usuarios_limpos;
-- Resposta: Há 10 usuários existentes na base.

-- 2. Cidades diferentes
SELECT COUNT(DISTINCT city) FROM my_db.usuarios_limpos;
-- Resposta: Há 10 cidades diferentes.

-- 3. Distribuição de usuários por cidade
SELECT city, COUNT(*) AS qtd_usuarios FROM my_db.usuarios_limpos GROUP BY city;
-- Resposta: Cada usuário mora em uma região diferente.

-- 4. Empresas cadastradas
SELECT DISTINCT company_name FROM my_db.usuarios_limpos;
-- Resposta: 10 empresas diferentes aparecem (a empresa Romaguera aparece 2 vezes: Crona e Jacobson).

-- 5. Verificação de dados ausentes e duplicados
SELECT * FROM my_db.usuarios_limpos;
-- Resposta: Não há dados ausentes nem registros duplicados.


---
<img width="1095" height="824" alt="IMG_0950" src="https://github.com/user-attachments/assets/7bf08c37-873d-4e8f-ad69-584fb8e9b28b" />

---



### 🎙️ Apresentação Executiva do Dashboard (Relatório do Projeto)

> **De:** Calebe Valério (Analytics Engineer)  
> **Para:** Liderança de Business Intelligence  
> **Assunto:** Diagnóstico da Base de Clientes via API JSONPlaceholder  

Prezados, apresento os resultados da higienização da base de clientes consumida via API REST, processada em Python/Pandas, armazenada no DuckDB e visualizada no Looker Studio. 

Abaixo estão as respostas diretas aos requisitos solicitados:

1. **Volume de Usuários:** A base contém exatamente **10 usuários cadastrados**.
2. **Distribuição Geográfica (Cidades):** Existem **10 cidades distintas**. A presença de clientes é 100% pulverizada, significando que cada cliente reside em uma cidade diferente (todas possuem 1 usuário, sem concentração única).
3. **Mapeamento de Empresas:** Foram identificadas **10 entidades empresariais**. Destaque para o grupo *Romaguera*, que atua com duas divisões operacionais distintas na base (*Romaguera-Crona* e *Romaguera-Jacobson*).
4. **Qualidade dos Dados (Ausentes e Duplicados):** A base de dados final apresenta **0% de registros nulos e 0% de duplicidades**, estando completamente tratada e auditada pelo pipeline de ETL.
5. **Decisão de Arquitetura de Colunas:** Todas as colunas estruturais foram preservadas e organizadas (incluindo geolocalização e contatos) para garantir que o time de BI tenha granularidade total sem necessidade de novos tratamentos.

