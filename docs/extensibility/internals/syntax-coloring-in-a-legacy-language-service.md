---
title: 舊版語言服務中的語法著色 |Microsoft Docs
description: 瞭解 Visual Studio 如何在舊版語言服務中執行語法著色服務，以識別語言的元素，並以編輯器中的色彩顯示這些專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbf063efe30d90c84848222ff931be43834efbad
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876385"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>舊版語言服務中的語法著色

Visual Studio 使用著色服務來識別語言的元素，並在編輯器中以指定的色彩顯示。

## <a name="colorizer-model"></a>著色器模型
 語言服務 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 會執行介面，然後編輯器會使用此介面。 此實作為來自語言服務的不同物件，如下圖所示：

 ![SVC 色彩標示器圖形](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> 語法著色服務與標示文字的一般 Visual Studio 機制不同。 如需有關支援標示之一般機制的詳細資訊 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ，請參閱 [使用字型和色彩](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015)。

 除了著色器之外，語言服務也可以提供編輯器所使用的自訂可設定色彩專案，方法是通告它提供自訂的可設定色彩專案。 您可以藉由在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 相同的物件上執行介面，來執行這項作業 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 。 當編輯器呼叫方法時，它會傳回自訂可設定色彩專案的數目 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> ，而當編輯器呼叫方法時，它會傳回個別的自訂可設定色彩專案 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法會傳回可執行介面的物件 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 。 如果語言服務支援24位或高彩值，則必須 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 在與介面相同的物件上執行介面 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 。

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage 如何使用 Language Service 著色器

1. VSPackage 必須取得適當的語言服務，這需要 language service VSPackage 來執行下列作業：

    1. 使用物件 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 來執行介面，以取得要以色彩標示的文字。

         文字通常會使用實介面的物件來顯示 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。

    2. 藉由查詢 language service GUID 之 VSPackage 的服務提供者來取得語言服務。 語言服務會在登錄中依副檔名識別。

    3. 藉 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 由呼叫其方法，將語言服務與產生關聯 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 。

2. VSPackage 現在可以取得和使用著色器物件，如下所示：

    > [!NOTE]
    > 使用核心編輯器的 Vspackage 不需要明確取得語言服務的著色器物件。 一旦核心編輯器的實例取得適當的語言服務，它就會執行此處顯示的所有顏色標示工作。

    1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 在語言服務的物件上呼叫方法，以取得語言服務的著色器物件，此物件會執行和介面 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 。

    2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法，以取得特定範圍之文字的著色器資訊。

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 傳回值的陣列，以色彩標示文字範圍中的每個字元各一個。 這些值是可設定色彩專案清單中的索引，其為核心編輯器所維護的預設可設定色彩專案清單，或語言服務本身所維護的自訂可設定色彩專案清單。

    3. 使用方法所傳回的顏色標示資訊 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 來顯示選取的文字。

> [!NOTE]
> 除了使用語言服務著色器，VSPackage 也可以使用一般用途 Visual Studio 文字著色機制。 如需此機制的詳細資訊，請參閱 [使用字型和色彩](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015)。

## <a name="in-this-section"></a>本節內容
- [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)

 討論編輯器如何存取語言服務的語法著色，以及語言服務必須如何實行以支援語法著色。

- [如何︰使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 示範如何使用語言服務內建的可設定色彩專案。

- [自訂可設定色彩的項目](../../extensibility/internals/custom-colorable-items.md)

 討論如何執行自訂可設定色彩專案。
