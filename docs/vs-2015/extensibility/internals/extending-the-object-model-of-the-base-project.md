---
title: 擴充基底專案的物件模型 |Microsoft Docs
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
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187171"
---
# <a name="extending-the-object-model-of-the-base-project"></a>擴充基底專案的物件模型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案子類型可能會在下列位置擴充基底專案的自動化物件模型：  
  
- Project. 擴充項 ( " \<ProjectSubtypeName> " ) -這可讓專案子類型從提供具有自訂方法的物件 <xref:EnvDTE.Project> 。 專案子類型可以使用自動化擴充項來公開 `Project` 物件。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上實作為的介面，應從 `VSHPROPID_ExtObjectCATID`) 的 CATID 提供其 from <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (對應至 `itemid` VSITEMID_ROOT 值的物件 `VSITEMID` 。  
  
- 專案類型：擴充項 ( " \<ProjectSubtypeName> " ) -這可讓專案子類型從專案內的特定物件提供具有自訂方法的物件 <xref:EnvDTE.ProjectItem> 。 專案子類型可以使用自動化擴充項來公開此物件。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上實作為的介面，必須 `VSHPROPID_ExtObjectCATID` 從 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 對應至所需) CATID 的 from (提供其物件 `VSITEMID` 。  
  
- 專案。屬性–此集合會公開物件的設定獨立屬性 `Project` 。 如需專案屬性的詳細資訊，請參閱 <xref:EnvDTE.Project.Properties%2A> 。 專案子類型可以使用自動化擴充項，將其屬性加入至這個集合。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上實作為的介面，必須為 FROM VSHPROPID2 提供其物件 `VSHPROPID_BrowseObjectCATID` ， (從) 的 CATID 對應到 `itemid` VSITEMID_ROOT 的值 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 。  
  
- 設定：此集合會針對特定設定公開專案的設定相依屬性 (例如，Debug) 。 如需詳細資訊，請參閱 <xref:EnvDTE.Configuration>。 專案子類型可以使用自動化擴充項，將其屬性加入至這個集合。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上執行的介面，會提供其 CATID (的物件，以 `VSHPROPID_CfgBrowseObjectCATID` 對應至 `itemid`) 的值 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面是用來區別某個設定流覽物件與另一個。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
