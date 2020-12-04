---
title: 命令別名
description: 瞭解當您想要執行命令時，如何使用命令別名來輸入較少的字元。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dda564939652a09b64fec65747ca14d1315b3f1
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561067"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Command Aliases

命令別名可讓您在想要執行命令時鍵入較少的字元。 您要將別名鍵入到 [尋找/命令] 方塊或 [命令] 視窗。 例如，您可以使用預先定義的別名 `>of` (而不是輸入 `>File.OpenFile`)，來顯示 [開啟檔案] 對話方塊。

在 [命令] 視窗中鍵入 `alias` 可顯示目前的別名及其定義。 鍵入 `>cls` 可清除 [命令] 視窗的內容。 如果您想要查看特定命令的別名，請鍵入 `alias <command name>`。

您可以輕鬆地為其中一個 Visual Studio 命令 (不論是否包含引數) 建立自己的別名。 例如，`File.NewFile MyFile.txt` 的別名語法是 `alias MyAlias File.NewFile MyFile.txt`。 您可以使用 `alias <alias name> /delete` 刪除其中一個別名

下表包含預先定義的 Visual Studio 命令別名清單。 部分命令名稱有多個預先定義的別名。 按一下下列命令名稱的連結，即可顯示說明這些命令之正確語法、引數和參數的詳細主題。

|命令名稱：|Alias|完整名稱|
|------------------|-----------|-------------------|
|[列印命令](../../ide/reference/print-command.md)|?|Debug.Print|
|[快速監看式命令](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|新增專案|AddProj|File.AddNewProject|
|[Alias 命令](../../ide/reference/alias-command.md)|Alias|Tools.Alias|
|自動變數視窗|自動|Debug.Autos|
|中斷點視窗|bl|Debug.Breakpoints|
|切換中斷點|bp|Debug.ToggleBreakPoint|
|[呼叫堆疊] 視窗|CallStack|Debug.CallStack|
|清除書籤|ClearBook|Edit.ClearBookmarks|
|關閉|關閉|File.Close|
|關閉所有文件|CloseAll|Window.CloseAllDocuments|
|全部清除|cls|Edit.ClearAll|
|命令模式|cmd|View.CommandWindow|
|檢視程式碼|code|View.ViewCode|
|[列出記憶體命令](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[列出記憶體命令](../../ide/reference/list-memory-command.md)為 ANSI|da|Debug.ListMemory /Ansi|
|[列出記憶體命令](../../ide/reference/list-memory-command.md) (一位元組格式)|db|Debug.ListMemory /Format:OneByte|
|[列出記憶體命令](../../ide/reference/list-memory-command.md)為 ANSI (四位元組格式)|dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[列出記憶體命令](../../ide/reference/list-memory-command.md) (四位元組格式)|dd|Debug.ListMemory /Format:FourBytes|
|刪除至行開頭 (BOL)|DelBOL|Edit.DeleteToBOL|
|刪除至行結尾 (EOL)|DelEOL|Edit.DeleteToEOL|
|刪除水平空白|DelHSp|Edit.DeleteHorizontalWhitespace|
|檢視設計工具|設計工具|View.ViewDesigner|
|[列出記憶體命令](../../ide/reference/list-memory-command.md) (浮點數格式)|df|Debug.ListMemory/Format:Float|
|反組譯碼視窗|disasm|Debug.Disassembly|
|[列出記憶體命令](../../ide/reference/list-memory-command.md) (八位元組格式)|dq|Debug.ListMemory /Format:EightBytes|
|[列出記憶體命令](../../ide/reference/list-memory-command.md)為 Unicode|du|Debug.ListMemory /Unicode|
|[評估語句命令](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|
|結束|結束|File.Exit|
|格式化選取範圍|format|Edit.FormatSelection|
|全螢幕|FullScreen|View.FullScreen|
|[Start 命令](../../ide/reference/start-command.md)|g|Debug.Start|
|[移至命令](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|移至大括號|GotoBrace|Edit.GotoBrace|
|F1Help|説明|Help.F1Help|
|即時模式|immed|Tools.ImmediateMode|
|以文字形式插入檔案|InsertFile|Edit.InsertFileAsText|
|[列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)|kb|Debug.ListCallStack|
|變成小寫|Lcase|Edit.MakeLowercase|
|剪下行|LineCut|Edit.LineCut|
|刪除行|LineDel|Edit.LineDelete|
|列出成員|ListMembers|Edit.ListMembers|
|[區域變數] 視窗|本機|Debug.Locals|
|[記錄命令視窗輸出命令](../../ide/reference/log-command-window-output-command.md)|記錄|Tools.LogCommandWindowOutput|
|命令視窗標記模式|mark|Tools.CommandWindowMarkMode|
|記憶體視窗|Memory Memory1|Debug.Memory1|
|記憶體視窗 2|Memory2|Debug.Memory2|
|記憶體視窗 3|Memory3|Debug.Memory3|
|記憶體視窗 4|Memory4|Debug.Memory4|
|[設定基數命令](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[ShowWebBrowser 命令](../../ide/reference/showwebbrowser-command.md)|nav navigate|View.ShowWebBrowser|
|下一個書籤|NextBook|Edit.NextBookmark|
|[新增檔案命令](../../ide/reference/new-file-command.md)|nf|File.NewFile|
|新增專案|np NewProj|File.NewProject|
|[開啟檔案命令](../../ide/reference/open-file-command.md)|of Open|File.OpenFile|
|[開啟專案命令](../../ide/reference/open-project-command.md)|op|File.OpenProject|
|摺疊至定義/取消大綱|OutlineDefs StopOutlining|Edit.CollapseToDefinitions|
|不進入函數|p|Debug.StepOver|
|參數資訊|ParamInfo|Edit.ParameterInfo|
|跳出|pr|Debug.StepOut|
|上一個書籤|PrevBook|Edit.PreviousBookmark|
|列印檔案|print|File.Print|
|屬性視窗|props|View.PropertiesWindow|
|停止|q|Debug.StopDebugging|
|取消復原|重做|Edit.Redo|
|暫存器視窗|暫存器|Debug.Registers|
|執行至游標處|rtc|Debug.RunToCursor|
|儲存選取的項目|儲存|File.SaveSelectedItems|
|全部儲存|SaveAll|File.SaveAll|
|另存新檔|SaveAs|File.SaveSelectedItemsAs|
|[Shell 命令](../../ide/reference/shell-command.md)|殼層|Tools.Shell|
|停止在檔案中尋找|StopFind|Edit.FindInFiles /stop|
|交換錨點|SwapAnchor|Edit.SwapAnchor|
|逐步執行|t|Debug.StepInto|
|將選取範圍空白鍵轉定點|空白鍵轉定位鍵|Edit.TabifySelection|
|工作清單視窗|TaskList|View.TaskList|
|執行緒視窗|執行緒|Debug.Threads|
|水平並排顯示|TileH|Window.TileHorizontally|
|垂直並排|TileV|Window.TileVertically|
|切換書籤|ToggleBook|Edit.ToggleBookmark|
|[工具箱] 視窗|工具箱|View.Toolbox|
|[列出反組解碼命令](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|設成大寫|Ucase|Edit.MakeUppercase|
|復原|恢復|Edit.Undo|
|將選取範圍定位點轉空白|Untabify|Edit.UntabifySelection|
|監看式視窗|觀看|Debug.WatchN|
|切換自動換行|WordWrap|Edit.ToggleWordWrap|
|列出處理序|&#124;|Debug.ListProcesses|
|[列出執行緒命令](../../ide/reference/list-threads-command.md)|~ ~*k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
