---
title: CA2232： 標記 Windows Form 進入點，以 STAThread |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9345009b889b3c382ce0030c34b547a8fd337e0e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588045"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232：以 STAThread 標記 Windows Form 進入點
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2232： 以 STAThread 標記 Windows Form 進入點](https://docs.microsoft.com/visualstudio/code-quality/ca2232-mark-windows-forms-entry-points-with-stathread)。

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 組件參考<xref:System.Windows.Forms>命名空間，而它的進入點未標示為<xref:System.STAThreadAttribute?displayProperty=fullName>屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.STAThreadAttribute> 表示的 COM 執行緒模型應用程式是單一執行緒 apartment。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。 如果屬性不存在，則應用程式會使用多執行緒的 apartment 模型不支援 Windows Form。

> [!NOTE]
>  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 使用應用程式架構的專案不會將標示**Main** stathread 的方法。 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]編譯器自動執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入<xref:System.STAThreadAttribute>屬性至進入點。 如果<xref:System.MTAThreadAttribute?displayProperty=fullName>屬性存在，則將它移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，如果您正在開發.NET Compact framework 中，為其<xref:System.STAThreadAttribute>屬性是不必要的和不受支援。

## <a name="example"></a>範例
 下列範例示範如何正確使用<xref:System.STAThreadAttribute>。

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]



