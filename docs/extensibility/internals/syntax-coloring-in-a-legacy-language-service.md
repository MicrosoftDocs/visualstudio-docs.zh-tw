---
title: 舊版語言服務中的語法著色 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa3dcadfc7774766c0e76617ce133d2c30ba2aa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186317"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>舊版語言服務中的語法著色

Visual Studio 使用著色服務來識別語言的元素，並在編輯器中以指定的色彩顯示。

## <a name="colorizer-model"></a>著色器模型
 語言服務會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面，然後由編輯器使用。 此實作為語言服務的個別物件，如下圖所示：

 ![SVC 色彩標示器圖形](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> 語法著色服務有別于上色文字的一般 Visual Studio 機制。 如需有關支援上色之一般 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 機制的詳細資訊，請參閱[使用字型和色彩](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)。

 除了著色器之外，語言服務也可以提供編輯器所使用的自訂可設定色彩專案，方法是廣告它提供自訂的可設定色彩專案。 若要這麼做，您可以在執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 介面的相同物件上進行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 介面。 當編輯器呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 方法時，它會傳回自訂可設定色彩專案的數目，而當編輯器呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 方法時，它會傳回個別的自訂可設定色彩專案。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 方法會傳回可執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 介面的物件。 如果語言服務支援24位或高彩的值，它就必須在與 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 介面相同的物件上，執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 介面。

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage 如何使用語言服務著色器

1. VSPackage 必須取得適當的語言服務，這需要語言服務 VSPackage 來執行下列動作：

    1. 使用執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 介面的物件，以取得要以色彩標示的文字。

         通常會使用可執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 介面的物件來顯示文字。

    2. 藉由查詢語言服務 GUID 之 VSPackage 的服務提供者，取得語言服務。 語言服務會在登錄中以副檔名來識別。

    3. 藉由呼叫其 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 方法，讓語言服務與 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 產生關聯。

2. VSPackage 現在可以取得並使用著色器物件，如下所示：

    > [!NOTE]
    > 使用「核心編輯器」的 Vspackage 不需要明確地取得語言服務的著色器物件。 一旦核心編輯器的實例取得適當的語言服務，它就會執行此處顯示的所有顏色標示工作。

    1. 藉由在語言服務的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 物件上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 方法，取得語言服務的著色器物件，它會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>，並 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> 介面。

    2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法，以取得特定文字範圍的著色器資訊。

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 會傳回值的陣列，每個字元在要以色彩標示的文字範圍中各一個。 這些值是可設定色彩專案清單的索引，這是核心編輯器所維護的預設可設定色彩專案清單，或是語言服務本身維護的自訂可設定色彩專案清單。

    3. 使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法所傳回的顏色標示資訊，以顯示選取的文字。

> [!NOTE]
> 除了使用語言服務著色器之外，VSPackage 也可以使用一般用途 Visual Studio 文字著色機制。 如需此機制的詳細資訊，請參閱[使用字型和色彩](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)。

## <a name="in-this-section"></a>本章節內容
- [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)

 討論編輯器如何存取語言服務的語法著色，以及語言服務必須執行哪些內容來支援語法著色。

- [如何︰使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 示範如何從語言服務使用內建的可設定色彩專案。

- [自訂可設定色彩的項目](../../extensibility/internals/custom-colorable-items.md)

 討論如何執行自訂可設定色彩專案。