# SQL-projects-
These are SQL projects that I have personally worked on

-- Using select statement to answer questions 
select * from sales;

select SaleDate, Amount, Customers from sales;
select Amount, Customers, GeoID from sales;

-- Adding calculated columns 
select SaleDate, Amount, Amount / Boxes from sales;

select SaleDate, Amount, Amount / Boxes as 'Amount per box' from sales;

-- WHERE clauses 
select * from sales
where amount > 10000;

Select * from sales
where amount > 10000
order by Amount desc;

select * from sales
where GeoID = 'G1'
order by PID, Amount desc;

select * from sales
where Amount > 10000
and SaleDate >= '2022-01-01';
