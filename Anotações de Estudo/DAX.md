# 🔹 DAX

A linguagem **DAX** (*Data Analysis Expressions*) é amplamente usada no **Microsoft Power BI**, **Excel Power Pivot** e **Analysis Services** para realizar cálculos e análises em dados tabulares. Ela permite criar medidas, colunas calculadas e tabelas dinâmicas que respondem ao contexto de filtro aplicado nos relatórios.

## Aqui estão alguns dos comandos e funções mais usados em DAX:


<details>
<summary>Funções Agregadoras</summary>
   
## **Funções Agregadoras**:

   - `SUM`:
     ```dax
     Total Sales = SUM(Sales[Amount])
     ```
     Isso calcula a soma dos valores na coluna "Amount" da tabela "Sales".

   - `AVERAGE`:
     ```dax
     Average Price = AVERAGE(Products[Price])
     ```
     Calcula a média dos preços dos produtos na tabela "Products".

   - `COUNT`:
     ```dax
     Number of Orders = COUNT(Orders[OrderID])
     ```
     Conta o número de IDs de pedidos na tabela "Orders".

</details>

<details>
<summary>Funções Lógicas</summary>

## **Funções Lógicas**:

   - `IF`:
     ```dax
     Status = IF(Sales[Amount] > 1000, "High", "Low")
     ```
     Avalia se o valor na coluna "Amount" é maior que 1000 e retorna "High" se verdadeiro, caso contrário, "Low".

   - `AND`:
     ```dax
     Eligible = AND(Sales[Amount] > 1000, Sales[Region] = "North")
     ```
     Verifica se o valor na coluna "Amount" é maior que 1000 e a região é "North".

   - `OR`:
     ```dax
     Discount Eligibility = OR(Sales[Amount] > 2000, Sales[CustomerLevel] = "Preferred")
     ```
     Verifica se o valor na coluna "Amount" é maior que 2000 ou se o nível do cliente é "Preferred".

</details>

<details>
<summary>Funções de Tabela</summary>

## **Funções de Tabela**:

   - `FILTER`:
     ```dax
     High Sales = FILTER(Sales, Sales[Amount] > 1000)
     ```
     Cria uma nova tabela com apenas as linhas da tabela "Sales" em que o valor na coluna "Amount" seja maior que 1000.

   - `ALL`:
     ```dax
     All Customers = ALL(Customers)
     ```
     Remove todos os filtros aplicados à tabela "Customers", retornando a tabela completa.

   - `VALUES`:
     ```dax
     Unique Products = VALUES(Products[ProductName])
     ```
     Retorna uma tabela com valores únicos da coluna "ProductName" da tabela "Products".

</details>

<details>
<summary>Funções de Tempo</summary>

## **Funções de Tempo**:

   - `TODAY`:
     ```dax
     Current Date = TODAY()
     ```
     Retorna a data atual.

   - `YEAR`:
     ```dax
     Order Year = YEAR(Orders[OrderDate])
     ```
     Extrai o ano da coluna "OrderDate" da tabela "Orders".
     
</details>

<details>
<summary>Funções de Texto</summary>
   
## **Funções de Texto**:

   - `CONCATENATE`:
     ```dax
     Full Name = CONCATENATE(Users[FirstName], " ", Users[LastName])
     ```
     Combina as colunas "FirstName" e "LastName" da tabela "Users" em um nome completo.

   - `LEFT`:
     ```dax
     First Letter = LEFT(Products[ProductName], 1)
     ```
     Retorna a primeira letra do nome do produto na coluna "ProductName".

</details>

<details>
<summary>Funções de Data e Hora</summary>

## **Funções de Data e Hora**:

   - `DATEDIFF`:
     ```dax
     Days Between = DATEDIFF(Orders[OrderDate], Orders[ShipDate], DAY)
     ```
     Calcula o número de dias entre as colunas "OrderDate" e "ShipDate" na tabela "Orders".

   - `DATEADD`:
     ```dax
     Next Quarter = DATEADD(Calendar[Date], 1, QUARTER)
     ```
     Adiciona um trimestre à data na coluna "Date" da tabela "Calendar".

</details>

<details>
<summary>Funções de Informação de Tabela</summary>
   
## **Funções de Informações de Tabela**:

1. `COLUMNS`:
   ```dax
   Column Names = COLUMNS(Sales)
   ```
   Retorna uma lista de nomes de colunas da tabela "Sales".

2. `ROW`:
   ```dax
   New Customer = ROW("CustomerName", "John", "OrderCount", 3)
   ```
   Cria uma nova linha (tabela) com as colunas e valores especificados.

3. `CONTAINS`:
   ```dax
   Contains Product = CONTAINS(Products, Products[ProductName], "Widget")
   ```
   Verifica se a tabela "Products" contém a palavra "Widget" na coluna "ProductName".

</details>

<details>
<summary>Funções de Gerenciamento de Contexto</summary>
   
## **Funções de Gerenciamento de Contexto**:

