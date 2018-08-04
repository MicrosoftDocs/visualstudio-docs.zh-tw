---
title: 擴充的基底的專案物件模型 |Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a297d8d70db2254e5c6ea2f64f3ab4cbadc3936
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497203"
---
# <a name="extend-the-object-model-of-the-base-project"></a>擴充基底的專案物件的模型

專案子類型可能會擴充自動化物件模型的基底的專案，在下列位置：

-   Project.Extender ("\<ProjectSubtypeName >"): 這可讓專案子類型，提供物件以自訂的方法，從<xref:EnvDTE.Project>物件。 專案子類型可以使用 Automation 擴充項，來公開`Project`物件。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面應該提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>(對應至`itemid`的值[VSITEMID。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID。

-   ProjectItem.Extender ("\<ProjectSubtypeName >"): 這可讓物件提供自訂的方法，從特定專案子類型<xref:EnvDTE.ProjectItem>專案內的物件。 專案子類型可以使用 automation 擴充項，來公開此物件。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面必須提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(對應至所需<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID。

-   Project.Properties： 此集合會公開組態無關屬性`Project`物件。 如需詳細資訊`Project`屬性，請參閱<xref:EnvDTE.Project.Properties%2A>。 專案子類型可以使用 Automation 擴充項，將其內容新增至這個集合。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面必須提供其物件`VSHPROPID_BrowseObjectCATID`從 VSHPROPID2 (對應至`itemid`的值[VSITEMID。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)，從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID。

-   Configuration.Properties： 此集合會公開組態相關專案的屬性 （例如，偵錯） 對特定組態。 如需詳細資訊，請參閱<xref:EnvDTE.Configuration>。 專案子類型可以使用 Automation 擴充項，將其內容新增至這個集合。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作介面提供其物件的 CATID `VSHPROPID_CfgBrowseObjectCATID` (對應至`itemid`的值[VSITEMID。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>))。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面用來區別某個設定瀏覽的物件。

## <a name="see-also"></a>另請參閱

<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>