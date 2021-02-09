---
title: 控制部署的更新
description: 深入了解當您從網路安裝時如何變更 Visual Studio 尋找更新的位置。
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ffa088de8852b0d5884cd4d9db5e65e1c179164b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868539"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>控制網路型 Visual Studio 部署的更新

企業系統管理員通常會建立配置，並將配置裝載於網路檔案共用上，以部署給終端使用者。

## <a name="controlling-where-visual-studio-looks-for-updates"></a>控制 Visual Studio 尋找更新的位置

根據預設，即使從網路共用中部署安裝，Visual Studio 仍然會持續在線上尋找更新。 如果有可用的更新，使用者即可安裝它。 從 Web 下載離線配置中找不到的任何已更新內容。

如果您想要直接控制 Visual Studio 如何查看更新，則可以修改它所尋找的位置。 您也可以控制您的使用者要更新的目標版本。 若要這樣做，請依照下列步驟執行：

1. 建立離線配置：

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. 將配置複製到您想要裝載配置的檔案共用：

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. 修改配置中的 response.json 檔案，並變更 `channelUri` 值，以指向系統管理員所控制的 channelManifest.json 複本。

   請務必在值中逸出反斜線，如下列範例所示：

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   使用者現在就可以從這個共用執行安裝程式，以安裝 Visual Studio。

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

當企業系統管理員判斷應該將使用者更新到較新版的 Visual Studio 時，可以[更新配置位置](update-a-network-installation-of-visual-studio.md)以併入已更新的檔案，如下所示。

1. 使用與下列命令類似的命令：

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. 請確認已更新配置中的 response.json 檔案仍然包含您的自訂，尤其是 channelUri 修改，如下所示：

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   來自此配置的現有 Visual Studio 安裝會在 `\\server\share\VS\ChannelManifest.json` 上尋找更新。 如果 channelManifest.json 比使用者安裝的還新，Visual Studio 會通知使用者有可用的更新。

   新的安裝會直接從配置中自動安裝已更新的 Visual Studio 版本。

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>控制 Visual Studio IDE 中的通知

::: moniker range="vs-2017"

如上所述，Visual Studio 會檢查其安裝來源位置 (例如，網路共用或網際網路)，以查看是否有任何可用的更新。 有可用的更新時，Visual Studio 會利用視窗右上角的通知旗標來通知使用者。

   ![更新的通知旗標](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

如上所述，Visual Studio 會檢查其安裝來源位置 (例如，網路共用或網際網路)，以查看是否有任何可用的更新。 有可用更新時，Visual Studio 會使用視窗右下角的通知圖示通知使用者。

   ![Visual Studio IDE 中的通知圖示](media/vs-2019/notification-bar.png "Visual Studio IDE 中的通知圖示")

::: moniker-end

如果您不想要通知使用者有可用的更新，則可以停用通知。 (例如，如果您透過中央軟體散發機制提供更新，則可能會想要停用通知)。

::: moniker range="vs-2017"

因為 Visual Studio 2017 [將登錄項目儲存在私人登錄](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)，所以您不能以一般方式直接編輯登錄。 不過，Visual Studio 包含 `vsregedit.exe` 公用程式，讓您可用來變更 Visual Studio 設定。 您可以使用下列命令來關閉通知：

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

因為 Visual Studio 2019 [將登錄項目儲存在私人登錄中](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)，所以您不能以一般方式直接編輯登錄。 不過，Visual Studio 包含 `vsregedit.exe` 公用程式，讓您可用來變更 Visual Studio 設定。 您可以使用下列命令來關閉通知：

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(請務必取代符合您想要編輯之已安裝執行個體的目錄)。

> [!TIP]
> 使用 [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) 可尋找用戶端工作站上特定的 Visual Studio 執行個體。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)
