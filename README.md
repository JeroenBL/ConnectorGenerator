# ConnectorGenerator

![Total downloads (specific asset, latest release)](https://img.shields.io/github/downloads/JeroenBL/ConnectorGenerator/latest/connectorgenerator-2.4.0.vsix?label=Total%20downloads)
![GitHub Tag](https://img.shields.io/github/v/tag/jeroenbl/connectorgenerator?label=Latest%20release&color=0a6cd8)

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
    - [Create a new connector](#create-a-new-connector)
      - [From the command palette](#from-the-command-palette)
      - [From the context menu](#from-the-context-menu)
    - [Caching](#caching)
    - [Code snippets](#code-snippets)
      - [Using snippets](#using-snippets)
      - [Updating the cache](#updating-the-cache)
    - [Detecting variables holding sensitive information](#detecting-variables-holding-sensitive-information)
    - [Highlighting HelloID specific variables](#highlighting-helloid-specific-variables)
    - [Advanded error diagnostics](#advanded-error-diagnostics)
    - [Adding connector templates files](#adding-connector-templates-files)
    - [Change the FieldMapping systemGUID to the systemName](#change-the-fieldmapping-systemguid-to-the-systemname)
    - [Development features](#development-features)
  - [Contributing](#contributing)
    - [Bug report](#bug-report)
    - [Feature request](#feature-request)

## Introduction

Hi 👋

If you're looking to create a new target connector for HelloID provisioning and don't know where to start, you're in the right place.

This _ConnectorGenerator_ extension for VSCode is the perfect starting point for building out your new connector, with all the essential resources you'll need to get started.

If you're a new to the templates and the _ConnectorGenerator_ refer to the [QuickStart](https://jeroenbl.github.io/helloid/templates-quickStart/) to help you get started.

## Features

| Feature                                      | Remarks |
|----------------------------------------------|---------|
| [Create a new target connector for HelloID provisioning.](#create-a-new-connector) | Enables users to generate a HelloID connector with predefined scaffolding. |
| [PowerShell code snippets.](#code-snippets) | Provides reusable PowerShell code snippets to streamline development. |
| [Detect variables holding sensitive information.](#detecting-variables-holding-sensitive-information) | Scans PowerShell scripts for potential secrets and warns the user. __This feature is enabled by default__. |
| [Code highligting for HelloID specific variables.](#highlighting-helloid-specific-variables) | highlighting for HelloID variables like `$actionContext` and `$outputContext` in .ps1 files. __This feature is enabled by default__. |
| [Advanced error diagnostics.](#advanded-error-diagnostics) | Error diagnostics for unassigned `Invoke-RestMethod` and `Invoke-WebRequest` calls in PowerShell scripts. |
| [Adding connector templates files.](#adding-connector-templates-files) | Add connector templates files using the context menu allowing you to easy extend an already existing connector. |
| [Change the FieldMapping systemGUID to the systemName.](#change-the-fieldmapping-systemguid-to-the-systemname) | Allows you to easy change the systemGUID to the systemName. |
| [Development features](#development-features) | Enables development features. Useful when making changes to the templates. __This feature is disabled by default__. |

## Used libraries

The following libraries are used in this extension:

| Library | Version | URL                                 |
| ------- | ------- | ----------------------------------- |
| Axios   | `1.7.7` | https://www.npmjs.com/package/axios |

## Using the _ConnectorGenerator_ VSCode extension

### Create a new connector

#### From the command palette

1. Open the command palette by clicking on `View -> Command palette` or press `ctrl+shift+p` (`cmd+shift+p` on mac).
2. Search for `Create new HelloID connector project scaffolding`.
3. Select the connector type `target`.
4. Enter a name for the connector.
5. Browse to the location where you want the files to be created and press `enter`.

#### From the context menu

> Only available when a new file (can be of any type) is opened.

1. Right click to open the context menu.
2. Click on `ConnectorGenerator -> Create new HelloID connector project scaffolding`.
3. Select the connector type `target`.
4. Enter a name for the connector.
5. Browse to the location where you want the files to be created and press `enter`.

> The source connector templates are currently not available.

### Caching

When creating a new connector based of the template, the latest release will be downloaded from: https://github.com/Tools4everBV/HelloID-Conn-Prov-Target-V2-Template/releases. The zip file will be unpacked and saved to in user folder using the latest release version as the folderName.

  - __Windows__: `C:\Users\<username>\<vscode-version>\extensions\connectorteam.connectorgenerator-<version>/cache`
  - __macOS__: `~/.vscode/extensions/connectorteam.connectorgenerator-<version>/cache`
  - __Linux__: `~/.vscode/extensions/connectorteam.connectorgenerator-<version>/cache`

The latest will only be donwloaded in case the locally cached version is __older__ then the latest version available on GitHub.

### Code snippets

From version `1.2.0` Code snippets can be retrieved directly from the context menu: `ConnectorGenerator -> Retrieve code snippets` or from the command palette. Code snippets are retrieved from our [_helper_ repository on _GitHub_](https://github.com/Tools4everBV/HelloID-Lib-Prov-HelperFunctions/tree/main/PowerShell/Scripts) and cached locally in your user directory.

  - __Windows__: `C:\Users\<username>\<vscode-version>\extensions\connectorteam.connectorgenerator-<version>/cache/snippets.json`
  - __macOS__: `~/.vscode/extensions/connectorteam.connectorgenerator-<version>/cache/snippets.json`
  - __Linux__: `~/.vscode/extensions/connectorteam.connectorgenerator-<version>/cache/snippets.json`

#### Using snippets

In order to use a code snippet:

1. Select a snippet from the list and click the arrow button to expand.
2. Click `Copy` to copy the snippet to the clipboard.

#### Updating the cache

The snippets cache can __only be updated manually__ by clicking: `Refresh snippet cache` from the status bar.

### Detecting variables holding sensitive information

To prevent uploading secrets _ConnectorGenerator_ actively scans for variables that might contain sensitive information. Potentially unsafe variables will marked _red_ to make them stand out.

To disable this feature:

1. Open the VSCode settings windows by clicking on: `ctrl + ,` or (`cmd + ,` on macOs).
2. Type: `connectorgenerator` to go to the section for this extension.
3. Make sure to toggle: `Enable Secret Scanning`.

### Highlighting HelloID specific variables

HelloID specific variables like `$actionContext` and `$outputContext` can be highlighted. Hovering above the variable will display an information window and containing the link to documentation.

To enable this feature:

1. Open the VSCode settings windows by clicking on: `ctrl + ,` or (`cmd + ,` on macOs).
2. Type: `connectorgenerator` to go to the section for this extension.
3. Make sure to toggle: `Enable HelloID variable highlight`.

### Advanded error diagnostics

With PowerShell, most __cmdlets__ write their output to the output stream. However, in HelloID this is not supported as all output should be written to the `$outputContext`. Therefore, __cmdlets__ like `Invoke-RestMethod` should always be assigned to a variable or outputted to `$null`. The _ConnectorGenerator_ checks __cmdlets__ for potential unwanted output in the output stream.

> Currently, this feature cannot be disabled.

### Adding connector templates files

From version `2.3.0` its possible to add connector templates files using the context menu allowing you to easy extend an already existing connector.

To add a template file:

1. In the __explorer__ window, click right to open the context menu.
2. Select `add connector template file`.
3. Select the template you wish to add.

> Missing folders will automatically be created!

![addTemplate](https://raw.githubusercontent.com/JeroenBL/ConnectorGenerator/refs/heads/main/assets/addTemplateFile.gif)

### Change the FieldMapping systemGUID to the systemName

If you're fieldmapping uses account data from other systems, when exported, the JSON contains a _GUID_ instead of the system name. This will manually need to be resolved. To make this easier, the extension provides the option to change the _GUID_ to the system name.

1. In the __explorer__ window, select the `fieldMapping.json`.
2. Right to open the context menu.
3. Select `replace field mapping system name`.

![fieldMapping](https://raw.githubusercontent.com/JeroenBL/ConnectorGenerator/refs/heads/main/assets/fieldMapping.gif)

> Currently, only the `MicrosoftActiveDirectory` system name is supported.

### Development features

If you wish to extend or modify the template, you can do so by creating a new folder in the cache folder. Make sure the name of the new folder adheres to [semver](https://semver.org/).

To create a connector based of your updated version:

1. Open the VSCode settings windows by clicking on: `ctrl + ,` or (`cmd + ,` on macOs).
3. Type: `connectorgenerator` to go to the section for this extension.
2. Make sure to toggle: `Enable Version Selection For Development Purposes`.

This will enable two features:

- Quikly open the cache folder from the status bar by clicking on: `Open cache folder`.
- Option to select a template version when you create a new connector.

> Note that, with this feature `enabled` __new templates__ will __not__ be __downloaded__ from the GitHub repository. Instead, the __local cache__ is __always__ used as the __primary source__.

## Contributing

If you have an idea or suggestion for improving the _ConnectorGenerator_ VSCode extension, one of the best ways to get involved is by opening up an issue on [GitHub repository.](https://github.com/JeroenBL/ConnectorGenerator)

### Bug report
🪲

To submit a new issue, navigate to the `Issues` tab on the repository page and click the `New Issue` button. Describe the issue in as much detail as possible, including any error messages or steps to reproduce the issue. This will help the development team to diagnose and fix the problem.

### Feature request
🚀

To request a new feature, create a new issue using the same process as for a bug report. Be sure to describe the feature you would like to see added, and explain how it would improve your experience.
