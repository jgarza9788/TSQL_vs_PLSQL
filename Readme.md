T-SQL vs PL/SQL
---

# T-SQL vs. PL/SQL Syntax Comparison

## 1. **Declaring Variables**

### T-SQL:
```sql
DECLARE @variable_name datatype;
SET @variable_name = value;
```

### PL/SQL:
```sql
DECLARE
    variable_name datatype := value;
BEGIN
    -- Code block
END;
```

## 2. **Conditional Statements**

### T-SQL:
```sql
IF condition
BEGIN
    -- Code block
END
ELSE
BEGIN
    -- Code block
END
```

### PL/SQL:
```sql
IF condition THEN
    -- Code block
ELSIF another_condition THEN
    -- Code block
ELSE
    -- Code block
END IF;
```

## 3. **Loops**

### T-SQL:
```sql
WHILE condition
BEGIN
    -- Code block
END
```

### PL/SQL:
```sql
LOOP
    -- Code block
    EXIT WHEN condition;
END LOOP;

-- or

WHILE condition LOOP
    -- Code block
END LOOP;

-- or

FOR counter_variable IN lower_bound..upper_bound LOOP
    -- Code block
END LOOP;
```

## 4. **Error Handling**

### T-SQL:
```sql
BEGIN TRY
    -- Code block
END TRY
BEGIN CATCH
    -- Error handling code
END CATCH
```

### PL/SQL:
```sql
BEGIN
    -- Code block
EXCEPTION
    WHEN exception_name THEN
        -- Error handling code
END;
```

## 5. **Stored Procedures**

### T-SQL:
```sql
CREATE PROCEDURE procedure_name
    @parameter datatype
AS
BEGIN
    -- Code block
END;
```

### PL/SQL:
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameter_name datatype)
IS
BEGIN
    -- Code block
END procedure_name;
```

## 6. **Function Declaration**

### T-SQL:
```sql
CREATE FUNCTION function_name (@parameter datatype)
RETURNS return_datatype
AS
BEGIN
    -- Code block
    RETURN value;
END;
```

### PL/SQL:
```sql
CREATE OR REPLACE FUNCTION function_name (parameter_name datatype)
RETURN return_datatype
IS
BEGIN
    -- Code block
    RETURN value;
END function_name;
```

## 7. **Executing SQL within Code Blocks**

### T-SQL:
```sql
-- Embedded SQL
SELECT column_name
INTO @variable_name
FROM table_name
WHERE condition;
```

### PL/SQL:
```sql
-- Embedded SQL
SELECT column_name
INTO variable_name
FROM table_name
WHERE condition;
```

## 8. **Transaction Control**

### T-SQL:
```sql
BEGIN TRANSACTION;
-- Code block
COMMIT TRANSACTION;

-- or

ROLLBACK TRANSACTION;
```

### PL/SQL:
```sql
BEGIN
    -- Code block
    COMMIT;
    -- or
    ROLLBACK;
END;
```

## 9. **Cursor Management**

### T-SQL:
```sql
DECLARE cursor_name CURSOR FOR
    SELECT column_name FROM table_name;

OPEN cursor_name;
FETCH NEXT FROM cursor_name INTO @variable_name;

WHILE @@FETCH_STATUS = 0
BEGIN
    -- Code block
    FETCH NEXT FROM cursor_name INTO @variable_name;
END;

CLOSE cursor_name;
DEALLOCATE cursor_name;
```

### PL/SQL:
```sql
DECLARE
    CURSOR cursor_name IS
        SELECT column_name FROM table_name;
    variable_name datatype;
BEGIN
    OPEN cursor_name;
    LOOP
        FETCH cursor_name INTO variable_name;
        EXIT WHEN cursor_name%NOTFOUND;
        -- Code block
    END LOOP;
    CLOSE cursor_name;
END;
```

## 10. **Comments**

### T-SQL:
```sql
-- Single-line comment

/*
Multi-line comment
*/
```

### PL/SQL:
```sql
-- Single-line comment

/*
Multi-line comment
*/
```

---

This document provides a high-level comparison of the syntactical differences between T-SQL and PL/SQL for common database operations. Each SQL dialect has its own unique set of capabilities and limitations, so it's important to understand these differences when migrating or working in a cross-platform environment.