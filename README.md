# ConnectorGenerator

<p align="left">
  <img src="https://raw.githubusercontent.com/JeroenBL/ConnectorGenerator/main/logo.png" width="500">
</p>

## Table of contents

- [ConnectorGenerator](#connectorgenerator)
  - [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Used libraries](#used-libraries)
  - [Using the _ConnectorGenerator_ VSCode extension](#using-the-connectorgenerator-vscode-extension)
    - [Create a new connector](#create-a-new-connector)
      - [From the command palette](#from-the-command-palette)
      - [From the context menu](#from-the-context-menu)
    - [Code snippets](#code-snippets)
      - [Using snippets](#using-snippets)
  - [Other useful VSCode extensions](#other-useful-vscode-extensions)
  - [Contributing](#contributing)
    - [Bug report](#bug-report)
    - [Feature request](#feature-request)
    - [Code changes](#code-changes)

## Introduction

Hi 👋

If you're looking to create a new target connector for HelloID provisioning and don't know where to start, you're in the right place.

This _ConnectorGenerator_ extension for VSCode is the perfect starting point for building out your new connector, with all the essential resources you'll need to get started.

## Used libraries

The following libraries are used in this extension:

| Library | Version | URL                                 |
| ------- | ------- | ----------------------------------- |
| Axios   | `1.6.5` | https://www.npmjs.com/package/axios |

## Using the _ConnectorGenerator_ VSCode extension

### Create a new connector

#### From the command palette

1. Open the command palette by clicking on `View -> Command palette` or press `ctrl+shift+p` (`cmd+shift+p` on mac).
2. Search for `Create new HelloID connector project scaffolding`.
3. Select the connector type `target`.
4. Enter a name for the connector.
5. Browse to the location where you want the files to be created and press `enter`.

#### From the context menu

1. Right click to open the context menu.
2. Click on `ConnectorGenerator -> Create new HelloID connector project scaffolding`.
3. Select the connector type `target`.
4. Enter a name for the connector.
5. Browse to the location where you want the files to be created and press `enter`

>❗The source connector templates are currently not available.

### Code snippets

The _ConnectorGenerator_ VSCode extension also adds a few useful code snippets specifically for PowerShell. Currently the following snippets are available:

| Snippet                        | Description                                                                                                                                                                                                                                                                                 |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add TLS 1.2                    | - Code snippet that adds support for TLS 1.2                                                                                                                                                                                                                                                |
| Convert body to UTF-8          | - Code snippet that converts a JSON body to UTF-8.                                                                                                                                                                                                                                          |
| Basic authentication           | - Code snippet for basic authentication.<br> - Based on `$actionContext.Configuration.UserName` and `$actionContext.Configuration.Password`.                                                                                                                                                |
| APIKey authentication          | - Code snippet for fixed APIKey authentication.<br> - Based on `$actionContext.Configuration.APIKey`.                                                                                                                                                                                       |
| OAuth2 authentication          | - Code snippet for authentication using OAuth2.<br> - Includes both a `POST` in order to retrieve the token and and example `GET` for using the token.<br> - Based on `$actionContext.Configuration.ClientId` and `$actionContext.Configuration.ClientSecret`.                              |
| Session authentication         | - Code snippet for authentication using a _cookie_ stored in a _session_ variable.<br> - Includes both a `POST` in order to retrieve the cookie and example `GET` for using the cookie.<br> - Based on `$actionContext.Configuration.UserName` and `$actionContext.Configuration.Password`. |
| Filter contracts in scope      | - Code snippet that filters `$personContext.Person.Contracts`.                                                                                                                                                                                                                              |

#### Using snippets

Snippets are accessible from any _PowerShell_ script either by:

- The snippet identifier _ConnectorGenerator_
- Using the snippet hotkey `ctrl+spacebar` (`cmd+spacebar` on mac) and browse to `ConnectorGenerator`

## Other useful VSCode extensions

There are several useful VSCode extensions that can be helpful when building PowerShell connectors. Here are a few examples:

- __PowerShell__<br>https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell<br>
The PowerShell extension provides a rich set of features for PowerShell development, including syntax highlighting, code snippets, IntelliSense, and more. This extension can be incredibly helpful when building PowerShell connectors, as it provides an efficient and intuitive environment for writing, testing, and debugging PowerShell code.

- __Code Spell Checker__<br>https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker<br>
This extension checks the spelling of words in your code and comments, ensuring that everything is spelled correctly and improving the readability and professionalism of your code.

- __GitHub Markdown Preview__<br>https://marketplace.visualstudio.com/items?itemName=bierner.github-markdown-preview<br>
With GitHub Markdown Preview, you can see exactly how your documentation will look when published to GitHub, ensuring that it is clear, concise, and easy to read. This can be particularly useful when documenting your PowerShell connector code, as it allows you to create professional-looking documentation that is easy to understand and follow.

- __ByeByeSecret__<br>https://github.com/JeroenBL/ByeByeSecret<br>
ByeByeSecret is a VSCode extension that actively scans your PowerShell code for potential secrets by identifying variables that may hold confidential information. It then notifies you with a visual alert.

## Contributing

If you have an idea or suggestion for improving the _ConnectorGenerator_ VSCode extension, one of the best ways to get involved is by opening up an issue on [GitHub repository.](https://github.com/JeroenBL/ConnectorGenerator)

### Bug report
🪲

To submit a new issue, navigate to the `Issues` tab on the repository page and click the `New Issue` button. Describe the issue in as much detail as possible, including any error messages or steps to reproduce the issue. This will help the development team to diagnose and fix the problem.

### Feature request
🚀

To request a new feature, create a new issue using the same process as for a bug report. Be sure to describe the feature you would like to see added, and explain how it would improve your experience.

### Code changes

If you would like to contribute code changes, you can do so by creating a pull request on the repository. Be sure to fork the repository and create a new branch for your changes. Once you have made your changes, create a pull request and describe the changes you have made and why they are necessary. Your changes will be reviewed by the development team, and if accepted, merged into the main branch of the repository.
