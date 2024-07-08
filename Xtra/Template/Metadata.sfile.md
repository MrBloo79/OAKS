Project and others metadata
__
__
```js
// Get folder as domain
function getDomain(path) {
  let parts = path.split("/");
  let fileName = parts.pop();
  let parentName = parts.pop();
  if (fileName.slice(0, -3) != parentName) {
      return parentName;
  }
  return parts.pop();
}
```
__
__
__
```js
// Get file metadata depending on type (project, contact, atomic or other)
function getMetadata(type) {
    atomicTypes = ['hint', 'post', 'tool', 'file', 'mail', 'memo', 'domain', 'list'];
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
    metadata += `Domain:: [[${domain}]]\n`;
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
    if (type == 'domain' || type == 'list') {
        metadata += `\`\`\`pack-view ${type}\n`;
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
book
```
__
```js
return getMetadata('book');
```
__
__
```
comics
```
__
```js
return getMetadata('comics');
```
__
__
```
single
```
__
```js
return getMetadata('single');
```
__
__
```
album
```
__
```js
return getMetadata('album');
```
__
__
```
artist
```
__
```js
return getMetadata('artist');
```
__
__
```
movie
```
__
```js
return getMetadata('movie');
```
__
__
```
series
```
__
```js
return getMetadata('series');
```
__
__
```
toy
```
__
```js
return getMetadata('toy');
```
__
__
```
party
```
__
```js
return getMetadata('party');
```
__
__
```
arcade
```
__
```js
return getMetadata('arcade');
```
__
__
```
list
```
__
```js
return getMetadata('list');
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