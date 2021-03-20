---
title: 可用的工具
description: 可以用來自訂開發環境的所有 devinit 工具清單。
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 482e838edf47d63235f60f013bd18eff586f83e8
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672197"
---
# <a name="available-tools"></a>可用工具

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

下表包含所有目前可用的 devinit 工具清單。

| 工具                                                                                             | 描述                                                                                                 |
|--------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [**azurecli-login**](tool-azurecli-login.md)                                                     | 用來執行 Azure CLI 命令的工具 `az login --device-code` 。                                             |
| [**choco-install**](tool-choco-install.md)                                                       | 安裝 chocolatey 套件的工具。                                                                        |
| [**choco-upgrade**](tool-choco-upgrade.md)                                                       | 升級 chocolatey 封裝的工具。                                                                        |
| [**dotnet-restore**](tool-dotnet-restore.md)                                                     | 此工具可還原 .NET 專案的相依性和工具。                                               |
| [**dotnet-toolinstall**](tool-dotnet-toolinstall.md)                                             | 例如，安裝 .NET Core 工具 (的工具。 dotnet-ef)                                                 |
| [**enable-iis**](tool-enable-iis.md)                                                             | 此工具可啟用 IIS 功能，並安裝最新的 ASP.NET 裝載套件組合。                                  |
| [**msi-install**](tool-msi-install.md)                                                           | 用來安裝 MSI 檔案的工具（提供路徑或 URL）。                                                              |
| [**npm-install**](tool-npm-install.md)                                                           | 安裝 NPM 套件的工具。                                                                               |
| [**nuget-restore**](tool-nuget-restore.md)                                                       | 用來還原 NuGet 套件的工具。                                                                         |
| [**require-azureartifactscredentialprovider**](tool-require-azureartifactscredentialprovider.md) | 安裝 Azure Artifacts 認證提供者。                                                           |
| [**require-azurecli**](tool-require-azurecli.md)                                                 | 安裝 Azure CLI 的工具。                                                                              |
| [**require-dotnetcoresdk**](tool-require-dotnetcoresdk.md)                                       | 安裝 .NET Core SDK 和共用執行時間的工具。                                                       |
| [**require-dotnetframeworksdk**](tool-require-dotnetframeworksdk.md)                             | 安裝 .NET Framework SDK 的工具。                                                                     |
| [**require-mssql**](tool-require-mssql.md)                                                       | 安裝 MS SQL Server 2019 的工具。                                                                         |
| [**require-nodejs**](tool-require-nodejs.md)                                                     | 用來安裝 Nodejs 和 NPM 的工具。                                                                             |
| [**require-nuget**](tool-require-nuget.md)                                                       | 安裝 NuGet 的工具。                                                                                      |
| [**require-npm**](tool-require-npm.md)                                                           | 用來安裝 NPM 的工具。                                                                                        |
| [**require-psmodule**](tool-require-psmodule.md)                                                 | 從資源庫安裝 PowerShell 模組的工具。                                                        |
| [**require-vcpkg**](tool-require-vcpkg.md)                                                       | 用來安裝 vcpkg 的工具。                                                                                      |
| [**require-vscomponent**](tool-require-vscomponent.md)                                           | 根據檔案修改 VS 安裝的工具 `.vsconfig` 。                                                |
| [**需要-winget**](tool-require-winget.md)                                                     | 用來安裝 winget 的工具。                                                                                     |
| [**windowsfeature-enable**](tool-windowsfeature-enable.md)                                       | 工具組啟用 Windows 功能。                                                                           |
| [**windowsfeature-disable**](tool-windowsfeature-disable.md)                                     | 工具組停用 Windows 功能。                                                                          |
| [**windowsfeature-list**](tool-windowsfeature-list.md)                                           | 列出所有 Windows 功能的啟用/停用狀態的工具。                                              |
| [**set-env**](tool-set-env.md)                                                                   | 用來查看及設定環境變數的工具。                                                                 |
| [**vcpkg-install**](tool-vcpkg-install.md)                                                       | 透過 vcpkg 安裝套件的工具。                                                                         |
| [**winget-安裝**](tool-winget-install.md)                                                     | 透過 winget 安裝套件的工具。                                                                        |
| [**wsl-install**](tool-wsl-install.md)                                                           | 適用于 Linux 的視窗子系統安裝和設定 Linux 散發版本的工具。                             |
