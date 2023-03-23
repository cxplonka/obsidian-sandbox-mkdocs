# Best Practices

This is an overview over the best practices when creatin content with obsidian and deploy/convert the stuff to MkDocs Material.

## Obsidian settings

To get the best experience when working with Obsidian and MkDocs Material the following `app.json`  settings should be enabled, stored in the `docs\.obsidian` folder:

```json
{
  "attachmentFolderPath": "assets/images",
  "newLinkFormat": "relative",
  "alwaysUpdateLinks": true,
  "showLineNumber": true,
  "useMarkdownLinks": false,
  "showUnsupportedFiles": true
}
```

- `attachmentFolderPath: assets\images` when you drop content like images these will the be stored in `assets\images` move differnet content to `svg` order `data` folders
- `newLinkFormat: relative` droped content is referenced relative to the docs folder
- `alwaysUpdateLinks: true` handled renaming of files and headers and updates references
- `useMarkdownLinks: true` the plugins can better handle anchor links to headers
- `showUnsupportedFiles: true` then you can drop all files into obsidian

## Create a notice

When create a notice the filename should short and compact, because this is managed by the file sytem.

Use the main header which will be visible in the MkDocs Material sidebar for navigation like:

```md
# My main header
```

## Links

### Reference to an header anchor

When converting markdown to html with MkDocs the plugins will generate header anchor like `#obsidian-settings`, Obsidian will generate `#Obsidian settings`, so the plugins of MkDocs will handle this when you use wikilinks syntax:

```md
[[#Obsidian settings]]
```

this link will be converted to `#obsidian-settings`.

Ex. my anchor to [[#Obsidian settings]].