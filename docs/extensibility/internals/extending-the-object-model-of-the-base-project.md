---
title: 擴充的基底的專案物件模型 |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 607a63dc84db2811a4a2d158be07f158b849e1ad
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329038"
---
# <a name="extend-the-object-model-of-the-base-project"></a>擴充基底的專案物件的模型

專案子類型可能會擴充自動化物件模型的基底的專案，在下列位置：

- Project.Extender("\<ProjectSubtypeName>"):這可讓專案子類型，提供物件以自訂的方法，從<xref:EnvDTE.Project>物件。 專案子類型可以使用 Automation 擴充項，來公開`Project`物件。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面應該提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>(對應至`itemid`的值[VSITEMID。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID。

- ProjectItem.Extender("\<ProjectSubtypeName>"):這可讓物件提供自訂的方法，從特定專案子類型<xref:EnvDTE.ProjectItem>專案內的物件。 專案子類型可以使用 automation 擴充項，來公開此物件。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面必須提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(對應至所需<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID。

- Project.Properties:這個集合會公開組態無關屬性`Project`物件。 如需 `Project` 屬性的詳細資訊，請參閱<xref:EnvDTE.Project.Properties%2A>。 專案子類型可以使用 Automation 擴充項，將其內容新增至這個集合。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面必須提供其物件`VSHPROPID_BrowseObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(對應至`itemid`的值[VSITEMID。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID。

- Configuration.Properties:這個集合會公開組態相關專案的屬性 （例如，偵錯） 對特定組態。 如需詳細資訊，請參閱 <xref:EnvDTE.Configuration>。 專案子類型可以使用 Automation 擴充項，將其內容新增至這個集合。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作介面提供其物件的 CATID `VSHPROPID_CfgBrowseObjectCATID` (對應至`itemid`的值[VSITEMID。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>))。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面用來區別某個設定瀏覽的物件。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>