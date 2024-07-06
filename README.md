<img align="right" width="100" height="100" src="images/icon_metabase.png"/>

<img align="right" width="70" height="70" src="images/icon_sql.png"/>

# Análise em SQL: gere planos de ação a partir das suas consultas
<sub> Criando insights e gráficos por meio da linguagem SQL </sub>

> Construa um dashboard utilizando SQL no metabase em busca de definir os próximos passos de uma Edtech. Deverá utilizar as informações para estabelecer a estratégia da empresa para o próximo ano.

## 1. Contexto

Suponha que você seja um analista de dados em uma empresa Edtech. Sua empresa está focada
em acelerar seu crescimento aumentando o número de usuários cadastrados.
Portanto, você foi solicitado a analisar vários aspectos da aquisição de clientes para ver o status
do crescimento de novos usuários em sua empresa.

## 2. Sobre os dados
Os dicionário dos dados foram definidos abaixo:

<img align="center" src="images/sql_1.png"/>

<img align="center" src="images/sql_2.png"/>

<img align="center" src="images/sql_3.png"/>

<img align="center" src="images/sql_4.png"/>

## 3. Entrega
Dessa forma, é necessário criar um dashboard para permitir que a equipe de
negócios desenvolva planos de ação com o objetivo de aumentar o número de usuários
cadastrados e impulsionar o crescimento da empresa.

## 4. Desenvolvimento e códigos SQL

- [x] Para saber a distribuição de pessoas do sexo masculino e feminino foi utilizado o código:

`select 
count(lead_id), gender
from 
leads_basic_details
group by 
gender`

**Gráfico de pizza:**

<img align="center" src="images/pizza_1.png"/>

- [x] Consulta da quantidade de leads por grau de escolaridade:

`select count(lead_id) as Quantidade, current_education
from leads_basic_details
group by current_education
order by Quantidade`

**Gráfico de barras:**
<br>

<img align="center" src="images/graph_1.png"/>

- [x] Percentual de tempo assistido pela por idioma:

`language, avg(watched_percentage) as Porcentagem
from leads_demo_watched_details
where watched_percentage > 0.5
group by language`

**Obteve-se a tabela:**
<br>

<img align="center" width="220" height="170" src="images/language_1.png"/>
<br>

- [x] Quantidade de ligações atendidas por plataforma ao longo do tempo:

`select call_done_date, lead_gen_source, count(call_status)
from leads_interaction_details
left join 
leads_basic_details on leads_interaction_details.lead_id = leads_basic_details.lead_id
where 
call_status = 'successful'
group by 
lead_gen_source, call_done_date`

**Gráfico de linhas:**

<img align="center" src="images/ligacoes_1.png"/>

<br>

## 5. Conclusão

Mesmo com as consultas simples em SQL no METABASE, foi possível obter insights sobre os usuários que utilizam a plataforma assim como, com os dados obtidos, construir estratégias para a aquisição de novos clientes no futuro. 
