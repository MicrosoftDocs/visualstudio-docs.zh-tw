---
title: 建立項目型態 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709074"
---
# <a name="create-project-types"></a>建立項目型態
您可以通過建立新[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]項目 類型進行擴充。 要創建新的項目類型,必須瞭解多個概念並完成多個步驟。 以下主題概述了如何創建項目類型。

## <a name="in-this-section"></a>本節內容
- [專案類型設計決策](../../extensibility/internals/project-type-design-decisions.md)

 討論在創建新專案類型之前必須做出的專案、專案檔持久性和承諾機制設計決策。

- [檢查表:建立新的項目型態](../../extensibility/internals/checklist-creating-new-project-types.md)

 概述了創建支援編輯代碼和編譯、構建、調試和部署專案中應用程式等程式設計任務的新項目類型時必須遵循的步驟。

- [使用項目工廠建立項目實體](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 提供有關如何提供和使用專案工廠創建新專案實例的資訊。

- [註冊項目類型](../../extensibility/internals/registering-a-project-type.md)

 提供提供預設路徑和數據的註冊表中的語句的代碼示例,以及包含每個語句註冊表腳本中的條目的表。

- [專案持久性](../../extensibility/internals/project-persistence.md)

 討論`IPersistFileFormat`使用 來保留檔和非基於檔的專案物件。

- [使用 MSBuild](../../extensibility/internals/using-msbuild.md)

 描述項目類型如何使用[!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)]生成引擎來允許使用者[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]從 命令列和命令行生成。

## <a name="related-sections"></a>相關章節
- [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 解釋程式碼檢視工具(如**物件瀏覽器**和**類視圖**視窗)的體系結構。 描述用於在 VSPackage 中實現物件瀏覽的介面和方法。

- [新增項目和項目項目樣本](../../extensibility/internals/adding-project-and-project-item-templates.md)

 討論專案在確定打開專案項時使用哪個編輯器以及如何操縱專案資源方面的重要性。

- [使用 Windows 安裝程式安裝 VS 套件](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 展示如何為 VSPackage 提供其自己的唯一識別,以及如何在 Windows 安裝程式套件(中包裝 VSPackage DLL 和其他資訊 *)用於*部署到客戶的 MSI 檔)。

- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)

 描述視圖[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和位址層次結構的方式。

- [VSPackage](../../extensibility/internals/vspackages.md)

 提供 VSPackage 的概述,這是一個可安裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的 COM 物件,可擴展環境並討論如何實現自己的 VSPackage。

- [專案類型](../../extensibility/internals/project-types.md)

 討論如何使用專案來修改代碼、編譯和生成代碼以及運行和調試代碼,並提供有關如何創建專案類型的詳細主題的連結。
