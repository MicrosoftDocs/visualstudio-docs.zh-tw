---
title: CA2213:可處置的欄位應該受到處置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cbb606729fe89eb5c2ebe3c814096ef39120836a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685261"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213:可處置的欄位應該受到處置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別可實作<xref:System.IDisposable?displayProperty=fullName>宣告的型別，也會實作的欄位<xref:System.IDisposable>。 <xref:System.IDisposable.Dispose%2A>欄位的方法不由呼叫<xref:System.IDisposable.Dispose%2A>宣告型別的方法。

## <a name="rule-description"></a>規則描述
 類型會負責處置所有 unmanaged 資源;這可以藉由實作<xref:System.IDisposable>。 此規則會檢查以查看是否可處置型別`T`宣告欄位`F`也就是可處置型別的執行個體`FT`。 每個欄位`F`，此規則會嘗試找出呼叫`FT.Dispose`。 此規則會搜尋呼叫的方法`T.Dispose`，和一個較低的層級 (藉由呼叫的方法所呼叫的方法`FT.Dispose`)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫<xref:System.IDisposable.Dispose%2A>之實作類型的欄位上<xref:System.IDisposable>如果您是負責配置和釋放 unmanaged 的資源保留的欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，如果您不負任何責任的釋放資源保留 欄位中，或呼叫<xref:System.IDisposable.Dispose%2A>比規則檢查更深入的呼叫層級，就會發生。

## <a name="example"></a>範例
 下列範例顯示型別`TypeA`可實<xref:System.IDisposable>(`FT`中先前的討論)。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>範例
 下列範例顯示型別`TypeB`，藉由宣告欄位違反這項規則`aFieldOfADisposableType`(`F`先前的討論中) 做為可處置的類型 (`TypeA`) 並不會呼叫<xref:System.IDisposable.Dispose%2A>欄位上。 `TypeB` 對應至`T`中先前的討論。

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName> [處置模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
