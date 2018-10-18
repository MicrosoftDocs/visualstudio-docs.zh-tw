---
title: 程式碼分析應用程式錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66d611903c71cc526c01c1062c85ceef2e7975f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225013"
---
# <a name="code-analysis-application-errors"></a>程式碼分析應用程式錯誤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
本節是 managed 程式碼分析工具所產生的錯誤訊息的參考。 若要取得特定的錯誤訊息的說明，請輸入中的錯誤號碼**尋找**方塊中的索引。

## <a name="in-this-section"></a>本節內容

|||
|-|-|
|[CA0001](ca0001.md)|在 managed 程式碼分析工具不會指出預期的錯誤狀況，例外狀況。|
|[CA0051](ca0051.md)|未不選取任何規則。|
|[CA0052](ca0052.md)|若要分析未不選取任何目標。|
|[CA0053](ca0053.md)|無法載入規則組件。|
|[CA0054](ca0054.md)|自訂規則組件具有無效的 XML 資源。|
|[CA0055](ca0055.md)|無法載入檔案：\<路徑 >|
|[CA0056](ca0056.md)|專案檔具有不正確的版本的分析工具。|
|[CA0057](ca0057.md)|違規無法對應至目前的目標和規則集。|
|[CA0058](ca0058.md)|無法載入參考的組件。|
|[CA0059](ca0059.md)|命令列參數時發生錯誤。|
|[CA0060](ca0060.md)|無法載入組件的間接參考。|
|[CA0061](ca0061.md)|規則 '*RuleId*' 找不到。|
|[CA0062](ca0062.md)|規則 '*RuleId*'中的規則集所參考的'*RuleSetName*' 找不到。|
|[CA0063](ca0063.md)|無法載入規則集檔案或其相依的規則集檔案。|
|[CA0064](ca0064.md)|不執行任何分析，因為指定的規則集未包含任何 FxCop 規則。|
|[CA0065](ca0065.md)|不支援的中繼資料建構： 類型 '*TypeName*'包含的屬性和具有相同名稱的欄位'*PropertyFieldName*'|
|[CA0066](ca0066.md)|值 '*VersionID*' 提供給 **/targetframeworkversion**不是可辨識的版本。|
|[CA0067](ca0067.md)|找不到目錄。|
|[CA0068](ca0068.md)|偵錯目標組件，找不到資訊 *'AssemblyName'*。|
|[CA0069](ca0069.md)|使用替代的平台。 *FrameworkVersion1*找不到。 使用*FrameworkVersion2*改。 為獲得最佳分析結果請確定已安裝正確的.NET Framework。|
|[CA0070](ca0070.md)|無法載入組件或類型，因為安全性權限。|
|[CA0501](ca0501.md)|無法讀取輸出報告。|
|[CA0502](ca0502.md)|不支援的語言。|
|[CA0503](ca0503.md))|Deprectated 屬性。 使用 superceding 屬性|
|[CA0504](ca0504.md)|已忽略規則目錄，因為它不存在|
|[CA0505](ca0505.md)|Deprectated 屬性。 使用 superceding 屬性|
|[FxCopCmd 錯誤](fxcopcmd-errors.md)|Managed 程式碼分析錯誤。|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|程式碼分析簽入原則錯誤。|

## <a name="related-sections"></a>相關章節

- [撰寫安全程式碼的指導方針](http://msdn.microsoft.com/en-us/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [應用程式生命週期管理工具 中的錯誤疑難排解資源](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)