1. `CALCULATE`:
   ```dax
   Total Sales in 2022 = CALCULATE(SUM(Sales[Amount]), Sales[Year] = 2022)
   ```
   Calcula o total de vendas para o ano de 2022.

2. `ALLSELECTED`:
   ```dax
   Total Sales All Selected = CALCULATE(SUM(Sales[Amount]), ALLSELECTED(Sales))
   ```
   Calcula o total de vendas, ignorando todos os filtros, exceto aqueles selecionados pelo usuário.

3. `EARLIER`:
   ```dax
   Previous Row Sales = EARLIER(Sales[Amount])
   ```
   Retorna o valor da coluna "Amount" na linha anterior do contexto de filtro.

4. `FILTERS`:
   ```dax
   Active Filters = FILTERS()
   ```
   Retorna uma tabela com os filtros ativos no contexto atual.

</details>

<details>
<summary>Funções de de Tratamento de Erros</summary>

## **Funções de Tratamento de Erros**:

1. `ISBLANK`:
   ```dax
   Check if Description is Blank = IF(ISBLANK(Products[Description]), "No description available", Products[Description])
   ```
   Verifica se a coluna "Description" está em branco e fornece uma mensagem personalizada.

2. `IFERROR`:
   ```dax
   Safe Division = IFERROR(DIVIDE(1, 0), 0)
   ```
   Tenta realizar uma divisão segura e retorna 0 em caso de erro.

3. `ERROR`:
   ```dax
   Custom Error = ERROR("This is a custom error message.")
   ```
   Retorna uma mensagem de erro personalizada.

</details>

<details>
<summary>Funções de Tabelas Relacionadas</summary>
   
## **Funções de Valores em Tabelas Relacionadas**:

1. `RELATED`:
   ```dax
   Salesperson Name = RELATED(Salespeople[Name])
   ```
   Retorna o nome do vendedor relacionado à tabela "Salespeople".

2. `RELATEDTABLE`:
   ```dax
   Related Orders = RELATEDTABLE(Orders)
   ```
   Retorna uma tabela relacionada à tabela "Orders".

3. `RELATEDTO`:
   ```dax
   Total Sales by Related Customer = SUMX(Customers, RELATEDTO(Sales[Amount]))
   ```
   Calcula o total de vendas relacionadas a cada cliente na tabela "Customers".

</details>

<details>
<summary>Funções de Classificação e Filtragem</summary>
   
## **Funções de Classificação e Filtragem**:

1. `RANKX`:
   ```dax
   Sales Rank = RANKX(Sales, Sales[Amount])
   ```
   Calcula a classificação das vendas com base no valor na coluna "Amount".

2. `TOPN`:
   ```dax
   Top 10 Products by Sales = TOPN(10, Products, Sales[Amount])
   ```
   Retorna os 10 produtos com as maiores vendas.

3. `FILTER`:
   ```dax
   High-Value Customers = FILTER(Customers, Customers[TotalPurchase] > 1000)
   ```
   Filtra os clientes com um valor total de compra superior a 1000.

</details>

<details>
<summary>Funções de Matriz</summary>
   
## **Funções de Matriz**:

1. `SUMX`:
   ```dax
   Total Sales = SUMX(Sales, Sales[Quantity] * Sales[Price])
   ```
   Calcula o total de vendas multiplicando a quantidade pelo preço para cada linha de vendas.

2. `AVERAGEX`:
   ```dax
   Average Sales per Order = AVERAGEX(Orders, RELATED(Sales[Amount]))
   ```
   Calcula a média de vendas relacionadas a cada pedido na tabela "Orders".

3. `COUNTAX`:
   ```dax
   Count of High-Value Products = COUNTAX(Products, IF(Products[Price] > 100, 1, 0))
   ```
   Conta os produtos com preço superior a 100 na tabela "Products".

</details>

<details>
<summary>Funções de Manipulação de Dados</summary>
   
## **Funções de Manipulação de Dados**:

1. `UNION`:
   ```dax
   Combined Sales = UNION(Sales2022, Sales2023)
   ```
   Combina duas tabelas de vendas em uma única tabela.

2. `EXCEPT`:
   ```dax
   Unique Customers = EXCEPT(AllCustomers, VIPCustomers)
   ```
   Retorna os clientes que não estão na lista de clientes VIP.

3. `INTERSECT`:
   ```dax
   Shared Products = INTERSECT(PromotionalProducts, BestSellingProducts)
   ```
   Retorna os produtos que estão em ambas as listas de produtos promocionais e mais vendidos.

</details>

<details>
<summary>Funções de Geolocalização</summary>
   
## **Funções de Geolocalização**:

1. `DISTANCE`:
   ```dax
   Distance to Store = DISTANCE(StoreLocation, CustomerLocation)
   ```
   Calcula a distância entre a localização da loja e a localização do cliente.

2. `GEOGRAPHYPOINT`:
   ```dax
   Customer Location = GEOGRAPHYPOINT(Customer[Latitude], Customer[Longitude])
   ```
   Cria um ponto de geolocalização com base nas coordenadas de latitude e longitude do cliente.
