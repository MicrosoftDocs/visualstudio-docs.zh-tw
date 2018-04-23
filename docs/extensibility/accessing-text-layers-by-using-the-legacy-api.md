---
title: 使用舊版 API 存取文字層 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d21b31940f1e1ebca767b9d3f0cf5ab802181bda
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>使用舊版 API 存取文字圖層
文字層通常會封裝文字配置的某些層面。 比方說，「 函式-一次 「 圖層會隱藏的文字之前和之後包含插入號 （文字插入點） 的函式。  
  
 緩衝區與檢視中，位於文字層，而且會修改此檢視會看到緩衝區的內容的方式。  
  
## <a name="text-layer-information"></a>文字層資訊  
 下列清單描述文字圖層中的運作方式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   文字層中的文字可以裝飾的語法著色和標記。  
  
-   您目前無法實作您自己的圖層。  
  
-   圖層會公開<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，其衍生自<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>。 文字緩衝區本身也會實作為圖層，可讓檢視，以多型方式處理基礎的圖層中。  
  
-   檢視和緩衝區之間，可能位於任何數目的層。 每個圖層只會處理它下, 一層，而檢視處理大部分的最高的層級。 （檢視沒有緩衝區的一些資訊。）  
  
-   圖層可能會影響其下方的圖層。 它不會影響超出源自標準事件上面的圖層。  
  
-   在編輯器中，隱藏的文字、 綜合的文字和自動換行會實作為圖層。 您可以實作隱藏和綜合文字而不直接與圖層的互動。 如需詳細資訊，請參閱[舊版語言服務中的大綱](../extensibility/internals/outlining-in-a-legacy-language-service.md)和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>。  
  
-   每個文字圖層的透過公開自己區域座標系統<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>介面。 行換行圖層，例如，可能包含兩行，而基礎文字緩衝區可能包含只有一行。  
  
-   檢視與外界溝通的圖層透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>介面。 您可以使用此介面來協調檢視緩衝區座標的座標。  
  
-   任何圖層例如綜合文字層源自文字必須提供本機實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>。  
  
-   除了<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，文字層必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>引發的事件和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>介面。  
  
## <a name="see-also"></a>另請參閱  
 [自訂編輯器中著色的語法](../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用文字標記與舊版應用程式開發介面](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [使用舊版 API 自訂編輯器控制項和功能表](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)