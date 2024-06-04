````pack-source domain
# Alignment Zone

```dataview
TABLE WITHOUT ID
    Domain,
    file.link AS Project,
    link(Status, Status.aliases) AS S,
    Rank AS P,
    Due,
    Details
FROM #project
WHERE contains(file.path, replace(this.file.name, "Vault", "/"))
```

# Action Zone

```dataview
TABLE WITHOUT ID
    file.link AS Project,
    regexreplace(task.text, "([➕📅⏳✅]|(\[|\()[🏅💬👤🔗]).*", "") AS Action,
    [[Map]].get[task.status] AS S,
    task.🏅 AS P,
    task.due AS Due,
    task.🔗 AS Details
FROM #project
FLATTEN file.tasks AS task
WHERE contains(file.path, replace(this.file.name, "Vault", "/"))
```

# Knowledge Zone

```dataview
TABLE WITHOUT ID
    Domain,
    file.link AS Asset,
    Status,
    file.tags[0] AS Type,
    Details
FROM !#project AND !#domain AND !"Xtra"
WHERE contains(file.path, replace(this.file.name, "Vault", "/"))
```
````