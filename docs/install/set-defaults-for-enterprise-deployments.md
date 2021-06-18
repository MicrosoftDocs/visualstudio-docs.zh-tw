---
title: 設定企業部署的預設
description: 深入了解 Visual Studio 企業部署的網域原則和其他組態作業。
ms.date: 04/13/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cc88e6ffe91b111626fa76057742233527bf203f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306900"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>設定 Visual Studio 企業部署的預設值

您可以設定會影響 Visual Studio 部署的登錄原則。 這些原則對電腦而言是全域的，而且會影響：

- 與其他版本或執行個體共用之某些套件安裝的位置
- 封裝的位置和是否快取
- 應如何套用系統管理員更新

您可以使用[命令列選項](use-command-line-parameters-to-install-visual-studio.md)設定這些原則中的某些原則、在您的電腦上設定登錄值，或者甚至使用群組原則在整個組織發佈它們。

## <a name="registry-keys"></a>登錄機碼

您可以在數個位置設定企業預設值，以透過群組原則或直接在登錄中啟用控制項。 Visual Studio 會循序查看是否有任何已設定的企業原則，只要一發現下列順序的原則值，則會忽略剩餘的機碼。

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (64 位元作業系統)

如果尚未設定，某些登錄值會在第一次使用時自動設定。 這種做法可確保後續安裝會使用相同的值。 這些值會儲存在第二個登錄機碼 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` 中。

您可以設定下列登錄值：

::: moniker range="vs-2017"

| **名稱**                      | **型別**                    | **預設值**                                         | **說明**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                   | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | 儲存套件資訊清單和套件承載 (後者為選擇性) 的目錄。 如需詳細資訊，請參閱 [停用或移動套件](disable-or-move-the-package-cache.md) 快取頁面。                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`      | `REG_DWORD`                 | 1                                                   | 保留套件承載，即使已安裝它們。 您可以隨時變更該值。 停用原則將移除您所修復或修改之執行個體的任何已快取套件承載。 如需詳細資訊，請參閱 [停用或移動套件](disable-or-move-the-package-cache.md) 快取頁面。                                                                                                                                                                             |
| `SharedInstallationPath`      | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared  | 在各個 Visual Studio 執行個體版本上共用之某些套件的安裝目錄。 您可以隨時變更此值，但它只會影響未來的安裝。 任何已安裝在舊位置的產品都不得移動，否則可能無法正常運作。                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`  | `REG_DWORD`                 | 0                                                   | 防止安裝程式為所有已安裝的 Visual Studio 產品自動下載更新。 您可以隨時變更該值。                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled` | `REG_DWORD`                 | 0                                                   | 允許將系統管理員更新套用至用戶端電腦。 如果此值遺失或設為0，系統管理員更新將會遭到封鎖。 此值適用于系統管理用途。 如需詳細資訊，請參閱 [啟用系統管理員更新](enabling-administrator-updates.md)。                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`  | `REG_DWORD`                 | 0                                                   | 指出使用者不想接收 Visual Studio 的系統管理員更新。 如果登錄值不存在或集合值為0，表示 Visual Studio 使用者想要接收 Visual Studio 的系統管理員更新。 這適用于開發人員使用者 (是否擁有用戶端電腦) 的系統管理員許可權。 如需詳細資訊，請參閱套用 [系統管理員更新](../install/applying-administrator-updates.md#understanding-configuration-options)。 |
| `UpdateConfigurationFile`     | `REG_SZ` 或 `REG_EXPAND_SZ` | % ProgramData% \Microsoft\VisualStudio\updates.config | 用於設定系統管理更新的檔案路徑。 如需詳細資訊，請參閱設定 [系統管理員更新的方法](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)。                                                                                                                                                                                                                                             |

::: moniker-end

::: moniker range="vs-2019"

| **名稱**                         | **型別**                    | **預設值**                                         | **說明**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                      | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | 儲存套件資訊清單和套件承載 (後者為選擇性) 的目錄。 如需詳細資訊，請參閱 [停用或移動套件](disable-or-move-the-package-cache.md) 快取頁面。                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`         | `REG_DWORD`                 | 1                                                   | 保留套件承載，即使已安裝它們。 您可以隨時變更該值。 停用原則將移除您所修復或修改之執行個體的任何已快取套件承載。 如需詳細資訊，請參閱 [停用或移動套件](disable-or-move-the-package-cache.md) 快取頁面。                                                                                                                                                                             |
| `SharedInstallationPath`         | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared  | 在各個 Visual Studio 執行個體版本上共用之某些套件的安裝目錄。 您可以隨時變更此值，但它只會影響未來的安裝。 任何已安裝在舊位置的產品都不得移動，否則可能無法正常運作。                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`     | `REG_DWORD`                 | 0                                                   | 防止安裝程式為所有已安裝的 Visual Studio 產品自動下載更新。 您可以隨時變更該值。                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | 允許將系統管理員更新套用至用戶端電腦。 如果此值遺失或設為0，系統管理員更新將會遭到封鎖。 此值適用于系統管理用途。 如需詳細資訊，請參閱 [啟用系統管理員更新](enabling-administrator-updates.md)。                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | 指出使用者不想接收 Visual Studio 的系統管理員更新。 如果登錄值不存在或集合值為0，表示 Visual Studio 使用者想要接收 Visual Studio 的系統管理員更新。 這適用于開發人員使用者 (是否擁有用戶端電腦) 的系統管理員許可權。 如需詳細資訊，請參閱套用 [系統管理員更新](../install/applying-administrator-updates.md#understanding-configuration-options)。 |
| `UpdateConfigurationFile`        | `REG_SZ` 或 `REG_EXPAND_SZ` | % ProgramData% \Microsoft\VisualStudio\updates.config | 用於設定系統管理更新的檔案路徑。 如需詳細資訊，請參閱設定 [系統管理員更新的方法](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)。                                                                                                                                                                                                                                             |
| `BaselineStickinessVersions2019` | `REG_SZ` 或 `REG_EXPAND_SZ` | `16.7.0`                                            | 用戶端應保留的服務基準次要版本。 如需詳細資訊，請參閱套用 [系統管理員更新](../install/applying-administrator-updates.md#understanding-configuration-options) 頁面。                                                                                                                                                                                                                                                    |

::: moniker-end

::: moniker range=">=vs-2022"

| **名稱**                         | **型別**                    | **預設值**                                         | **說明**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                      | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | 儲存套件資訊清單和套件承載 (後者為選擇性) 的目錄。 如需詳細資訊，請參閱 [停用或移動套件](disable-or-move-the-package-cache.md) 快取頁面。                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`         | `REG_DWORD`                 | 1                                                   | 保留套件承載，即使已安裝它們。 您可以隨時變更該值。 停用原則將移除您所修復或修改之執行個體的任何已快取套件承載。 如需詳細資訊，請參閱 [停用或移動套件](disable-or-move-the-package-cache.md) 快取頁面。                                                                                                                                                                             |
| `SharedInstallationPath`         | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramFiles%\Microsoft Visual Studio\Shared       | 在各個 Visual Studio 執行個體版本上共用之某些套件的安裝目錄。 您可以隨時變更此值，但它只會影響未來的安裝。 任何已安裝在舊位置的產品都不得移動，否則可能無法正常運作。                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`     | `REG_DWORD`                 | 0                                                   | 防止安裝程式為所有已安裝的 Visual Studio 產品自動下載更新。 您可以隨時變更該值。                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | 允許將系統管理員更新套用至用戶端電腦。 如果此值遺失或設為0，系統管理員更新將會遭到封鎖。 此值適用于系統管理用途。 如需詳細資訊，請參閱 [啟用系統管理員更新](enabling-administrator-updates.md)。                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | 指出使用者不想接收 Visual Studio 的系統管理員更新。 如果登錄值不存在或集合值為0，表示 Visual Studio 使用者想要接收 Visual Studio 的系統管理員更新。 這適用于開發人員使用者 (是否擁有用戶端電腦) 的系統管理員許可權。 如需詳細資訊，請參閱套用 [系統管理員更新](../install/applying-administrator-updates.md#understanding-configuration-options)。 |
| `UpdateConfigurationFile`        | `REG_SZ` 或 `REG_EXPAND_SZ` | % ProgramData% \Microsoft\VisualStudio\updates.config | 用於設定系統管理更新的檔案路徑。 如需詳細資訊，請參閱設定 [系統管理員更新的方法](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)。                                                                                                                                                                                                                                             |
| `BaselineStickinessVersions2019` | `REG_SZ` 或 `REG_EXPAND_SZ` | `16.7.0`                                            | 用戶端應保留的服務基準次要版本。 如需詳細資訊，請參閱套用 [系統管理員更新](../install/applying-administrator-updates.md#understanding-configuration-options) 頁面。                                                                                                                                                                                                                                                    |

::: moniker-end

> [!IMPORTANT]
> 如果在任何安裝之後變更 `CachePath` 登錄原則，則必須將現有的套件快取移至新位置，並確定它受到保護，讓 `SYSTEM` 和 `Administrators` 都具有完全控制權限，而 `Everyone` 具有讀取權限。
> 無法移動或保護現有的快取，日後安裝可能會發生問題。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

- [安裝 Visual Studio](install-visual-studio.md)
- [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
- [套用系統管理員更新](applying-administrator-updates.md)
- [停用或移動套件快取](disable-or-move-the-package-cache.md)
- [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
