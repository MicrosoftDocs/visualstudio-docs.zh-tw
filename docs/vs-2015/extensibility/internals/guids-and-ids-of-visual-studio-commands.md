---
title: 命令的 Guid 和識別碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2feef3cbe72b7eb8db96052236fe483733e22273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538134"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio 命令的 GUID 和識別碼
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 整合式開發環境中所包含命令的 GUID 和識別碼值 (IDE) 是在安裝為 Visual Studio SDK 一部分的 .vsct 檔案中定義。 如需詳細資訊，請參閱 [IDE 定義的命令、功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

 如需如何使用 .vsct 檔中所定義 IDE 物件的詳細資訊，請參閱 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

## <a name="finding-a-command-definition"></a>尋找命令定義
 因為 Visual Studio 定義了1000個以上的命令，所以在這裡列出它們是不切實際的。 相反地，請依照下列步驟來找出命令的定義。

#### <a name="to-locate-a-command-definition"></a>找出命令定義

1. 在 Visual Studio 中，開啟 *VISUAL STUDIO SDK 安裝路徑*\VisualStudioIntegration\Common\Inc\ 資料夾中的下列檔案： SharedCmdDef. .Vsct、ShellCmdDef. .Vsct、VsDbgCmdUsed. .Vsct、Venusmenu. .vsct。

    大部分 Visual Studio 的命令都定義于 SharedCmdDef. .vsct 和 ShellCmdDef. .vsct 中。 VsDbgCmdUsed 會定義與偵錯工具相關的命令，而 Venusmenu 則會定義 Web 開發專用的命令。

2. 如果命令是功能表項目，請注意功能表項目的確切文字。 如果命令是工具列上的按鈕，請注意當您暫停時所顯示的工具提示文字。

3. 按 CTRL + F 以開啟 [ **尋找** ] 對話方塊。

4. 在 [ **尋找目標** ] 方塊中，輸入您在步驟2記下的文字。

5. 確認 **所有開啟的檔** 都顯示在 [ **查詢** ] 方塊中。

6. 按一下 [ **尋找下一個]** 按鈕，直到在 `<Strings>` [button 元素](../../extensibility/button-element.md)的區段中選取文字為止。

    `<Button>`命令出現在中的元素是命令定義。

   當您找到命令定義之後，您可以藉由建立與命令具有相同和值的 [CommandPlacement](../../extensibility/commandplacement-element.md) 專案，將命令的複本放在另一個功能表或工具列上 `guid` `id` 。 如需詳細資訊，請參閱 [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。

### <a name="special-cases"></a>特殊案例
 在下列情況下，功能表文字或工具提示文字可能不會與命令定義中的內容完全相符。

- 包含加底線的字元的功能表項目，**例如 [檔案] 功能表上**的 [**列印**] 命令，其中的 P 會加上底線。

     在功能表項目名稱中加上 ' & ' 字元的字元會顯示為加上底線。 不過，.vsct 檔案是以 XML 撰寫的，使用 ' & ' 字元來表示特殊字元，而且必須要顯示的 & 符號必須標記為 ' &amp; '。 因此，在 .vsct 檔案中， **print** 命令會顯示為「 &amp; 列印」。

- 具有動態文字的命令，例如**儲存***目前的檔案名*，以及動態產生的功能表項目，例如 [**最近使用**的檔案] 清單上的專案。

     沒有可靠的方式可以搜尋動態文字。 相反地，請透過查閱 [guid 和 id Visual Studio 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 或 [Guid 和 Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)的識別碼，尋找裝載所需命令的群組，並搜尋該群組的識別碼。 如果命令定義沒有群組做為其 [父元素](../../extensibility/parent-element.md)，請搜尋 SharedCmdPlace. .Vsct 和 ShellCmdPlace. .vsct (或 VsDbgCmdPlace. .vsct for 偵錯工具命令，) 針對 `<CommandPlacement>` 設定命令父系的元素。 SharedCmdPlace. .vsct、ShellCmdPlace. .vsct、andVsDbgCmdPlace. .vsct 位於 *VISUAL STUDIO SDK 安裝路徑*\VisualStudioIntegration\Common\Inc\ 資料夾中。

## <a name="see-also"></a>另請參閱
 [Menucommand 對比與 OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) [Visual Studio 命令資料表 (。.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [.Vsct XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)
