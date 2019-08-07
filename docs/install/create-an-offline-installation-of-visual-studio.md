---
title: 建立離線安裝
description: 了解如何在有不可靠網際網路連線或低頻寬時離線安裝 Visual Studio。
ms.date: 07/24/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 616c27f16b4fca9be6f8dab3cdf70fafae52f193
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483512"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>建立 Visual Studio 的離線安裝

::: moniker range="vs-2017"

我們已設計 Visual Studio 2017 可在各種網路和電腦組態中正常運作。 雖然建議您嘗試 [Visual Studio Web 安裝程式](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) (這是小型檔案，並可讓您掌握所有最新修正程式和功能)，但我們了解您可能無法這麼做。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 的設計適用於各種網路和電腦組態。 雖然建議您嘗試 [Visual Studio Web 安裝程式](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) (這是小型檔案，並可讓您掌握所有最新修正程式和功能)，但我們了解您可能無法這麼做。

::: moniker-end

例如，您可能有不可靠網際網路連線，或具有低頻寬的連線。 若是如此，您有幾個選項：您可以使用新的 [全部下載後安裝] 功能來下載檔案後再安裝，也可以使用命令列來建立檔案的本機快取。

> [!NOTE]
> 如果您是企業系統管理員，想要將 Visual Studio 部署至已啟用網際網路防火牆的用戶端工作站網路，請參閱[建立 Visual Studio 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)和[安裝 Visual Studio 離線安裝所需憑證](../install/install-certificates-for-visual-studio-offline.md)頁面。

## <a name="use-the-download-all-then-install-feature"></a>使用 [全部下載後安裝] 功能

::: moniker range="vs-2017"

[**15.8 版的新功能**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install)：在您下載 Web 安裝程式之後，請從 Visual Studio 安裝程式中選取新的 [全部下載後安裝]  選項。 然後，繼續執行您的安裝。

   ![[全部下載後安裝] 選項](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

在您下載 Web 安裝程式之後，請從 Visual Studio 安裝程式中選取新的 [全部下載後安裝]  選項。 然後，繼續執行您的安裝。

   ![[全部下載後安裝] 選項](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

我們設計了 [全部下載後安裝] 功能，讓您能夠針對下載 Visual Studio 的同一部電腦將 Visual Studio 下載成單一安裝。 如此一來，您便可以放心地先中斷與 Web 的連線，再安裝 Visual Studio。

> [!IMPORTANT]
> 請勿使用 [全部下載後安裝] 功能來建立要傳輸至另一部電腦的離線快取。 此功能並不是設計來進行該用途。 <br><br>如果您想要建立離線快取，將 Visual Studio 安裝在另一部電腦上，請參閱本頁面的[使用命令列建立本機快取](#use-the-command-line-to-create-a-local-cache)一節，以了解如何建立本機快取，或參閱[建立 Visual Studio 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)頁面，以了解如何建立網路快取。

## <a name="use-the-command-line-to-create-a-local-cache"></a>使用命令列來建立本機快取

在您下載小型啟動載入器之後，請使用命令列來建立本機快取。 然後，使用本機快取安裝 Visual Studio (此程序會取代適用於舊版本的 ISO 檔案)。

方式如下：

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>步驟 1 - 下載 Visual Studio 啟動載入器

您必須具有網際網路連線才能完成此步驟。

從下載您所選擇之 Visual Studio 版本的 Visual Studio 啟動載入器開始。 您的安裝程式檔案 (或啟動載入器) 將會符合或類似於下列其中一個檔案。

::: moniker range="vs-2017"

| 版本                    | 檔案                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

::: moniker-end

::: moniker range="vs-2019"

| 版本                    | 檔案                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>步驟 2 - 建立本機安裝快取

您必須具有網際網路連線才能完成此步驟。

> [!IMPORTANT]
> 如果您安裝的是 Visual Studio Community，則必須在安裝 30 天內啟用它。 這需要網際網路連線。

開啟命令提示字元，然後使用下列範例中的其中一個命令。 這裡所列的範例假設您使用 Visual Studio Community Edition；請根據您的版本適當地調整命令。

> [!TIP]
> 為了防止發生錯誤，請確保完整安裝路徑少於 80 個字元。

- 針對 .NET Web 和 .NET 桌面開發，請執行：

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- 針對 .NET 桌面和 Office 開發，請執行：

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- 針對 C++ 桌面開發，請執行：

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- 若要建立具有所有功能的完整本機配置 (這會花很長的時間&mdash;有_非常多_功能)，請執行：

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > 完整的 Visual Studio 配置至少需要 35 GB 磁碟空間。 如需詳細資訊，請參閱[系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs/)。 如需如何建立只包含您要安裝之元件的配置資訊，請參閱[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)。

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > 完整的 Visual Studio 配置至少需要 35 GB 磁碟空間。 如需詳細資訊，請參閱[系統需求](/visualstudio/releases/2019/system-requirements/)。 如需如何建立只包含您要安裝之元件的配置資訊，請參閱[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)。

::: moniker-end

如果您想要安裝英文以外的語言，請將 `en-US` 變更為[語言地區設定清單](#list-of-language-locales)中的地區設定。 然後，使用[可用的元件和工作負載清單](workload-and-component-ids.md)，進一步自訂您的安裝快取。

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>步驟 3 - 從本機快取安裝 Visual Studio

> [!TIP]
> 當您從本機安裝快取執行時，安裝程式會使用每個檔案的本機版本。 但如果您在安裝期間選取不存在於快取中的元件，則安裝程式會嘗試從網際網路下載它們。

若要確定您只會安裝先前下載的檔案，請使用您用來建立配置快取的相同命令列選項。 例如，如果您已使用下列命令建立配置快取：

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

然後，使用此命令來執行安裝：

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!NOTE]
> 如果您收到錯誤指出簽章不正確，您必須安裝更新的憑證。 開啟離線快取中的 [憑證] 資料夾。 按兩下每個憑證檔案，然後點選完成 [憑證管理員精靈]。 如果系統要求您輸入密碼，則請保留空白。

### <a name="list-of-language-locales"></a>語言地區設定清單

| **語言地區設定** | **Language** |
| ----------------------- | --------------- |
| cs-CZ | 捷克文 |
| de-DE | 德文 |
| en-US | 英文 |
| es-ES | 西班牙文 |
| fr-FR | 法文 |
| it-IT | 義大利文 |
| ja-JP | 日文 |
| ko-KR | 韓文 |
| pl-PL | 波蘭文 |
| pt-BR | 葡萄牙文 - 巴西 |
| ru-RU | 俄文 |
| tr-TR | 土耳其文 |
| zh-CN | 簡體中文 |
| zh-TW | 繁體中文 |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

- [建立 Visual Studio 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)
- [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
- [安裝 Visual Studio 離線安裝所需的憑證](../install/install-certificates-for-visual-studio-offline.md)
- [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
