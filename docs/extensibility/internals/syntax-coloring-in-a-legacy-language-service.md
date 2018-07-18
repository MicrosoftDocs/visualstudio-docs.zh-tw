---
title: 使用語法色彩編碼舊版語言服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 172f06f4e30f1320b6e17332cb2b54af91f7ed01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136051"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>使用語法色彩編碼舊版語言服務

Visual Studio 會使用著色服務識別語言的項目，並顯示在編輯器中指定的色彩。

## <a name="colorizer-model"></a>色彩標示器模型
 此語言服務會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面，然後由編輯器。 這個實作是語言服務的個別物件，如下圖所示：

 ![SVC 色彩標示器圖形](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
>  語法著色服務會與上色功能文字的一般 Visual Studio 機制分開。 如需有關一般[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]機制支援上色功能，請參閱[使用字型和色彩](../../extensibility/using-fonts-and-colors.md)。

 除了色彩標示器，語言服務可以提供自訂色彩的項目所使用的編輯器中，廣告會提供自訂色彩項目。 您可以藉由實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>介面實作在相同物件上的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面。 編輯器 中呼叫時，它會傳回的自訂色彩的項目數<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法，且會傳回個別的自訂色彩項目的編輯器 中進行呼叫時<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法會傳回該物件會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>介面。 如果語言服務支援 24 位元或高色彩值，它必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>上相同的物件做為介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>介面。

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage 如何使用語言服務色彩標示器

1.  VSPackage 必須取得適當的語言服務，這需要語言服務 VSPackage 也可以執行下列作業：

    1.  使用實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面，以取得會以色彩標示的文字。

         文字通常會顯示使用該物件會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。

    2.  取得語言服務藉由查詢語言服務 GUID VSPackage 的服務提供者。 語言服務是以副檔名識別登錄中。

    3.  建立關聯之語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>藉由呼叫其<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法。

2.  VSPackage 可以現在取得及使用的色彩標示器物件，如下所示：

    > [!NOTE]
    > 使用核心編輯器的 Vspackage，不需要明確地取得語言服務的色彩標示器物件。 核心編輯器執行個體取得適當的語言服務，因為它會執行所有顏色標示工作如下所示。

    1.  取得語言服務的色彩標示器物件，它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>介面，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>語言服務上的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>物件。

    2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，以取得特定範圍的色彩標示器資訊的文字。

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 傳回值，其中一個以色彩標示的文字範圍的每個字元的陣列。 有效值為維護核心編輯器的預設色彩項目的清單或自訂色彩項目的清單，語言服務本身所維護的色彩項目的清單中的索引。

    3.  使用所傳回的顏色標示資訊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，以顯示所選的文字。

> [!NOTE]
>  除了使用語言服務色彩標示器，VSPackage 也可以使用一般用途的 Visual Studio 文字著色機制。 如需有關這項機制的詳細資訊，請參閱[使用字型和色彩](../../extensibility/using-fonts-and-colors.md)。

## <a name="in-this-section"></a>本節內容
 [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)討論編輯器如何存取語言服務的語法著色和語言服務必須實作以支援的語法著色。

 [如何： 使用內建的色彩項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)示範如何使用內建的色彩項目從語言服務。

 [自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)討論如何實作自訂色彩項目。

## <a name="see-also"></a>另請參閱

- [使用字型和色彩](../../extensibility/using-fonts-and-colors.md)