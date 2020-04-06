---
title: 項目屬性使用者介面 |微軟文件
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706389"
---
# <a name="project-property-user-interface"></a>專案屬性使用者介面

項目子型態可以使用專案**屬性頁**對話方塊中的項目,因為它們由基礎專案提供,隱藏或使唯讀控制項和整個頁面提供,或將專案子類型特定的**頁面添加到「屬性頁」** 對話框中。

## <a name="extending-the-project-property-dialog-box"></a>擴充項目屬性對話框

專案子類型實現自動化擴展器和專案配置流覽物件。 這些擴展器實現<xref:EnvDTE.IFilterProperties>介面,使特定屬性隱藏或唯讀。 基礎專案的屬性**頁**對話框由基礎項目實現,該對話框表示自動化擴展器執行的篩選。

延伸**項目屬性**對話框的過程概述如下:

- 基本專案通過實現<xref:EnvDTE80.IInternalExtenderProvider>介面從專案子類型檢索擴展器。 基礎專案的流覽、專案自動化和專案配置流覽物件都實現了此介面。

- 項目流覽物件<xref:EnvDTE80.IInternalExtenderProvider>的<xref:EnvDTE80.IInternalExtenderProvider>實現和專案自動化物件委託給專案子類型聚合器的實現(即`QueryInterface`,<xref:EnvDTE80.IInternalExtenderProvider><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>它們用於專案物件)。

- 基本專案配置流覽物件還<xref:EnvDTE80.IInternalExtenderProvider>實現 直接從專案子類型配置物件連接到自動化擴展器中。 其實現委託給專案子<xref:EnvDTE80.IInternalExtenderProvider>類型聚合器實現的介面。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>,由專案設定流覽物件實現,傳<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>回物件 。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>,也實現由專案配置流覽物件,<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>返回物件。

- 專案子類型可以通過檢索<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>以下 值來確定基本專案在運行時的各種可擴充物件的相應 CATID:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

要決定專案範圍的 CATID,專案子型態將檢索 VSITEMID 的屬性[。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)從`VSITEMID typedef`。 專案子類型可能還希望控制為項目顯示哪些**屬性頁**對話框頁,這兩個頁面都與配置無關,並且與配置無關。 某些專案子類型可能需要刪除內置頁面並添加專案子類型特定頁面。 為了啟用此功能,託管客戶端項目呼叫以下屬性<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>的方法:

- `VSHPROPID_PropertyPagesCLSIDList`• 與配置無關的屬性頁的 CLSID 的分號分隔清單。

- `VSHPROPID_CfgPropertyPagesCLSIDList —`與配置相關的屬性頁的 CLSID 的分號分隔清單。

由於專案子類型聚合<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件,它可以覆蓋這些屬性的定義,以控制顯示的屬性**頁**對話方塊。 專案子類型可以從內部基專案中檢索這些屬性,然後根據需要添加或刪除 CLSID。

項目子類型添加的新屬性頁將從基礎項目實現中傳遞專案配置瀏覽物件。 此專案配置瀏覽物件支援自動化擴展器。 有關自動化擴充器的詳細資訊,請參閱[實現與使用自動化擴充器](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)。 專案子類型調用<xref:EnvDTE.Project.Extender%2A>實現的屬性頁,用於檢索其自己的專案子類型配置流覽物件,該物件擴展了基礎專案的配置流覽物件。

## <a name="see-also"></a>另請參閱

- <xref:EnvDTE.IFilterProperties>
- [屬性頁對話框](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
