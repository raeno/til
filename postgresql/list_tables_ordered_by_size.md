# Show all tables sizes ordered

#### Faster version - only table size
```sql
SELECT table_name, 
    pg_size_pretty(pg_relation_size(quote_ident(table_name))) as size,
    pg_relation_size(quote_ident(table_name)) as detailed_size    
FROM information_schema.tables
WHERE table_schema = 'public'
ORDER BY detailed_size DESC
```


#### Slower version - also displays total size for relation including all indexes
```sql
SELECT table_name, 
    pg_size_pretty(pg_relation_size(quote_ident(table_name))) as size,
    pg_size_pretty(pg_total_relation_size(quote_ident(table_name))) as total_size_with_indexes,
    pg_relation_size(quote_ident(table_name)) as detailed_size,
    pg_total_relation_size(quote_ident(table_name)) as total_size_with_indexes
FROM information_schema.tables
WHERE table_schema = 'public'
ORDER BY pg_relation_size(quote_ident(table_name)) DESC
```
