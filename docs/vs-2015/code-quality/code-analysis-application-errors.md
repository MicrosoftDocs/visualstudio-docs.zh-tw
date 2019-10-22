---
title: 程式碼分析應用程式錯誤
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9fa92e773c3dc130d0c0fc0ce05cc270dc9b6e53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669014"
---
# <a name="code-analysis-application-errors"></a>程式碼分析應用程式錯誤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
本節參考 managed 程式碼分析工具所產生的錯誤訊息。 若要取得特定錯誤訊息的說明，請在索引的 [**尋找**] 方塊中輸入錯誤代碼。

## <a name="in-this-section"></a>本章節內容

|||
|-|-|
|[CA0001](ca0001.md)|在 managed 程式碼分析工具中引發例外狀況，但未指出預期的錯誤情況。|
|[CA0051](ca0051.md)|未選取任何規則。|
|[CA0052](ca0052.md)|未選取要分析的目標。|
|[CA0053](ca0053.md)|無法載入規則元件。|
|[CA0054](ca0054.md)|自訂規則元件包含不正確 XML 資源。|
|[CA0055](ca0055.md)|無法載入檔案： \<path >|
|[CA0056](ca0056.md)|專案檔具有不正確的分析工具版本。|
|[CA0057](ca0057.md)|違規無法對應到目前的目標和規則集。|
|[CA0058](ca0058.md)|無法載入參考的元件。|
|[CA0059](ca0059.md)|命令列參數錯誤。|
|[CA0060](ca0060.md)|無法載入間接參考的元件。|
|[CA0061](ca0061.md)|找不到規則 '*RuleId*'。|
|[CA0062](ca0062.md)|找不到規則集 '*RuleSetName*' 中參考的規則 '*RuleId*'。|
|[CA0063](ca0063.md)|無法載入規則集檔案或它的其中一個相依規則集檔案。|
|[CA0064](ca0064.md)|未執行任何分析，因為指定的規則集未包含任何 FxCop 規則。|
|[CA0065](ca0065.md)|不支援的元資料結構：類型 '*TypeName*' 同時包含屬性和具有相同名稱 '*PropertyFieldName*' 的欄位|
|[CA0066](ca0066.md)|提供給 **/targetframeworkversion**的值 '*VersionID*' 不是可辨識的版本。|
|[CA0067](ca0067.md)|找不到目錄。|
|[CA0068](ca0068.md)|找不到目標群組件 *' AssemblyName '* 的偵錯工具資訊。|
|[CA0069](ca0069.md)|使用替代平臺。 找不到*FrameworkVersion1* 。 改為使用*FrameworkVersion2* 。 若要獲得最佳分析結果，請確定已安裝正確的 .NET Framework。|
|[CA0070](ca0070.md)|無法載入元件或類型，因為安全性許可權。|
|[CA0501](ca0501.md)|無法讀取輸出報告。|
|[CA0502](ca0502.md)|不支援的語言。|
|[CA0503](ca0503.md)|屬性已被取代。 使用取代屬性|
|[CA0504](ca0504.md)|已忽略規則目錄，因為它不存在|
|[CA0505](ca0505.md)|屬性已被取代。 使用取代屬性|
|[FxCopCmd 錯誤](fxcopcmd-errors.md)|Managed 程式碼分析錯誤。|

## <a name="related-sections"></a>相關章節

- [撰寫安全程式碼的指導方針](https://msdn.microsoft.com/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [針對應用程式生命週期管理工具中的錯誤進行疑難排解的資源](https://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)