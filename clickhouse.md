# clickhouse-markdown

```
// set database
USE DATABASE_NAME

// show all table
SELECT name from system.tables where database='DATABASE_NAME'

// delete (background job)
ALTER TABLE TABLE_NAME on CLUSTER '{cluster}' DELETE where xxx

// check unfinish async func
SELECT table, command, is_done, latest_failed_part, latest_fail_time, latest_fail_reason
FROM system.mutations
WHERE is_done = 0 and database='DATABASE_NAME'

// get partition list
SELECT partition FROM system.parts WHERE database='DATABASE_NAME' AND table='TABLE_NAME' GROUP BY partition

// select with partition
SELECT  * FROM DATABASE_NAME.TABLE_NAME WHERE (_partition_value.1) = 'PARTITION'

// drop table/view
drop table if exists DATABASE_NAME.TABLE_NAME on cluster '{cluster}';
drop view if exists DATABASE_NAME.VIEW_NAME on cluster '{cluster}';

// optimize
OPTIMIZE TABLE TABLE_NAME final DEDUPLICATE

// rename table
RENAME TABLE TABLE_NAME TO NEW_TABLE_NAME on cluster '{cluster}';

// truncate table
TRUNCATE DATABASE_NAME.TABLE_NAME

// update value
UPDATE DATABASE_NAME.TABLE_NAME SET COL_NAME = '*' WHERE SEL_CONDITION;

// add column
ALTER TABLE DATABASE_NAME.TABLE_NAME ADD COLUMN COL_NAME COL_TYPE;
```
