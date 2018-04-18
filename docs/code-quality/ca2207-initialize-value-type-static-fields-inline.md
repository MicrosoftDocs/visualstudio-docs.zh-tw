---
title: CA2207： 必須初始化實值類型的靜態欄位內嵌 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5d063cda94451feef28aba9715033234d9adaa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207：必須初始化實值類型的靜態欄位內嵌
|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 實值類型會宣告明確靜態建構函式。  
  
## <a name="rule-description"></a>規則描述  
 實值型別宣告時，它會進行預設初始化其中所有的實值型別欄位會設定為零，而所有參考型別欄位會都設定為`null`(`Nothing`在 Visual Basic 中)。 明確的靜態建構函式只保證執行個體建構函式之前，或呼叫靜態成員的類型。 因此，如果型別而不需要呼叫的執行個體建構函式建立時，靜態建構函式不一定會執行。  
  
 如果所有靜態資料會初始化的內嵌宣告，且沒有明確的靜態建構函式，C# 和 Visual Basic 編譯器新增`beforefieldinit`MSIL 類別定義的旗標。 編譯器也會加入私用靜態建構函式，其中包含靜態初始設定程式碼。 此私用靜態建構函式一定會執行前存取任何類型的靜態欄位。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形時宣告，因此移除靜態建構函式初始化的所有靜態資料。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1810：必須初始化參考類型內部的靜態欄位](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)