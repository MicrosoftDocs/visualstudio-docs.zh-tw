---
title: 宣告屬性視窗中選取項目追蹤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002449"
---
# <a name="announcing-property-window-selection-tracking"></a>宣告屬性視窗選取範圍追蹤
如果您想要使用**屬性** 視窗或**屬性**頁面，例如，表單、 文字或選取範圍，您想要查看屬性，則您必須將完全了解如何的您協調選取項目。 例如，您必須知道您是否擁有單一選取或是多重選取。 接著，您需要宣布 IDE 使用您選取項目類型 （單一或多個）<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面。 這個介面會提供所需的資訊**屬性**視窗。  
  
### <a name="to-announce-selection-to-the-environment"></a>宣佈環境的選取範圍  
  
1. 呼叫`QueryInterface`針對<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>。  
  
    1. 若要這樣做，請使用站台指標建立時傳遞至檢視。  
  
    2. 呼叫`QueryService`的檢視從`SID_STrackSelection`服務。  
  
         這會傳回的指標<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>方法，每次變更您的選擇，並將傳遞指標給實作的物件<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  
  
     選取項目容器物件可以使用單一或多個選取項目，並包含中的選取項目資訊`IDispatch`物件。 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>方法會通知**屬性**選取項目已變更的視窗。 **屬性**接著在使用物件的視窗<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>來判斷是否有發生單一或多個選取項目，以及實際的物件選取項目為何。  
  
     如果您指定多個選取的項目，則**屬性**視窗中尋找之物件的通用屬性的交集。 如果您指定單一物件的選取項目，則**屬性**視窗會顯示所有的一個物件的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../extensibility/internals/extending-properties.md)   
 [屬性頁](../extensibility/internals/property-pages.md)