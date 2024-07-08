````pack-source domain
# Alignment Zone

```dataview
TABLE WITHOUT ID
    file.link AS Project,
    link(Status, Status.aliases) AS S,
    Value AS V,
    Due,
    Domain,
    More
FROM #project
WHERE contains(file.path, this.file.name)
```

# Action Zone

```dataview
TABLE WITHOUT ID
    regexreplace(task.text, "((➕|📅|⏳|✅)|(\(|\[)(⭐|💬|👤|🔗)).*", "") AS Action,
    [[Icon]].get[task.status] AS S,
    task.⭐ AS V,
    task.due AS Due,
    link(choice(task.blockId,file.name + "#^" +task.blockId,file.name),file.name) AS Project,
    task.🔗 AS More
FROM #project
FLATTEN file.tasks AS task
WHERE contains(file.path, this.file.name)
```

# Knowledge Zone

```dataview
TABLE WITHOUT ID
    file.link AS Asset,
    link(Status, Status.aliases) AS S,
    file.tags[0] AS Type,
    Domain,
    More
FROM !#project
WHERE contains(file.path, this.file.name) AND file.path != this.file.path
```
````