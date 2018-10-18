---
title: CA1040： 避免空介面 |Microsoft Docs
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
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b5e2ff26842f63ea1c21e599b301e4ce4e78bf80
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190314"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040：避免空的介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 介面不會宣告任何成員或實作兩個或多個其他介面。

## <a name="rule-description"></a>規則描述
 介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空的介面並未定義任何成員。 因此，它不會定義可以實作的合約。

 如果您的設計包含空白預期類型的介面實作，您可能使用介面作為標記或用來識別類型的群組。 如果這個識別會在執行階段，若要完成這項作業的正確方式是使用自訂屬性。 使用存在該屬性中，不存在或屬性的屬性，來識別目標類型。 如果識別必須發生在編譯時期，它可接受使用空的介面。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除介面，或將成員加入至它。 如果空的介面來標示一組型別，取代介面的自訂屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，介面用來識別在編譯時期的一組型別時。

## <a name="example"></a>範例
 下列範例會顯示空的介面。

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]



