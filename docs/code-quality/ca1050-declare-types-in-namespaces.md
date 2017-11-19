---
title: "CA1050： 宣告命名空間中的型別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c0aeaaf3531c45668b8804a6285be5df211c2754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050：在命名空間中宣告類型
|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的類型被定義已命名的命名空間的範圍之外。  
  
## <a name="rule-description"></a>規則描述  
 類型會宣告在命名空間，以防止名稱衝突，並做為組織物件階層架構中的相關的類型的方式。 是任何具名命名空間外部的類型是不能在程式碼中參考的全域命名空間中。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，將命名空間中的型別。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 雖然您不一定要隱藏此規則的警告，則若要這樣做，當組件不會與其他組件一起使用。  
  
## <a name="example"></a>範例  
 下列範例示範具有不正確的命名空間中，外部宣告的型別程式庫和具有相同名稱的命名空間中宣告的類型。  
  
 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## <a name="example"></a>範例  
 下列應用程式會使用先前定義的文件庫。 請注意，外部命名空間宣告的型別時，會建立名稱`Test`不合格的命名空間。 也請注意，存取`Test`輸入`Goodspace`，命名空間名稱是必要項。  
  
 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]