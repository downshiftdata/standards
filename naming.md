# Naming Conventions

*"There are two hard problems in computer science: cache invalidation, naming things, and off-by-one errors." - source unknown*

## General Principles

1. Barring mitigating factors, avoid abbreviations.
1. Capitalize abbreviations with PascalCase or camelCase as appropriate. Do not use all caps. *Example: `KpiJson`, not `KPIJSON`.*
1. Use present tense when naming. *Example: `ModifyDate`, not `ModifiedDate`.*
1. All other things considered, choose names so that elements that are tightly coupled are alphabetically adjacent and well-sorted.

## Database Naming Principles

1. Do not use the `dbo` schema.
1. For write procedures, use an ObjectVerb or Object_Verb syntax. *Example: `Invoice_Insert`, not `InsertInvoice`.*
1. For `BIT` elements, use an `Is` prefix when feasible. *Example: `IsActive`, not `Active`.*
1. Use all caps for all SQL keywords. *Example: `SELECT MyColumn FROM MyTable;`.*
1. Use all lower case for table aliases. Alias using the first character of each word, appending a number if necessary. *Example: `SELECT mt.MyColumn FROM MyTable AS mt;`.*
1. Use camelCase only for object-scoped elements (e.g. anything defined by `DECLARE`). Use PascalCase for everything else. *Example: `@MyParameter` is a parameter of a stored procedure, but `@myVariable` is a variable declared within the stored procedure.*
1. For enumeration tables, use a `Key` suffix for the primary key field and a `Name` suffix for the enumeration name. When including the enumeration in another table, do not use the `Key` suffix. *Example: `MyTable.MyEnum` refers to `MyEnum.MyEnumKey`, and `MyEnum` also contains `MyEnum.MyEnumName`.*
1. For tables that are not enumerations, use a `Key` suffix for all primary key and foreign key fields. For primary keys, use the name of the table when feasible. *Example: `MyTableKey` for `MyTable`.*
1. The suffix `Log` is reserved for write-once tables. *Example: `AuthorizationLog`.*
1. The suffix `History` is reserved for the write-once partition of a two- or three-table horizontally-partitioned table set. The keyword `Revision` is reserved for the column that tracks the revision number of each row of this table. *Example: For example, for a row that has been inserted and then updated twice in a two-table set, `Invoice.Revision` holds `3`, while `InvoiceHistory.Revision` holds `1` and `2` for the rows stored there.*

### TODO

- Index and constraint names