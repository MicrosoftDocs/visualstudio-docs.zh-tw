---
title: 在低頻寬或不可靠的網路環境安裝 | Microsoft Docs
description: 了解網路不穩定或頻寬較低時如何使用 Visual Studio 安裝程式，以及如何使用命令列來下載安裝檔案。
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: b273efb06e7b2e70617d28dcafc85735bcfb1fd1
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138796"
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>在低頻寬或不可靠的網路環境安裝 Visual Studio 2017

建議您嘗試使用 Visual Studio Web 安裝程式&mdash; 相信您在大多數情況下會發現這是很好的體驗。

 > [!div class="button"]
 > [下載 Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

不過，如果您的網際網路連線無法使用或不可靠，您可以使用命令列來建立完成離線安裝所需之檔案的本機快取。 方式如下：

> [!NOTE]
> 如果您是企業系統管理員，而且想要將Visual Studio 2017 部署至已啟用網際網路防火牆的用戶端工作站網路，請參閱[建立 Visual Studio 2017 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)和[安裝 Visual Studio 離線安裝所需的憑證](../install/install-certificates-for-visual-studio-offline.md)頁面。

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>步驟 1 - 下載 Visual Studio 啟動載入器

從下載您所選擇之 Visual Studio 版本的 Visual Studio 啟動載入器開始。

您的安裝程式檔案 (具體而言，即為啟動載入器檔案) 將會符合或類似於下列其中一個檔案。

| 版本                    | 檔案                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>步驟 2 - 建立本機安裝快取

您必須具有網際網路連線才能完成此步驟。 若要建立本機配置，請開啟命令提示字元，然後使用下列範例的其中一個命令。 這裡的範例假設您是使用 Visual Studio Community Edition。請根據您的版本適當地調整命令。

- 針對 .NET Web 和 .NET 桌面開發，請執行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- 針對 .NET 桌面和 Office 開發，請執行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- 針對 C++ 桌面開發，請執行：

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- 若要建立具有所有功能的完整本機配置 (這會花很長的時間&mdash;有_非常多_功能)，請執行：

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

如果您想要安裝英文以外的語言，請將 `en-US` 變更為此頁面底部清單的地區設定。 使用這個[可用的元件和工作負載清單](workload-and-component-ids.md)，視需要進一步自訂您的安裝快取。

> [!IMPORTANT]
> 完整的 Visual Studio 2017 配置至少需要 35 GB 的磁碟空間，並可能需要花費一些時間才能完成下載。 如需如何建立只含有您要安裝的元件之配置的資訊，請參閱[使用命令列參數來安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)。

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>步驟 3 - 從本機快取安裝 Visual Studio

> [!TIP]
> 當您從本機安裝快取執行時，安裝程式會使用每個檔案的本機版本。 但如果您在安裝期間選取不存在於快取中的元件，我們將嘗試從網際網路下載它們。

若要確保您只會安裝已下載的檔案，請使用您用來建立配置快取的相同命令列選項。 例如，如果您已使用下列命令建立配置快取：

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

請使用此命令來執行安裝：

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> 如果您收到錯誤指出簽章不正確，您必須安裝更新的憑證。 開啟離線快取中的 [憑證] 資料夾。 按兩下每個憑證檔案，然後點選完成 [憑證管理員精靈]。 如果要求您輸入密碼，請保留空白。

## <a name="list-of-language-locales"></a>語言地區設定清單

| **語言地區設定** | **Language** |
| ----------------------- | --------------- |
| cs-CZ | 捷克文 |
| de-DE | 德文 |
| zh-TW | 英文 |
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

* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 工作負載和元件識別碼](workload-and-component-ids.md)
