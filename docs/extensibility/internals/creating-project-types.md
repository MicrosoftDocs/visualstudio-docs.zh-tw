---
title: 建立專案類型 |Microsoft Docs
description: 瞭解如何藉由設計、建立和註冊支援程式設計工作的新專案類型，來擴充 Visual Studio。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4038a122c6d2ec5f6ed29df6e529b2bff2e2bb71
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329922"
---
# <a name="create-project-types"></a>建立專案類型
您可以藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由建立新的專案類型來擴充。 若要建立新的專案類型，您必須瞭解數個概念並完成一些步驟。 下列主題提供如何建立專案類型的總覽。

## <a name="in-this-section"></a>本節內容
- [專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)

 討論在建立新的專案類型之前，您必須建立的專案、專案檔持續性和承諾用量技師修理設計決策。

- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)

 概述您必須遵循的步驟，以建立新的專案類型，以支援在專案中編輯程式碼及編譯、建立、偵測和部署應用程式的程式設計工作。

- [使用 project factory 建立專案實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 提供如何提供和使用專案 factory 來建立新專案實例的相關資訊。

- [註冊專案類型](../../extensibility/internals/registering-a-project-type.md)

 提供登錄中提供預設路徑和資料之語句的程式碼範例，以及包含每個語句的登入指令檔之專案的資料表。

- [專案持續性](../../extensibility/internals/project-persistence.md)

 討論 `IPersistFileFormat` 如何使用來保存檔案和非檔案型專案物件。

- [使用 MSBuild](../../extensibility/internals/using-msbuild.md)

 描述您的專案類型如何使用 [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] 組建引擎讓使用者在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令列中建立。

## <a name="related-sections"></a>相關章節
- [支援符號流覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 說明程式碼查看工具的架構，例如 **物件瀏覽器** 和 **類別檢視** 視窗。 描述在 VSPackage 中用來執行物件流覽的介面和方法。

- [新增專案與專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)

 討論專案在決定開啟專案專案時所使用的編輯器，以及如何操作專案資源時所扮演的意義。

- [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 說明如何為您的 VSPackage 提供自己的唯一身分識別，以及如何 (Windows Installer 套件中包裝您的 VSPackage Dll 和其他資訊 *。MSI* 檔案) 部署至您的客戶。

- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)

 描述 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 查看和定址階層的方式。

- [VSPackages](../../extensibility/internals/vspackages.md)

 提供 VSPackage 的總覽，此為可安裝的 COM 物件，可延伸 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境並討論如何執行您自己的 VSPackage。

- [專案類型](../../extensibility/internals/project-types.md)

 討論如何使用專案來修改程式碼、編譯和建立程式碼、執行和偵錯工具代碼，以及提供有關如何建立專案類型的詳細主題連結。
