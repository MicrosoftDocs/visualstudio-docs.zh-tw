---
title: 檢查清單：建立新的專案類型 |Microsoft Docs
description: 瞭解在 Visual Studio 中建立及顯示新的專案類型時必須完成的工作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a8cdeb250b81a39a5d9350da61a872ef43ae23b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944494"
---
# <a name="checklist-create-new-project-types"></a>檢查清單：建立新的專案類型
您必須完成幾項工作，才能建立新的專案類型。 下列檢查清單提供這些工作的指南：

1. 為您的新專案類型設計功能。 如需詳細資訊，請參閱 [專案類型設計決策](../../extensibility/internals/project-type-design-decisions.md)。

2. 判斷哪些編輯器用於程式碼和其他專案專案。 您可以使用 [核心] 或 [標準編輯器]，也可以建立和使用專案特定的編輯器。 如需詳細資訊，請參閱 [建立自訂編輯器和設計](../../extensibility/creating-custom-editors-and-designers.md) 工具和 [如何：開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)。

3. 判斷您的專案專案在 **類別檢視** 與 **物件瀏覽器** 中的參與程度。 如需詳細資訊，請參閱 [支援符號流覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。

4. 根據您先前為專案和專案專案所做的設計決策，來衍生新的類別。

5. 撰寫下列專案類型元件的程式碼：

    - Project factory：管理建立新專案和開啟現有的專案。 如需詳細資訊，請參閱 [使用專案處理站建立專案實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。

    - 專案階層和命令處理。 如需詳細資訊，請參閱 [使用 HierUtil7 專案類別來執行 c + +) 的專案 (類型 ](/previous-versions/bb166212(v=vs.100))、 [專案模型的](../../extensibility/internals/elements-of-a-project-model.md)專案、 [專案模型核心元件](../../extensibility/internals/project-model-core-components.md)，以及 [menucommand 對比與 OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)的比較。

    - 專案專案管理，包括將專案加入至 [ **新增專案** ] 對話方塊。 如需詳細資訊，請參閱 [加入專案和專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md) ，以及 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)。

    - 專案狀態和個別專案的持續性。 如需詳細資訊，請參閱 [開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)。 如需解決方案資訊的持續性，請參閱 [方案](../../extensibility/internals/solutions-overview.md)。

    - 要在屬性視窗中顯示的設定獨立屬性。 如需詳細資訊，請參閱 [擴充屬性](../../extensibility/internals/extending-properties.md)。

    - 在屬性頁中執行的專案設定屬性，以顯示與設定相依的屬性。 如需詳細資訊，請參閱 [管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

    - 列舉部署的輸出。 如需詳細資訊，請參閱 [輸出的專案](../../extensibility/internals/project-configuration-for-output.md)設定。

    - 專案啟動服務。 如需詳細資訊，請參閱專案模型和[專案模型核心元件](../../extensibility/internals/project-model-core-components.md)[的元素](../../extensibility/internals/elements-of-a-project-model.md)。

    - 可以自動化的物件或衍生自的類別 `IDispatch` 。

    - XML 命令表 (*. .vsct*) 檔。 如需詳細資訊，請參閱 [Visual Studio 命令表格 (. .vsct) ](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔。

6. 測試、偵測和啟動您的專案類型。

7. 藉由設定為的值，在 [**加入參考**] 對話方塊的 [**專案**] 索引標籤中顯示您的專案 `VARIANT_TRUE` `VSHPROPID_ShowProjInSolutionPage` 。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。

8. 建立 Microsoft Installer (*.msi*) 檔案，以安裝您的 vspackage。 如需詳細資訊，請參閱 [使用 Windows Installer 安裝 vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)、 [註冊專案類型](../../extensibility/internals/registering-a-project-type.md)和 [vspackage](../../extensibility/internals/vspackages.md)。

## <a name="see-also"></a>另請參閱
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [建立專案類型的時機](../../extensibility/internals/when-to-create-project-types.md)
- [建立專案類型](../../extensibility/internals/creating-project-types.md)