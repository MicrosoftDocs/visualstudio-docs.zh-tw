---
title: "擴充的基底的專案物件模型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b92fe7fece58dd2006507f0285d3c440af437ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-object-model-of-the-base-project"></a>擴充基底的專案物件的模型
專案子類型可能會擴充自動化物件模型的基底的專案，在下列位置：  
  
-   Project.Extender (「\<ProjectSubtypeName >")-這可讓專案子類型，提供物件，以及自訂方法的方法從<xref:EnvDTE.Project>。 專案子類型可使用 Automation 擴充項公開`Project`物件。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面應該提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>(對應至`itemid`VSITEMID_ROOT 的值從`VSITEMID`) CATID。  
  
-   ProjectItem.Extender (「\<ProjectSubtypeName >")-這可讓物件提供自訂方法，從特定專案子類型<xref:EnvDTE.ProjectItem>專案內的物件。 專案子類型都可以使用來公開此物件的 Automation 擴充項。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面需要提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(對應至所需`VSITEMID`) CATID。  
  
-   Project.Properties-此集合會公開組態獨立屬性`Project`物件。 如需有關專案屬性的詳細資訊，請參閱<xref:EnvDTE.Project.Properties%2A>。 專案子類型可以使用 Automation 擴充項来加入此集合及其屬性。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面需要提供其物件`VSHPROPID_BrowseObjectCATID`從 VSHPROPID2 (對應至`itemid`VSITEMID_ROOT 的值從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID。  
  
-   Configuration.Properties-此集合會公開 （例如，偵錯） 的特定組態的專案組態相依屬性。 如需詳細資訊，請參閱 <xref:EnvDTE.Configuration>。 專案子類型可以使用 Automation 擴充項来加入此集合及其屬性。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作介面提供其物件的 CATID `VSHPROPID_CfgBrowseObjectCATID` (對應至`itemid`值<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>)。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面用來區別一個組態瀏覽的物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>