---
title: 擴展基礎項目的物件模型 |微軟文件
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708402"
---
# <a name="extend-the-object-model-of-the-base-project"></a>擴充基礎項目的物件模型

專案子型態可在以下位置延伸基礎項目的自動化物件模型:

- Project.Extender("\<專案子類型名稱>"):這允許專案子類型<xref:EnvDTE.Project>提供 具有物件自定義方法的物件。 專案子型態可以使用自動化擴充器`Project`公開物件 。 在<xref:EnvDTE80.IInternalExtenderProvider>主項目子類型聚合器上實現的介面應`VSHPROPID_ExtObjectCATID`提供 其物件為<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>from( 對應於`itemid` [VSITEMID 的值)。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID。

- ProjectItem.Extender("\<專案子類型名稱>"):這允許專案子類型提供具有專案中<xref:EnvDTE.ProjectItem>特定 物件的自定義方法的物件。 項目子類型可以使用自動化擴展器公開此物件。 在<xref:EnvDTE80.IInternalExtenderProvider>主項目子類型聚合器上實現的介面需要`VSHPROPID_ExtObjectCATID`為<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>來自<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>(對應於) CATID 提供其物件。

- Project.屬性:此集合公開`Project`物件與配置無關的屬性。 如需 `Project` 屬性的詳細資訊，請參閱<xref:EnvDTE.Project.Properties%2A>。 項目子類型可以使用自動化擴展器將其屬性添加到此集合。 在<xref:EnvDTE80.IInternalExtenderProvider>主項目子類型聚合器上實現的介面需要`VSHPROPID_BrowseObjectCATID`為<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>提供其 物件`itemid`(對應於[VSITEMID 的值)。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID。

- 配置.屬性:此集合公開特定配置的專案的與配置相關的屬性(例如,除錯)。 如需詳細資訊，請參閱 <xref:EnvDTE.Configuration>。 項目子類型可以使用自動化擴展器將其屬性添加到此集合。 在<xref:EnvDTE80.IInternalExtenderProvider>主項目子類型聚合器上實現的介面為`VSHPROPID_CfgBrowseObjectCATID`CATID 提供其物件`itemid`(對應於[VSITEMID 的值)。根](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>))。 該<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面用於區分一個配置瀏覽物件和另一個配置流覽物件。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
