---
title: 專案屬性使用者介面 |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a83e5c9fb633322da536e62f1ba03484b965b162
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252347"
---
# <a name="project-property-user-interface"></a>專案屬性使用者介面

專案子類型可以使用 [專案**屬性頁**] 對話方塊中的專案，因為它們是由基底專案提供、隱藏或建立唯讀控制項和提供的整頁，或將專案子類型特有的頁面加入至 [**屬性頁**] 對話方塊方框.

## <a name="extending-the-project-property-dialog-box"></a>擴充專案屬性對話方塊

專案子類型會實行自動化擴充項和專案設定流覽物件。 這些擴充項會<xref:EnvDTE.IFilterProperties>執行介面，讓特定屬性隱藏或唯讀。 基底專案所實作為基底專案的 [**屬性頁**] 對話方塊，會接受自動化擴充項所執行的篩選。

擴充**專案屬性**對話方塊的程式如下所述：

- 基底專案會藉由執行<xref:EnvDTE80.IInternalExtenderProvider>介面，從專案子類型抓取擴充項。 [流覽]、[專案自動化] 和 [專案設定] 流覽基底專案的物件全都會執行此介面。

- 專案流覽物件<xref:EnvDTE80.IInternalExtenderProvider>和專案自動化物件委派的實作為專案子類型匯總工具<xref:EnvDTE80.IInternalExtenderProvider>的執行`QueryInterface` （也就是<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ， <xref:EnvDTE80.IInternalExtenderProvider>在專案物件）。

- 基底專案設定 [流覽物件] <xref:EnvDTE80.IInternalExtenderProvider>也會執行，直接從專案子類型設定物件連接到自動化擴充項。 它的執行會委派<xref:EnvDTE80.IInternalExtenderProvider>給專案子類型匯總工具所實作為的介面。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>由 [專案設定] [流覽物件] 所執行<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ，會傳回物件。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>也是由專案設定的流覽物件所執行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>會傳回物件。

- 專案子類型可以藉由抓取下列<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>值，在執行時間為基底專案的各種可延伸物件判斷適當的 catid：

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

為判斷專案範圍的 Catid，專案子類型會針對 VSITEMID 取得上述屬性[。根。](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef` 專案子類型可能也會想要控制針對專案顯示哪些**屬性頁**對話方塊頁面，分別設定相依和設定無關。 某些專案子類型可能需要移除內建頁面，並加入專案子類型的特定頁面。 為了啟用此功能，managed 用戶端專案會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>下列屬性的方法：

- `VSHPROPID_PropertyPagesCLSIDList`-與設定無關的屬性頁的 Clsid 清單（以分號分隔）。

- `VSHPROPID_CfgPropertyPagesCLSIDList —`與設定相關之屬性頁的 Clsid 清單（以分號分隔）。

因為專案子類型會匯總<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件，所以它可以覆寫這些屬性的定義，以控制要顯示哪些**屬性頁**對話方塊。 專案子類型可以從內部基底專案取得這些屬性，然後視需要新增或移除 Clsid。

專案子類型新增的新屬性頁會從基底專案的執行中，將專案設定 [流覽] 物件。 此專案設定： [流覽物件] 支援 Automation 擴充項。 如需 AutomationExtenders 的詳細資訊，請參閱[執行和使用自動化](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)擴充項。 專案子類型呼叫<xref:EnvDTE.Project.Extender%2A>所實作為的屬性頁，可取得自己的專案子類型設定流覽物件，以擴充基底專案的設定流覽物件。

## <a name="see-also"></a>另請參閱

- <xref:EnvDTE.IFilterProperties>
- [[屬性頁] 對話方塊](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
