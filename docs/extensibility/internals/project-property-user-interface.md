---
title: "專案屬性的使用者介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36d8f6afebf09d4efd176ba204dcc6f485a56124
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="project-property-user-interface"></a>專案屬性的使用者介面
專案子類型可以使用專案中的項目**屬性頁**對話方塊所提供的基底的專案，隱藏或做唯讀控制項和整個網頁提供，或將專案子類型特有的頁面加入至**屬性頁** 對話方塊。  
  
## <a name="extending-the-project-property-dialog-box"></a>擴充專案的 [屬性] 對話方塊  
 專案子類型會實作 automation 擴充項和瀏覽專案組態的物件。 這些擴充項實作<xref:EnvDTE.IFilterProperties>介面，以隱藏或唯讀狀態，讓特定的屬性。 **屬性頁**對話方塊的基底的專案，藉由基底的專案中，接受由 Automation 擴充項的篩選。  
  
 延伸的程序**專案屬性**對話方塊如下所述：  
  
-   基底的專案擷取的擴充項的專案子類型藉由實作<xref:EnvDTE80.IInternalExtenderProvider>介面。 瀏覽、 專案自動化和基底的所有專案的專案組態瀏覽的物件會實作這個介面。  
  
-   實作<xref:EnvDTE80.IInternalExtenderProvider>針對專案瀏覽的物件和專案 automation 物件委派給<xref:EnvDTE80.IInternalExtenderProvider>實作專案子類型的彙總工具 (也就是它們`QueryInterface`如<xref:EnvDTE80.IInternalExtenderProvider>上<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>專案物件）。  
  
-   基底的專案設定瀏覽的物件也會實作<xref:EnvDTE80.IInternalExtenderProvider>專案子類型的組態物件從 Automation 擴充項中直接連接。 它的實作會委派至<xref:EnvDTE80.IInternalExtenderProvider>專案子類型的彙總工具所實作的介面。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>專案設定瀏覽物件，傳回實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>也由專案組態瀏覽物件，傳回實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>物件。  
  
-   專案子類型可以擷取下列來判斷基底的專案，在執行階段的各種可擴充物件的適當項 Catid<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>值：  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 若要判斷專案範圍項 Catid，專案子類型擷取的上述屬性<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>從`VSITEMID``typedef`。 專案子類型也可能想要控制哪個**屬性頁**對話方塊頁面會顯示專案中，獨立設定和組態相關。 某些專案子類型可能需要移除內建網頁，並加入專案子類型的特定頁面。 若要啟用此功能，受管理的用戶端專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>方法的下列屬性：  
  
-   `VSHPROPID_PropertyPagesCLSIDList`— 組態無關的屬性頁 Clsid 的分號分隔清單。  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`組態相關的屬性頁 Clsid 以分號分隔清單。  
  
 因為專案子類型的彙總<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件，它可以覆寫這些屬性，以控制哪個定義**屬性頁**對話方塊會顯示。 專案子類型可以擷取這些屬性從內部的基底專案然後加入或視需要移除的 Clsid。  
  
 新加入的專案子類型的屬性頁的基底專案實作散發專案設定瀏覽的物件。 這個專案設定瀏覽物件支援 Automation 擴充項。 如需有關 AutomationExtenders 的詳細資訊，請參閱[實作和使用 Automation 擴充項](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)。 專案子類型呼叫所實作的屬性頁<xref:EnvDTE.Project.Extender%2A>擷取他們自己專案子類型組態瀏覽物件擴充的基底的專案設定瀏覽的物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE.IFilterProperties>   
 [屬性頁對話方塊](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)