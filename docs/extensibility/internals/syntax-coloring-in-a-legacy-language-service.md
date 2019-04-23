---
title: 舊版語言服務中的語法著色 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e193f5c8363cda4e3519df45d001a1972865813e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057756"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>舊版語言服務中的語法著色

Visual Studio 會使用色彩服務識別語言的項目，並使用指定的色彩，在編輯器中顯示它們。

## <a name="colorizer-model"></a>色彩標示器模型
 語言服務會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面，然後由編輯器。 此實作是語言服務中，從個別的物件，如下圖所示：

 ![SVC 色彩標示器圖形](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
>  語法著色服務是不同於一般的 Visual Studio 機制，以色彩標示文字。 如需有關一般[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]機制支援標示色彩，請參閱[使用的字型和色彩](../../extensibility/using-fonts-and-colors.md)。

 除了色彩標示器，其語言服務可以提供自訂色彩的項目所使用的編輯器中，廣告會提供自訂色彩的項目。 您可以藉由實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>介面實作的相同物件上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面。 當編輯器呼叫時，它會傳回的自訂色彩的項目數<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法，且會傳回個別的自訂色彩項目的時，編輯器會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法會傳回該物件會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>介面。 如果語言服務支援 24 位元或高的色彩值，就必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>上的相同物件的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>介面。

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage 如何使用語言服務色彩標示器

1. VSPackage 必須取得適當的語言服務，它會要求語言服務 VSPackage 來執行下列作業：

    1. 使用物件，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面，以取得會以色彩標示的文字。

         文字通常會顯示使用該物件會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。

    2. 查詢的語言服務 GUID VSPackage 的服務提供者，以取得語言服務。 語言服務是以副檔名識別登錄中。

    3. 建立關聯的語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>藉由呼叫其<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法。

2. VSPackage 現在取得及使用的色彩標示器物件，如下所示：

    > [!NOTE]
    > 使用核心編輯器的 Vspackage，不需要明確地取得語言服務的色彩標示器物件。 核心編輯器的執行個體取得適當的語言服務，因為它會執行如下所示的所有顏色標示工作。

    1. 取得語言服務的色彩標示器物件，它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>，並<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>介面，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>語言服務的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>物件。

    2. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，以取得特定範圍的色彩標示器資訊的文字。

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 傳回值，一個用於以色彩標示的文字範圍中的每個字元的陣列。 值是到維護核心編輯器的預設色彩的項目清單或自訂色彩項目的清單，語言服務本身所維護的可設定色彩的項目清單的索引。

    3. 使用所傳回的顏色標示資訊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，以顯示選取的文字。

> [!NOTE]
>  除了使用語言服務色彩標示器，VSPackage 也可以使用一般用途的 Visual Studio 文字著色機制。 如需有關這項機制的詳細資訊，請參閱 <<c0> [ 使用的字型和色彩](../../extensibility/using-fonts-and-colors.md)。

## <a name="in-this-section"></a>本節內容
- [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)

 討論如何編輯器存取語言服務的語法著色和語言服務必須實作以支援的語法著色。

- [如何：使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 示範如何使用內建可設定色彩的項目從語言服務。

- [自訂可設定色彩的項目](../../extensibility/internals/custom-colorable-items.md)

 討論如何實作自訂色彩的項目。

## <a name="see-also"></a>另請參閱

- [使用字型和色彩](../../extensibility/using-fonts-and-colors.md)