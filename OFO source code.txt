create database Online_Food_Ordering;
use Online_Food_Ordering;

create table customers (
  customer_id int primary key NOT NULL,
  first_name varchar (255) NOT NULL,
  last_name varchar (255) NOT NULL,
  email_id varchar (255) NOT NULL,
  cpassword varchar (255) NOT NULL,
  phone_no varchar (10) NOT NULL,
  cstate varchar (255) NOT NULL,
  city varchar (255) NOT NULL,
  landmark varchar (255) NOT NULL,
  pincode int NOT NULL);


insert into customers values
('1', 'nikita', 'joshi', 'nrj2000@gmail.com', '12345', '9111111111', 'Maharashtra', 'Mumbai', 'state bank', '574154'),
('2', 'sristi', 'kushwaha', 'sristiii2@gmail.com', '123456', '9764316497', 'Maharashtra', 'Mumbai', 'urva store', '574154'),
('3', 'mansi', 'kasar', 'mansik11@gmail.com', '2345', '9888888856', 'Maharashtra', 'Mumbai', 'urva store', '574154'),
('4', 'sheldon', 'cooper', 'shldonc45@gmail.com', '12345', '9865326598', 'Maharashtra', 'Mumbai', 'hsr layout', '500004'),
('5', 'penny', 'hofstader', 'penny14@gmail.com', '45698', '9081649731', 'Maharashtra', 'Mumbai', 'bda complex hbr layout', '560102'),
('6', 'leonard', 'hofstader', 'leonard00@gmail.com', '123456', '9632895563', 'Maharashtra', 'Mumbai', 'vijayanagar vijaya bank layout', '560040'),
('7', 'raj', 'koothrapalli', 'rajk29@gmail.com', '123456', '9741628856', 'Maharashtra', 'Mumbai', 'urva store', '574154'),
('8', 'howard', 'wolowitz', 'wolowitz77@gmail.com', '123', '9741628856', 'Maharashtra', 'Mumbai', 'city centre mall mg road', '574154'),
('9', 'amy', 'fowler', 'fowleramy@gmail.com', '123', '9101928856', 'Maharashtra', 'Mumbai', 'near state bank circle', '574154');
select * from customers;


create table menu1 (
 menu_id int NOT NULL primary key,
 menu_name varchar (255) NOT NULL,
 price int NOT NULL);


insert into menu1 values
('1', 'Deep Dish Pizza', '450'),
('2', 'Loaded Nachos', '275'),
('3', 'Cheesy Poutine', '300'),
('4', 'Jalapeno Cheese Balls', '260'),
('5', 'Burj Khalifa Burger', '175'),
('6', 'Peri-Peri Fries', '200'),
('7', 'Alfredo Pasta', '325'),
('8', 'Burnt-garlic Noodles', '280'),
('9', 'Green Thai Curry', '360'),
('10', 'Red velvet Mousse', '220'),
('11', 'Dark Fantasy Eclaire', '180'),
('12', 'Chocolate Overload Waffle', '160');
select *  from menu1;


create table order2 (
 order_id int primary key NOT NULL,
 customer_id int foreign key references customers(customer_id) NOT NULL,
 menuid int foreign key references menu1(menu_id),
 quantity int NOT NULL DEFAULT '1',
 orderstatus varchar (255) DEFAULT NULL,
 ordertime time);


insert into order2 values
('138', '2', '8', '2', 'DELIVERED', '12:58:42'),
('139', '9', '4', '3', 'DELIVERED', '12:58:37'),
('140', '4', '2', '2', 'DELIVERED', '12:58:53'),
('141', '5', '1', '1', 'DELIVERED', '12:58:47'),
('143', '3', '5', '3', 'DELIVERED', '04:21:26'),
('146', '1', '12', '3', 'DELIVERED', '05:43:38'),
('147', '7', '11', '1', 'DELIVERED', '05:43:42'),
('148', '8', '6', '2', 'DELIVERED', '14:12:03'),
('149', '2', '9', '4', 'DELIVERED', '09:55:38'),
('150', '3', '7', '1', 'DELIVERED', '15:28:08'),
('151', '4', '9', '3', 'PAYMENT_CONFIRMED', '04:36:31'),
('152', '7', '10', '4', 'PAYMENT_CONFIRMED', '04:36:31'),
('153', '8', '2', '4', 'DELIVERED', '09:55:47'),
('156', '1', '6', '2', 'DELIVERED', '04:31:09'),
('159', '5', '12', '2', 'ADDED_TO_CART', '07:59:28'),
('160', '3', '10', '3', 'DELIVERED', '04:16:04'),
('162', '4', '3', '1', 'PAYMENT_CONFIRMED', '09:54:04'),
('165', '8', '11', '1', 'DELIVERED', '10:58:53');
select * from order2;


