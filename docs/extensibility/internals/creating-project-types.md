---
title: "建立專案類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7c0bba9b80e4e874f222ce00834f44a2d93e3e7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-types"></a>建立專案類型
您可以擴充[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由建立新的專案類型。 若要建立新的專案類型，您必須了解幾個概念，並完成步驟的數目。 下列主題提供如何建立專案類型的概觀。  
  
## <a name="in-this-section"></a>本章節內容  
 [專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)  
 討論的項目、 專案檔的持續性，並承諾修理設計決策，您必須建立新的專案類型之前進行。  
  
 [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)  
 提供建立新的專案類型支援與編輯程式碼並編譯、 建置、 偵錯，以及您的專案中部署應用程式的程式設計工作所必須遵循的步驟的概觀。  
  
 [使用 Project Factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 提供有關如何提供並用專案 factory 來建立新專案的執行個體的資訊。  
  
 [註冊專案類型](../../extensibility/internals/registering-a-project-type.md)  
 提供程式碼範例的陳述式從登錄機提供預設路徑和資料，以及資料表包含每個陳述式的登錄指令碼中的項目。  
  
 [專案持續性](../../extensibility/internals/project-persistence.md)  
 討論使用`IPersistFileFormat`可保存檔案與非檔案型的專案物件。  
  
 [使用 MSBuild](../../extensibility/internals/using-msbuild.md)  
 描述如何使用您的專案類型[!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)]建置引擎，讓使用者從建置[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和在命令列。  
  
## <a name="related-sections"></a>相關章節  
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 說明這類檢視工具的程式碼的架構**物件瀏覽器**和**類別檢視**視窗。 描述的介面和方法，可用來在 VSPackage 中實作瀏覽的物件。  
  
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 討論重要性專案中扮演的以便判斷哪些編輯器使用開啟的專案項目時，可以管理專案資源的方式。  
  
 [使用 Windows Installer 安裝 VSPackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 示範如何提供它自己的唯一識別您的 VSPackage，以及如何將 VSPackage Dll 和其他資訊包裝在 Windows Installer 封裝 (。MSI 檔案） 以部署至您的客戶。  
  
 [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 描述如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]檢視和位址階層。  
  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 提供的 VSPackage，可安裝的 COM 物件延伸概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境，並討論如何實作您自己的 VSPackage。  
  
 [專案類型](../../extensibility/internals/project-types.md)  
 討論如何使用專案來修改程式碼、 編譯和建置程式碼，以及執行和偵錯程式碼，並提供有關如何建立專案類型的詳細主題的連結。