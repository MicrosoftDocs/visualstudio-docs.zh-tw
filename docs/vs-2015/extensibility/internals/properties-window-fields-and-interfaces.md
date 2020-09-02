---
title: 屬性視窗欄位和介面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700828"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

用來決定要在 [ **屬性** ] 視窗中顯示哪些資訊的模型是根據焦點在 IDE 中的視窗。 在選取的視窗內，每個視窗和物件都可以將其選取內容物件推送至全域選取內容。 當視窗具有焦點時，環境會以視窗框架中的值來更新全域選取內容。 當焦點變更時，就會進行選取內容。  
  
## <a name="tracking-selection-in-the-ide"></a>在 IDE 中追蹤選取專案  
 IDE 所擁有的視窗框架或網站有一個稱為的服務 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 。 下列步驟顯示如何將焦點變更為另一個開啟的視窗，或在 **方案總管**中選取不同的專案專案，以變更 [ **屬性** ] 視窗中顯示的內容。  
  
1. 由您的 VSPackage 所建立的物件，該物件位於所選視窗呼叫中，並 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 具有 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 。  
  
2. 選取的視窗所提供的選取專案容器會建立自己的 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 物件。 當選取範圍變更時，VSPackage 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 以在環境中通知任何接聽程式，包括 **屬性** 視窗在內的變更。 它也可讓您存取與新選項相關的階層和專案資訊。  
  
3. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 並傳遞給它。參數中選取的階層專案會 `VSHPROPID_BrowseObject` 填入 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 物件。  
  
4. 針對要求的專案，會傳回衍生自 [IDispatch 介面](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) 的物件 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ，且環境會將它包裝成 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (查看下列步驟) 。 如果呼叫失敗，則環境會進行第二個呼叫 `IVsHierarchy::GetProperty` ，並將階層 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 專案或專案提供的選取容器傳遞給它。  
  
    您的專案 VSPackage 不會建立， <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 因為環境提供的視窗 VSPackage 會執行它 (例如， **方案總管**) <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 代表它的結構。  
  
5. 環境會叫用的方法 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ，以根據 `IDispatch` 要在 [ **屬性** ] 視窗中填入的介面來取得物件。  
  
   當 [ **屬性** ] 視窗中的值變更時，vspackage 會執行 `IVsTrackSelectionEx::OnElementValueChangeEx` ，並將 `IVsTrackSelectionEx::OnSelectionChangeEx` 變更回報給元素值。 然後環境會叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 用或，讓 [ **屬性** ] 視窗中顯示的資訊與屬性值同步。 如需詳細資訊，請參閱在 [屬性視窗中更新屬性值](../../misc/updating-property-values-in-the-properties-window.md)。  
  
   除了在 **方案總管** 中選取不同的專案專案，以顯示與該專案相關的屬性之外，您也可以使用 [ **屬性** ] 視窗上提供的下拉式清單，從表單或文件視窗中選擇不同的物件。 如需詳細資訊，請參閱 [屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)。  
  
   您可以將 [ **屬性** ] 視窗方格中的資訊顯示方式從字母順序變更為類別，如果有的話，您也可以按一下 [ **屬性** ] 視窗上的適當按鈕，開啟所選物件的屬性頁。 如需詳細資訊，請參閱 [屬性視窗按鈕](../../extensibility/internals/properties-window-buttons.md) 和 [屬性頁](../../extensibility/internals/property-pages.md)。  
  
   最後，[ **屬性** ] 視窗的底部也包含 [ **屬性** ] 視窗方格中所選取之欄位的描述。 如需詳細資訊，請參閱 [從屬性視窗取得欄位描述](../../misc/getting-field-descriptions-from-the-properties-window.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)
