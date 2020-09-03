---
title: 使用舊版 API 存取文字層 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148016"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>使用舊版 API 存取文字圖層
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字層通常會封裝一些文字版面配置的層面。 例如，「一次性函式」層會隱藏包含插入號 (文字插入點) 的函式之前和之後的文字。  
  
 文字圖層位於緩衝區和視圖之間，它會修改視圖看到緩衝區內容的方式。  
  
## <a name="text-layer-information"></a>文字層資訊  
 下列清單描述文字圖層在中的運作方式 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ：  
  
- 文字圖層中的文字可以使用語法著色和標記來裝飾。  
  
- 您目前無法執行自己的圖層。  
  
- 圖層 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> 會公開，其衍生自 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 。 文字緩衝區本身也會實作為圖層，可讓視圖處理基礎圖層的多型。  
  
- 在視圖與緩衝區之間可能有任意數目的層級。 每一層都只會處理其下的圖層，而視圖主要會處理最上層的層級。  (view 的確有一些有關緩衝區的資訊 )   
  
- 圖層只會影響其下的層級。 它不會影響超出原始標準事件的層級。  
  
- 在編輯器中，隱藏文字、綜合文字和自動換行都會實作為圖層。 您可以執行隱藏和綜合文字，而不需要直接與圖層互動。 如需詳細資訊，請參閱 [在舊版語言服務中的大綱](../extensibility/internals/outlining-in-a-legacy-language-service.md) 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> 。  
  
- 每個文字層都有自己的本機座標系統，會透過 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> 介面公開。 例如，換行圖層可能包含兩行，而基礎文字緩衝區可能只包含一行。  
  
- 此視圖會透過介面與分層通訊 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> 。 使用這個介面可協調具有緩衝區座標的視圖座標。  
  
- 任何圖層（例如，產生文字的綜合文字層）都必須提供的本機實作為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> 。  
  
- 此外 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> ，文字層必須 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 在介面中執行和引發事件 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> 。  
  
## <a name="see-also"></a>另請參閱  
 [自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)   
 [搭配舊版 API 使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [使用舊版 API 自訂編輯器控制項及功能表](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
