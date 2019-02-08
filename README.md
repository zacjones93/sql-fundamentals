# sql-fundamentals

### Step 1 - Creating a Table

```
create table Users (
    create_date date,
    last_name text,
    first_name text,
    email text
);
```

### Step 2 - Adding Data

```
insert into Users (create_date, last_name, first_name, email) values ('2018-06-06', 'clark', 'tyler', 'tyler@gmail.com');
```

```
insert into Users (create_date, last_name, first_name, email) values ('2018-08-20', 'Jones', 'Bob', 'bob@gmail.com');
```

### Step 3 - Selecting Data

```
select * from Users;
```

### Step 4 - Updating Data

```
update Users set last_name = 'berry' where last_name = 'clark';
```

### Step 5 - Deleting Data

```
delete from Users where last_name = 'Jones’;
```

```
truncate table Users
```

```
drop table Users
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
    first_name text,
    email text not null,
    constraint PK_Users primary key (email)
);
```

### Step 7 - Working with Indexes

```
create index create_dates ON Users (create_date);
```

```
drop index table_name.index_name;
```

### Step 8 - Aggregate functions and grouping data

```
select min(create_date), last_name, first_name from Users;
```

```
select max(create_date), last_name, first_name from Users;
```

```
select create_date, last_name, first_name from Users group by ;
```

### Step 9 - Filtering Data

```
select create_date, last_name, first_name from Users where  ;
```

### Step 10 - Joining Tables

```
create table User_address (email text, address text, state text, zip text);
```

```
insert into User_address (
  address,
  state,
  zip,
  email
) values ('1540 wood st', 'TX', '78225', 'bob@gmail.com');
```

```
select * from Users u left outer join User_address ua on u.email = ua.email;
```
