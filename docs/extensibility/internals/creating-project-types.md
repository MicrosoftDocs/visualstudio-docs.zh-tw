---
title: 建立專案類型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 005765cb66a23f2efcf0c8defb323120d79bef60
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314568"
---
# <a name="create-project-types"></a>建立專案類型
您可以擴充[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由建立新的專案類型。 若要建立新的專案類型，您必須了解幾個概念，並完成幾個步驟。 下列主題提供如何建立專案類型的概觀。

## <a name="in-this-section"></a>本節內容
- [專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)

 討論項目、 專案檔案持續性，以及您必須先建立新的專案類型之前的承諾用量 mechanic 設計決策。

- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)

 提供建立新的專案類型支援這類編輯程式碼和編譯、 建置、 偵錯和部署您的專案中的應用程式的程式設計工作，您必須遵循的步驟概觀。

- [使用 project factory 建立專案執行個體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 提供如何提供，並使用 project factory 來建立新專案的執行個體的相關資訊。

- [註冊專案類型](../../extensibility/internals/registering-a-project-type.md)

 提供陳述式從登錄提供預設路徑和資料，以及資料表包含項目從登錄指令碼，每個陳述式的程式碼的範例。

- [專案持續性](../../extensibility/internals/project-persistence.md)

 討論使用`IPersistFileFormat`來保存檔案和非檔案型專案物件。

- [使用 MSBuild](../../extensibility/internals/using-msbuild.md)

 描述如何使用您的專案類型[!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)]建置引擎，讓使用者從建置[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和在命令列。

## <a name="related-sections"></a>相關章節
- [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 說明這類檢視工具的程式碼的架構**物件瀏覽器**並**類別檢視**視窗。 描述用來在 VSPackage 中實作物件瀏覽的方法與介面。

- [將專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)

 討論在判斷哪一個編輯器使用開啟的專案項目時，播放專案的重要性，且可以操作專案資源的方式。

- [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 示範如何為 VSPackage 提供它自己唯一的身分識別，以及如何將 VSPackage Dll 和其他資訊包裝在一個 Windows Installer 套件 ( *。MSI*檔案) 部署至您的客戶。

- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)

 描述如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]檢視和位址階層。

- [VSPackage](../../extensibility/internals/vspackages.md)

 提供的 VSPackage，可安裝的 COM 物件延伸概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境，並討論如何實作您自己的 VSPackage。

- [專案類型](../../extensibility/internals/project-types.md)

 討論如何使用專案來修改程式碼、 編譯和建置程式碼，以及執行和偵錯程式碼，並提供有關如何建立專案類型的詳細主題的連結。