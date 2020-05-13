---
title: 指令、選單和工具列 |微軟文件
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
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709495"
---
# <a name="commands-menus-and-toolbars"></a>命令、選單和工具列
功能表和工具列是使用者存取 VSPackage 中命令的方式。 命令是完成工作 (例如，列印文件、重新整理檢視，或建立新檔案) 的功能。 功能表和工具列是一種圖形方式，方便向使用者呈現您的命令。 通常，相關的命令會一起聚集在相同的功能表或工具列上。

- 功能表通常會顯示為聚集在整合式開發環境 (IDE) 或工具視窗頂端的一連串單字字串。 功能表也可以顯示為滑鼠右鍵事件的結果，並且指的是該內容中的快顯功能表。 按一下時，會展開功能表以顯示一個或多個命令。 按一下時，命令可以執行工作，或啟動包含其他命令的子功能表。 一些著名的選單名稱是**檔案**,**編輯**, 檢視 ,**檢視**與**視窗**。 有關詳細資訊,請參閱[延伸選單和指令](../../extensibility/extending-menus-and-commands.md)。

- 工具列通常是數串的按鈕和其他控制項 (例如下拉式方塊、清單方塊、文字方塊和功能表控制器)。 所有工具列控制項都是與命令相關聯。 按一下工具列按鈕時，會啟動其相關聯的命令。 工具列按鈕通常會有圖示建議基礎命令 (例如 [列印] 命令的印表機)。 在下拉式清單控制項中，清單中的每個項目都是與不同的命令相關聯。 功能表控制器是一種混合體，其中，控制項的一邊是工具列按鈕，另一邊則是按一下時顯示其他命令的向下箭號。 關於詳細資訊,請參閱[將選單控制器加入工具列](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)。

- 建立命令時，也必須一併建立它的事件處理常式。 事件處理常式可判斷命令的顯示和啟用時間、可讓您修改其文字，並確保在啟動時適當地回應命令 (路由遞送)。 在大部分情況下，IDE 會使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面來處理命令。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中的命令會以階層方式路由遞送，即從最內層命令內容開始 (根據本機選取範圍) 到最外層內容 (根據全域選取範圍)。 加入主功能表的命令可立即用於指令碼編寫。 有關詳細資訊,請參閱[選單指令與 OleMenu 指令](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)與[選擇內容 。](../../extensibility/internals/selection-context-objects.md)

  要定義新功能表和工具列,必須在 Visual Studio 命令表 *(.vsct*) 檔中描述它們。 Visual Studio 包樣本為您創建此檔,以及支援範本選擇的任何命令、工具列和編輯器的必要元素。 或您可以使用此處描述的 XML 架構編寫自己的 *.vsct*檔案[:VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)。

  有關使用 *.vsct*檔案的詳細資訊,請參閱[可視化工作室命令表 (.vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

  本節中的主題介紹了命令、功能表和工具列在 VSPackages 中的工作方式。

## <a name="in-this-section"></a>本節內容
- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 命令表格式規範的深入描述。

- [視覺化工作室指令表 (.vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 描述命令表基於 XML 的語法和編譯器。

- [預設命令、群組與工具列放置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 描述預定義的命令、組、功能表和工具列。

- [IDE 定義的指令、選單和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 指定預先定義的功能表、命令和命令組可[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]供IDE使用。

- [指令設計](../../extensibility/internals/command-design.md)

 說明如何設計命令。

- [優化選單和工具列指令](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 提供命令的準則。

- [使命令可用](../../extensibility/internals/making-commands-available.md)

 說明如何使命令可供視覺工作室使用。

- [使用互通程式集的指令和選單](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 說明如何實現使用互操作程式集的命令。

## <a name="related-sections"></a>相關章節
- [VS 套件的指令路由](../../extensibility/internals/command-routing-in-vspackages.md)

 解釋 VSPackages 中的命令路由。
