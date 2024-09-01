# Oh-R-Mighty

**Oh-R-Mighty** is an Object-Relational Mapping (ORM) tool built with Python. The goals of this project are to practice SQL and object-oriented programming.

## Features

**Oh-R-Mighty** offers the following features:

- **Object-Oriented Mapping**: Map Python classes to database tables.
- **CRUD Operations**: Perform create, read, update, and delete operations with ease.
- **Query Interface**: Run queries using a user-friendly API.
- **Relationships**: Define and manage relationships between entities, such as one-to-one, one-to-many, and many-to-many.
- **Migrations**: Manage database schema changes with migration scripts.
- **Transactions**: Execute database operations within transactions to ensure data integrity.
- **Hooks and Validation**: Add custom validation and hook logic to run before or after certain operations.
- **Caching**: Optionally cache query results to improve performance.

## Getting Started

### Define Your Models

Start by defining your models using Python classes and decorators provided by **Oh-R-Mighty**.

```python
from oh_r_mighty import Entity, Column, PrimaryKey

@Entity('users')
class User:
    @PrimaryKey()
    id: int

    @Column()
    name: str

    @Column()
    email: str
```

Performing CRUD Operations
With your models defined, you can start performing CRUD operations.

```python
user = User()
user.name = "John Doe"
user.email = "john.doe@example.com"
user.save()

# Fetching a user
users = User.query().where(name='John Doe').get()

# Updating a user
user.name = "Jane Doe"
user.save()

# Deleting a user
user.delete()

```

Running Queries
Oh-R-Mighty provides a fluent API for building complex queries.

```python
users = User.query()
    .where(name__like='%Doe%')
    .order_by('-created_at')
    .get()
```

Defining Relationships
Manage relationships between your entities easily.

```python
@Entity('posts')
class Post:
    @PrimaryKey()
    id: int

    @Column()
    title: str

    @ManyToOne('User')
    user: User
```

![Discovery Image](./discovery.jpg)

