---
title: Ca1504： 必須檢閱可能造成誤導的欄位名稱 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 592fc516dad51db10e80cdcbdf652cbf4329f4ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504：必須檢視可能造成誤導的欄位名稱
|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|分類|Microsoft.Maintainability|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 執行個體欄位名稱開頭為"s_"或名稱`static`(`Shared`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 欄位開頭為"m_"。  
  
## <a name="rule-description"></a>規則描述  
 許多使用者關聯的靜態資料的欄位名稱開頭為"s_"。 同樣地，欄位名稱開頭為"m_"與相關聯的執行個體 （成員） 資料。 更容易維護的程式碼的名稱應遵循通常使用的慣例。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請使用適當的前置詞重新命名欄位。 或者，讓目前的後置詞同意透過加入或移除欄位`static`修飾詞。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。