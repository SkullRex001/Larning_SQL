
# SQL Commands Documentation

This README provides various SQL commands for database management, including renaming, deleting, and modifying databases, as well as creating tables and establishing foreign key relationships.

## 1. Rename a Database

```sql
ALTER DATABASE sample2
MODIFY NAME = sample3;
```

Alternatively, using a system procedure:

```sql
EXEC sp_renameDB 'sample3', 'sample4';
```

## 2. Delete a Database

```sql
DROP DATABASE sample2;
```

## 3. Delete a Database with Multiple Users

To delete a database when multiple users are accessing it:

```sql
ALTER DATABASE sample2
SET SINGLE_USER
WITH ROLLBACK IMMEDIATE;
```

## 4. Create and Insert into a Database

### Create Database

```sql
CREATE DATABASE avs;
USE avs;
```

### Create Tables

#### `tblPerson` Table

```sql
CREATE TABLE tblPerson (
    ID INT NOT NULL PRIMARY KEY,
    Name NVARCHAR(50) NOT NULL,
    Email NVARCHAR(50) NOT NULL,
    GenderID INT
);
```

#### `tblGender` Table

```sql
CREATE TABLE tblGender (
    ID INT NOT NULL PRIMARY KEY,
    Gender NVARCHAR(50) NOT NULL
);
```

## 5. Alter Table and Add Foreign Key

To establish a relationship between `tblPerson` and `tblGender`:

```sql
ALTER TABLE tblPerson
ADD CONSTRAINT tblePerson_GenderID_FK
FOREIGN KEY (GenderID) REFERENCES tblGender(ID);
```
