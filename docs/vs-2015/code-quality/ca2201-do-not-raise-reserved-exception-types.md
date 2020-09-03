---
title: CA2201：不要引發保留的例外狀況類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9533a597a33deaed17ff2a73d56ef306ea7b5613
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546337"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201:不要引發保留的例外狀況類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|類別|Microsoft. 使用量|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會引發太過一般或執行時間所保留的例外狀況類型。

## <a name="rule-description"></a>規則描述
 下列例外狀況類型太普遍，無法提供足夠的資訊給使用者：

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  下列例外狀況類型是保留的，而且應該只由 common language runtime 擲回：

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **不要擲回一般例外狀況**

  如果您在程式庫或架構中擲回一般例外狀況類型（例如 <xref:System.Exception> 或 <xref:System.SystemException> ），它會強制取用者攔截所有例外狀況，包括不知道如何處理的未知例外狀況。

  相反地，會擲回已經存在於架構中的更衍生型別，或建立您自己的衍生自的型別 <xref:System.Exception> 。

  **擲回特定例外狀況**

  下表顯示參數，以及當您驗證參數時所擲回的例外狀況，包括屬性 set 存取子中的 value 參數：

|參數描述|例外狀況|
|---------------------------|---------------|
|`null` 參考|<xref:System.ArgumentNullException?displayProperty=fullName>|
|在允許的值範圍之外 (例如集合或清單的索引) |<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|`enum`值無效|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|包含的格式不符合方法的參數規格 (例如) 的格式字串 `ToString(String)`|<xref:System.FormatException?displayProperty=fullName>|
|否則無效|<xref:System.ArgumentException?displayProperty=fullName>|

 當作業對物件擲回的目前狀態無效時 <xref:System.InvalidOperationException?displayProperty=fullName>

 在已處置的物件上執行作業時，會擲回 <xref:System.ObjectDisposedException?displayProperty=fullName>

 當作業不受支援時 (例如在覆寫的 **資料流程中。寫入** 開啟以讀取) 擲回的資料流程 <xref:System.NotSupportedException?displayProperty=fullName>

 轉換會產生溢位 (例如在明確的轉換運算子多載) 擲回 <xref:System.OverflowException?displayProperty=fullName>

 在所有其他情況下，請考慮建立您自己的衍生自的型別， <xref:System.Exception> 並擲回該型別。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將擲回例外狀況的類型變更為不是其中一個保留類型的特定類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1031:不要攔截一般例外狀況類型](../code-quality/ca1031-do-not-catch-general-exception-types.md)
