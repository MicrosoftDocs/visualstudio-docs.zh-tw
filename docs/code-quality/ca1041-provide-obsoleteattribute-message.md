---
title: "CA1041： 提供 ObsoleteAttribute 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a7536130842c78ca2c00bab1afc3caf842e02cba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041：提供 ObsoleteAttribute 訊息
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 使用標示的型別或成員<xref:System.ObsoleteAttribute?displayProperty=fullName>屬性並沒有其<xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>指定屬性。  
  
## <a name="rule-description"></a>規則描述  
 <xref:System.ObsoleteAttribute>用來標記已被取代的程式庫類型和成員。 程式庫的取用者應該避免使用任何類型或已標記為過時的成員。 這是因為它可能不支援，且最終會移除來自較新版本的程式庫。 當類型或成員標記為使用<xref:System.ObsoleteAttribute>經過編譯之後，<xref:System.ObsoleteAttribute.Message%2A>顯示屬性的屬性。 以便提供使用者有關過時類型或成員的資訊。 這項資訊通常包括多久過時的型別或成員會支援程式庫設計工具並使用慣用的取代項目。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，加入`message`參數<xref:System.ObsoleteAttribute>建構函式。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告，因為<xref:System.ObsoleteAttribute.Message%2A>屬性會提供有關過時類型或成員的重要資訊。  
  
## <a name="example"></a>範例  
 下列範例顯示過時的成員具有正確宣告<xref:System.ObsoleteAttribute>。  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>