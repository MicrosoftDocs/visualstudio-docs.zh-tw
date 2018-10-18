---
title: 使用舊版 API 存取文字圖層 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4f60a5b385ee24f2855e67e92f8a563d2603be0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183530"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>使用舊版 API 存取文字圖層
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字層通常會封裝在某種程度的文字版面配置。 比方說，「 函式-一次 「 圖層會隱藏文字之前和之後包含文字插入點 （caret) 的函式。  
  
 文字層位於緩衝區和檢視之間，它會修改此檢視會看到緩衝區的內容的方式。  
  
## <a name="text-layer-information"></a>文字層資訊  
 下列清單描述文字圖層中的運作方式[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
-   使用語法著色和標記，可以裝飾文字圖層中的文字。  
  
-   您目前無法實作您自己的層級。  
  
-   圖層會公開<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，其係衍生自<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>。 文字緩衝區本身也會實作成圖層，可讓多型方式處理基礎層的檢視。  
  
-   檢視與緩衝區之間，可能位於任何數目的層。 每個圖層只會處理它下, 一層，而檢視處理大部分的最上層的圖層。 （檢視沒有緩衝區的一些資訊。）  
  
-   圖層可能會影響其下方的圖層。 它不會影響其上方的圖層，超出原始標準事件。  
  
-   在編輯器中，隱藏的文字、 綜合的文字和自動換行會實作為圖層。 您可以實作隱藏與綜合文字而不需要直接互動的層級。 如需詳細資訊，請參閱 <<c0> [ 舊版語言服務中的大綱](../extensibility/internals/outlining-in-a-legacy-language-service.md)和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>。  
  
-   每個文字圖層有它自己透過公開的區域座標系統<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>介面。 換行的線條圖層，例如，可能包含兩行而基礎的文字緩衝區可能會包含只有一行。  
  
-   檢視與外界溝通的圖層透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>介面。 您可以使用這個介面來協調緩衝區座標檢視座標表示。  
  
-   任何圖層等來源文字的綜合文字圖層必須提供本機實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>。  
  
-   除了<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>，文字圖層必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>引發的事件和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>介面。  
  
## <a name="see-also"></a>另請參閱  
 [自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [使用舊版 API 自訂編輯器控制項及功能表](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)

