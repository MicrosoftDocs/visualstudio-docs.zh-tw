---
title: 擴充基底專案的物件模型 |Microsoft Docs
description: 瞭解如何使用專案子類型，在 Visual Studio 中擴充基底專案的自動化物件模型。
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 23541124e48df0c3760d38ff8205f086281034fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887038"
---
# <a name="extend-the-object-model-of-the-base-project"></a>擴充基底專案的物件模型

專案子類型可能會在下列位置擴充基底專案的自動化物件模型：

- Project. 擴充項 ( " \<ProjectSubtypeName> " ) ：這可讓專案子類型從物件提供具有自訂方法的物件 <xref:EnvDTE.Project> 。 專案子類型可以使用自動化擴充項來公開 `Project` 物件。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上實作為的介面，應該為的 from (提供其物件，其會 `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> 對應至 `itemid` VSITEMID 的值 [。Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID。

- 專案類型：擴充項 ( " \<ProjectSubtypeName> " ) ：這可讓專案子類型從專案內的特定物件提供具有自訂方法的物件 <xref:EnvDTE.ProjectItem> 。 專案子類型可以使用自動化擴充項來公開此物件。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上實作為的介面，必須 `VSHPROPID_ExtObjectCATID` 從 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 對應至所需) CATID 的 from (提供其物件 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> 。

- 專案。屬性：此集合會公開與設定無關的物件屬性 `Project` 。 如需 `Project` 屬性的詳細資訊，請參閱<xref:EnvDTE.Project.Properties%2A>。 專案子類型可以使用自動化擴充項，將其屬性加入至這個集合。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上實作為的介面，必須為的 from (提供其物件，以 `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 對應至 `itemid` VSITEMID 的值 [。Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID。

- 設定。屬性：此集合會針對特定設定公開專案的設定相依屬性 (例如，Debug) 。 如需詳細資訊，請參閱<xref:EnvDTE.Configuration>。 專案子類型可以使用自動化擴充項，將其屬性加入至這個集合。 在 <xref:EnvDTE80.IInternalExtenderProvider> 主要專案子類型匯總工具上執行的介面，會提供其適用于 CATID (的物件，以 `VSHPROPID_CfgBrowseObjectCATID` 對應至 `itemid` VSITEMID 的值 [。根目錄](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面是用來區別某個設定流覽物件與另一個。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
