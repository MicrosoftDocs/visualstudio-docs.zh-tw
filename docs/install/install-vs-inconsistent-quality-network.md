---
title: "在低頻寬或不可靠的網路環境安裝 | Microsoft Docs"
description: "描述 Visual Studio 安裝程式如何在不可靠的網路情況下運作，並說明如何在開始安裝之前下載安裝檔案。"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>在低頻寬或不可靠的網路環境安裝 Visual Studio 2017
我們設計了新的 Visual Studio 2017 安裝程式，以適用於各種不同的網路和電腦情況。

- 安裝 Visual Studio 所需的檔案分佈在全球傳遞網路，因此我們可從當地伺服器提供檔案給您；
- 在安裝程序期間，我們會嘗試三種不同的下載技術 (WebClient、BITS 和 WinInet) 以將防毒和 Proxy 軟體的干擾降到最低；
- 新的工作負載型模型表示您需要安裝的項目比舊版 Visual Studio 要少。

因此，建議您試用新的 Web 安裝程式，相信您會發現良好的體驗。 但如果您想在開始安裝 Visual Studio 之前確定是否已成功下載安裝檔案，包在我們身上。 您可以使用命令列來建立所需之檔案的本機快取，然後再開始安裝。

方式如下：

## <a name="download-the-visual-studio-bootstrapper"></a>下載 Visual Studio 啟動載入器
從下載您所選擇之 Visual Studio 版本的 Visual Studio 啟動載入器開始。

您的安裝程式檔案 (具體而言，即為啟動載入器檔案) 將會符合或類似於下列其中一個檔案。

| 版本                    | 檔案                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>建立本機安裝快取
若要建立本機配置，請開啟命令提示字元，然後使用下列範例的其中一個命令。 這裡的範例假設您已下載 Visual Studio Community 啟動載入器：請根據您的版本適當地調整命令。

- 針對 .NET Web 和 .NET 桌面開發，請執行：
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- 針對 .NET 桌面和 Office 開發，請執行：
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- 針對 C++ 桌面開發，請執行：
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- 若要建立具有所有功能的完整本機配置 (這會花很長的時間，有_非常多_功能！)，請執行：
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

如果您想要安裝英文以外的語言，請將 `en-US` 變更為此頁面底部清單的地區設定。 使用這個[可用的元件和工作負載清單](workload-and-component-ids.md)，視需要進一步自訂您的安裝快取。

## <a name="install-from-the-local-cache"></a>從本機快取安裝
當您從本機安裝快取執行時，我們會使用每個檔案的本機版本。 但如果您在安裝期間選取不存在於快取中的元件，我們將嘗試從網際網路下載它們。

若要確保您只會安裝已下載的檔案，請使用您用來建立配置快取的相同命令列選項。 例如，如果您已使用下列命令建立配置快取：

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

請使用此命令來執行安裝：

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>語言地區設定清單
| **語言地區設定** | **語言** |
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

## <a name="see-also"></a>另請參閱
* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

