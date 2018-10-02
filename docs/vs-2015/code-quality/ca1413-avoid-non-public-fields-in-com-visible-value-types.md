---
title: CA1413： 避免在 COM 可見實值類型中的非公用欄位 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 29765a07ba7a9389301036c0d25a525932297f7c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588317"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413：避免在 COM 可見的實值類型中使用非公用欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1413： 避免在 COM 可見實值類型中的非公用欄位](https://docs.microsoft.com/visualstudio/code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types)。

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 特別標示為可見的元件物件模型 (COM) 實值型別宣告的非公用執行個體欄位。

## <a name="rule-description"></a>規則描述
 COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 檢閱資訊，不應該公開，或將具有非預期的設計或安全性影響欄位的內容。

 根據預設，所有公用實值型別會作為 COM 可見 不過，以減少誤判，此規則需要明確指示類型的 COM 的可視性。 包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設定為`false`且型別必須標示有<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定為`true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，並保持隱藏的欄位，將實值型別變更為參考型別，或移除<xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性從型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，公開的欄位是否可接受的。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱
 [以相互操作 Unmanaged 程式碼](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)[限定互通的.NET 類型](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



