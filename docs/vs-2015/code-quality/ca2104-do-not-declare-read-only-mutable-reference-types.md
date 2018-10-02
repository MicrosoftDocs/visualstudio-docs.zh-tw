---
title: CA2104： 不要宣告唯讀的可變動參考類型 |Microsoft Docs
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
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e4c94ae65f22051c51dc16c678177a13ed75095c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588462"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104：不要宣告唯讀的可變動參考類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2104： 不要宣告唯讀的可變動參考類型](https://docs.microsoft.com/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types)。

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|分類|Microsoft.Security|
|中斷變更|非重大|

## <a name="cause"></a>原因
 外部可見類型包含了可變動參考類型的外部可見唯讀欄位。

## <a name="rule-description"></a>規則描述
 可變動類型是可以修改執行個體資料的類型。 <xref:System.Text.StringBuilder?displayProperty=fullName>類別是可變動參考類型的範例。 它包含成員可以變更類別的執行個體的值。 不可變的參考類型的範例是<xref:System.String?displayProperty=fullName>類別。 已執行個體化之後，可以永遠不會變更其值。

 唯讀修飾詞 ([readonly](http://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4)在 C# 中， [ReadOnly](http://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8)中[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，和[const](http://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) c + + 中) 的參考類型欄位 （c + + 中的指標） 可防止欄位取代為另一個執行個體的參考型別。 不過，修飾詞不會防止執行個體資料的欄位正在修改透過參考類型。

 唯讀陣列欄位免套用此規則，但改為導致違反[CA2105： 陣列欄位不應該為唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md)規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除唯讀修飾詞，或是否可接受的重大變更，請使用不可變的類型取代欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的警告，如果欄位類型是不可變。

## <a name="example"></a>範例
 下列範例顯示會導致違反此規則的欄位宣告。

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]



