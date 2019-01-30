---
title: 建立離線安裝
description: 了解如何在有不可靠網際網路連線或低頻寬時離線安裝 Visual Studio。
ms.date: 01/15/2019
ms.custom: seodec18
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: cbf0f68f090219aea8f3ddde31e697463f8e9ee3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035519"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>建立 Visual Studio 2017 的離線安裝

我們已設計 Visual Studio 2017 可在各種網路和電腦組態中正常運作。 雖然建議您嘗試 [Visual Studio Web 安裝程式](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (這是小型檔案，並可讓您掌握所有最新修正程式和功能)，但我們了解您可能無法這麼做。

例如，您可能有不可靠網際網路連線，或具有低頻寬的連線。 若是如此，您有幾個選項：您可以使用新的 [全部下載後安裝] 功能來下載檔案後再安裝，也可以使用命令列來建立檔案的本機快取。

> [!NOTE]
> 如果您是企業系統管理員，而且想要將Visual Studio 2017 部署至已啟用網際網路防火牆的用戶端工作站網路，請參閱[建立 Visual Studio 2017 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)和[安裝 Visual Studio 離線安裝所需的憑證](../install/install-certificates-for-visual-studio-offline.md)頁面。

## <a name="use-the-download-all-then-install-feature"></a>使用 [全部下載後安裝] 功能

[**15.8 中的新功能**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
)：在您下載 Web 安裝程式之後，請從 Visual Studio 安裝程式中選取新的 [全部下載後安裝]**** 選項。 然後，繼續執行您的安裝。

   ![[全部下載後安裝] 選項](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>使用命令列來建立本機快取

在您下載小型啟動載入器之後，請使用命令列來建立本機快取。 然後，使用本機快取安裝 Visual Studio (此程序會取代適用於舊版本的 ISO 檔案)。

方式如下：

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>步驟 1 - 下載 Visual Studio 啟動載入器

您必須具有網際網路連線才能完成此步驟。

從下載您所選擇之 Visual Studio 版本的 Visual Studio 啟動載入器開始。 您的安裝程式檔案 (或啟動載入器) 將會符合或類似於下列其中一個檔案。

| 版本                    | 檔案                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>步驟 2 - 建立本機安裝快取

您必須具有網際網路連線才能完成此步驟。

> [!IMPORTANT]
> 如果您是安裝 Visual Studio Community 2017，您必須在安裝的 30 天內啟用它。 這需要網際網路連線。

開啟命令提示字元，然後使用下列範例中的其中一個命令。 這裡所列的範例假設您使用 Visual Studio Community Edition；請根據您的版本適當地調整命令。

> [!TIP]
> 為了防止發生錯誤，請確保完整安裝路徑少於 80 個字元。

- 針對 .NET Web 和 .NET 桌面開發，請執行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- 針對 .NET 桌面和 Office 開發，請執行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- 針對 C++ 桌面開發，請執行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- 若要建立具有所有功能的完整本機配置 (這會花很長的時間&mdash;有_非常多_功能)，請執行：

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

  > [!NOTE]
  > 完整的 Visual Studio 2017 配置至少需要 35 GB 的磁碟空間。 如需如何建立只含有您要安裝的元件之配置的資訊，請參閱[使用命令列參數來安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)。

如果您想要安裝英文以外的語言，請將 `en-US` 變更為[語言地區設定清單](#list-of-language-locales)中的地區設定。 然後，使用[可用的元件和工作負載清單](workload-and-component-ids.md)，進一步自訂您的安裝快取。

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>步驟 3 - 從本機快取安裝 Visual Studio

> [!TIP]
> 當您從本機安裝快取執行時，安裝程式會使用每個檔案的本機版本。 但如果您在安裝期間選取不存在於快取中的元件，則安裝程式會嘗試從網際網路下載它們。

若要確定您只會安裝先前下載的檔案，請使用您用來建立配置快取的相同命令列選項。 例如，如果您已使用下列命令建立配置快取：

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

然後，使用此命令來執行安裝：

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

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

- [建立 Visual Studio 2017 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)
- [安裝 Visual Studio 離線安裝所需的憑證](../install/install-certificates-for-visual-studio-offline.md)
- [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 2017 工作負載和元件識別碼](workload-and-component-ids.md)
