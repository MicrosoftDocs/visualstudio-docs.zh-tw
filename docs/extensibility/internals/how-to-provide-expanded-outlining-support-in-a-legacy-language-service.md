---
title: "提供支援的語言服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fd353e39e3e3edbdbdb929fa16abb74126dbbc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>如何： 擴充大綱中提供支援舊版語言服務
有兩個選項，來擴充您的語言支援的大綱支援**摺疊至定義**命令。 您可以將控制編輯器的大綱區域，並將用戶端控制大綱區域。  
  
## <a name="adding-editor-controlled-outline-regions"></a>加入控制編輯器的大綱區域  
 使用此方式來建立大綱區域，然後讓編輯器中，以處理是否在區域會展開，摺疊，等等。 提供大綱支援兩個選項，這個選項是最穩定。 針對這個選項，您必須建立新的大綱區域某段指定的文字使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>。 此區域建立之後，其行為被控制編輯器。 您可以使用下列程序來實作控制編輯器的大綱區域。  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>若要實作一個控制編輯器的大綱區域  
  
1.  呼叫`QueryService`的<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     這將指標傳回至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>傳遞給指定的文字緩衝區的指標。 這將指標傳回至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>緩衝區的物件。  
  
3.  呼叫<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>加入一個或多新一次大綱區域。  
  
     這個方法可讓您指定的大綱、 移除或保留，保留現有的大綱區域是否和大綱區域是展開還是摺疊，只要預設的文字範圍。  
  
## <a name="adding-client-controlled-outline-regions"></a>新增用戶端控制大綱區域  
 使用這個方法來實作，用戶端控制 （或智慧） 大綱類似使用[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]語言服務。 語言服務，可管理它自己的大綱監視文字緩衝區內容，才能終結舊的大綱區域，他們就會變成無效時，並視需要建立新的大綱區域。  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>若要實作的用戶端控制大綱區域  
  
1.  呼叫`QueryService`如<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。 這將指標傳回至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>傳遞給指定的文字緩衝區的指標。 這會決定是否隱藏的文字工作階段已經存在的緩衝區。  
  
3.  如果文字工作階段已經存在，則您不需要建立一個，以及一個指向現有指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件傳回。 使用這個指標來列舉及建立大綱區域。 否則，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>建立隱藏的文字的工作階段緩衝區。 指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件傳回。  
  
    > [!NOTE]
    >  當您呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>，您可以指定隱藏的文字用戶端 (也就是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>物件)。 此用戶端會通知您時隱藏文字或展開或摺疊，只要使用者大綱區域。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>結構) 參數： 指定的值為<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>中`iType`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構，以指出您要建立一個大綱區域，而不是隱藏的區域。 指定區域是用戶端控制，或在控制編輯器`dwBehavior`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。 智慧大綱實作可以包含混合的編輯器和用戶端控制大綱區域。 指定的大綱區域摺疊時，例如"…"，在顯示的橫幅文字`pszBanner`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。 編輯器的隱藏區域的預設橫幅文字是"…"。