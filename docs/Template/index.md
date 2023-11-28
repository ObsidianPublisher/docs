---
title: Installation
---

Mkdocs Obsidian is a combination of an Obsidian plugin and a Material mkdocs template that allows you to create a personal wiki site based on your Obsidian Vault.

If you are familiar with GitHub Pages, you can easily use the [Mkdocs Material Template](https://squidfunk.github.io/mkdocs-material/) by directly templating it using the [GitHub template](https://github.com/ObsidianPublisher/template-gh-pages/generate).

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

> [!INFO] [[Plugin/Configuration example|See here for advanced configuration within obsidian]]

## Upgrading

To keep your template up to date, you should follow these steps:
1. Add a star to the [ObsidianPublisher/sync_template](https://github.com/ObsidianPublisher/sync_template) repository to stay informed about updates.
2. Regularly check for new releases, which will contain:
    - The upgraded files in a `zip` file named `changed_files.zip`
    - All important files (excluding `mkdocs.yml`) in a `zip` file named `release.zip`
    - A list of edited files in the CHANGELOG
3. You can also set up a [Github Actions](https://github.com/features/actions) workflow to automatically update the template files every 24 hours.

Note that, you should not edit or configure the files that are provided with the template.

See [[Workflow#Update|here]] for more information about the update workflow.
