---
title: 屬性和方法擴充的專案子類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23510ffbb42e0c0c37c07e0ee80ae15f99e5df00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>屬性和擴充的專案子類型的方法
專案子類型都有大量的電力來影響專案的行為，因為它會建構為彙總工具的基底的專案。 本節摘要說明的某些功能，可增強或修改專案子類型。  
  
## <a name="features-gained-by-aggregation"></a>彙總所得到的功能  
 下表摘要說明的許多方法可彙總來覆寫基底的專案中的專案子類型。  
  
|覆寫彙總方法|專案子類型|  
|---------------------------------------|---------------------|  
|從<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|可讓專案子類型<br /><br /> -變更標題和圖示的專案節點。<br />-完全覆寫專案`Browse`物件。<br />-控制是否可以重新命名專案。<br />控制排序次序。<br />控制動態說明的使用者內容。|  
|從<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|可讓專案子類型，來控制有哪些內容的服務可供設計工具和編輯器。|  
|從<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|可讓專案子類型<br /><br /> -參與專案命令的命令路由。<br />新增、 移除或停用環境命令的專案和方案總管 中的命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|可讓專案子類型來篩選使用者會看到在**加入新項目** 對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|可讓專案子類型<br /><br /> -判斷指定的檔案副檔名的預設產生器。<br />-人類可讀取的產生器名稱對應至 COM 物件。|  
  
## <a name="properties-used-by-project-subtypes"></a>專案子類型所用的屬性  
 環境和基底專案系統可以使用從屬性<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>下列表格詳細說明可控制的專案系統的各種功能的專案子類型的列舉型別。  
  
|VSHPROPID 屬性|專案子類型|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|可讓專案子類型，來控制內容的**加入項目** 對話方塊。 專案子類型可以提供新的範本目錄的規格、 將新的項目類型加入、 移除現有的項目，和重新組織的基底的專案中的項目子集**加入項目** 對話方塊。|  
|`PropertyPagesCLSIDList`|可讓專案子類型來新增或移除組態無關的屬性頁。|  
|`CfgPropertyPagesCLSIDList`|可讓專案子類型來新增或移除組態相關的屬性頁。|  
|`ExtObjectCATID`|可讓專案子類型，以提供 Automation 擴充項的專案或專案項目物件知道擴充項 CATID。 專案子類型，例如可以提供自訂`Project.Extender("<subtype>")`物件。|  
|`BrowseObjectCATID`|可讓專案子類型提供的 Automation 擴充項`Browse`知道擴充項 CATID 物件。 例如，專案子類型可以加入額外的屬性，以<xref:EnvDTE.Project.Properties%2A>集合。|  
|`CfgBrowseObjectCATID`|可讓專案子類型，以提供的專案設定瀏覽物件的 Automation 擴充項。 例如，專案子類型可以加入額外的屬性，以<xref:EnvDTE.Configuration.Properties%2A>集合。|  
|`CfgExtObjectCATID`|可讓專案子類型的組態物件提供 Automation 擴充項。|  
|`DefaultPlatformName`|可讓專案子類型，以判斷專案的組態物件的平台名稱。|  
  
 基底的專案提供上述屬性的預設實作。 基底專案取得這些藉由呼叫`QueryInterface`如<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>上的最外層的專案子類型，如此可讓專案子類型覆寫屬性的實作。  
  
## <a name="see-also"></a>另請參閱  
 [設計專案子類型](../../extensibility/internals/project-subtypes-design.md)