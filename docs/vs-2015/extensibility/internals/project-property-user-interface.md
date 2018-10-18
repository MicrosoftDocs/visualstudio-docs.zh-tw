---
title: 專案屬性使用者介面 |Microsoft Docs
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
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57c9bb58ab1d930c6beb2e1cfa9cc4b9b6ec52fc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172285"
---
# <a name="project-property-user-interface"></a>專案屬性使用者介面
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案子類型可以使用專案中的項目**屬性頁** 對話方塊中所提供的基底的專案中，隱藏或做唯讀控制項和整個網頁提供，或將專案子類型專用頁面新增至**屬性頁** 對話方塊。  
  
## <a name="extending-the-project-property-dialog-box"></a>擴充專案的 [屬性] 對話方塊  
 專案子類型會實作 automation 擴充項和專案設定瀏覽物件。 這些擴充項實作<xref:EnvDTE.IFilterProperties>介面，可讓特定的屬性，隱藏或唯讀狀態。 **屬性頁**對話方塊中的基底的專案中，藉由將基底的專案中，會接受由 Automation 擴充項的篩選。  
  
 擴充程序**專案屬性** 對話方塊中所述：  
  
-   基底的專案從專案子類型擷取的擴充項，藉由實作<xref:EnvDTE80.IInternalExtenderProvider>介面。 瀏覽、 專案自動化和基底的所有專案的專案設定瀏覽物件會實作這個介面。  
  
-   實作<xref:EnvDTE80.IInternalExtenderProvider>給專案瀏覽的物件和專案自動化物件委派到<xref:EnvDTE80.IInternalExtenderProvider>實作專案子類型的彙總工具 (也就是它們`QueryInterface`如<xref:EnvDTE80.IInternalExtenderProvider>上<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>專案物件）。  
  
-   基底的專案設定瀏覽的物件也會實作<xref:EnvDTE80.IInternalExtenderProvider>直接連接 Automation 擴充項專案子類型的組態物件中。 它的實作會委派給<xref:EnvDTE80.IInternalExtenderProvider>專案子類型的彙總工具所實作的介面。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>藉由將專案設定瀏覽物件，傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>也藉由將專案設定瀏覽物件，傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>物件。  
  
-   專案子類型可以決定適當的 Catid 不同的可擴充物件的基底的專案，在執行階段擷取下列<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>值：  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 若要判斷專案範圍的 Catid，專案子類型擷取的上述屬性<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>從`VSITEMID``typedef`。 專案子類型也可以控制哪些**屬性頁**對話方塊頁面會顯示專案的組態相依和獨立的設定。 某些專案子類型可能需要移除內建的頁面，並加入專案子類型的特定頁面。 若要啟用此功能，受管理的用戶端專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>方法的下列屬性：  
  
-   `VSHPROPID_PropertyPagesCLSIDList` -設定獨立屬性頁 Clsid 的以分號分隔清單。  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —` 組態相依屬性頁 Clsid 的以分號分隔的清單。  
  
 因為專案子類型的彙總<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件，則可以覆寫的定義，這些屬性，以控制哪些**屬性頁**對話方塊會顯示。 專案子類型可以擷取這些屬性從內部的基底專案然後新增或視需要移除 Clsid。  
  
 新加入的專案子類型的屬性頁會散發專案設定瀏覽物件的基底專案的實作。 此專案設定瀏覽物件支援 Automation 擴充項。 如需有關 AutomationExtenders 的詳細資訊，請參閱[實作和使用 Automation 擴充項](http://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356)。 專案子類型呼叫所實作的屬性頁<xref:EnvDTE.Project.Extender%2A>擷取擴充的基底專案的 [設定] 瀏覽物件自己專案子類型設定瀏覽物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE.IFilterProperties>   
 [屬性頁對話方塊](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)

