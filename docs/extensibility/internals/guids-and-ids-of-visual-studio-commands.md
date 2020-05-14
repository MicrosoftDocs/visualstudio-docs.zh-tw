---
title: Visual Studio 命令的 GUID 和 IT |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708259"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio 指令的 GUID 和 IT
Visual Studio 整合式開發環境 (IDE) 中包含的指令的 GUID 和 ID 值在作為 Visual Studio SDK 的一部分安裝的 .vsct 檔案中定義。 有關詳細資訊,請參閱[IDE 定義的指令、選單和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

 有關如何處理*在 .vsct*檔中定義的 IDE 物件的詳細資訊,請參閱[延伸選單和指令](../../extensibility/extending-menus-and-commands.md)。

## <a name="find-a-command-definition"></a>尋找指令定義
 由於 Visual Studio 定義了 1000 多個命令,因此在此處列出所有這些命令是不切實際的。 相反,請按照以下步驟查找命令的定義。

### <a name="to-locate-a-command-definition"></a>尋找指令定義

1. 在 Visual Studio 中,在 *<Visual Studio\>SDK 安裝路徑\\[VisualStudio 集成]公共_Inc*資料夾中打開以下檔:SharedCmdDef.vsct、ShellCmdDef.vsct、VsDbgCmdUsed.vsct、Venusmenu.vsct 。 *SharedCmdDef.vsct* *ShellCmdDef.vsct* *VsDbgCmdUsed.vsct* *Venusmenu.vsct*

    大多數可視化工作室命令在*SharedCmdDef.vsct*和*ShellCmdDef.vsct 中*定義。 *VsDbgCmdUsed.vsct*定義與除錯器相關的命令 *,Venusmenu.vsct*定義特定於 Web 開發的命令。

2. 如果命令是功能表項,請注意功能表項的確切文本。 如果該命令是工具列上的按鈕,請注意暫停時顯示的工具提示文本。

3. 按**Ctrl**+**F**打開「**搜尋」** 對話框。

4. 在「**尋找內容」** 框中,鍵入您在步驟 2 中注意到的文字。

5. 認證**所有開啟的文件**是否顯示在「**檢視」** 框中。

6. 按下 **「 尋找下一步**」按鈕,直到`<Strings>`在[按鈕元素](../../extensibility/button-element.md)部分中選擇文本。

    該`<Button>`命令中顯示的元素是命令定義。

   找到命令定義後,可以通過創建與命令具有`guid`相同`id`和 值的 Command[放置元素](../../extensibility/commandplacement-element.md)將命令的副本放在另一個功能表或工具列上。 關於詳細資訊,請參閱[建立可重用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。

### <a name="special-cases"></a>特殊案例
 在以下情況下,功能表文本或工具提示文本可能不完全匹配命令定義中的內容。

- 包含帶下劃線字元的功能表項,如 **「檔**」功能表上的 **「列印」** 命令,其中*P*加下下劃線。

     選單項名稱中由 & 字元開頭的字元顯示為下劃線。 但是 *,.vsct*檔用 XML 編寫,它使用安培 (&) 字元來指示特殊字元,並且要求必須顯示要顯示的放大器必須拼寫為*&amp;amp;* 因此,在 *.vsct*檔中,「**列印」** 命令顯示為*&amp;amp;列印*。

- 具有動態文本的命令,如 **「儲存**\<當前檔\>名」和動態生成的功能表項,如 **「最近檔**」清單中的專案。

     沒有可靠的方法來搜索動態文本。 相反,通過查閱 Visual Studio 功能表的[GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或 Visual Studio[工具列的 GUID 和 ID,](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)並搜尋該組的 ID,找到承載所需命令的組。 如果命令定義沒有將組作為其[父元素](../../extensibility/parent-element.md),則搜索*SharedCmdPlace.vsct*和*ShellCmdPlace.vsct(* 或用於除錯器命令的*VsDbgCmdPlace.vsct)* 的元素`<CommandPlacement>`,以設定命令的父元素。 *SharedCmdPlace.vsct* *、ShellCmdPlace.vsct*和*VsDbgCmdPlace.vsct*位於*\<可視\>化工作室 SDK 安裝路徑\\[VisualStudio 集成]通用_Inc*資料夾中。

## <a name="see-also"></a>另請參閱

- [視覺化工作室指令表 (.vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)
