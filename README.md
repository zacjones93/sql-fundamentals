# sql-fundamentals

## Setup
For mac - [install homebrew](https://brew.sh/), then run `brew install postgres`

For windows- [Installer](https://www.postgresql.org/download/windows/)

After installation open terminal and run `psql postgres`

### Step 1 - Creating a Table

```
create table Users (
    create_date date,
    user_handle uuid,
    last_name text,
    first_name text
);
```

### Step 2 - Adding Data

```
insert into Users (create_date, user_handle, last_name, first_name ) values ('2018-06-06', 'a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11', 'clark', 'tyler');
```

```
insert into Users values ('2019-01-10', uuid_generate_v4(), 'johnson', 'patrick');
```

### Step 3 - Selecting Data

```
select * from Users;
```
```
select first_name, last_name, current_time from Users;
```
```
select first_name as FirstName, last_name as LastName, current_time as today from Users;
```
```
select distinct(last_name) from Users;
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
```
drop table Users;
```

### Step 6 - Working with Constraints

```
create table Users (
    create_date date,
    user_handle uuid,
    last_name text,
    first_name text,
    constraint PK_Users primary key (user_handle)
);
```

```
create table Users (
    create_date date not null,
    user_handle uuid not null unique,
    last_name text,
    first_name text not null
);
```

### Step 7 - Working with Indexes

```
create index test1_user_handle_index ON Users (user_handle);
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
```
select * from Users where create_date between '2018-05-01' and '2018-09-01';
```

### Step 10 - Joining Tables

```
create table Purchases (date date, user_handle uuid, sku uuid, quantity int);
```

```
insert into Purchases (date, user_handle, sku, quantity) values ('2018-12-12', 'a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11', uuid_generate_v4(), 2);
```

```
insert into Purchases values ('2019-02-02', uuid_generate_v4(), uuid_generate_v4(), 1);
```

```
select * from Users u left outer join Purchases ua on u.email = ua.email;
```
### Step 11 - Subqueries

```
select u.total, u.create_date, first_name from Users us inner join (select count(create_date) as total, create_date from Users group by create_date) u on u.create_date = us.create_date;
```
```
select create_date, first_name from Users where create_date = (select min(create_date) from Users);
```
