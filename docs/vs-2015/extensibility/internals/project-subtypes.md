---
title: 專案子類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ad1e105d43c40782b13d8799b20626e57363c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838790"
---
# <a name="project-subtypes"></a>專案子類型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案子類型可讓您自訂或類別的專案系統行為 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 自訂包括將其他資料儲存在專案檔中、在 [ **加入新專案** ] 對話方塊中新增或篩選項目、控制元件的調試和部署方式，以及擴充 [專案 **屬性頁** ] 對話方塊。 Vspackage 使用 COM 匯總來執行專案子類型。  
  
> [!NOTE]
> Visual C++ 專案系統不支援專案子類型。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 本身會使用專案子類型來執行 SQL Server 和智慧型裝置專案。  
  
## <a name="in-this-section"></a>本節內容  
 [設計專案子類型](../../extensibility/internals/project-subtypes-design.md)  
 描述專案子類型的概念。  
  
 [專案子類型的初始化順序](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 依環境描述程式設計專案子類型的初始化順序 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [專案子類型所擴充的屬性和方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 提供使用專案子類型最常擴充之功能和方法的詳細說明。  
  
 [在 MSBuild 專案檔中保存資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 描述如何將資料保存在專案檔中，以及如何使用在專案 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 子類型匯總層級中維護專案檔中的資料。  
  
 [專案屬性使用者介面](../../extensibility/internals/project-property-user-interface.md)  
 描述專案子類型如何修改專案 **屬性頁** 對話方塊。  
  
 [擴充基底專案的物件模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 提供有關專案子類型如何使用 Automation 擴充項來延伸 automation 物件模型的資訊。  
  
 [參與新增項目對話方塊](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 描述如何在 [ **加入新專案** ] 對話方塊中加入專案。  
  
 [將資料儲存於專案檔](../../extensibility/saving-data-in-project-files.md)  
 說明專案子類型如何使用 Managed Package Framework (MPF) ，來儲存和取出專案檔中的子類型特定資料。  
  
 [處理特製化的部署](../../extensibility/internals/handling-specialized-deployment.md)  
 說明專案子類型如何藉由實作為介面，來提供特製化的部署行為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 。  
  
 [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)  
 描述在 [專案設計工具] 中加入和移除屬性頁。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供詳細 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 專案的主題連結。
