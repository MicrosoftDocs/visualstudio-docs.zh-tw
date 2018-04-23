---
title: Guid 和 Id 的 Visual Studio 命令 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 1566b7e252867779e2bf7cbf26e2a6cbcb8b009f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Guid 和 Id 的 Visual Studio 命令
會安裝 Visual Studio SDK 的一部分的.vsct 檔案中定義的 GUID 和 ID 的值包含在 Visual Studio 整合式的開發環境 (IDE) 中的命令。 如需詳細資訊，請參閱[IDE-Defined 命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 如需如何使用 IDE.vsct 檔案中定義的物件的詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
## <a name="finding-a-command-definition"></a>尋找命令定義  
 因為 Visual Studio 會定義超過一千命令，所以予以列出，這裡並不實用。 相反地，請遵循下列步驟來找出命令的定義。  
  
#### <a name="to-locate-a-command-definition"></a>若要找出命令定義  
  
1.  在 Visual Studio 中，開啟下列檔案中的*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc\ 資料夾： SharedCmdDef.vsct、 ShellCmdDef.vsct、 VsDbgCmdUsed.vsct、 Venusmenu.vsct。  
  
     Visual Studio 的大部分命令 SharedCmdDef.vsct 和 ShellCmdDef.vsct 中定義。 VsDbgCmdUsed.vsct 定義命令的相關偵錯工具，而 Venusmenu.vsct 定義專屬於 Web 程式開發的命令。  
  
2.  如果命令是功能表項目，請注意功能表項目的的確切文字。 如果工具列上的按鈕命令，請注意當您暫停它時所顯示的工具提示文字。  
  
3.  按下 CTRL + F 可以開啟**尋找** 對話方塊。  
  
4.  在**尋找**方塊中，輸入在步驟 2 中記下的文字。  
  
5.  確認**所有開啟的文件**會顯示在**查看**方塊。  
  
6.  按一下**找下一個**按鈕中選取的文字，直到`<Strings>`區段[按鈕項目](../../extensibility/button-element.md)。  
  
     `<Button>`命令會在出現的項目，則命令定義。  
  
 當您已經找到命令定義時，您可以藉由建立另一個功能表或工具列上放置一份命令[CommandPlacement 元素](../../extensibility/commandplacement-element.md)，具有相同的`guid`和`id`做為命令的值。 如需詳細資訊，請參閱[建立可重複使用群組的按鈕](../../extensibility/creating-reusable-groups-of-buttons.md)。  
  
### <a name="special-cases"></a>特殊案例  
 在下列情況中，功能表文字或工具提示文字可能不完全相同功能的命令定義。  
  
-   功能表項目，包括加底線的字元，例如**列印**命令**檔案**功能表上，在其中 P 加上底線。  
  
     所顯示的功能表項目名稱中的 '&' 字元前面附加的字元，加上底線。 不過，.vsct 檔案以 XML 撰寫，會使用 '&' 字元，來指示特殊字元，並且需要顯示以連字號，必須使用拼字為&amp;'。 因此，在.vsct 檔案中， **P**rint 命令會顯示成 '&amp;列印 '。  
  
-   命令，具有動態文字，例如**儲存***目前檔案名稱*，並以動態方式產生功能表項目，例如項目上**最近使用的檔案**清單。  
  
     沒有可靠的方式可搜尋的動態文字。 相反地，尋找裝載查閱所需的命令群組[Guid 和 Id 的 Visual Studio 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)或[Guid 和 Id 的 Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)，並搜尋該群組的識別碼。 如果命令不需要定義群組做為其[父項目](../../extensibility/parent-element.md)，搜尋 SharedCmdPlace.vsct 和 ShellCmdPlace.vsct （或偵錯工具命令的 VsDbgCmdPlace.vsct）`<CommandPlacement>`設定的父系的項目命令。 SharedCmdPlace.vsct，ShellCmdPlace.vsct，andVsDbgCmdPlace.vsct 位於*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc\ 資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [MenuCommand 對比OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)