---
title: DROP CONSTRAINT
summary: Use the ALTER CONSTRAINT statement to remove constraints from columns.
toc: false
---

The `DROP CONSTRAINT` [statement](sql-statements.html) is part of `ALTER TABLE` and removes constraints from columns.

<div id="toc"></div>

## Synopsis

{% include sql/diagrams/drop_constraint.html %}

## Required Privileges

The user must have the `CREATE` [privilege](privileges.html) on the table. 

## Parameters

| Parameter | Description |
|-----------|-------------|
| `table_name` | The name of the table with the constraint you want to drop. |
| `name` | The name of the constraint you want to drop. |


## Example

~~~ sql
> SHOW CONSTRAINTS FROM orders;
~~~
~~~
+--------+---------------------------+-------------+-----------+----------------+
| Table  |           Name            |    Type     | Column(s) |    Details     |
+--------+---------------------------+-------------+-----------+----------------+
| orders | fk_customer_ref_customers | FOREIGN KEY | customer  | customers.[id] |
| orders | primary                   | PRIMARY KEY | id        | NULL           |
+--------+---------------------------+-------------+-----------+----------------+
~~~
~~~ sql
> ALTER TABLE orders DROP CONSTRAINT fk_customer_ref_customers;
~~~
~~~
ALTER TABLE
~~~
~~~ sql
> SHOW CONSTRAINTS FROM orders;
~~~
~~~
+--------+---------+-------------+-----------+---------+
| Table  |  Name   |    Type     | Column(s) | Details |
+--------+---------+-------------+-----------+---------+
| orders | primary | PRIMARY KEY | id        | NULL    |
+--------+---------+-------------+-----------+---------+
~~~

{{site.data.alerts.callout_info}}You cannot drop the <code>primary</code> constraint, which indicates your table's <a href="primary-key.html">Primary Key</a>.{{site.data.alerts.end}}

## See Also

- [`DROP COLUMN`](drop-column.html)
- [`DROP INDEX`](drop-index.html)
- [`ALTER TABLE`](alter-table.html)