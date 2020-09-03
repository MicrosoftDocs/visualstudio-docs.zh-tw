---
title: CA2213：應該處置可處置的欄位 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534572"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213:可處置的欄位應該受到處置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別，這個型別 <xref:System.IDisposable?displayProperty=fullName> 會針對也會實作為型別的宣告欄位 <xref:System.IDisposable> 。 宣告 <xref:System.IDisposable.Dispose%2A> 類型的方法不會呼叫欄位的方法 <xref:System.IDisposable.Dispose%2A> 。

## <a name="rule-description"></a>規則描述
 類型負責處置其所有非受控資源;這是藉由實作為完成的 <xref:System.IDisposable> 。 這項規則會檢查可處置的型別是否宣告了 `T` `F` 可處置型別的實例欄位 `FT` 。 針對每個欄位 `F` ，此規則會嘗試找出對的呼叫 `FT.Dispose` 。 此規則會搜尋呼叫的方法 `T.Dispose` ，而其中一個層級較低 () 所呼叫方法所呼叫的方法 `FT.Dispose` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請 <xref:System.IDisposable.Dispose%2A> 在 <xref:System.IDisposable> 您負責配置和釋出欄位所持有的非受控資源時，對執行類型的欄位呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不負責釋出欄位所持有的資源，或呼叫 <xref:System.IDisposable.Dispose%2A> 發生于比規則檢查更深層的呼叫層級，就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示的類型 `TypeA` 會 <xref:System.IDisposable> `FT` 在上一個討論) 中執行 (。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>範例
 下列範例顯示的型別 `TypeB` 違反了這項規則，方法是 `aFieldOfADisposableType` `F` 在先前的討論中宣告欄位 () 為可處置的型別 (`TypeA`) ，而不是 <xref:System.IDisposable.Dispose%2A> 在欄位上呼叫。 `TypeB` 對應于 `T` 上一個討論中的。

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName>[Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
