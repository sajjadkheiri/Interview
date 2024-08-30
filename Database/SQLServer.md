# SQL Server

### What is the difference between Function and SP : 

 **Function:** A stored procedure is a precompiled collection of SQL statements that can perform a variety of tasks, including data modification,
data retrieval, and control-of-flow operations. SPs can take input parameters, return output parameters, and return result sets.
They are typically used to:

1. Perform complex business logic or data processing
2. Encapsulate data modifications or validation rules
3. Improve performance by reducing network traffic and compilation overhead
5. Can return multiple result sets or output parameters
6. Can modify data or have side effects

**SP:** A function is a self-contained block of code that takes input parameters, performs calculations or operations,
and returns a single value. Functions can be used in SQL statements like any other expression.
They are typically used to:

1. Improve code reusability
2. Can only return a single value (scalar or table-valued)
3. Cannot modify data or have side effects
4. Can be used in SELECT, WHERE, and ORDER BY clauses
5. Can be indexed, if they are deterministic and precise
