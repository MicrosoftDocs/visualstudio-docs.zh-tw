---
title: 屬性 Window Fields and Interfaces |Microsoft Docs
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
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a413fd1787e4197cf46de6936523ef576016a37
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300309"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

若要判斷哪些資訊會顯示在選取的模型**屬性**視窗根據在 IDE 中具有焦點的視窗。 每個視窗中，然後選取視窗內的物件可以有其推送至全域範圍內容的選取項目內容物件。 該視窗具有焦點時，環境會更新全域選取範圍內容視窗框架的值。 當焦點變更時，因此會選取範圍內容。  
  
## <a name="tracking-selection-in-the-ide"></a>追蹤在 IDE 中的選取範圍  
 視窗框架或 IDE 中，所擁有的網站有一個稱為服務<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。 下列步驟示範如何變更在 [選取項目，使用者將焦點變更為另一個開啟的視窗，或選取不同的專案項目中所造成**方案總管] 中**，實作變更中顯示的內容**屬性**視窗。  
  
1.  VSPackage 是 value 中選取的視窗呼叫所建立的物件<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>能夠<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>叫用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2.  選取容器，所選取的視窗中，提供建立它自己<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。 當選取範圍的 VSPackage 會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>通知任何接聽程式，在環境中，包括**屬性**視窗中，變更。 它也提供新的選取範圍相關的階層] 和 [項目資訊的存取權。  
  
3.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>並將其傳遞中選取的階層項目`VSHPROPID_BrowseObject`參數會填入<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。  
  
4.  物件衍生自[IDispatch 介面](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)會傳回<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>要求的項目，且環境會包裝到<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>（請參閱下一個步驟）。 如果呼叫失敗，環境會第二個呼叫`IVsHierarchy::GetProperty`，並選取容器<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>的階層項目或項目提供。  
  
     VSPackage 不會建立的專案<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因為環境提供視窗 VSPackage 實作它 (例如**方案總管 中**) 建構<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代替它。  
  
5.  環境叫用的方法<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>若要取得根據物件`IDispatch`介面，以填入**屬性**視窗。  
  
 中的值時**屬性** 視窗變更時，實作 Vspackage`IVsTrackSelectionEx::OnElementValueChangeEx`和`IVsTrackSelectionEx::OnSelectionChangeEx`來報告變更的項目值。 環境再叫用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>或是<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>保持中顯示的資訊**屬性**視窗同步處理的屬性值。 如需詳細資訊，請參閱 <<c0> [ 更新 [屬性] 視窗中的屬性值](../../misc/updating-property-values-in-the-properties-window.md)。  
  
 除了選取不同的專案項目**方案總管 中**顯示該項目的相關的屬性，您也可以選擇從使用下拉式清單上可用的表單或文件視窗內的不同物件**屬性**視窗。 如需詳細資訊，請參閱 <<c0> [ 屬性視窗的物件清單](../../extensibility/internals/properties-window-object-list.md)。  
  
 您可以變更資訊會顯示在的方式**屬性**成類別目錄，從依字母順序排列的視窗方格，如果有的話，則您也可以上適當的按鈕，即可開啟所選物件的屬性頁**屬性**視窗。 如需詳細資訊，請參閱 <<c0> [ 屬性視窗的按鈕](../../extensibility/internals/properties-window-buttons.md)並[屬性頁](../../extensibility/internals/property-pages.md)。  
  
 最後，底部**屬性** 視窗也包含在選取的欄位的說明**屬性**視窗方格。 如需詳細資訊，請參閱 <<c0> [ 從 [屬性] 視窗取得欄位描述](../../misc/getting-field-descriptions-from-the-properties-window.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)

