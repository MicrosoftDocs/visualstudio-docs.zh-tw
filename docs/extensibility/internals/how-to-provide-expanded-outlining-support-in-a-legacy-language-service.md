---
title: 提供語言服務中的支援 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a26d9dbc67f502e30968f3db89834b12e02ae3e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965547"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>HOW TO：提供展開大綱的支援，在舊版語言服務
有兩個選項用於擴充大綱的支援，您只能支援的語言**摺疊至定義**命令。 您可以將控制編輯器的大綱區域，並將用戶端控制的大綱區域。  
  
## <a name="adding-editor-controlled-outline-regions"></a>新增控制編輯器的大綱區域  
 使用此方法來建立一個大綱區域，然後可讓編輯器來處理是否已展開的區域，摺疊，等等。 兩個選項提供大綱的支援，此選項是最不穩固。 針對這個選項，您必須建立新的外框區域的文字所使用的指定範圍內<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>。 此區域建立之後，編輯器會控制其行為。 您可以使用下列程序來實作編輯器控制大綱區域。  
  
### <a name="to-implement-an-editor-controlled-outline-region"></a>若要實作一個控制編輯器的大綱區域  
  
1.  呼叫`QueryService`的 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     這會傳回的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，傳入指定的文字緩衝區的指標。 這會傳回的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>緩衝區的物件。  
  
3.  呼叫<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>加入一個或多新增一次大綱區域。  
  
     這個方法可讓您指定的外框、 移除或保留，現有的大綱區域是否和外框區域是否為展開或摺疊的預設值的文字範圍。  
  
## <a name="add-client-controlled-outline-regions"></a>新增用戶端控制的大綱區域  
 使用這個方法，來實作，用戶端控制 （或智慧型） 大綱類似，供[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]語言服務。 若要摧毀舊的大綱區域，當它們變成無效時，並視需要建立新的大綱區域，語言服務，可管理它自己的大綱監視文字緩衝區內容。  
  
### <a name="to-implement-a-client-controlled-outline-region"></a>若要實作的用戶端控制的大綱區域  
  
1.  呼叫`QueryService`針對<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。 這會傳回的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>，傳入指定的文字緩衝區的指標。 這會決定是否隱藏的文字的工作階段已存在的緩衝區。  
  
3.  如果文字工作階段已經存在，則您不需要建立一個，並指向現有的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>會傳回物件。 使用此指標來列舉及建立大綱區域。 否則，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>建立隱藏的文字的工作階段緩衝區。 指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>會傳回物件。  
  
    > [!NOTE]
    >  當您呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>，您可以指定隱藏的文字，用戶端 (也就是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>物件)。 此用戶端通知時隱藏的文字，或是大綱區域為展開或摺疊，只要使用者。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>結構) 參數：指定的值為<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>中`iType`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構，以指出您要建立大綱區域，而不是隱藏的區域。 指定的區域是用戶端控制，或以控制編輯器`dwBehavior`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。 智慧型大綱實作可以包含各種編輯器和用戶端控制大綱區域。 指定大綱區域摺疊時，例如 "..."，在顯示的橫幅文字`pszBanner`隸屬<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。 編輯器的預設橫幅文字的隱藏區域為"..."。