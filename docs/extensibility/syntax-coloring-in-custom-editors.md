---
title: 自訂編輯器中著色的語法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e087e82754244b7abda530f733a6047447f4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="syntax-coloring-in-custom-editors"></a>自訂編輯器中著色的語法
Visual Studio 環境 SDK 編輯器，包括核心編輯器中，使用語言服務找出特定語法的項目，並使用指定的色彩，給定文件檢視中顯示它們。

## <a name="colorization-requirements"></a>顏色標示需求
 必須實作語言服務的色彩標示器的所有編輯器：

1.  使用實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>管理的文字會以色彩標示和實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>提供文件檢視的文字。

2.  查詢使用的語言服務的識別 GUID VSPackage 的服務提供者來取得特定語言服務的介面。

3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>物件實作的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。 這個方法產生關聯之語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>實作 VSPackage 用來管理會以色彩標示的文字。

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>語言服務的色彩標示器核心編輯器使用方式
 當以色彩標示器語言服務透過執行個體的核心編輯器、 剖析和呈現的文字語言服務的色彩標示器會自動進行而不需要您採取任何進一步的介入。

 IDE 以透明的方式：

-   呼叫以剖析和分析的文字加入或修改在實作中的色彩標示器視<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。

-   可確保所提供的文件檢視所提供的顯示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>更新實作並重新繪製使用的色彩標示器所傳回的資訊。

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>語言服務的色彩標示器的非核心編輯器使用方式
 非核心編輯器執行個體也可以使用語言服務的語法顏色標示服務，但必須明確地擷取和套用服務的色彩標示器，而且重繪其本身的文件檢視。

 若要這樣做，非核心編輯器必須：

1.  取得語言服務的色彩標示器物件 (它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>)。 VSPackage 會藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>語言服務的介面上的方法。

2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法來要求特定的一段文字會以色彩標示。

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法會傳回值的陣列，一個用於每個字母的文字範圍以色彩標示。 它也可以識別文字範圍，為特定類型的色彩項目，例如註解、 關鍵字或資料類型。

3.  使用所傳回的顏色標示資訊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>重新繪製，並顯示其文字。

> [!NOTE]
> 除了使用語言服務的色彩標示器，VSPackage 可以選擇使用一般用途的 Visual Studio 環境 SDK 文字著色機制。 如需有關這項機制的詳細資訊，請參閱[使用字型和色彩](../extensibility/using-fonts-and-colors.md)。

## <a name="see-also"></a>另請參閱

- [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [實作語法著色](../extensibility/internals/implementing-syntax-coloring.md)
- [如何︰使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [自訂可設定色彩的項目](../extensibility/internals/custom-colorable-items.md)