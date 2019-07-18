---
title: 在維護基底上時更新 Visual Studio
description: 了解如何在維護基底上時更新 Visual Studio。
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bf167c46e9b7dd9317278c7ce388977c4cc9428a
ms.sourcegitcommit: f369ff7e84b0216f01570a486c7be80ca6d0e61a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68250324"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>在維護基底上時更新 Visual Studio

Visual Studio 2019 將在其[產品生命週期](/visualstudio/productinfo/release-rhythm#release-channel-updates)期間進行頻繁的更新。 更新將會包含可能新增功能和元件的次要版本更新 (例如，從 16.0 到 16.1)，以及只包含重大問題目標修正的維護更新 (例如，從 16.0.4 到 16.0.5)。

企業系統管理員可以選擇將其用戶端保持在維護基準。 維護基準由維護更新支援，直到下一個維護基準發行過後一年。

維護基準選項讓開發人員和系統管理員能更彈性地採用新功能、錯誤 (Bug) 修正或次要更新中包含的元件。 第一個服務基準是 16.0.x。 如需詳細資訊，請參閱 [Enterprise 與 Professional 客戶的支援選項](https://docs.microsoft.com/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers)。

## <a name="how-to-get-onto-a-servicing-baseline"></a>如何進入服務基準

若要開始使用維護基準，請從 [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) 下載固定版本的 Visual Studio 安裝程式啟動載入器。 啟動載入器有指向該特定版本之產品設定、工作負載和元件的連結。

> [!NOTE]
> 請小心區別固定版本啟動載入器和標準啟動載入器。 標準啟動載入器是設定為使用 Visual Studio 的最新可用版本。 從 My.VisualStudio.com 下載標準啟動載入器時，它們在檔案名稱中會有數字 (例如，vs_enterprise__123456789-123456789.exe)。

在安裝期間，企業系統管理員必須設定其用戶端以防止用戶端更新至最新版本。 您可以透過多種方式來設定用戶端：
- [變更回應設定檔中的 `channelUri` 設定](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network)，以在配置或本機資料夾中使用通道資訊清單。
- [透過命令列執行修改 channelUri](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet)，以使用非存在的檔案。
- [在用戶端系統上設定原則來停用更新](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating)，以防止用戶端自行更新。

### <a name="install-a-servicing-baseline-on-a-network"></a>在網路上安裝服務基準

使用網路配置安裝的系統管理員，應修改配置中 *response.json* 檔案內的 `channelUri` 值，以使用相同資料夾中的 *channelmanifest.json*。 如需相關步驟，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。 變更 `channelUri` 值可讓用戶端在配置位置中尋找更新。

### <a name="install-a-servicing-baseline-via-the-internet"></a>透過網際網路安裝服務基準

針對網際網路型安裝，請將 `--channelUri` 與不存在的通道資訊清單新增至用來啟動安裝程式的命令列。 這會禁止 Visual Studio 使用最新的可用版本進行更新。 以下為範例：

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>使用原則設定來停用用戶端更新

控制用戶端更新的另一個選項是[關閉更新通知](controlling-updates-to-visual-studio-deployments.md)。 如果在安裝時未變更 channelUri 值，請使用此選項。 它將禁止用戶端接收指向最新可用版本的連結。 在用戶端上，仍然需要固定版本啟動載入器來更新到特定版本。

## <a name="how-to-stay-on-a-servicing-baseline"></a>如何保持服務基準

當維護基準更新可用時，該維護更新的固定版本啟動載入器檔案可在 [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) 取得。

針對透過網路配置進行部署的系統管理員，系統管理員需要更新[版面配置位置](update-a-network-installation-of-visual-studio.md)。 從該位置安裝的用戶端會收到更新通知。 如果需要部署至用戶端更新，請遵循[這些指示](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines)。 當修改 'response.json' 以進行更新時，請勿新增額外的工作負載、元件或語言。 在產品更新後，必須以「修改」部署的方式管理這些設定。

針對網際網路型安裝，請執行新的固定版本啟動載入器，其中 `--channelUri` 參數指向用戶端上不存在的通道資訊清單。 如果更新是以無訊息或被動模式進行部署，請使用兩個不同的命令：

1. 更新 Visual Studio 安裝程式：

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. 更新 Visual Studio 應用程式本身：

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [如何在回應檔中定義設定](automated-installation-with-response-file.md)
* [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)
