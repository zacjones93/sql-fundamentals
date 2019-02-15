# sql-fundamentals

## Setup
[Download for Windows / Linux](https://www.sqlite.org/download.html)
```
sqlite3
```
```
.headers on
```
```
.mode column
```

### Step 1 - Creating a Table

```
create table Users (
    create_date date,
    last_name text,
    first_name text,
    email text
);
```

[More on types](https://www.journaldev.com/16774/sql-data-types#sql-numeric-data-types)

### Step 2 - Adding Data

```
insert into Users (create_date, last_name, first_name, email) values ('2018-06-06', 'clark', 'tyler', 'tyler@gmail.com');
```

```
insert into Users values ('2018-08-20', 'Jones', 'Bob', 'bob@gmail.com');
```

```
insert into Users values (date('now'), 'Jones', 'Bob', 'bob@gmail.com');
```

### Step 3 - Selecting Data

```
select * from Users;
```
```
select first_name, last_name, date('now') from Users;
```
```
select first_name as FirstName, last_name as LastName, date('now') as today from Users;
```

### Step 4 - Updating Data

```
update Users set last_name = 'berry', first_name = 'jerry' where last_name = 'clark';
```

### Step 5 - Deleting Data

```
delete from Users where last_name = 'Jones';
```

```
truncate table Users;
```
*truncate Does not work in SQLite, just use delete without filter*
```
drop table Users;
```

### Step 6 - Working with Constraints

```
create table Users (
    create_date date,
    last_name text,
    first_name text,
    email text,
    constraint PK_Users primary key (email)
);
```

```
create table Users (
    create_date date,
    last_name text,
    first_name text not null,
    email text,
    constraint PK_Users primary key (email)
);
```

### Step 7 - Working with Indexes

```
create index create_dates ON Users (create_date);
```

```
.indexes Users
```

```
drop index create_date;
```

### Step 8 - Aggregate functions and grouping data

```
select min(create_date), last_name, first_name from Users;
```

```
select max(create_date), last_name, first_name from Users;
```

```
select count(*), last_name from Users group by last_name;
```

### Step 9 - Filtering Data

```
select create_date, last_name, first_name from Users where  last_name = 'clark';
```

### Step 10 - Joining Tables

```
create table Purchases (email text, order_number text, item text, cost int, date datetime);
```

```
insert into Purchases (email, order_number, item, cost, date) values ('tyler@gmail.com', '111-222-3121', 'razors', 23.20, '2019-01-12 12:30:12');
```

```
select * from Users u left outer join Purchases ua on u.email = ua.email;
```
