---
title: Per files settings
---

## Changing repository

:sparkles: It is now possible to set a repository directly in the frontmatter with the `repo` key.

> [!warning]
> - Your GitHub token must work for this repository
> - The function that uploads multiple notes won't send files to this "per-file" repository. Only the command `Upload single current active note` will work, with the [[Upload#Auto Clean-Up|autoclean]] if activated. You can disable it using the frontmatter!
> - The key works in this order: `username/repo/branch/autoclean`, `username/repo/brach`, `username/repo`, and `repo`. You can also use a YAML object like this:
>  ```yaml
>  repo:
>    owner: username
>    repo: repo
>    branch: branch
>    autoclean: true or false
>  ```
> Globally, if you share only one file, all functions will be on the per-file repository instead of the global one.
> Also, the settings will be the **same** as the global one, except for the repository settings such as image and folder.

:sparkles: You can also set multiple repositories in the frontmatter with the `multipleRepo` key. It works like the `repo` key, but you can set multiple repositories in a list format.
> [!example] Example
> ```yaml
> multipleRepo:
>  - owner: username
>    repo: repo
>    branch: branch
>    autoclean: false
>  - owner: username
>    repo: repo
>    branch: branch
>    autoclean: false
> ```
> In this behavior, the `autoclean` will be set to `false` by default.

## Frontmatter keys explanation

Some settings can be overridden based on your frontmatter key (of the file send):

1. For links conversion, using the `links` key, you can create a YAML object with:
    - `mdlinks`: to force converting to markdown links.
    - `convert` or `links`: to remove the links and keep only the string (alt text or filename).
    - `internals`: Convert internal links to their counterpart in the website (in relative path). Disabled, links will be kept as is.
    - `nonShared`: Same as above, but for links pointing to unshared files. Disabled, links will be transformed to keep the filename. Note that you can use `links: false` and `mdlinks: true` outside the YAML object if you want to just use one option.
2. Embed settings, using the `embed` key :
    - `send: false` to avoid sending the embedded files (not attachments!)
    - `remove: true` to remove any mention of these files. As before, you can use one-key settings using `embed` (for sending) and `removeEmbed` (for citation removing)
3. `Attachment` : allow per-file settings for attachments (images, pdfs, sound, video… Any attachment supported by Obsidian)
    - `send: false` to avoid sending the files
    - `folder` to change the default folder. Beware that changing this setting can have strange effects with autocleaning! You can, again, use a one-key setting using `attachmentLinks` for the folder and `attachment: false` to avoid sending.
4. `dataview` to override dataview settings.
5. `hardbreak` for markdown hard break.
6. `baselink` : to change the base link for the copy links function. Note, using this key will disable the remove part settings. You need to use the object `copylink` to edit the remove part, as follow:
  - `base`: to change the base link
  - `remove` : To remove some part specific to this file.
7. `path` : override all path settings and create a path from the root. Use `/` or let it empty to set it to the root of the repository.

To set a file as your homepages, set `title: index` in its frontmatter. Don't forget to turn on frontmatter title in [Upload configuration](Upload.md).

## Quick references

### Using yaml object

```yaml
links:
  mdlinks: boolean #convert to markdownlinks 
  convert: boolean #transform to simple string with keeping alt text or file name/ title (it removes the [[]] or []())
embed:
  send: boolean #prevent sending embed
  remove: boolean #remove embed citation completely (replace to empty string the ![[]] or ![]())
attachment: 
  send: boolean #prevent sending attachment
  folder: string #change default folder for attachment
dataview: boolean #force/prevent dataview queries conversion
hardbreak: boolean #same but for hardbreak
repo: 
  branch: string #change default branch 
  repo: string #change default repository
  owner: string #change default owner (it's your github Username)
  autoclean: boolean #disable auto cleaning
baselink: string #change base link for copylink settings
```

For multiple Repo :
```yaml
links:
  mdlinks: boolean #convert to markdownlinks 
  convert: boolean #transform to simple string with keeping alt text or file name/ title (it removes the [[]] or []())
embed:
  send: boolean #prevent sending embed
  remove: boolean #remove embed citation completely (replace to empty string the ![[]] or ![]())
attachment: 
  send: boolean #prevent sending attachment
  folder: string #change default folder for attachment
dataview: boolean #force/prevent dataview queries conversion
hardbreak: boolean #same but for hardbreak
baselink: string #change base link for copylink settings
multipleRepo: 
  - repo:
      branch: string #change default branch 
      repo: string #change default repository
      owner: string #change default owner (it's your github Username)
      autoclean: boolean #enable auto cleaning
  - repo:
      branch: string #change default branch 
      repo: string #change default repository
      owner: string #change default owner (it's your github Username)
      autoclean: boolean #enable auto cleaning
```

### Using simple name

```yaml
mdlinks: boolean #convert to markdown links
links: boolean #remove [[]] or []() and keep just alt text or filename/title
removeEmbed: boolean #remove totally the citation of an embed notes (replace to empty string the ![[]] or ![]())
attachmentLinks: string #ovverride default folder for attachments
attachment: boolean #prevent sending attachment
dataview: boolean
hardbreak: boolean
repo: string #owner/repo/branch/clean or owner/repo/branch or owner/repo or repo
autoclean: boolean #disable auto cleaning (use it only if you don't set in the repo!)
baselink: string #change base link for copylink settings
```

For multiple Repo :
```yaml
mdlinks: boolean #convert to markdown links
links: boolean #remove [[]] or []() and keep just alt text or filename/title
removeEmbed: boolean #remove totally the citation of an embed notes (replace to empty string the ![[]] or ![]())
attachmentLinks: string #ovverride default folder for attachments
attachment: boolean #prevent sending attachment
dataview: boolean
hardbreak: boolean
baselink: string #change base link for copylink settings
multipleRepo: list of string 
    - owner/repo/branch/autoclean or owner/repo or repo
    - owner/repo/branch/autoclean or owner/repo or repo
```

Default value is derivative from your settings : (`settings.keys` refer to your settings)

```yaml
links:
  mdlinks: settings.wikilinks
  convert: true
embed: 
  send: settings.embed
  remove: false
attachment:
  send: settings.attachment
  folder: settings.default_folder_image || settings.default_folder || filepath
dataview: settings.dataview
hardbreak: settings.hardbreak
repo: #same for multipleRepo
  branch: settings.branch
  repo: settings.repo
  owner: settings.owner
autoclean: settings.auto_clean
baselink: string #change base link for copylink settings
```
