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

select SaleDate, Amount from sales
where amount > 10000 and year(SaleDate) = 2022
order by amount desc;

-- BETWEEN condition
select * from sales 
where Boxes > 0 and Boxes <= 50;

select * from sales 
where Boxes between 0 and 50;

-- working with dates
select SaleDate, Amount, Boxes, weekday(SaleDate) as 'Day of week'  
from sales
where weekday(SaleDate) = 4; 

-- using other tables
select * from people
where team = 'Delish' or team = 'Jucies';

select * from people
where team in ('Delish' , 'Jucies');

select * from people
where salesperson like 'B%';

select * from people
where salesperson like '%B%'; 

select * from sales;

select SaleDate, Amount,
		case when amount < 1000 then 'under 1K'
			when amount < 5000 then 'under 5k'
            when amount < 10000 then 'under 10k'
            else '10k or more'
            end as 'amount category'
from sales;

-- using JOINS

select * from sales;

select * from people;

select s.SaleDate, s.Amount, p.Salesperson, p.SPID, p.spid
from sales s
join people p on p.spid = s.SPID;


select s.SaleDate, s.Amount, pr.Product
from sales s
left join products pr on pr.pid = s.pid;


-- JOINING MULTIPLE TABLES
select s.SaleDate, p.Salesperson, pr.Product, p.team
from sales s
join people p on p.SPID = s.SPID 
join products pr on pr.pid = s.pid;


-- JOIN with CONDITIONS
select s.SaleDate, p.Salesperson, pr.Product, p.team, s.Amount
from sales s
join people p on p.SPID = s.SPID 
join products pr on pr.pid = s.pid
join geo g on g.geoid = s.geoid
where s.amount < 500
and p.team = ''
and g.geo in ('new zealand', 'india')
order by saledate
