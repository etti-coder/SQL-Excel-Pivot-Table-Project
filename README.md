# Bikestores_SQL-Excel-Project
Sql used for the analysis and excel used for the visualisation

## Project Objecticves and goals
- To know the sales activities and trends for 2016-2018
- As per reveneue per region
- Per store
- Per product category and brand
- Top ten costomers and sales reps for same period

## Collect and understand data

- Relational database(SQL)

## Clean and transform dataset
- Missing and duplicate values
- Data types conversion
- Direct and indirect data Joins of tables

## Analyse data

- Code and script for  table joins

````sql
select
   ord.order_id,
   CONCAT(cus.first_name, ' ', cus.last_name) as 'customers',
   cus.city,
   cus.state,
   ord.order_date,
   sum(ite.quantity) as 'total units',
   sum(ite.quantity * ite.list_price) as 'revenue',
   pro.product_name,
   cat.category_name,
  sto.store_name,
concat(sta.first_name, ' ' ,sta.last_name)sales_rep
from sales.orders ord
Join sales.customers cus
on ord.customer_id = cus.customer_id
join sales.order_items ite
on ord.order_id = ite.order_id
join production.products pro
on ite.product_id = pro.product_id
join production.categories cat
on pro.category_id = cat.category_id
join sales.stores sto
on ord.store_id = sto.store_id
join sales.staffs sta
on ord.staff_id = sta.staff_id
group by 
    ord.order_id,
   CONCAT(cus.first_name, ' ', cus.last_name),
   cus.city,
   cus.state,
   ord.order_date, 
   pro.product_name,
   cat.category_name,
   sto.store_name,
   concat(sta.first_name, ' ' ,sta.last_name)
````
## Interpret results(Pivot Charts)



