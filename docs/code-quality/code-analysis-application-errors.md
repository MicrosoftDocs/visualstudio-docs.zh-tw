---
title: 程式碼分析應用程式錯誤
ms.date: 11/04/2016
description: 瞭解 managed 程式碼分析工具在 Visual Studio 中產生的錯誤訊息。 查看錯誤碼和對應的描述。
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f5c217e8d043d0363b66a63c84c78829f640065
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860577"
---
# <a name="code-analysis-application-errors"></a>程式碼分析應用程式錯誤

本節是 managed 程式碼分析工具所產生之錯誤訊息的參考。

## <a name="in-this-section"></a>本節內容

|程式碼|描述|
|-|-|
|[CA0001](ca0001.md)|在 managed 程式碼分析工具內引發例外狀況，而此工具並未指出預期的錯誤狀況。|
|[CA0051](ca0051.md)|未選取任何規則。|
|[CA0052](ca0052.md)|未選取要分析的目標。|
|[CA0053](ca0053.md)|無法載入規則元件。|
|[CA0054](ca0054.md)|自訂規則元件有不正確 XML 資源。|
|[CA0055](ca0055.md)|無法載入檔案：\<path>|
|[CA0056](ca0056.md)|專案檔案的分析工具版本不正確。|
|[CA0057](ca0057.md)|違規無法對應到目前的目標和規則集。|
|[CA0058](ca0058.md)|無法載入參考的元件。|
|[CA0059](ca0059.md)|命令列參數錯誤。|
|[CA0060](ca0060.md)|無法載入間接參考的元件。|
|[CA0061](ca0061.md)|找不到規則 '*RuleId*'。|
|[CA0062](ca0062.md)|找不到在規則集 '*RuleSetName*' 中參考的規則 '*RuleId*'。|
|[CA0063](ca0063.md)|無法載入規則集檔案或其中一個相依的規則集檔案。|
|[CA0064](ca0064.md)|未執行任何分析，因為指定的規則集未包含任何 FxCop 規則。|
|[CA0065](ca0065.md)|不支援的元資料結構：類型 '*TypeName*' 同時包含屬性和名稱為 '*PropertyFieldName*' 的欄位|
|[CA0066](ca0066.md)|提供給 **/targetframeworkversion** 的值 '*VersionID*' 不是可辨認的版本。|
|[CA0067](ca0067.md)|找不到目錄。|
|[CA0068](ca0068.md)|找不到目標群組件 *' AssemblyName '* 的偵錯工具資訊。|
|[CA0069](ca0069.md)|使用替代平臺。 找不到 *FrameworkVersion1* 。 改為使用 *FrameworkVersion2* 。 為了獲得最佳分析結果，請確定已安裝正確的 framework 版本。|
|[CA0070](ca0070.md)|因為安全性許可權，所以無法載入元件或類型。|
|[CA0501](ca0501.md)|無法讀取輸出報告。|
|[CA0502](ca0502.md)|不支援的語言。|
|[CA0503](ca0503.md)|屬性已被取代。 使用取代的屬性|
|[CA0504](ca0504.md)|因為規則目錄不存在，所以已予以忽略|
|[CA0505](ca0505.md)|屬性已被取代。 使用取代的屬性|
|[FxCopCmd 錯誤](fxcopcmd-errors.md)|Managed 程式碼分析錯誤。|

## <a name="related-sections"></a>相關章節

- [Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)
- [分析 Managed 程式碼品質](../code-quality/code-analysis-for-managed-code-overview.md)
