---
title: Visual Studio 命令的 Guid 和識別碼 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7670eacc875bf7c5437d9bb92cc1932753093bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186649"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio 命令的 Guid 和識別碼
Visual Studio 整合式開發環境（IDE）中所包含命令的 GUID 和 ID 值，是在 Visual Studio SDK 中安裝的 .vsct 檔案中定義。 如需詳細資訊，請參閱[IDE 定義的命令、功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

 如需如何使用 *.vsct*檔案中定義之 IDE 物件的詳細資訊，請參閱[擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

## <a name="find-a-command-definition"></a>尋找命令定義
 由於 Visual Studio 定義了1000個以上的命令，因此在此列出全部不可行。 相反地，請遵循下列步驟來找出命令的定義。

### <a name="to-locate-a-command-definition"></a>找出命令定義

1. 在 Visual Studio 中，開啟 *< VISUAL STUDIO SDK 安裝路徑*中的下列檔案\>\VisualStudioIntegration\Common\Inc\\資料夾： *SharedCmdDef .vsct*、 *ShellCmdDef. .vsct*、VsDbgCmdUsed *。* *Venusmenu. .vsct*。

    大部分的 Visual Studio 命令都定義于*SharedCmdDef. .vsct*和*ShellCmdDef. .vsct*中。 *VsDbgCmdUsed*會定義與偵錯工具相關的命令，而*Venusmenu*則會定義 Web 開發特有的命令。

2. 如果命令是功能表項目，請注意功能表項目的確切文字。 如果命令是工具列上的按鈕，請注意在其上暫停時所顯示的工具提示文字。

3. 按**Ctrl**+**F**以開啟 [**尋找**] 對話方塊。

4. 在 [**尋找目標**] 方塊中，輸入您在步驟2記下的文字。

5. 確認**所有開啟的檔**都顯示在 [**查詢**] 方塊中。

6. 按一下 [**尋找下一個]** 按鈕，直到在[按鈕元素](../../extensibility/button-element.md)的 [`<Strings>`] 區段中選取文字為止。

    命令出現在中的 `<Button>` 元素是命令定義。

   找到命令定義之後，您可以建立一個[CommandPlacement](../../extensibility/commandplacement-element.md)專案，其具有與命令相同的 `guid` 和 `id` 值，將命令的複本放在另一個功能表或工具列上。 如需詳細資訊，請參閱[建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。

### <a name="special-cases"></a>特殊案例
 在下列情況下，功能表文字或工具提示文字可能不會完全符合命令定義中的內容。

- 包含加底線的字元的功能表項目，**例如 [檔案] 功能表上**的 [**列印**] 命令，其中*P*會加上底線。

     在功能表項目名稱中，前面加上連字號（&）字元的字元會顯示為加底線。 不過， *.vsct*檔案是以 XML 撰寫的，它會使用連字號（&）字元來表示特殊字元，而且必須將符號顯示為 *&amp;amp;* 。 因此，在 *.vsct*檔案中， **Print**命令會顯示為 *&amp;amp;列印*。

- 具有動態文字的命令，例如 [**儲存**\<目前的檔案名\>] 和 [動態產生的功能表項目]，例如 [**最近使用**的檔案] 清單中的專案。

     沒有可靠的方法可搜尋動態文字。 相反地，請尋找裝載所需命令的群組，方法是諮詢[Visual Studio 功能表的 guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)[和 Visual Studio 工具列的 guid 和](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)識別碼，然後搜尋該群組的識別碼。 如果命令定義沒有群組做為其[父元素](../../extensibility/parent-element.md)，請搜尋*SharedCmdPlace .vsct*和*ShellCmdPlace. .vsct* （或適用于偵錯工具命令的*VsDbgCmdPlace. .vsct* ），以取得設定之父系的 `<CommandPlacement>` 元素。命令. *SharedCmdPlace. .vsct*、 *ShellCmdPlace .vsct*和*VsDbgCmdPlace. .vsct*位於 *\<Visual Studio SDK 安裝路徑\>\VisualStudioIntegration\Common\Inc\\* 資料夾中。

## <a name="see-also"></a>請參閱

- [Visual Studio 命令資料表（. .vsct）檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [.VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)
