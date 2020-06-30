---
title: CA2220：完成項應呼叫基類完成項 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540656"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220:完成項應該呼叫基底類別完成項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 覆寫的類型 <xref:System.Object.Finalize%2A?displayProperty=fullName> 不會呼叫 <xref:System.Object.Finalize%2A> 其基類中的方法。

## <a name="rule-description"></a>規則描述
 最終化必須透過繼承階層架構 (Inheritance Hierarchy) 進行傳播。 若要確保這一點，類型必須 <xref:System.Object.Finalize%2A> 從其本身的方法中呼叫其基類方法 <xref:System.Object.Finalize%2A> 。 C # 編譯器會自動新增對基類完成項的呼叫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請從您的方法呼叫基底類型的 <xref:System.Object.Finalize%2A> 方法 <xref:System.Object.Finalize%2A> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 某些以通用語言執行平臺為目標的編譯器會將基底類型的完成項呼叫插入 Microsoft 中繼語言（MSIL）。 如果報告來自此規則的警告，則您的編譯器不會插入呼叫，而且您必須將它新增至您的程式碼。

## <a name="example"></a>範例
 下列 Visual Basic 範例顯示在 `TypeB` <xref:System.Object.Finalize%2A> 其基類中正確呼叫方法的類型。

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>另請參閱
 [Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
