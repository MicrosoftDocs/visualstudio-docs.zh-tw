---
title: CA2232:Windows Forms 進入點必須標記 STAThread
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 06772f8dd91c27834b329293d06cfbc2a7dcfcef
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230762"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232:Windows Forms 進入點必須標記 STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因
元件會參考<xref:System.Windows.Forms>命名空間，而且其進入點不會<xref:System.STAThreadAttribute?displayProperty=fullName>以屬性標記。

## <a name="rule-description"></a>規則描述
 <xref:System.STAThreadAttribute>表示應用程式的 COM 執行緒模型是單一執行緒的單元。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。 如果屬性不存在，應用程式會使用多執行緒的單元模型，這不支援 Windows Forms。

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]使用應用程式架構的專案不需要以 STAThread 標記**Main**方法。 編譯器[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]會自動執行此工作。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請<xref:System.STAThreadAttribute>將屬性新增至進入點。 <xref:System.MTAThreadAttribute?displayProperty=fullName>如果屬性存在，請將它移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果您要針對 .NET Compact Framework 進行開發， <xref:System.STAThreadAttribute>而不需要且不支援屬性，則可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例示範的正確用法<xref:System.STAThreadAttribute>：

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]