---
title: 依項目子型態擴充的屬性和方法 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706201"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>專案子類型所擴充的屬性和方法
專案子類型具有很大的力量來影響項目的行為,因為它是作為基礎專案的聚合器構造的。 本節總結了一些可以通過專案子類型進行增強或修改的功能。

## <a name="features-gained-by-aggregation"></a>透過集合取得的功能
 下表總結了聚合使專案子類型能夠在基礎專案中重寫的許多方法。

|將聚合覆寫的方法|專案子類型|
|---------------------------------------|---------------------|
|從<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|使項目子型別<br /><br /> - 更改項目節點的標題和圖示。<br />- 完全`Browse`覆蓋 項目物件。<br />- 控制是否可以重新命名專案。<br />- 控制排序順序。<br />- 控制動態幫助的使用者上下文。|
|從<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|使專案子類型能夠控制向設計人員和編輯器提供的上下文服務。|
|從<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|使項目子型別<br /><br /> - 參與專案命令的命令路由。<br />- 添加、刪除或禁用專案環境命令和解決方案資源管理器活動命令。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|使專案子類型能夠篩選使用者在「**添加新專案」** 對話框中看到的內容。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|使項目子型別<br /><br /> - 確定給定檔副檔名的預設產生器。<br />- 將人可讀生成器名稱映射到 COM 物件。|

## <a name="properties-used-by-project-subtypes"></a>專案子型態使用的屬性
 環境和基礎項目系統可以使用下表中詳細屬性<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID><xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>和 枚舉,使專案子類型能夠控制專案系統的各種功能。

|VSHPROPID 屬性|專案子類型|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|允許專案子型別控制 **「添加專案」** 對話框的內容。 專案子型態可以提供樣本目錄的新規範、添加新類型的項、刪除現有項以及重新組織基礎專案「**新增專案」** 對話方塊中的項目集。|
|`PropertyPagesCLSIDList`|允許項目子類型添加或刪除與配置無關的屬性頁。|
|`CfgPropertyPagesCLSIDList`|允許項目子類型添加或刪除與配置相關的屬性頁。|
|`ExtObjectCATID`|允許專案子類型透過瞭解擴展器 CATID 為專案或專案項物件提供自動化擴充器。 例如,專案子類型可以提供自定義`Project.Extender("<subtype>")`物件。|
|`BrowseObjectCATID`|允許專案子類型透過瞭解擴展器 CATID`Browse`為物件提供自動化擴充器。 例如,專案子類型可以向<xref:EnvDTE.Project.Properties%2A>集合添加額外的屬性。|
|`CfgBrowseObjectCATID`|允許專案子類型為專案配置瀏覽物件提供自動化擴展器。 例如,專案子類型可以向<xref:EnvDTE.Configuration.Properties%2A>集合添加額外的屬性。|
|`CfgExtObjectCATID`|允許專案子類型為配置物件提供自動化擴展器。|
|`DefaultPlatformName`|允許專案子類型確定專案配置物件的平臺名稱。|

 基礎專案提供上述屬性的預設實現。 基礎項目通過在最外層的專案`QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>子 類型上調用來獲取這些,從而允許專案子類型覆蓋屬性的實現。

## <a name="see-also"></a>另請參閱
- [設計專案子類型](../../extensibility/internals/project-subtypes-design.md)
