# NoUseDatabase

USE DATABASE statements are not allowed.

regex: `(?is)(?=.*\b(use)\b)(?=.*\b(database)\b)`

# Sample Failing Scripts
``` sql
--changeset amalik:create_order_table_w_use_statement
USE DATABASE mydb;
create or replace table order_table (
    orderkey number(38,0),
    custkey number(38,0)
)
;
```

# Sample Error Message
``` 
CHANGELOG CHECKS
----------------
Checks completed validation of the changelog and found the following issues:

Check Name:         Check for specific patterns in sql (NoUseDatabase)
Changeset ID:       create_order_table_w_use_statement
Changeset Filepath: changelog.sql
Check Severity:     BLOCKER (Return code: 4)
Message:            Error! USE DATABASE statements are not allowed.
```

# Step-by-Step
| Prompt | Command or User Input |
| ------ | ----------------------|
| > | `liquibase checks customize --check-name=SqlUserDefinedPatternCheck` |
| Give your check a short name for easier identification (up to 64 alpha-numeric characters only) [SqlUserDefinedPatternCheck1]: | `NoUseDatabase` |
| Set the Severity to return a code of 0-4 when triggered. (options: 'INFO'=0, 'MINOR'=1, 'MAJOR'=2, 'CRITICAL'=3, 'BLOCKER'=4)? [INFO]: | `<Choose a value: 0, 1, 2, 3, 4>` |
| Set 'SEARCH_STRING' (options: a string, or a valid regular expression): | `(?is)(?=.*\b(use)\b)(?=.*\b(database)\b)` |
| Set 'MESSAGE' [A match for regular expression <SEARCH_STRING> was detected in Changeset <CHANGESET>.]: | `Error! USE DATABASE statements are not allowed.` |
| Set 'STRIP_COMMENTS' (options: true, false) [true]: | `true` |
