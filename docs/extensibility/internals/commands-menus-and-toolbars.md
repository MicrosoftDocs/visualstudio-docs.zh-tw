---
title: 命令、功能表和工具列 |Microsoft Docs
description: 瞭解 Visual Studio 中的命令、功能表和工具列，包括這些命令、功能表和工具列，以及它們在 Vspackage 中的運作方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad763e748fc20a9704df48b17a5d3d8d40c3883c
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304790"
---
# <a name="commands-menus-and-toolbars"></a>命令、功能表和工具列
功能表和工具列是使用者存取 VSPackage 命令的方式。 命令是完成工作 (例如，列印文件、重新整理檢視，或建立新檔案) 的功能。 功能表和工具列是一種圖形方式，方便向使用者呈現您的命令。 通常，相關的命令會一起聚集在相同的功能表或工具列上。

- 功能表通常會顯示為聚集在整合式開發環境 (IDE) 或工具視窗頂端的一連串單字字串。 功能表也可以顯示為滑鼠右鍵事件的結果，並且指的是該內容中的快顯功能表。 按一下時，會展開功能表以顯示一個或多個命令。 按一下時，命令可以執行工作，或啟動包含其他命令的子功能表。 某些 **知名的功能表名稱是 [** 檔案]、[ **編輯**]、[ **視圖**] 和 [ **視窗]**。 如需詳細資訊，請參閱 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

- 工具列通常是數串的按鈕和其他控制項 (例如下拉式方塊、清單方塊、文字方塊和功能表控制器)。 所有工具列控制項都是與命令相關聯。 按一下工具列按鈕時，會啟動其相關聯的命令。 工具列按鈕通常會有圖示建議基礎命令 (例如 [列印] 命令的印表機)。 在下拉式清單控制項中，清單中的每個項目都是與不同的命令相關聯。 功能表控制器是一種混合體，其中，控制項的一邊是工具列按鈕，另一邊則是按一下時顯示其他命令的向下箭號。 如需詳細資訊，請參閱 [將功能表控制器加入至工具列](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)。

- 建立命令時，也必須一併建立它的事件處理常式。 事件處理常式可判斷命令的顯示和啟用時間、可讓您修改其文字，並確保在啟動時適當地回應命令 (路由遞送)。 在大部分情況下，IDE 會使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面來處理命令。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中的命令會以階層方式路由遞送，即從最內層命令內容開始 (根據本機選取範圍) 到最外層內容 (根據全域選取範圍)。 加入主功能表的命令可立即用於指令碼編寫。 如需詳細資訊，請參閱 [menucommand 對比與 OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015) 和 [選取內容物件](../../extensibility/internals/selection-context-objects.md)。

  若要定義新的功能表和工具列，您必須在 Visual Studio 的命令資料表中加以描述， (*. .vsct*) 檔。 Visual Studio 套件範本會為您建立此檔案，並提供必要的元素，以支援您在範本中選取的任何命令、工具列和編輯器。 或者，您也可以使用以下所述的 XML 架構來撰寫您自己的 *.vsct* 檔案： [.vsct XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)。

  如需使用 *.vsct* 檔案的詳細資訊，請參閱 [Visual Studio 命令表格 (. .vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔。

  本節中的主題說明命令、功能表和工具列在 Vspackage 中的運作方式。

## <a name="in-this-section"></a>本節內容
- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 命令表格格式規格的深入說明。

- [Visual Studio 命令表格 (. .vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 描述命令資料表的 XML 語法和編譯器。

- [預設命令、群組和工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 描述預先定義的命令、群組、功能表和工具列。

- [IDE 定義的命令、功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 指定可供 IDE 使用的預先定義功能表、命令和命令群組 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [命令設計](../../extensibility/internals/command-design.md)

 說明如何設計命令。

- [優化功能表和工具列命令](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 提供命令的指導方針。

- [讓命令可供使用](../../extensibility/internals/making-commands-available.md)

 說明如何讓命令可用於 Visual Studio。

- [使用 interop 元件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 說明如何執行使用 interop 元件的命令。

## <a name="related-sections"></a>相關章節
- [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)

 說明 Vspackage 中的命令路由。