---
title: Visual Studio 命令的 Guid 和 Id |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1440eb7da0299b79aa063d999d581cc159a88e50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898290"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio 識別碼和 Guid 的命令
已安裝 Visual Studio SDK 的一部分的.vsct 檔案中定義的 Visual Studio 整合式的開發環境 (IDE) 中包含的命令 GUID 和 ID 值。 如需詳細資訊，請參閱 < [IDE 定義的命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 如需有關如何使用 IDE 中所定義的物件 *.vsct*檔，請參閱[擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## <a name="find-a-command-definition"></a>尋找命令定義  
 Visual Studio 定義超過 1000 個的命令，因為我們不能此處列出它們。 相反地，請遵循下列步驟來找出命令的定義。  
  
### <a name="to-locate-a-command-definition"></a>若要找出命令定義  
  
1. 在 Visual Studio 中，開啟下列檔案中的 *< Visual Studio SDK 安裝路徑\>\VisualStudioIntegration\Common\Inc\\* 資料夾：*SharedCmdDef.vsct*， *ShellCmdDef.vsct*， *VsDbgCmdUsed.vsct*， *Venusmenu.vsct*。  
  
    大部分的 Visual Studio 命令定義於*SharedCmdDef.vsct*並*ShellCmdDef.vsct*。 *VsDbgCmdUsed.vsct*定義命令的相關偵錯工具，並*Venusmenu.vsct*定義專屬於 Web 開發的命令。  
  
2. 如果命令的功能表項目，請注意功能表項目的的確切文字。 如果工具列上的按鈕命令，請注意當您暫停它時所顯示的工具提示文字。  
  
3. 按下**Ctrl**+**F**以開啟**尋找** 對話方塊。  
  
4. 在 **尋找目標**方塊中，輸入步驟 2 記下的文字。  
  
5. 確認**所有開啟的文件**會顯示在**查看** 方塊中。  
  
6. 按一下 **尋找下一步**按鈕，直到中選取的文字`<Strings>`一節[按鈕項目](../../extensibility/button-element.md)。  
  
    `<Button>`命令中所顯示的項目是命令定義。  
  
   當您發現命令定義時，您可以藉由建立另一個功能表或工具列上放置一份命令[CommandPlacement 元素](../../extensibility/commandplacement-element.md)具有相同`guid`和`id`做為命令的值。 如需詳細資訊，請參閱 <<c0> [ 建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
### <a name="special-cases"></a>特殊案例  
 在下列情況中，功能表文字或工具提示文字可能不完全相同功能的命令定義。  
  
-   功能表項目包含未加上底線的字元，例如**列印**命令**檔案**功能表上，在其中*P*會加上底線。  
  
     會加上連字號的字元 (&) 中的功能表項目名稱字元會顯示為加上底線。 不過， *.vsct*檔案會在 XML 中，使用連字號 (&) 字元表示特殊字元，且需要顯示連字號必須拼出，做為寫入 *&amp;a m p;*。 因此，在 *.vsct*檔案，**列印**命令會顯示成 *&amp;a m p;列印*。  
  
-   命令，例如具有動態的文字**儲存**\<目前的檔名\>，和動態產生功能表項目，例如項目**最近使用的檔案**清單。  
  
     沒有任何可靠的方法，以進行動態文字搜尋。 相反地，尋找 群組可裝載所需的命令諮詢[Visual Studio 識別碼和 Guid 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Guid 和 Id Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)，並搜尋該群組的識別碼。 如果命令不需要定義群組做為其[父元素](../../extensibility/parent-element.md)，搜尋*SharedCmdPlace.vsct*並*ShellCmdPlace.vsct* (或*VsDbgCmdPlace.vsct*偵錯工具命令) 的`<CommandPlacement>`設定命令的父代的項目。 *SharedCmdPlace.vsct*， *ShellCmdPlace.vsct*，以及*VsDbgCmdPlace.vsct*位於*\<Visual Studio SDK 安裝路徑\>\VisualStudioIntegration\Common\Inc\\*資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [Menucommand 對比OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio 命令表檔案 (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
