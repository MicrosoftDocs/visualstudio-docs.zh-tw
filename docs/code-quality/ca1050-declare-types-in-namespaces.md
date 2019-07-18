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
ms.openlocfilehash: 8cac669b96f362d6da73e3eb2f373137c3d9bdd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778514"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050:類型必須在命名空間中宣告

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型被定義已命名的命名空間的範圍之外。

## <a name="rule-description"></a>規則描述
 型別會宣告在命名空間，以避免名稱發生衝突，以及組織物件階層架構中的相關的類型的方法。 任何已命名的命名空間以外的類型是不在程式碼中參考的全域命名空間中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將型別命名空間中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 雖然您永遠都隱藏此規則的警告，則若要這樣做，當組件絕不會使用與其他組件。

## <a name="example"></a>範例
 下列範例示範具有不正確的命名空間中，外部宣告的型別程式庫和具有相同名稱的命名空間中宣告的類型。

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>範例
 下列應用程式會使用先前定義的文件庫。 請注意，外部命名空間宣告的型別時，會建立名稱`Test`未限定的命名空間。 也請注意，若要存取`Test`輸入`Goodspace`，命名空間名稱為必要項。

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]