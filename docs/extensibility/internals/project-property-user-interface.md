---
title: 專案屬性消費者介面 |Microsoft Docs
description: 瞭解專案子類型如何修改基底專案所提供的 [專案屬性頁] 對話方塊。
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77e3554f2a3fd3b0dc1d608bb7d0a1198116a4e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903585"
---
# <a name="project-property-user-interface"></a>專案屬性使用者介面

專案子類型可以使用專案 [ **屬性頁** ] 對話方塊中的專案，因為它們是由基底專案提供、隱藏或設為提供的唯讀控制項和整個頁面，或是將專案子類型專用頁面新增至 [ **屬性頁** ] 對話方塊。

## <a name="extending-the-project-property-dialog-box"></a>擴充專案屬性對話方塊

專案子類型會實行 automation 擴充項和專案設定流覽物件。 這些擴充項會執行 <xref:EnvDTE.IFilterProperties> 介面，以隱藏特定屬性或將其設為唯讀。 基底專案所執行之基底專案的 [ **屬性頁** ] 對話方塊會接受 Automation 擴充項所執行的篩選。

擴充 **專案屬性** 對話方塊的程式如下所示：

- 基底專案藉由執行介面，從專案子類型抓取擴充項 <xref:EnvDTE80.IInternalExtenderProvider> 。 流覽、專案自動化和專案設定會流覽基底專案的物件，全都會執行這個介面。

- <xref:EnvDTE80.IInternalExtenderProvider>專案流覽物件和專案自動化物件委派的實作為 <xref:EnvDTE80.IInternalExtenderProvider> 專案子類型匯總工具的實 (也就是它們 `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 專案物件) 上。

- 基底專案設定流覽物件也會 <xref:EnvDTE80.IInternalExtenderProvider> 在自動化擴充項中，直接從專案子類型設定物件進行連線。 其實作為委派給 <xref:EnvDTE80.IInternalExtenderProvider> 專案子類型匯總工具所執行的介面。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>由 project configuration browse 物件所執行，會傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 物件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>（也會由專案設定流覽物件所執行）會傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> 物件。

- 專案子類型可透過抓取下列值，在執行時間為基底專案的各種擴充物件判斷適當的 Catid <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ：

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

為了判斷專案範圍的 Catid，專案子類型會抓取上述屬性以進行 [VSITEMID。的根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` 。 專案子類型可能也會想要控制針對專案顯示的 **屬性頁** 對話方塊頁面，設定相依和設定無關。 某些專案子類型可能需要移除內建的頁面，並加入專案子類型的特定頁面。 為了啟用此功能，managed 用戶端專案會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 下列屬性的方法：

- `VSHPROPID_PropertyPagesCLSIDList` —以分號分隔的設定獨立屬性頁 Clsid 清單。

- `VSHPROPID_CfgPropertyPagesCLSIDList —` 與設定相依之屬性頁的 Clsid 清單（以分號分隔）。

由於專案子類型會匯總 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 物件，因此它可以覆寫這些屬性的定義，以控制要顯示的 **屬性頁** 對話方塊。 專案子類型可以從內部基底專案中取得這些屬性，然後視需要新增或移除 Clsid。

專案子類型所加入的新屬性頁面，會從基底專案執行中，傳遞專案設定流覽物件。 此專案設定流覽物件支援 Automation 擴充項。 如需 AutomationExtenders 的詳細資訊，請參閱 [執行和使用 Automation](/previous-versions/0y92k2w2(v=vs.140))擴充項。 專案子類型所實的屬性頁面 <xref:EnvDTE.Project.Extender%2A> 會呼叫，以抓取其自己的專案子類型設定流覽物件，此物件會擴充基底專案的設定流覽物件。

## <a name="see-also"></a>另請參閱

- <xref:EnvDTE.IFilterProperties>
- [[屬性頁] 對話方塊](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))