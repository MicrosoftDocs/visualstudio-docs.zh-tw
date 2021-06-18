---
title: 控制部署的更新
description: 深入了解當您從網路安裝時如何變更 Visual Studio 尋找更新的位置。
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f15281db55381dadbfd3370eb10a04feeab9c3a5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307566"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>控制網路型 Visual Studio 部署的更新

企業系統管理員通常會建立配置，並將其裝載于網路檔案共用上，以部署至其終端使用者。 此頁面說明如何正確地設定網路設定選項。

## <a name="controlling-where-visual-studio-looks-for-updates"></a>控制 Visual Studio 尋找更新的位置

**案例1：用戶端原本是從配置安裝，但設定為從網路設定位置或 web 接收更新**

根據預設，即使安裝原本是從網路共用部署，Visual Studio 仍會繼續線上尋找更新。 如果網路上有可用的更新，則使用者可以安裝該更新。 雖然系統會先針對任何更新的產品位檢查網路設定快取，如果找不到，則 Visual Studio 會從 web 尋找並下載更新的產品位。

**案例2：原本安裝的用戶端應該只從網路設定接收更新**

如果您想要控制 Visual Studio 用戶端尋找更新的位置，例如，如果您的用戶端電腦沒有網際網路存取，而且您想要確保它只會從配置中進行安裝，則您可以設定用戶端安裝程式尋找更新產品位的位置。 最好先確定已正確設定這項設定，然後用戶端才會從配置進行初始安裝。

1. 建立離線配置：

   ```shell
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. 將配置複製到您想要裝載配置的檔案共用：

   ```shell
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. 修改配置 `response.json` 中的檔案，並將 `channelUri` 值變更為指向系統管理員控制的 channelManifest.js複本。

   請務必在值中逸出反斜線，如下列範例所示：

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   終端使用者現在可以從這個共用執行安裝程式，以安裝 Visual Studio。

   ```shell
   \\server\share\VS\vs_enterprise.exe
   ```

當企業系統管理員判斷應該將使用者更新到較新版的 Visual Studio 時，可以[更新配置位置](update-a-network-installation-of-visual-studio.md)以併入已更新的檔案，如下所示。

1. 使用與下列命令類似的命令：

   ```shell
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. 確定 `response.json` 已更新版面配置中的檔案仍包含您的自訂專案，特別是 channelUri 修改，如下所示：

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

來自此配置的現有 Visual Studio 安裝會在 `\\server\share\VS\ChannelManifest.json` 上尋找更新。 如果 channelManifest.json 比使用者安裝的還新，Visual Studio 會通知使用者有可用的更新。

從用戶端起始的任何安裝更新都會自動直接從配置安裝更新版的 Visual Studio。

**案例3：用戶端原本是從 web 安裝，但現在應該只從網路設定接收更新**

在某些情況下，用戶端電腦可能已從 web 安裝 Visual Studio，但現在系統管理員想要讓所有未來的更新都來自受控版面配置。 唯一支援的方法是建立具有所需產品版本的網路設定，然後在用戶端電腦上， _從配置位置_ 執行啟動載入器 (例如 `\\server\share\vs_enterprise.exe`) 。 在理想的情況下，原始用戶端安裝會使用啟動載入器從網路設定使用正確設定的 ChannelURI 進行，但是從網路設定位置執行更新的啟動載入器也可以運作。 其中一個動作會在用戶端電腦上，以該特定版面配置位置的連接來內嵌。 這種情況下，唯一需要注意的是，設定檔案中的 "ChannelURI" `response.json` 必須與在原始安裝發生時在用戶端電腦上設定的 ChannelURI 相同。 這個值最有可能是設定為網際網路 [發行頻道](https://aka.ms/vs/16/release/channel)。

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>控制 Visual Studio IDE 中的通知

::: moniker range="vs-2017"

如上所述，Visual Studio 會檢查其安裝來源位置 (例如，網路共用或網際網路)，以查看是否有任何可用的更新。 有可用的更新時，Visual Studio 會利用視窗右上角的通知旗標來通知使用者。

   ![更新的通知旗標](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019"

如上所述，Visual Studio 會檢查其安裝來源位置 (例如，網路共用或網際網路)，以查看是否有任何可用的更新。 有可用更新時，Visual Studio 會使用視窗右下角的通知圖示通知使用者。

   ![Visual Studio IDE 中的通知圖示](media/vs-2019/notification-bar.png "Visual Studio IDE 中的通知圖示")

::: moniker-end

如果您不想讓終端使用者收到更新通知，可以停用通知。 (例如，如果您透過中央軟體散發機制提供更新，則可能會想要停用通知)。

::: moniker range="vs-2017"

因為 Visual Studio 2017 [將登錄項目儲存在私人登錄](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)，所以您不能以一般方式直接編輯登錄。 不過，Visual Studio 包含 `vsregedit.exe` 公用程式，讓您可用來變更 Visual Studio 設定。 您可以使用下列命令來關閉通知：

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

因為 Visual Studio 2019 [將登錄項目儲存在私人登錄中](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)，所以您不能以一般方式直接編輯登錄。 不過，Visual Studio 包含 `vsregedit.exe` 公用程式，讓您可用來變更 Visual Studio 設定。 您可以使用下列命令來關閉通知：

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range=">=vs-2022"

由於 Visual Studio 2022 會將 [登錄專案儲存在私人登錄中](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)，因此您無法以一般方式直接編輯登錄。 不過，Visual Studio 包含 `vsregedit.exe` 公用程式，讓您可用來變更 Visual Studio 設定。 您可以使用下列命令來關閉通知：

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(請務必取代符合您想要編輯之已安裝執行個體的目錄)。

> [!TIP]
> 使用 [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) 可尋找用戶端工作站上特定的 Visual Studio 執行個體。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [啟用系統管理員更新](enabling-administrator-updates.md)
* [套用系統管理員更新](applying-administrator-updates.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)
