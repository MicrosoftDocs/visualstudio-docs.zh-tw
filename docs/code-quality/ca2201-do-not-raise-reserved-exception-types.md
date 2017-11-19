---
title: "CA2201： 不要引發保留的例外狀況類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 713018b96aed70d52b1b11e75b0c2993312ef474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201：不要引發保留的例外狀況類型
|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 方法會引發的例外狀況類型，這是過於普遍或所保留的執行階段。  
  
## <a name="rule-description"></a>規則描述  
 下列的例外狀況型別則過於提供足夠的資訊給使用者：  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 是保留的應該只能由 common language runtime 會擲回下列例外狀況類型：  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **不會擲回一般例外狀況**  
  
 如果您會擲回一般例外狀況類型，例如<xref:System.Exception>或<xref:System.SystemException>它會強制在文件庫或架構中，取用者，以攔截所有例外狀況，包括未知不知道如何處理的例外狀況。  
  
 相反地，擲回衍生程度較大的型別已存在於架構，或建立自己的型別衍生自<xref:System.Exception>。  
  
 **擲回特定例外狀況**  
  
 下表顯示參數和驗證參數，包括實值參數中的 set 存取子屬性時所擲回的例外狀況：  
  
|參數描述|例外狀況|  
|---------------------------|---------------|  
|`null`參考|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|允許範圍之外的值 （例如集合或清單的索引）|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|無效`enum`值|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|包含不符合方法的參數規格的格式 (例如的格式字串`ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|否則將會無效|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 作業無效時的目前狀態的物件擲回<xref:System.InvalidOperationException?displayProperty=fullName>  
  
 已處置的物件上執行作業時擲回<xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 不支援的作業時 (例如在覆寫**Stream.Write**開啟來讀取資料流中) 會擲回<xref:System.NotSupportedException?displayProperty=fullName>  
  
 當轉換導致溢位 （例如在明確轉型運算子多載） 時擲回<xref:System.OverflowException?displayProperty=fullName>  
  
 對於所有其他情況下，請考慮建立您自己的類型衍生自<xref:System.Exception>，則會擲回。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，變更擲回的例外狀況的類型不是其中一個保留的類型為特定類型。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1031：不要攔截一般例外狀況類型](../code-quality/ca1031-do-not-catch-general-exception-types.md)