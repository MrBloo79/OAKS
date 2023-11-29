Project and assets metadata
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
// Get file type depending on type
function getMetadata(base, derived="", extra="") {
    type = '';
    if (base == 'project') {
        type += '# type\n\n';
    }
    let tags = [derived, base, extra].filter(t => t !== "").join(', #');
    type += `Type: #${tags}\n`;
    let date = new Date().toISOString().slice(0, 10);
    type += `Created:: ${date}\n`;
    if (base == 'project') {
        type += 'Due:: \n';
    }
    type += 'Status:: [[Identified]]\n';
    if (base == 'item' || base == 'project') {
        type += 'Rank:: \n';
        type += 'Recipient:: \n';
    }
    if (base == 'project') {
        type += 'Requester:: \n';
        type += 'Assignee:: \n';
    }
    let domain = getDomain(app.workspace.getActiveFile().path);
    type += `Domain:: ${domain}\n`;
    type += 'Details:: \n';
    if (derived == 'contact' || base == 'item' || base == 'project') {
        type += 'Motive:: \n';
    }
    if (derived == 'contact') {
        type += 'Mail: \n';
        type += 'Phone: \n';
        type += 'Activity:: \n';
        type += 'Environment:: \n';
    }
     if (base == 'project') {
        type += '\n# Content\n\n';
        type += '# Journal\n\n';
    }
   
    return type;
}
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
__
```
contact
```
__
```js
return getMetadata('asset', 'contact');
```
__
__
```
doc
```
__
```js
return getMetadata('asset', 'doc');
```
__
__
```
mail
```
__
```js
return getMetadata('asset', 'mail');
```
__
__
```
memo
```
__
```js
return getMetadata('asset', 'memo');
```
__
__
```
article
```
__
```js
return getMetadata('asset', 'article');
```
__
__
```
hint
```
__
```js
return getMetadata('asset', 'hint');
```
__