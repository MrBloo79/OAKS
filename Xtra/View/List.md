````pack-source list
```dataview
TABLE WITHOUT ID
    file.link AS Name,
    link(Status, Status.aliases) AS S,
    Value as V,
    Recipient,
    Motive,
    More
FROM !#project
WHERE contains(file.path, this.file.name)
```
````