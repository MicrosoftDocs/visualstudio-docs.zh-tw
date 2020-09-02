---
title: 宣告屬性視窗選取範圍追蹤 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002449"
---
# <a name="announcing-property-window-selection-tracking"></a>宣告屬性視窗選取範圍追蹤
如果您想要使用 [ **屬性** ] 視窗或 [ **屬性** ] 頁面（例如，您想要查看其屬性的表單、文字或選取專案），則必須具備協調選取範圍的完整知識。 例如，您必須知道您是否有單一選取或多重選取專案。 然後，您必須使用介面，在 IDE 中宣告您的選取類型 (單一或多個) <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 。 此介面提供 [ **屬性** ] 視窗所需的資訊。  
  
### <a name="to-announce-selection-to-the-environment"></a>宣佈對環境的選擇  
  
1. `QueryInterface`的呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 。  
  
    1. 若要這樣做，請使用在建立時傳遞給視圖的網站指標。  
  
    2. `QueryService`從服務的視圖呼叫 `SID_STrackSelection` 。  
  
         這會傳回的指標 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 。  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>每次選取變更時呼叫方法，然後將指標傳遞至實的物件 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 。  
  
     選取容器物件可以使用單一或多個選取專案，並在物件中包含選取專案資訊 `IDispatch` 。 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 方法會通知 [ **屬性** ] 視窗選取範圍已變更。 [ **屬性** ] 視窗接著會使用中的物件 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 來判斷是否已發生單一或多個選取專案，以及實際的物件選項。  
  
     如果您指定多個選取專案，則 [ **屬性** ] 視窗會尋找物件的通用屬性之間的交集。 如果您指定單一物件選取專案，[ **屬性** ] 視窗就會顯示一個物件的所有屬性。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../extensibility/internals/extending-properties.md)   
 [屬性頁](../extensibility/internals/property-pages.md)