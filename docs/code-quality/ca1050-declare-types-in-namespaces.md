---
title: CA1050:類型必須在命名空間中宣告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 869ff99243349ae01c63da0a7d9e6544761cbd39
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922504"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050:類型必須在命名空間中宣告

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
公用或受保護的類型定義于命名空間的範圍外。

## <a name="rule-description"></a>規則描述
類型會在命名空間中宣告, 以避免名稱衝突, 以及在物件階層中組織相關類型的方法。 在任何命名空間之外的類型, 都位於無法在程式碼中參考的全域命名空間中。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請將類型放在命名空間中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
雖然您永遠不需要隱藏此規則的警告, 但當元件永遠不會與其他元件一起使用時, 可以安全地執行此動作。

## <a name="example"></a>範例
下列範例顯示的程式庫在命名空間外宣告的類型不正確, 以及命名空間中宣告了相同名稱的類型。

[!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
[!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>範例
下列應用程式會使用先前定義的程式庫。 請注意, 當命名空間未限定名稱`Test`時, 會建立在命名空間外部宣告的類型。 另請注意, 若要`Test`存取中`Goodspace`的類型, 則需要命名空間名稱。

[!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
[!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]