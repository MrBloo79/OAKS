Type: #domain
Created:: 2023-10-03
Status:: [[Detailed]]
Domain:: 
Details:: Root for top-level domains

# Alignment Zone

```dataview
TABLE WITHOUT ID
    file.link AS Project,
    Status,
    Rank AS Priority,
    Due,
    Domain,
    Details
FROM #project 
```

# Action Zone

```dataview
TABLE WITHOUT ID
    regexreplace(task.text, "([➕📅⏳✅]|\[|\([🏅💬👤🔗]).*", "") AS Action,
    "`" + task.status + "`" AS S,
    task.🏅 AS P,
    task.due AS Due,
    file.link AS Project,
    task.🔗 AS Details
FROM #project 
FLATTEN file.tasks AS task
```

# Knowledge Zone

```dataview
TABLE WITHOUT ID
    file.link AS Asset,
    file.tags[0] AS Type,
    Status,
    Domain,
    Details
FROM #asset OR #item
WHERE !contains(file.path, "Xtras")
```