---
title: 清單:建立新的項目類型 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709742"
---
# <a name="checklist-create-new-project-types"></a>檢查表:建立新的項目型態
您必須完成多個工作才能建立新的項目類型。 以下檢查表提供了這些工作的指南:

1. 設計新項目類型的功能。 有關詳細資訊,請參閱[項目類型設計決策](../../extensibility/internals/project-type-design-decisions.md)。

2. 確定哪些編輯器用於代碼和其他項目元素。 您可以使用核心編輯器或標準編輯器,也可以創建和使用特定於專案的編輯器。 有關詳細資訊,請參閱[建立自訂編輯器和設計器](../../extensibility/creating-custom-editors-and-designers.md)[以及如何:開啟特定於項目的編輯器](../../extensibility/how-to-open-project-specific-editors.md)。

3. 確定專案專案在**類視圖**和**物件瀏覽器**中的參與程度。 有關詳細資訊,請參閱[支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。

4. 基於您以前為專案和專案專案專案所做的設計決策派生新類。

5. 為以下項目型態元件編寫碼:

    - 項目工廠,管理創建新專案和打開現有專案。 關於詳細資訊,請參閱[使用專案工廠建立項目實例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)。

    - 項目層次結構和命令處理。 有關詳細資訊,請參閱使用[HierUtil7 專案類別來實現專案類型(C++)、](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)[專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md),[專案模型核心元件](../../extensibility/internals/project-model-core-components.md)以及[MenuCommands 與 OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)。

    - 專案專案管理,包括將專案添加到 **「新項目**」對話方塊。 有關詳細資訊,請參閱[新增專案和專案項目樣本](../../extensibility/internals/adding-project-and-project-item-templates.md)以及[註冊項目和專案樣本](../../extensibility/internals/registering-project-and-item-templates.md)。

    - 項目狀態和單個項的持久性。 有關詳細資訊,請參閱[開啟和儲存項目項目](../../extensibility/internals/opening-and-saving-project-items.md)。 有關解決方案資訊的持久性,請參閱[解決方案](../../extensibility/internals/solutions-overview.md)。

    - 要在"屬性"視窗中顯示與配置無關的屬性。 有關詳細資訊,請參閱[副檔屬性](../../extensibility/internals/extending-properties.md)。

    - 在屬性頁中實現的專案配置屬性以顯示與配置相關的屬性。 關於詳細資訊,請參考[管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

    - 枚舉部署的輸出。 有關詳細資訊,請參閱[輸出的項目設定](../../extensibility/internals/project-configuration-for-output.md)。

    - 項目啟動服務。 有關詳細資訊,請參閱[專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)與[專案模型核心元件](../../extensibility/internals/project-model-core-components.md)。

    - 物件或派生自`IDispatch`的類可用於自動化。

    - XML 指令表 (*.vsct*) 檔案。 有關詳細資訊,請參閱[可視化工作室命令表 (.vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

6. 測試、調試和啟動項目類型。

7. 通過將`VARIANT_TRUE`設置`VSHPROPID_ShowProjInSolutionPage`為的值,在 **「添加參考」** 對話方塊的「**項目**」選項卡中顯示專案。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。

8. 建立用於安裝 VS 套件的 Microsoft 安裝程式 (*.msi*) 檔案。 有關詳細資訊,請參閱使用[Windows 安裝程式安裝 VS 套件](../../extensibility/internals/installing-vspackages-with-windows-installer.md),[註冊項目類型](../../extensibility/internals/registering-a-project-type.md)與[VS 套件](../../extensibility/internals/vspackages.md)。

## <a name="see-also"></a>另請參閱
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [何時建立項目型態](../../extensibility/internals/when-to-create-project-types.md)
- [建立項目型態](../../extensibility/internals/creating-project-types.md)
