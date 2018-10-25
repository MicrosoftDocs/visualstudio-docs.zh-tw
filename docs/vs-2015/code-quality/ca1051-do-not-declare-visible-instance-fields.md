---
title: CA1051： 不要宣告可見的執行個體欄位 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 691f5fe87d775d2bff2fc15ff15ca8022478b3a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910546"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051：不要宣告可見的執行個體欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型都有的外部可見的執行個體欄位。

## <a name="rule-description"></a>規則描述
 欄位的主要用法應該是當做實作詳細資料。 欄位應該`private`或`internal`，而且應該使用屬性公開。 很容易存取的屬性，它可存取的欄位，以及可以變更的屬性存取子中的程式碼，如型別的功能展開，而不導入重大變更。 只會傳回私用或內部欄位的值的屬性已最佳化，以執行與同等存取欄位;很少效能已改善使用外部可見欄位相關聯屬性。

 外部可見的指`public`， `protected`，並`protected internal`(`Public`， `Protected`，和`Protected Friend`Visual Basic 中) 存取範圍層級。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將欄位設`private`或`internal`並將它公開使用的外部可見的屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 外部可見的欄位不會提供屬性無法使用的任何權益。 此外，公用欄位不能受到[連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)。 請參閱[CA2112： 受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。

## <a name="example"></a>範例
 下列範例顯示型別 (`BadPublicInstanceFields`)，違反這項規則。 `GoodPublicInstanceFields` 顯示更正的程式碼。

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA2112：受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>另請參閱
 [連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



