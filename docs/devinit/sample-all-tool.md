---
title: 所有工具
description: 使用所有 devinit 工具的範例。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e81fa07581d457a9046c7ed51e76582bd429eda0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943628"
---
# <a name="all-tools"></a>所有工具

這個範例有 `devinit.json` ，它會安裝所有可用的 devinit 工具。

## <a name="devinitjson"></a>.devinit.json

```json
{
  "$schema": "./devinit.schema-3.0.json",
  "comments": "A sample dot-devinit file",
  "run": [
    {
      "tool": "azurecli-login",
      "comments": "Logs in to Azure Cli."
    },
    {
      "tool": "choco-install",
      "input": "kubernetes-cli",
      "additionalOptions": "--version 1.18.1",
      "comments": "Additional options are appended to the 'choco install' command line. In this case, we pass in the specific package version to install."
    },
    {
      "tool": "choco-upgrade",
      "input": "kubernetes-cli",
      "additionalOptions": "--version 1.18.2",
      "comments": "Additional options are appended to the 'choco upgrade' command line. In this case, we pass in the specific package version to install."
    },
    {
      "tool": "dotnet-restore",
      "input": "C:\\app1\\app1.csproj",
      "comments": "Restores the dependencies and tools of a project using .NET Core. Input can be used to provide .sln path or project file path."
    },
    {
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global",
      "comments": "Installs a .NET Core tool."
    },
    {
      "tool": "enable-iis",
      "comments": "Enables IIS features and installs the latest ASP.NET hosting bundle."
    },
    {
      "tool": "msi-install",
      "input": "https://www.7-zip.org/a/7z1900.msi",
      "comments": "Installs the 7-Zip MSI",
    },
    {
      "tool": "npm-install",
      "input": "some-package",
      "additionalOptions": "--some-additional-options",
      "comments": "Installs an NPM package"
    },
    {
      "tool": "nuget-restore",
      "comments": "Restores nuget packages to current directory 'Packages' folder. Input is optional and used for packages.config path.",
      "input": "C:\\packages.config"
    },
    {
      "tool": "require-azureartifactscredentialprovider",
      "comments": "Installs Azure Artifacts Credential Provider."
    },
    {
      "tool": "require-azurecli",
      "comments": "Always installs latest of Azure CLI for Windows."
    },
    {
      "tool": "require-choco",
      "input": "0.10.15"
    },
    {
      "tool": "require-dotnetcoresdk",
      "comments": "If input is null, the sdk version is from global.json if it exists; otherwise, current LTS version."
    },
    {
      "tool": "require-dotnetcoresdk",
      "input": "3.1.200",
      "comments": "Input specifies an explicit SDK version."
    },
    {
      "tool": "require-dotnetframeworksdk",
      "input": "4.8.0",
      "comments": "Input specifies an explicit SDK version."
    },
    {
      "tool": "require-mssql",
      "input": "install",
      "comments": "Installs MS SQL."
    },
    {
      "tool": "require-nodejs",
      "input": "12.16.3",
      "comments": "Installs Node.js."
    },
    {
      "tool": "require-npm",
      "input": "6.14.4",
      "comments": "Installs NPM."
    },
    {
      "tool": "require-nuget",
      "input": "5.5.1",
      "comments": "Installs NuGet for given input version. If no input given, then installs latest."
    },
    {
      "tool": "require-psmodule",
      "input": "PowerShellGet",
      "additionalOptions": "-Repository PSGallery",
      "comments": "Installs specified PS module mentioned in input from PSGallery, unless repository mentioned in additional options."
    },
    {
      "tool": "require-vcpkg",
      "comments": "Installs vcpkg."
    },
    {
      "tool": "require-vscomponent",
      "input": "C:\\.vsconfig",
      "comments": "Imports .vsconfig file which is passed as input to Visual Studio."
    },
    {
      "tool": "set-env",
      "input": "Foo=Bar",
      "comments": "Set-env can set, display or delete individual variables and can display all variables."
    },
    {
      "tool": "vcpkg-install",
      "input": "some-package",
      "additionalOptions": "--some-additional-options",
      "comments": "Installs a package using vcpkg."
    },
    {
      "comments": "Enables the .NET Framework 3.5 feature.",
      "tool": "windowsfeature-enable",
      "input": "Microsoft-Windows-NetFx3-OC-Package"
    },
    {
      "comments": "Disables the IIS Asp.Net 4.5 feature.",
      "tool": "windowsfeature-disable",
      "input": "IIS-ASPNET45"
    },
    {
      "comments": "Lists the state of all Windows features.",
      "tool": "windowsfeature-list"
    },
    {
      "tool": "wsl-install",
      "input": "https://aka.ms/wslubuntu2004",
      "additionalOptions": "--wsl-version 1 --post-create-command some-post-create-command",
      "comments": "Installs distro from target URL using Windows Subsystem for Linux."
    }
  ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js開啟

存放庫根目錄中檔案 _.devcontainer.js_ 的內容。

```json
{
  "postCreateCommand": "devinit init"
}
```
