---
title: 專案子類型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73cf7fe43dcbe15bdeedf6822c9172533e6d420b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63423075"
---
# <a name="project-subtypes"></a>專案子類型
專案子類型可讓您自訂或 flavor 的專案系統的行為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 自訂包括將其他資料儲存在專案檔中，加入或篩選中的項目**加入新項目** 對話方塊中，控制組件進行偵錯和部署的方式和擴充專案**屬性頁面** 對話方塊。 Vspackage 實作專案子類型使用 COM 彙總。

> [!NOTE]
> 視覺效果C++專案系統不支援專案子類型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 實作 SQL Server 和智慧型裝置專案，本身就會使用專案子類型。

## <a name="in-this-section"></a>本節內容
- [設計專案子類型](../../extensibility/internals/project-subtypes-design.md)

 描述專案子類型的概念。

- [專案子類型的初始化順序](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 描述程式設計專案子類型初始設定順序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。

- [專案子類型所擴充的屬性和方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 提供方法最常使用的專案子類型擴充功能的詳細的描述。

- [在 MSBuild 專案檔中保存資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 描述如何將資料保存在專案檔，以及如何使用<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>跨專案子類型的彙總層級維護專案檔中的資料。

- [專案屬性使用者介面](../../extensibility/internals/project-property-user-interface.md)

 描述如何專案子類型可以修改專案**屬性頁** 對話方塊。

- [擴充基底專案的物件模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 提供有關專案子類型可以如何使用 Automation 擴充項擴充自動化物件模型的資訊。

- [參與加入新項目對話方塊](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 描述如何將項目加入**加入新項目** 對話方塊。

- [將資料儲存於專案檔](../../extensibility/saving-data-in-project-files.md)

 說明如何儲存和使用 Managed Package Framework (MPF) 擷取專案檔中的子型別特定資料專案子類型。

- [處理特製化的部署](../../extensibility/internals/handling-specialized-deployment.md)

 說明如何專案子類型時，可以藉由實作提供特製化的部署行為<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>介面。

- [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)

 說明新增和移除專案設計工具中的 屬性頁。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 提供詳細說明的主題連結[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案。