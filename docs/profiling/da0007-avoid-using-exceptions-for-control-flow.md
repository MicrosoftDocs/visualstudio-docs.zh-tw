---
title: DA0007：避免使用例外狀況控制流程 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26819be7cd001e87a6f94ac97d29c8a5e67f3932
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777695"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007：避免使用例外狀況進行控制流程

|||
|-|-|
|規則 ID|DA0007|
|類別|.NET Framework 使用方式|
|分析方法|全部|
|訊息|一致地擲回大量例外狀況。 請考慮在程式邏輯中減少使用例外狀況。|
|訊息類型|警告|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 25 個樣本才能觸發此規則。

## <a name="cause"></a>原因
 在分析資料中呼叫高比率的 .NET Framework 例外處理常式。 請考慮使用其他控制流程邏輯，以減少擲回的例外狀況數量。

## <a name="rule-description"></a>規則描述
 雖然使用例外處理常式來攔截中斷程式執行的錯誤和其他事件是一個好方法，但是在一般的程式執行邏輯中使用例外處理常式可能會很耗費資源，應予以避免。 在大部分情況下，最好只針對很少發生且未預期的情況使用例外狀況。 例外狀況不應該用來當做一般程式流程的一部分傳回值。 在許多情況下，您可以驗證值並使用條件式邏輯以暫止執行導致問題的陳述式，來避免引發例外狀況。

 有關詳細資訊，請參閱第 5 章的[異常管理](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management)部分 – 在 MSDN 上的**Microsoft 模式和實踐**庫**的提高 .NET 應用程式性能和可伸縮性**卷中**提高託管代碼性能**。

## <a name="how-to-investigate-a-warning"></a>如何調查警告
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至 [標記] 檢視。 查找包含 **.NET CLR@ProcessInstance異常（ ）\\* 的 Excel 引發 / 秒度量的**列。 判斷是否有特定的程式執行階段，當中的例外狀況處理比其他階段更頻繁。 使用取樣設定檔，嘗試識別 throw 陳述式以及產生頻繁例外狀況的 try/catch 區塊。 如果有必要，請在 catch 區塊中加入邏輯，協助您了解最常處理的例外狀況。 如果可行，請將經常執行的 throw 陳述式或 catch 區塊，取代為簡單的流程控制邏輯或驗證程式碼。

 例如，如果您發現應用程式經常處理 DivideByZeroException 例外狀況，在程式中新增邏輯來檢查分母是否有零值可改善應用程式的效能。
