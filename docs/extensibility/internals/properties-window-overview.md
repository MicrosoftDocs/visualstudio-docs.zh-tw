---
title: "屬性視窗概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0094accca0feb026fca02c78bf6e86fe512ce981
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-overview"></a>屬性視窗概觀
**屬性**視窗用來顯示在 windows 中提供的兩個主要類型中選取物件的屬性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 這兩種 windows 類型如下：  
  
-   例如方案總管、 類別檢視和物件瀏覽器工具視窗  
  
-   包含這類的編輯器和 form 設計工具、 以及 XML 編輯器、 HTML 編輯器的設計工具的文件視窗  
  
## <a name="using-the-properties-window"></a>使用 [屬性] 視窗  
 **屬性**視窗會顯示單一或多個選取的項目屬性。 如果選取多個項目，則會顯示所有選定物件的所有屬性的交集。  
  
 表單 [設計] 視窗或 HTML 編輯器中使用 COM + 中繼資料內所選物件的相關事件會顯示在**屬性**視窗。 例如，您可以選取一個按鈕，並顯示其相關聯的事件，例如`OnClick`事件，可以連結到該按鈕。  
  
 顯示在事件**屬性**視窗主要搭配繫結至程式碼的物件。 如果您正在編輯的檔案格式，但是沒有任何項目如何處理程式碼，都不會有任何事件。 事件只會顯示在**屬性**執行程式碼和特定物件相關聯的特定事件之間的繫結時，視窗。 這個範例會在所選的物件，該物件會在啟動時執行的程式碼。  
  
 下表列出所使用的主要介面**屬性**視窗。  
  
|介面名稱|說明|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|提供的類別清單**屬性**視窗，並將每一個屬性對應至類別目錄。|  
|[IDispatch 介面](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|公開物件的方法與屬性，以程式設計的工具和其他支援自動化的應用程式。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供省略符號 （...） 按鈕，稱為*建造商*，開啟強制回應對話方塊視窗物件本身所實作。 使用者在文字欄位中不容易輸入值時使用。 例如，可能會用來開啟 色彩選擇器，為您決定的 RGB 值。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供用來更新中所顯示資訊的物件的存取權**屬性**視窗。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>是由 Vspackage 實作每個視窗，其中包含要顯示的相關屬性與可選取物件。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供介面和結構的欄位類型的物件，例如使用方法的相關的資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|可讓 Vspackage 接收通知的選取範圍的事件，並擷取目前的專案階層架構、 項目、 項目值和命令 UI 內容的相關資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|提供存取多重選取的環境。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用來提供當地語系化的名稱顯示在某些屬性上**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知目前的選取項目，項目值或命令 UI 內容之變更的已註冊的 Vspackage。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|通知目前選取範圍變更的環境，並提供新的選取項目與相關的階層和項目資訊的存取權。|  
  
 如需進一步資訊`IDispatch`，請參閱 MSDN library。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)   
 [屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)