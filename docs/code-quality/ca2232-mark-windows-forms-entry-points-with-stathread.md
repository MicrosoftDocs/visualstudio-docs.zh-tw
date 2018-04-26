---
title: CA2232：以 STAThread 標記 Windows Form 進入點
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c5a1ba8eae4cc98242581d1ea525648b5e6b434b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232：以 STAThread 標記 Windows Form 進入點
|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 組件參考<xref:System.Windows.Forms>命名空間，而它的進入點不標記為<xref:System.STAThreadAttribute?displayProperty=fullName>屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.STAThreadAttribute> 表示的 COM 執行緒模型應用程式是單一執行緒 apartment。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。 如果屬性不存在，應用程式會使用多執行緒的 apartment 模式，不支援的 Windows Form。

> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 使用應用程式架構的專案不會將標示**Main**以 stathread 標記的方法。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編譯器會自動運作。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入<xref:System.STAThreadAttribute>屬性的進入點。 如果<xref:System.MTAThreadAttribute?displayProperty=fullName>屬性，則將它移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，如果您正在開發的.NET Compact Framework 中，為其<xref:System.STAThreadAttribute>屬性是不必要的和不受支援。

## <a name="example"></a>範例
 下列範例將示範正確的使用方式的<xref:System.STAThreadAttribute>。

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]