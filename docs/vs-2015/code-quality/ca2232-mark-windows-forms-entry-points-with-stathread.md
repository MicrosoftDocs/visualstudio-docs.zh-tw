---
title: CA2232：使用 STAThread 標示 Windows Forms 進入點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540279"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232:Windows Forms 進入點必須標記 STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 元件參考 <xref:System.Windows.Forms> 命名空間，而且其進入點未以 <xref:System.STAThreadAttribute?displayProperty=fullName> 屬性標記。

## <a name="rule-description"></a>規則描述
 <xref:System.STAThreadAttribute> 表示應用程式的 COM 執行緒模型為單一執行緒的單元。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。 如果屬性不存在，則應用程式會使用多執行緒的單元模型，Windows Forms 不支援此模型。

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 使用應用程式架構的專案不需要將 **Main** 方法標示為 STAThread。 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]編譯器會自動執行此工作。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將 <xref:System.STAThreadAttribute> 屬性新增至進入點。 如果 <xref:System.MTAThreadAttribute?displayProperty=fullName> 屬性存在，請將它移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您正在針對 .NET Compact Framework （其 <xref:System.STAThreadAttribute> 屬性是不必要且不受支援的）進行開發，則可以放心隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範的正確用法 <xref:System.STAThreadAttribute> 。

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
