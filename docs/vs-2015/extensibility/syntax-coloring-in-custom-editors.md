---
title: 自訂編輯器中的語法著色 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d690afae8d546b4597159bfd094a7a21d2528780
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945248"
---
# <a name="syntax-coloring-in-custom-editors"></a>自訂編輯器中的語法著色
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 環境 SDK 編輯器，包括核心編輯器中，找出特定的語法項目，並顯示，且指定的色彩，給定文件檢視使用的語言服務。  
  
## <a name="colorization-requirements"></a>顏色標示需求  
 所有編輯器實作語言服務的色彩標示器都必須：  
  
1.  使用物件，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>來管理會以色彩標示的文字和物件，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>提供文件檢視的文字。  
  
2.  取得特定語言服務的介面，藉由查詢 VSPackage 的服務提供者使用的語言服務的 GUID。  
  
3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法的物件，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。 這個方法將相關聯的語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>VSPackage 會使用來管理要會以色彩標示文字的實作。  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>語言服務的色彩標示器核心編輯器使用方式  
 當核心編輯器、 剖析和轉譯的文字語言服務的色彩標示器的執行個體所取得的色彩標示器的語言服務會自動進行而不需要採取任何進一步介入。  
  
 IDE 以透明的方式：  
  
-   呼叫以剖析和分析文字加入或修改在實作中的色彩標示器視<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。  
  
-   可確保所提供的文件檢視所提供的顯示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>實作會更新並重新繪製使用色彩標示器所傳回的資訊。  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>語言服務的色彩標示器的非核心編輯器使用方式  
 非核心編輯器執行個體也可以使用語言服務的語法顏色標示服務，但是必須明確地擷取和適用於服務的色彩標示器，並重新繪製其本身的文件檢視。  
  
 若要這樣做需要的非核心編輯器：  
  
1.  取得語言服務的色彩標示器物件 (它會實作`T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>)。 VSPackage 的做法是呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>語言服務的介面上的方法。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法來要求特定的一段文字會以色彩標示。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法會傳回值的陣列，一個用於文字中的每個字母跨越以色彩標示。 它也會識別文字範圍，為特定類型的可設定色彩的項目，例如註解、 關鍵字或資料類型。  
  
3.  使用所傳回的顏色標示資訊<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>重新繪製，並顯示其文字。  
  
> [!NOTE]
>  除了使用語言服務的色彩標示器，VSPackage 可以選擇使用一般用途的 Visual Studio 環境 SDK 文字著色機制。 如需有關這項機制的詳細資訊，請參閱 <<c0> [ 使用的字型和色彩](../extensibility/using-fonts-and-colors.md)。  
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法著色](../extensibility/internals/implementing-syntax-coloring.md)   
 [如何：使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自訂可設定色彩的項目](../extensibility/internals/custom-colorable-items.md)
