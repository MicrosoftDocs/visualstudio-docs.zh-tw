---
title: CA1050：宣告命名空間中的類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c56de70daeabd05215f68024339d5855686d529b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653838"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050：在命名空間中宣告類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型定義于命名空間的範圍外。

## <a name="rule-description"></a>規則描述
 類型會在命名空間中宣告，以避免名稱衝突，以及在物件階層中組織相關類型的方法。 在任何命名空間之外的類型，都位於無法在程式碼中參考的全域命名空間中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將類型放在命名空間中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 雖然您永遠不需要隱藏此規則的警告，但當元件永遠不會與其他元件一起使用時，可以安全地執行此動作。

## <a name="example"></a>範例
 下列範例顯示的程式庫在命名空間外宣告的類型不正確，以及命名空間中宣告了相同名稱的類型。

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>範例
 下列應用程式會使用先前定義的程式庫。 請注意，當名稱 `Test` 不是由命名空間限定時，會建立在命名空間外宣告的類型。 另請注意，若要存取 `Goodspace` 中的 `Test` 類型，則需要命名空間名稱。

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
