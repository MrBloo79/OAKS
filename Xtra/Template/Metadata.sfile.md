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
// Get file metadata depending on type
function getMetadata(base, derived="", extra="") {
    metadata = '';
    if (base == 'project') {
        metadata += '# Metadata\n\n';
    }
    let tags = [derived, base, extra].filter(t => t !== "").join(', #');
    metadata += `Type: #${tags}\n`;
    let date = new Date().toISOString().slice(0, 10);
    metadata += `Created:: ${date}\n`;
    if (base == 'project') {
        metadata += 'Due:: \n';
    }
    metadata += 'Status:: [[Identified]]\n';
    if (base == 'item' || base == 'project') {
        metadata += 'Rank:: \n';
        metadata += 'Recipient:: \n';
    }
    if (base == 'project') {
        metadata += 'Requester:: \n';
        metadata += 'Assignee:: \n';
    }
    let domain = getDomain(app.workspace.getActiveFile().path);
    metadata += `Domain:: ${domain}\n`;
    metadata += 'Details:: \n';
    if (base == 'contact' || base == 'item' || base == 'project') {
        metadata += 'Motive:: \n';
    }
    if (derived == 'contact') {
        metadata += 'Mail: \n';
        metadata += 'Phone: \n';
        metadata += 'Activity:: \n';
        metadata += 'Environment:: \n';
    }
     if (base == 'project') {
        metadata += '\n# Content\n\n';
        metadata += '# Journal\n\n';
    }
   
    return metadata;
}
```
__
__
```
contact
```
__
```js
return getMetadata('asset', 'contact')
```
__
contact
__
```
project
```
__
```js
return getMetadata('project')
```
__
project