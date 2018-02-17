
# to create a database

~~~sql
create database shop;
~~~

# to select a database

~~~sql
use shop;
~~~

# to create a table

~~~sql
create table users(
  id serial,
  name varchar(30) not null,
  email varchar(30) not null,
  password varchar(250) not null
);
~~~

# to create a table with one to may relationship

~~~sql
create table products (
  id serial,
  title varchar(255) not null,
  description text,
  image varchar(255),
  price int(11) not null,
  user_id bigint(20) unsigned,
  foreign key(user_id) references users(id) on delete cascade
);
~~~

# creating category table 

~~~sql
create table categories(
  id serial,
  name varchar(30)
);
~~~


# create a pivot table for many to many relationship

~~~sql
create table product_category(
  product_id bigint(20) unsigned,
  category_id bigint(20) unsigned,
  primary key(product_id, category_id),
  foreign key(product_id) references products(id) on delete cascade,
  foreign key(category_id) references categories(id) on delete cascade
);
~~~


# various way to insert data into database   

~~~sql
insert into users(name, email, password) values('mithu', 'mithu@gmail.com', 'secret');
insert into users values(1, 'mithu', 'mithu@gmail.com', 'secret');
insert into users set name='mithu', email='mithu@gmail.com', password='secret';
~~~


# inserting multiple data into users table   

~~~sql
insert into users(name, email, password) values
('mithu', 'mithu@gmail.com', 'secret'),
('hasan', 'hasan@gmail.com', 'secret'),
('helal', 'helal@gmail.com', 'secret'),
('qaim', 'qaim@gmail.com', 'secret'),
('jahir', 'jahir@gmail.com', 'secret'),
('huzur', 'huzur@gmail.com', 'secret'),
('huzur', 'huzur@gmail.com', 'secret'),
('ashiq', 'ashiq@gmail.com', 'secret') ;
~~~

# inserting multiple data into products table   

~~~sql
insert into products(title, description, price, user_id) values
('core i5 7200', '7th gen i5Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 180, 1),
('core i7 7500', '7th gen i7 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 280, 1),
('core i3 7100', '7th gen i3 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 190, 2),
('core i5 8400', '8th gen i5 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 180, 3),
('core i5 8400k', 'Unlocked 8th gen i5 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 380, 4),
('NOte 4', 'Samsung note 4 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 199, 5),
('NOte 8', 'Samsung note 8 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 600, 6),
('S 8', 'Samsung S 8 Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 656, 2),
('Samsung S7 edge', 'Samsung S 7 edge Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis, minima.', 980, 5)
;
~~~


# inserting multiple data into categories table   

~~~sql
insert into categories (name) values
('processor'),
('pc parts'),
('mobile')
;
~~~

# inserting multiple data into product_category pivot table   

~~~sql
insert into product_category(product_id, category_id) values
(1, 1),
(2, 1),
(3, 1),
(4, 1),
(5, 1),
(1, 2),
(2, 2),
(3, 2),
(4, 2),
(5, 2),
(6, 3),
(7, 3),
(8, 3),
(9, 3)
;

~~~

# join query

~~~sql
select products.id, products.title, products.price, users.name from products join users where products.user_id = users.id;
~~~

# join query using on clause

~~~sql
select products.id, products.title, products.price, products.user_id, users.name, users.email, users.password from products join users on users.id = products.user_id;
~~~

# fetching specific field using pivot table 

~~~sql
select products.id, products.title, products.price, products.user_id, users.name, users.email, users.password from products join users on users.id = products.user_id where user.id = 2;
~~~

# some sql
* mysql 
* mariadb
* oracle
* sqlserver
* pgsql
* dbase
* sqlite















# users 
# products
# categories
# product_category




