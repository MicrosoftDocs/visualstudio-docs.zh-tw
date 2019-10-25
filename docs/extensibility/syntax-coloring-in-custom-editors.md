---
title: 自訂編輯器中的語法著色 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302f463d93776d17be0251e6194375c15adc19
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718760"
---
# <a name="syntax-coloring-in-custom-editors"></a>自訂編輯器中的語法著色
Visual Studio 環境 SDK 編輯器，包括核心編輯器，請使用語言服務來識別特定的語法專案，並以指定的檔視圖色彩來顯示它們。

## <a name="colorization-requirements"></a>顏色標示需求
 所有執行語言服務著色器的編輯器都必須：

1. 使用物件來執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 來管理要以色彩標示的文字，以及執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 以提供文字檔視圖的物件。

2. 使用語言服務的識別 GUID 來查詢 VSPackage 的服務提供者，以取得特定語言服務的介面。

3. 呼叫執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>之物件的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 方法。 這個方法會將語言服務與 VSPackage 用來管理要以色彩標示之文字的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 實關聯。

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>語言服務著色器的核心編輯器使用方式
 當具有著色器的語言服務是由核心編輯器的實例取得時，語言服務的著色器會自動進行文字剖析和轉譯，而不需要在您的元件上進行任何進一步的介入。

 IDE 透明：

- 視需要呼叫著色器，以在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 的執行中新增或修改文字時進行剖析和分析。

- 確保會使用著色器所傳回的資訊來更新和重新繪製由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 執行所提供的檔視圖所提供的顯示。

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>語言服務著色器的非核心編輯器使用方式
 非核心編輯器實例也可以使用語言服務的語法顏色標示服務，但它們必須明確地取出和套用服務的著色器，並自行重新繪製其檔視圖。

 若要這麼做，非核心編輯器必須：

1. 取得語言服務的著色器物件（其會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>）。 VSPackage 會藉由在語言服務的介面上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 方法來執行這項操作。

2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法，要求以色彩標示特定範圍的文字。

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法會傳回值的陣列，這是以色彩標示的文字範圍中的每個字母各一個。 它也會將文字範圍識別為特定類型的可設定色彩專案，例如批註、關鍵字或資料類型。

3. 使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 所傳回的顏色標示資訊來重新繪製並顯示其文字。

> [!NOTE]
> 除了使用語言服務的著色器之外，VSPackage 還可以選擇使用一般用途的 Visual Studio 環境 SDK 文字著色機制。 如需此機制的詳細資訊，請參閱[使用字型和色彩](../extensibility/using-fonts-and-colors.md)。

## <a name="see-also"></a>請參閱

- [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [實作語法著色](../extensibility/internals/implementing-syntax-coloring.md)
- [如何︰使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [自訂可設定色彩的項目](../extensibility/internals/custom-colorable-items.md)