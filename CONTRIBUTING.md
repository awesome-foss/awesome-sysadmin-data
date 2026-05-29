# Contributing

Don't know where to start? Check issues labeled [`help wanted`](https://github.com/awesome-foss/awesome-sysadmin-data/issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22), [`bug`](https://github.com/awesome-foss/awesome-sysadmin-data/issues?q=is%3Aissue+is%3Aopen+label%3Abug) and [`curation`](https://github.com/awesome-foss/awesome-sysadmin-data/issues?q=is%3Aissue+is%3Aopen+label%3Acuration).

### Curation

- Software with no development activity for 6-12 months may be removed from the list
- Non-working software may be removed from the list
- Unmaintained software without an active community may be removed from the list
- Software with persistent, serious security issues will be removed from the list
- Problems should be reported automatically: [![](https://github.com/awesome-foss/awesome-sysadmin-data/actions/workflows/dead-links.yml/badge.svg)](https://github.com/awesome-foss/awesome-sysadmin-data/issues/1) [![](https://github.com/awesome-foss/awesome-sysadmin-data/actions/workflows/unmaintained-projects.yml/badge.svg)](https://github.com/awesome-foss/awesome-sysadmin-data/issues/1)

### Add software to the list

- [Create a new `software/software-name.yml` file](https://github.com/awesome-foss/awesome-sysadmin-data/new/master/software), based on the template in [.github/ISSUE_TEMPLATES/addition.md](.github/ISSUE_TEMPLATE/addition.md). Please use [kebab-case](https://en.wikipedia.org/wiki/Letter_case#Kebab_case) for file naming, for example, `my-awesome-software.yml`.
- Remove comments and unused optional fields
- Enter a descriptive commit message (such as `add My Awesome software`)
- Select `Create a new branch for this commit and start a pull request`
- Click `Propose new file`
- Click `Create pull request`

If you are not comfortable sending a pull request, please open a new [issue](https://github.com/awesome-foss/awesome-sysadmin-data/issues).

In [single page mode](https://github.com/awesome-foss/awesome-sysadmin) the software will only appear under the first category in its `tags` list, so choose wisely.

### Add a tag/category

Tags represent functional categories/features of the software and must be added to `tags/tag-name.yml` (use [existing tags](tags/) as an example). Any tag must have a minimum of 3 software projects referencing it. The [`Miscellaneous`](tags/miscellaneous.yml) tag can be used for software not matching any existing category.

```yaml
# project name
name: Log Management
# description of what this tag/category is about (markdown allowed)
description: 'Log Management tools: collect, parse, visualize...'
# (optional) list of related tags, by name
related_tags:
  - Metrics & Metric Collection
# (optional) external links
external_links:
  - title: awesome-selfhosted/Network Utilities
    url: https://github.com/awesome-selfhosted/awesome-selfhosted#network-utilities
# (optional) if this is set, no software items will be allowed to reference this tag, and the page will display a block asking to visit these links instead
redirect:
  - title: awesome-selfhosted/Software Development - Testing
    url: https://github.com/awesome-selfhosted/awesome-selfhosted#software-development---testing
```

### Add a license

[Free and Open-Source](https://en.wikipedia.org/wiki/Free_and_open-source_software) software licenses (preferably [SPDX identifier](https://spdx.org/licenses/), or custom licenses, must be added to `licenses.yml` (use [existing licenses](licenses.yml) as an example):

```yaml
  # short license identifier
- identifier: ZPL-1.2
  # full license name
  name: Zope Public License 1.2
  # link to the full license text
  url: http://zpl.pub/page/zplv12
```

### Add a language/platform

Languages/requirements/technologies used to run or build the software should be listed in `platforms/platform-name.yml` (use [existing platforms](platforms/) as an example):

```yaml
# language/platform name
name: Java
# general description of the programming language or deployment platform (markdown allowed)
description: "[Java](https://en.wikipedia.org/wiki/Java_(programming_language)) is a high-level, class-based, object-oriented programming language that is designed to have as few implementation dependencies as possible."
```

### Remove software from the list

Simply delete the appropriate file under `software/` and submit a Pull Request.
To do this from Github's web interface:
- use the [go to file](https://github.com/awesome-foss/awesome-sysadmin-data?search=1) feature to open the appropriate file (e.g. [`software/apache-ant.yml`](https://github.com/awesome-foss/awesome-sysadmin-data/blob/master/software/apache-ant.yml))
- Click the `...` button at the top right of the file view, and click `Delete file`
- In the `Commit changes` dialog, enter `Remove SOFTWARE_NAME (reason)` as your commit message, additional context in the `extended description` field, select `Create a new branch for this commit and start a pull request.`, and click `Commit Changes`

### Other guidelines

In addition to guidelines listed in the [Pull Request template](.github/PULL_REQUEST_TEMPLATE.md), these general rules help keep the list consistent:

- Pull Requests not respecting the PR template will be rejected and the submitter banned without explanations.
- The project you are adding should be intended for professional setup, not personal use.
- Please avoid redundant terms in project descriptions, such as _open-source_, _free_, _self-hosted_... as their presence on awesome-sysadmin already implies this.
- Prefer shorter forms for descriptions - for example, `Network backup and restore program` would be preferred to `A network backup and restore program` or `$PROJECT is a network backup and restore program`).
- If the the project has no documentation in English, please add `(documentation in $LANGUAGE)` at the end of the description.
- If the project is presented as an alternative to another service or application, please mention it as `(alternative to $PRODUCT1, $PRODUCT2)` at the end of the description.
- If the project is forked from another project, please add `(fork of $PROJECT)` at the end of the description.
- If you are adding software forked from another active project, please provide/link to a clear list of differences between both.
- If the project distributes a single static binary, please add the programming language in which it is written.

### What does not qualify

- Software that depends on a specific cloud provider
- Software that is a desktop, mobile, or command-line application, which relies on a separate file synchronisation/server program
- Software that requires you to write application code before producing a working end-user application (libraries, SDKs, ...)
- Software contributions that merely port an existing application to another system (e.g., Dockerization)

### Other operations

**Rename a tag/category:** the tag must be renamed in the appropriate `tags/mytag.yml` file. All references to it must be updated in `tags/*.yml` and `software/*.yml`.

**Automated tasks:**

```bash
$ make help
install             install build tools in a virtualenv
import              import data from the original list at https://github.com/awesome-foss/awesome-sysadmin
update_metadata     update metadata from project repositories/API
awesome_lint        check data against awesome-sysadmin guidelines
export_markdown     render markdown export from YAML data (https://github.com/awesome-foss/awesome-sysadmin)
export_html         render HTML export from YAML data (https://sysadmin.awesome-selfhosted.net/)
push_markdown       commit and push changes to the markdown repository
push_html           commit and push changes to the HTML site repository (amend previous commit and force-push)
url_check           check URLs for dead links or other connection problems
authors             update the AUTHORS file
clean               clean files generated by automated tasks
help                generate a list of targets with descriptions
```
