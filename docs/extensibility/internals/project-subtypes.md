---
title: 項目子類型 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706403"
---
# <a name="project-subtypes"></a>專案子類型
項目子類型允許您自定義或調味[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案系統的行為。 自定義包括在專案檔中保存其他資料、在 **「添加新專案」** 對話方塊中添加或篩選項、控制程式集的調試和部署方式以及擴展項目**屬性頁**對話方塊。 VS包使用 COM 聚合實現專案子類型。

> [!NOTE]
> Visual C++專案系統不支援專案子類型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本身使用專案子類型來實現 SQL Server 和智慧設備專案。

## <a name="in-this-section"></a>本節內容
- [設計專案子類型](../../extensibility/internals/project-subtypes-design.md)

 描述項目子類型的概念。

- [專案子類型的初始化順序](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 描述按[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境劃分的程式設計專案子類型初始化序列。

- [專案子類型所擴充的屬性和方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 提供使用專案子類型最常擴展的功能和方法的詳細說明。

- [在 MSBuild 專案檔中保存資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 描述如何在專案檔中保留數據,以及如何使用這些數據<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>跨專案子類型聚合級別維護專案檔中的數據。

- [專案屬性使用者介面](../../extensibility/internals/project-property-user-interface.md)

 描述項目子類型如何修改項目**屬性頁**對話方塊。

- [擴充基底專案的物件模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 提供有關專案子類型如何使用自動化擴展器擴展自動化物件模型的資訊。

- [參與新增項目對話方塊](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 描述如何加入新**項目對話框加入 。**

- [將資料儲存於專案檔](../../extensibility/saving-data-in-project-files.md)

 說明專案子類型如何使用託管包框架 (MPF) 在專案檔中保存和檢索特定於子類型的數據。

- [處理特製化的部署](../../extensibility/internals/handling-specialized-deployment.md)

 說明專案子類型如何通過實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>介面來提供專用部署行為。

- [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)

 描述項目設計器中的添加和刪除屬性頁。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 提供指向詳細說明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案的主題的連結。
