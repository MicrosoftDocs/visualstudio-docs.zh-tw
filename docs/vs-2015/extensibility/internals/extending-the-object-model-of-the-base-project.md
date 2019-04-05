---
title: 擴充的基底的專案物件模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 69ad1b421e648c5248501ebdf76f97fab7f3a66e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939401"
---
# <a name="extending-the-object-model-of-the-base-project"></a>擴充基底專案的物件模型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案子類型可能會擴充自動化物件模型的基底的專案，在下列位置：  
  
-   Project.Extender ("\<ProjectSubtypeName >") – 這可讓專案子類型，提供物件以自訂的方法，從<xref:EnvDTE.Project>。 專案子類型可以使用 Automation 擴充項，來公開`Project`物件。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面應該提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>(對應至`itemid`VSITEMID_ROOT 的值從`VSITEMID`) CATID。  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >") – 這可讓物件提供自訂的方法，從特定專案子類型<xref:EnvDTE.ProjectItem>專案內的物件。 專案子類型可以使用 Automation 擴充項，來公開此物件。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面必須提供其物件`VSHPROPID_ExtObjectCATID`從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(對應至所需`VSITEMID`) CATID。  
  
-   Project.Properties – 此集合會公開組態獨立屬性的`Project`物件。 如需有關專案屬性的詳細資訊，請參閱<xref:EnvDTE.Project.Properties%2A>。 專案子類型可以使用 Automation 擴充項，將其內容新增至這個集合。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作的介面必須提供其物件`VSHPROPID_BrowseObjectCATID`從 VSHPROPID2 (對應至`itemid`VSITEMID_ROOT 的值從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID。  
  
-   Configuration.Properties – 此集合會公開特定組態 （例如，偵錯） 的專案組態相依屬性。 如需詳細資訊，請參閱 <xref:EnvDTE.Configuration>。 專案子類型可以使用 Automation 擴充項，將其內容新增至這個集合。 <xref:EnvDTE80.IInternalExtenderProvider>主要專案子類型的彙總工具上實作介面提供其物件的 CATID `VSHPROPID_CfgBrowseObjectCATID` (對應至`itemid`的值<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面用來區別某個設定瀏覽的物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
