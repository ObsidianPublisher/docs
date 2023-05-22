---
title: Installation
---

Mkdocs Obsidian is a combination of an Obsidian plugin and a Material mkdocs template that allows you to create a personal wiki site based on your Obsidian Vault.

If you are familiar with GitHub Pages, you can easily use the [Mkdocs Material Template](https://www.squidfunk.github.io/mkdocs-material/) by directly templating it using the [GitHub template](https://github.com/ObsidianPublisher/template-gh-pages/generate).

Alternatively, if you prefer to use Netlify, you can also template this [Netlify repository](https://github.com/ObsidianPublisher/template-netlify-vercel/generate) and use it to deploy your personal wiki site.

## Installation steps

To use the Mkdocs Obsidian plugin and create a personal wiki site based on your Obsidian vault, you can follow these steps:

1. Create a GitHub account (if you don't have one already)
2. Template the blog by using one of the following options:
	- [GH Pages version](https://github.com/ObsidianPublisher/template-gh-pages/generate)
	- [Netlify version](https://github.com/ObsidianPublisher/template-netlify-vercel/generate)

3. Clone the repository by following the instructions [here](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories)
4. In parallel, download the Obsidian plugin by using the [BRAT](https://github.com/TfTHacker/obsidian42-brat) or the community plugins panel.
5. Configure the plugin's options by setting the repository name, GitHub username, GitHub token, and branch name.
6. Add the `share: true` key in the frontmatter of the notes you want to publish.
7. Customize the folder options (if desired)
8. Run the commands through the file menu or commands palette.
9. Update the `mkdocs.yml` file with your repository information.
10. Make sure to allow push access on GitHub.
11. Run `pip install -r requirements.txt` to install necessary packages (optional, only if you are in a local environment!)
12. You can deploy your site using GitHub Pages or Netlify.

> [!INFO] [[Obsidian Github Publisher/Configuration example|See here for advanced configuration within obsidian]]

## Upgrading

To keep your template up to date, you should follow these steps:
1. Add a star to the [ObsidianPublisher/sync_template](https://github.com/ObsidianPublisher/sync_template) repository to stay informed about updates.
2. Regularly check for new releases, which will contain:
    - The upgraded files in a `zip` file named `changed_files.zip`
    - All important files (excluding `mkdocs.yml`) in a `zip` file named `release.zip`
    - A list of edited files in the CHANGELOG
3. You can also set up a [Github Actions](https://github.com/features/actions) workflow to automatically update the template files every 24 hours.

Note that, you should not edit or configure the files that are provided with the template.

The action[ `auto_update.yml` ](https://github.com/ObsidianPublisher/sync_template/blob/main/.github/workflows/auto_update.yml) will automatically download the `release.zip` file from the latest release of the template repository, which contains all the template files.

> [!warning] .env files & github secrets
> 1. You need to create  or download the .env corresponding to your workflow. This file must be in `.github` folder. 
>   The file is normally already in your template, or you can grab it [here](https://github.com/ObsidianPublisher/sync_template/tree/main/.github). Take the file corresponding to your workflow (`.env_netlify` or `.env_gh-pages`), and rename it `.env`.
>   The .env file should contains the following variables:
>   ```
>   WORKFLOW_TYPE='netlify' / 'gh-pages'
>   CLEAN=true
>   IMG_DIR='assets/img'
>   AUTO_MERGE=false
>   DRY_RUN=false
>   ``` 
> 2. You need to create a `GH_TOKEN` secret in your repository settings. This token should have the `repo` and `workflows` scope. You can create a token [here](https://github.com/settings/tokens/new?description=PUBLISHER%20TEMPLATE&scopes=repo,workflow).
> [See here to know how to register it as a secret](https://docs.github.com/en/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository).

It will then upgrade your template by replacing the old files with the new ones. After the upgrade, the action will create a pull request in your repository, which you can review and either accept or reject.

This allows you to review the changes before they are applied to your template.

> [!warning] Don't edit any files in the `assets/css/template` folder! These file will be overwritten when updated.