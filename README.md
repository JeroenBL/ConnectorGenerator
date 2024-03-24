![Total downloads (specific asset, latest release)](https://img.shields.io/github/downloads/JeroenBL/ConnectorGenerator/latest/connectorgenerator-0.9.0.vsix)
![Latest version](https://img.shields.io/github/v/tag/jeroenbl/ConnectorGenerator)

# ConnectorGenerator

<p align="left">
  <img src="https://raw.githubusercontent.com/JeroenBL/ConnectorGenerator/main/logo.png" width="300">
</p>

## Table of contents

- [ConnectorGenerator](#connectorgenerator)
  - [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Features](#features)
  - [Used libraries](#used-libraries)
  - [Using the _ConnectorGenerator_ VSCode extension](#using-the-connectorgenerator-vscode-extension)
    - [Create a new _GitHub_ token](#create-a-new-github-token)
    - [Set the token](#set-the-token)
    - [Create a new connector](#create-a-new-connector)
      - [From the command palette](#from-the-command-palette)
      - [From the context menu](#from-the-context-menu)
    - [Code snippets](#code-snippets)
      - [Using snippets](#using-snippets)
    - [Tools4ever color themes](#tools4ever-color-themes)
      - [Set a theme](#set-a-theme)
    - [Detecting variables holding sensitive information](#detecting-variables-holding-sensitive-information)
  - [Contributing](#contributing)
    - [Bug report](#bug-report)
    - [Feature request](#feature-request)
    - [Code changes](#code-changes)

## Introduction

Hi 👋

If you're looking to create a new target connector for HelloID provisioning and don't know where to start, you're in the right place.

This _ConnectorGenerator_ extension for VSCode is the perfect starting point for building out your new connector, with all the essential resources you'll need to get started.

## Features

- [Create a new target connector for HelloID provisioning.](#create-a-new-connector)
- [PowerShell code snippets.](#code-snippets)
- [Tools4ever color themes.](#tools4ever-color-themes)
- [Possibility to detect variables holding sensitive information.](#detecting-variables-holding-sensitive-information)

## Used libraries

The following libraries are used in this extension:

| Library | Version | URL                                 |
| ------- | ------- | ----------------------------------- |
| Axios   | `1.6.5` | https://www.npmjs.com/package/axios |

## Using the _ConnectorGenerator_ VSCode extension

### Create a new _GitHub_ token

1. Browse to [`Developer settings`.](https://github.com/settings/tokens)
2. Click on `Generate new token`.
3. Select `Generate new token (classic)`.
4. Give your token a clear `Note`.
5. Set the expiration to `60` days.
6. __Only__ check the `repo (Full control of private repositories)` scope.
7. Click `Generate token`.
8. Make sure to __securely__ save your token.

### Set the token

1. Open the command palette by clicking on `View -> Command palette` or press `ctrl+shift+p` (`cmd+shift+p` on mac).
2. Browse to `Set ConnectorGenerator GitHub accessToken`.
3. Specify your _GitHub_ token and press `enter`.

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
| Filter contracts in scope      | - Code snippet that filters `$personContext.Person.Contracts`.
| Ignore SSL certificate check   | - Code snippet for ignoring the SSL certificate check. |
| Create immutable object        | - Code snippet for creating an immutable object using a closure. |
| Cloud usage for a *.pfx certificate | - Code snippet on how to use a *.pfx certificate within cloud PowerShell. |                                                                                                                                                                                                                      |
#### Using snippets

Snippets are accessible from any _PowerShell_ script either by:

- The snippet identifier _ConnectorGenerator_
- Using the snippet hotkey `ctrl+spacebar` and browse to `ConnectorGenerator`

### Tools4ever color themes

The extension comes with two _Tools4ever_ color themes.
  - Tools4ever-Dark
  - Tools4ever-Light

#### Set a theme

1. Color Theme picker by clicking on `File > Preferences > Theme > Color Theme` or press `ctrl+k & ctrl+t`. (`cmd+k cmd+t` on mac).
2. Select the theme you want and press `Enter`.

### Detecting variables holding sensitive information

A new feature in release `0.9.0` is the option to detect variables holding sensitive information. The potentially _unsafe_ variable clearly stands out from other variables.

![detect](https://raw.githubusercontent.com/JeroenBL/ConnectorGenerator/main/detect.png)

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

