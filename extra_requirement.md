# Requirement
As an extra requirement you’re asked to design (not implement) a efficient data structure that showsthe type of data of the following table given the spree_orders table from the database:
Basically the table consists of each email being a record on the table, a column for first order date, second order date and so on… we also want to see the order number of each order (first order, second order, etc...) on a different column.

# Analysis
The requirement talks about a data structure and this can be either a complex record type or a data model, lets review both approaches

## Complex Record Type
A complex record type is a type of record supported by most modern NoSQL databases, it can store in a single row, an array of data in one of its columns.

In this case we are required to use at least these
* id
* number
* total
* state
* created_at
* currency
* email

This way we can create a record similar to this:
```text
id:int
number:str
email:str
order{
      order:int (obtained using rank() by required keys) sorted by created_at
      created_at: datetime
      total:float
      state:str
      currency:str
      }
```
     
This can be stored in the database like BigQuery and then queried using the available SQL.

## Data model
If the solution required is one of a data model with tables, we can do a quick and simple model:

```text
                <---customer_id:id---
ORDER_TABLE                           CUSTOMER_TABLE
id                                    id
number                                email
order
total
created_at
customer_id
```

We can keep normalizing the model adding address table, etc, as needded
