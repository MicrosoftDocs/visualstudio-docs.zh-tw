---
title: CA1050： Declare 命名空間中的類型 |Microsoft Docs
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
ms.openlocfilehash: a0a4dcc53fac7dc9b7e189686a3b32e2fb4fd030
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539590"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050:類型必須在命名空間中宣告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型定義在命名空間的範圍之外。

## <a name="rule-description"></a>規則描述
 在命名空間中宣告型別，以避免名稱衝突，以及在物件階層中組織相關類型的方式。 在任何命名空間以外的類型，都位於無法在程式碼中參考的全域命名空間中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將類型放在命名空間中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 雖然您永遠不需要隱藏此規則的警告，但當元件永遠不會與其他元件一起使用時，可以安全地進行此作業。

## <a name="example"></a>範例
 下列範例顯示在命名空間外部宣告類型不正確的程式庫，以及在命名空間中宣告相同名稱的類型。

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>範例
 下列應用程式會使用先前定義的程式庫。 請注意，在命名空間以外宣告的型別，會在名稱不是 `Test` 由命名空間限定時建立。 另請注意，若要 `Test` 在中存取類型 `Goodspace` ，則需要命名空間名稱。

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
