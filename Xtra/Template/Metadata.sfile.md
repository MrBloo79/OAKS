Project and others metadata
__
__
```js
// Get folder as domain
function getDomain(path) {
  let parts = path.split("/");
  for (let i = parts.length - 2; i >= 0; i--) {
    if (parts[i] !== "Asset" && parts[i] !== "Project") {
      return `[[${parts[i]}]]`;
    }
  }
  return "[[Vault]]";
}
```
__
__
__
```js
// Get file metadata depending on type (project, contact, atomic or other)
function getMetadata(type) {
    atomicTypes = ['hint', 'post', 'tool', 'file', 'mail', 'memo', 'domain'];
    metadata = '---\n';
    metadata += `tags: ${type}\n`;
    metadata += '---\n\n';
    let date = new Date().toISOString().slice(0, 10);
    metadata += `Created:: ${date}\n`;
    if (type == 'project') {
        metadata += 'Due:: \n';
    }
    metadata += 'Status:: [[Identified]]\n';
    if (!atomicTypes.includes(type) && type != 'contact') {
        metadata += 'Value:: \n';
        metadata += 'Recipient:: \n';
    }
    if (type == 'project') {
        metadata += 'Requester:: \n';
        metadata += 'Assignee:: \n';
    }
    let domain = getDomain(app.workspace.getActiveFile().path);
    metadata += `Domain:: ${domain}\n`;
    metadata += 'More:: \n';
    if (!atomicTypes.includes(type)) {
        metadata += 'Motive:: \n';
    }
    if (type == 'contact') {
        metadata += 'Mail: \n';
        metadata += 'Phone: \n';
        metadata += 'Activity:: \n';
        metadata += 'Environment:: \n';
    }
    if (type == 'domain') {
        metadata += '```pack-view domain\n';
        metadata += '```\n';
    }
    return metadata;
}
```
__
__
```
hint
```
__
```js
return getMetadata('hint');
```
__
__
```
post
```
__
```js
return getMetadata('post');
```
__
__
```
tool
```
__
```js
return getMetadata('tool');
```
__
__
```
file
```
__
```js
return getMetadata('file');
```
__
__
```
memo
```
__
```js
return getMetadata('memo');
```
__
__
```
mail
```
__
```js
return getMetadata('mail');
```
__
__
```
contact
```
__
```js
return getMetadata('contact');
```
__
__
```
domain
```
__
```js
return getMetadata('domain');
```
__
__
```
project
```
__
```js
return getMetadata('project');
```
__