create table payment4 (
payment_id int primary key,
order_id int foreign key references order2(order_id) NOT NULL,
payment_type varchar (255) NOT NULL DEFAULT 'CASH_ON_DELIVERY',
payment_status varchar (255),
time_stamp time NOT NULL, 
check (payment_type ='CASH_ON_DELIVERY' or payment_type ='ONLINE_PAYMENT'), 
check (payment_status ='CONFIRMED' or payment_status ='NOT CONFIRMED')); 


insert into payment4 values
('7','138', 'CASH_ON_DELIVERY', 'CONFIRMED', '12:53:56'),
('8','139', 'CASH_ON_DELIVERY', 'CONFIRMED', '12:53:56'),
('9','140', 'ONLINE_PAYMENT', 'CONFIRMED', '12:57:37'),
('10','141', 'ONLINE_PAYMENT', 'CONFIRMED', '12:57:37'),
('11','143', 'CASH_ON_DELIVERY', 'NOT CONFIRMED', '17:43:49'),
('12','146', 'ONLINE_PAYMENT', 'CONFIRMED', '04:20:01'),
('13','147', 'ONLINE_PAYMENT', 'NOT CONFIRMED', '04:20:01'),
('14','148', 'CASH_ON_DELIVERY', 'CONFIRMED', '05:44:28'),
('15','149', 'CASH_ON_DELIVERY', 'CONFIRMED', '07:54:10'),
('16','150', 'CASH_ON_DELIVERY', 'CONFIRMED', '07:54:10'),
('17','151', 'CASH_ON_DELIVERY', 'CONFIRMED', '04:36:31'),
('18','152', 'CASH_ON_DELIVERY', 'NOT CONFIRMED', '04:36:31'),
('19','153', 'CASH_ON_DELIVERY', 'CONFIRMED', '04:36:31'),
('20','156', 'CASH_ON_DELIVERY', 'CONFIRMED', '06:29:11'),
('21','159', 'CASH_ON_DELIVERY', 'CONFIRMED', '04:15:10'),
('22','160', 'ONLINE_PAYMENT', 'CONFIRMED', '09:54:04'),
('23','162', 'ONLINE_PAYMENT', 'CONFIRMED', '10:57:53'),
('24','165', 'CASH_ON_DELIVERY', 'CONFIRMED', '05:44:28');
select * from payment4;


create table payment_details3 (
 payment_id int foreign key references payment4(payment_id) NOT NULL,
 customer_id int foreign key references customers(customer_id)NOT NULL,
 card_number varchar (16) NOT NULL,
 cvv int NOT NULL,
 exp_month int NOT NULL,
 exp_year int NOT NULL,
 primary key(payment_id, customer_id));


insert into payment_details3 values
('8', '9', '1234123412341234', '123', '10', '25'),
('9', '4', '1230123412341234', '123', '12', '34'),
('10', '5', '1234023412341234', '123', '3', '19'),
('11', '3', '1234163412341234', '122', '12', '22'),
('12', '1', '1234123612341234', '123', '12', '22'),
('13', '7', '1234123412306234', '123', '12', '22');
Select * from payment_details3;


--simple queries
select * from customers where first_name like 'S%';
select * from order2 where orderstatus='PAYMENT_CONFIRMED';
select distinct quantity from order2;
select * from payment_details2 where  customer_id>'4';

--update
update payment4 set payment_status='NOT CONFIRMED' where order_id='165';

--group by clause
select menuid, count(quantity) as no_of_orders from order2 where orderstatus='DELIVERED' group by menuid;

--join
select * from payment4 join payment_details2 on (payment4.payment_id=payment_details2.payment_id);

--left outer join
select * from menu1 left outer join order2 on (menu1.menu_id=order2.menuid) where menu1.price='275';

--view
create view order_detail as 
select * from order2
where menuid = (select menu_id from menu1 where menu_name='Peri-Peri Fries');
select * from order_detail;

--nested query
select menuid, quantity, orderstatus from order2 where menuid in (select menu_id from menu1 where price > '300' and quantity>'2');

select menu_name from menu1 where menu_id in (select menu_id from menu1 where price > '300');

--complex query
select payment_id as id, payment_type, payment_status, time_stamp as morning_time from payment4 
where time_stamp between '05:00:00' and '12:00:00' and payment_status='CONFIRMED' and payment_type='CASH_ON_DELIVERY' ;

--procedure
create procedure bill_detail
as 
select * from payment4 where payment_type='ONLINE_PAYMENT'
go
exec bill_detail;

select *  from menu1;

--trigger
create trigger price_limit on menu1 for update 
as
begin
if ((select price from inserted) > '150')
begin
print 'Updated Successfully';
commit
end
else
begin
print 'Price should be greater than 150';
rollback
end
end;0

update menu1 set price = '120' where menu_id = '12';


