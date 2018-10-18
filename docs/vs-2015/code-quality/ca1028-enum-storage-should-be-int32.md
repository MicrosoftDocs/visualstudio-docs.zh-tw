---
title: CA1028： 列舉儲存區應該是 Int32 |Microsoft Docs
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
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 305bd87a72de1e3ad22b8cf689f10ad49939a34b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304495"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028：列舉儲存區應該是 Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用列舉型別的基礎型別不是<xref:System.Int32?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設，<xref:System.Int32?displayProperty=fullName>資料型別用來儲存常數值。 即使您可以變更這個基礎類型，它不是必要或建議大部分的情況下。 請注意，沒有顯著的效能提升之後，即可使用小於資料型別<xref:System.Int32>。 如果您無法使用的預設資料類型，您應該使用其中一個的 Common Language 系統 (CLS)-標準的整數類資料類型， <xref:System.Byte>， <xref:System.Int16>， <xref:System.Int32>，或<xref:System.Int64>藉此確定，將以表示列舉型別的所有值符合 CLS 標準的程式設計語言。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正這項規則的違規情形，除非有大小或相容性問題，請使用<xref:System.Int32>。 情況下所在<xref:System.Int32>不夠大，要保存的值，請使用<xref:System.Int64>。 如果回溯相容性需要較小的資料類型，請使用<xref:System.Byte>或<xref:System.Int16>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 回溯相容性問題需要它才，則隱藏此規則的警告。 在應用程式無法遵守此規則通常不會不會造成問題。 在程式庫，其中語言互通性是必要的無法遵守此規則可能會影響您的使用者。

## <a name="example-of-a-violation"></a>發生違規的範例

### <a name="description"></a>描述
 下列範例顯示兩個未使用建議的基礎資料類型的列舉。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>範例，示範如何修正

### <a name="description"></a>描述
 下列範例會藉由變更基礎資料類型來修正上述違規<xref:System.Int32>。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700：不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>



