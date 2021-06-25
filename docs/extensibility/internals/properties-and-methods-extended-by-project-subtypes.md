---
title: 專案子類型所擴充的屬性和方法 |Microsoft Docs
description: 瞭解專案子類型可以增強或修改的功能，可讓您自訂 Visual Studio 專案系統的行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ddcf020cf0b3e3e4f0f4a7c61ff1f15ce9ded5e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903537"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>專案子類型所擴充的屬性和方法
專案子類型有許多強大的功能可影響專案的行為，因為它會被視為基底專案的匯總工具。 本節將摘要說明專案子類型可以增強或修改的部分功能。

## <a name="features-gained-by-aggregation"></a>匯總所取得的功能
 下表匯總了許多可讓您在基底專案中覆寫專案子類型的方法。

|由匯總覆寫的方法|專案子類型|
|---------------------------------------|---------------------|
|來源 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ：<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|啟用專案子類型<br /><br /> -變更專案節點的標題和圖示。<br />-完全覆寫專案 `Browse` 物件。<br />-控制是否可以重新命名專案。<br />-控制項排序次序。<br />-控制動態說明的使用者內容。|
|來源 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> ：<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|啟用專案子類型，以控制要提供給設計工具和編輯器的內容服務。|
|來源 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ：<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|啟用專案子類型<br /><br /> -參與專案命令的命令路由。<br />-新增、移除或停用專案環境命令，以及方案總管使用中命令。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|啟用專案子類型，以篩選使用者在 [ **加入新專案** ] 對話方塊中看到的內容。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|啟用專案子類型<br /><br /> -判斷指定副檔名的預設產生器。<br />-將人類可讀取的產生器名稱對應至 COM 物件。|

## <a name="properties-used-by-project-subtypes"></a>專案子類型所使用的屬性
 環境和基底專案系統可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> 下表中詳述的屬性和列舉， <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> 以啟用專案子類型來控制專案系統的各種功能。

|VSHPROPID 屬性|專案子類型|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|允許專案子類型控制 [ **加入專案** ] 對話方塊的內容。 專案子類型可以提供新的範本目錄規格、加入新的專案類型、移除現有的專案，以及在基底專案的 [ **加入專案** ] 對話方塊中重新組織專案的子集。|
|`PropertyPagesCLSIDList`|允許專案子類型新增或移除與設定無關的屬性頁面。|
|`CfgPropertyPagesCLSIDList`|允許專案子類型新增或移除與設定相依的屬性頁面。|
|`ExtObjectCATID`|允許專案子類型藉由瞭解擴充項 CATID，為專案或專案專案物件提供自動化擴充項。 例如，專案子類型可以提供自訂 `Project.Extender("<subtype>")` 物件。|
|`BrowseObjectCATID`|允許專案子類型藉由瞭解擴充項 CATID 來為物件提供自動化擴充項 `Browse` 。 例如，專案子類型可以將額外的屬性加入至 <xref:EnvDTE.Project.Properties%2A> 集合。|
|`CfgBrowseObjectCATID`|允許專案子類型為專案設定流覽物件提供自動化擴充項。 例如，專案子類型可以將額外的屬性加入至 <xref:EnvDTE.Configuration.Properties%2A> 集合。|
|`CfgExtObjectCATID`|允許專案子類型提供 configuration 物件的自動化擴充項。|
|`DefaultPlatformName`|允許專案子類型判斷專案設定物件的平臺名稱。|

 基底專案提供上述屬性的預設執行。 基底專案會藉由 `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 在最外層的專案子類型上呼叫來取得這些專案，進而允許專案子類型覆寫屬性的執行。

## <a name="see-also"></a>另請參閱
- [設計專案子類型](../../extensibility/internals/project-subtypes-design.md)
