---
title: 預設鍵盤快速鍵
description: 瞭解 Visual Studio 中的預設鍵盤快速鍵，可讓您存取各種命令和視窗。
ms.custom: SEO-VS-2020
ms.date: 06/21/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a63dbc1ad3ec544e52974a7ced9a69d4585ab629
ms.sourcegitcommit: b5744be07b7882e30bae67ef2810db56cf68344f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2021
ms.locfileid: "113487714"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Visual Studio 中的預設鍵盤快速鍵

您可以選擇適當的鍵盤快速鍵，在 Visual Studio 中存取各種[命令](reference/visual-studio-commands.md)和視窗。 此頁面會針對您可能已經在安裝 Visual Studio 時選擇的 [一般] 設定檔，列出預設命令捷徑。 無論您選擇哪一個設定檔，都可以開啟 [**選項**] 對話方塊，展開 [**環境**] 節點，然後選擇 [**鍵盤**] 來識別命令 [的快捷方式](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。 您也可以為指定的命令指派不同的捷徑，以自訂捷徑。

如需常用鍵盤快速鍵的清單和其他產能資訊，請參閱：

- [鍵盤祕訣](../ide/productivity-shortcuts.md)
- [生產力秘訣](../ide/productivity-features.md)。

如需 Visual Studio 中協助工具的詳細資訊，請參閱[協助工具秘訣和訣竅](../ide/reference/accessibility-tips-and-tricks.md)和 how [to：以獨佔方式使用鍵盤](../ide/reference/how-to-use-the-keyboard-exclusively.md)。

## <a name="most-popular-keyboard-shortcuts"></a>最熱門鍵盤快速鍵

除非另有指定，否則本節中的所有快速鍵都會全域套用。 「全域」內容表示快速鍵適用於 Visual Studio 中的任何工具視窗。

> [!NOTE]
> 您可以開啟 [選項] 對話方塊，展開 [環境] 節點，然後選擇 [鍵盤]，以[查看任何命令的捷徑](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。


#### <a name="build-popular-shortcuts"></a>組建：熱門快速鍵

|命令|鍵盤快速鍵 |命令 ID|
|-|-|-|
|組建方案|**Ctrl + Shift + B** | Build.BuildSolution |
|取消|**Ctrl + Break** | Build.Cancel |
|編譯|**Ctrl+F7** | Build.Compile |
|對解決方案執行程式碼分析|**Alt+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a>Debug：熱門快速鍵

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|遇到函數時中斷|**Ctrl + B**| Debug.BreakatFunction |
|全部中斷|**Ctrl + Alt + Break**| Debug.BreakAll |
|刪除所有中斷點|**Ctrl + Shift + F9**| Debug.DeleteAllBreakpoints |
|例外狀況|**Ctrl + Alt + E**| Debug.Exceptions |
|快速監看|**Ctrl + Alt + Q**<br /><br />或 **Shift + F9**| Debug.QuickWatch |
|重新啟動|**Ctrl+Shift+F5**| Debug.Restart |
|執行至游標處|**Ctrl + F10**| Debug.RunToCursor |
|設定下一個陳述式|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|開始|**F5**| Debug.Start |
|啟動但不進行調試|**Ctrl + F5**| Debug.StartWithoutDebugging |
|逐步執行|**F11**| Debug.StepInto |
|跳出|**Shift + F11**| Debug.StepOut |
|逐程序|**F10**| Debug.StepOver |
|停止偵錯|**Shift + F5**| Debug.StopDebugging |
|切換中斷點|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a>編輯：熱門快速鍵

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|中斷線|**Enter** [文字編輯器、報表設計工具、Windows Form 設計工具]<br /><br />或 **Shift + Enter** [文字編輯器]| Edit.BreakLine |
|折迭至定義|**Ctrl + M**、 **ctrl + O** [文字編輯器]| Edit.CollapseToDefinitions |
|批註選取範圍|**Ctrl + K**、 **ctrl + C** [文字編輯器]| Edit.CommentSelection |
|自動完成文字|**Alt + 向右箭** 號 [文字編輯器，工作流程設計工具]<br /><br />或 **Ctrl+空格鍵** [文字編輯器、工作流程設計工具]<br /><br />或 **Ctrl+K**、**W** [工作流程設計工具]<br /><br />或 **Ctrl+K、Ctrl+W** [工作流程設計工具]| Edit.CompleteWord |
|複製|**Ctrl + C**<br /><br />或 **Ctrl + Insert**| Edit.Copy |
|剪下|**Ctrl + X**<br /><br />或 **Shift + Delete**| Edit.Cut |
|刪除|**刪除** [Team Explorer]<br /><br />或 **Shift + Delete** [順序圖、UML 活動圖、分層圖]<br /><br />或 **Ctrl + Delete** [類別圖表]| Edit.Delete |
|Find|**Ctrl + F**| Edit.Find |
|尋找所有參考|**Shift + F12**| Edit.FindAllReferences |
|檔案中尋找|**Ctrl + Shift + F**| Edit.FindinFiles |
|尋找下一個|**F3**| Edit.FindNext |
|尋找下一個選取的|**Ctrl + F3**| Edit.FindNextSelected |
|格式化文件|**Ctrl+K、Ctrl+D** [文字編輯器]| Edit.FormatDocument |
|格式選取項目|**Ctrl+K、Ctrl+F** [文字編輯器]| Edit.FormatSelection |
|移至|**Ctrl + G**| Edit.GoTo |
|移至宣告|**Ctrl+F12**| Edit.GoToDeclaration |
|移至定義|**F12**| Edit.GoToDefinition |
|移至尋找下拉式方塊|**Ctrl+D**| Edit.GoToFindCombo |
|移至下一個位置|**F8**| Edit.GoToNextLocation |
|插入程式碼片段|**Ctrl + K**、 **ctrl + X**| Edit.InsertSnippet |
|插入索引標籤|**Tab** [報表設計工具、Windows Form 設計工具、文字編輯器]| Edit.InsertTab |
|垂直線剪下|**Ctrl+L** [文字編輯器]| Edit.LineCut |
|行向下擴充資料行|**Shift+Alt+向下鍵** [文字編輯器]| Edit.LineDownExtendColumn |
|上面的行開啟|**Ctrl + Enter** [文字編輯器]| Edit.LineOpenAbove |
|列出成員|**Ctrl+J** [文字編輯器、工作流程設計工具]<br /><br />或 **ctrl + K、ctrl + L** [工作流程設計工具]<br /><br />或 **Ctrl+K、L** [工作流程設計工具]| Edit.ListMembers |
|導覽至|**Ctrl +、**| Edit.NavigateTo |
|開啟檔案|**Ctrl + Shift + G**| Edit.OpenFile |
|改寫模式|**插入** [文字編輯器]| Edit.OvertypeMode |
|參數資訊|**Ctrl+Shift+空格鍵** [文字編輯器、工作流程設計工具]<br /><br />或 **Ctrl+K、Ctrl+P** [工作流程設計工具]<br /><br />或 **Ctrl+K、P** [工作流程設計工具]| Edit.ParameterInfo |
|貼上|**Ctrl + V**<br /><br />或 **Shift + Insert**| Edit.Paste |
|查看定義|**Alt + F12** [文字編輯器]| Edit.PeekDefinition |
|取消復原|**Ctrl + Y**<br /><br />或 **Shift + Alt + 倒退鍵**<br /><br />或 **Ctrl + Shift + Z**| Edit.Redo |
|取代|**Ctrl + H**| Edit.Replace |
|全選|**Ctrl + A**| Edit.SelectAll |
|選取目前的單字|**Ctrl + W** [文字編輯器]| Edit.SelectCurrentWord |
|選取 [取消]|**Esc** [文字編輯器、報表設計師、設定設計工具、Windows Form 設計工具、Managed 資源編輯器]| Edit.SelectionCancel |
|環繞|**Ctrl + K、Ctrl + S**| Edit.SurroundWith |
|靠左 Tab|**Shift+Tab** [文字編輯器、報表設計工具、Windows Form 編輯器]| Edit.TabLeft |
|切換所有大綱|**Ctrl+M、Ctrl+L** [文字編輯器]| Edit.ToggleAllOutlining |
|切換書籤|**Ctrl + k、ctrl + k** [文字編輯器]| Edit.ToggleBookmark |
|切換完成模式|**Ctrl+Alt+空格鍵** [文字編輯器]| Edit.ToggleCompletionMode |
|切換大綱展開|**Ctrl+M、Ctrl+M** [文字編輯器]| Edit.ToggleOutliningExpansion |
|取消選取專案的批註|**Ctrl+K、Ctrl+U** [文字編輯器]| Edit.UncommentSelection |
|復原|**Ctrl + Z**<br /><br />或 **Alt + 倒退鍵**| Edit.Undo |
|單字刪除到結尾|**Ctrl + Delete** [文字編輯器]| Edit.WordDeleteToEnd |
|Word 刪除以開始|**Ctrl+退格鍵** [文字編輯器]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>File：常用的快捷方式

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|結束|**Alt + F4**| File.Exit |
|新增檔案|**Ctrl + N**| File.NewFile |
|新增專案|**Ctrl + Shift + N**| File.NewProject |
|新網站|**Shift+Alt+N**| File.NewWebSite |
|開啟檔案|**Ctrl + O**| File.OpenFile |
|開啟專案|**Ctrl + Shift + O**| File.OpenProject |
|開啟網站|**Shift+Alt+O**| File.OpenWebSite |
|重新命名|**F2** [Team Explorer]| File.Rename |
|全部儲存|**Ctrl + Shift + S**| File.SaveAll |
|儲存選取的專案|**Ctrl + S**| File.SaveSelectedItems |
|在瀏覽器中檢視|**Ctrl + Shift + W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Project：熱門快速鍵

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|加入現有專案|**Shift + Alt + A**| Project.AddExistingItem |
|新增項目|**Ctrl + Shift + A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>重構：熱門快速鍵

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|擷取方法|**Ctrl+R、Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>工具：熱門快速鍵

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|附加至處理序|**Ctrl + Alt + P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>View：熱門快速鍵

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|類別視圖|**Ctrl + Shift + C**| View.ClassView |
|編輯標籤|**F2**| View.EditLabel |
|錯誤清單|**Ctrl + \\ 、ctrl + E**<br /><br />或 **Ctrl + \\ 、E**| View.ErrorList |
|向後導覽|**Ctrl +-**| View.NavigateBackward |
|向前流覽|**Ctrl + Shift +-**| View.NavigateForward |
|物件瀏覽器|**Ctrl + Alt + J**| View.ObjectBrowser |
|輸出|**Ctrl + Alt + O**| View.Output |
|屬性視窗|**F4**| View.PropertiesWindow |
|重新整理|**F5** [Team Explorer]| View.Refresh |
|伺服器 explorer|**Ctrl+Alt+S**| View.ServerExplorer |
|顯示智慧標籤|**Ctrl +。**<br /><br />或 **Shift + Alt + F10** [HTML 編輯器設計檢視]| View.ShowSmartTag |
|方案總管|**Ctrl + Alt + L**| View.SolutionExplorer |
|TFS Team explorer|**Ctrl + \\ 、ctrl + M**| View.TfsTeamExplorer |
|工具箱|**Ctrl + Alt + X**| View.Toolbox |
|查看程式碼|**Enter** [類別圖表]<br /><br />或 **F7** [設定設計工具]| View.ViewCode |
|檢視表設計工具|**Shift+F7** [HTML 編輯器原始碼檢視]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>視窗：熱門快速鍵

|命令|鍵盤快速鍵 [特殊內容]|命令 ID|
|-|-|-|
|啟動文件視窗|**Esc**| Window.ActivateDocumentWindow |
|關閉文件視窗|**Ctrl + F4**| Window.CloseDocumentWindow |
|下一個文件視窗|**Ctrl + F6**| Window.NextDocumentWindow |
|下一個文件視窗導覽|**Ctrl + Tab**| Window.NextDocumentWindowNav |
|下一個分割窗格|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>全域快速鍵

這些鍵盤快速鍵都是 *全域* 的，也就是說，您可以在任何 Visual Studio 視窗有焦點時使用這些快速鍵。

- [分析](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [編輯](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [專案](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [測試](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [架構](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [編輯器內容功能表](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [Project 和方案內容功能表](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [測試總管](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [建置](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [檔案](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [重構](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [工具](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [類別檢視內容功能表](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [說明](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [方案總管](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [檢視](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [偵錯](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [負載測試](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [球隊](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)
- [Window](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [偵錯工具內容功能表](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [其他內容功能表](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Team Foundation 內容功能表](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)
- [診斷中樞](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)

### <a name="analyze"></a><a name="bkmk_analyze"></a> 分析

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|向後導覽|**Shift+Alt+3**| Analyze.NavigateBackward |
|向前流覽|**Shift+Alt+4**| Analyze.NavigateForward |

### <a name="architecture"></a><a name="bkmk_architecture"></a> 架構

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|新增圖表|**Ctrl + \\ 、ctrl + N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> 建立

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|組建選取專案|**Ctrl+B** (Visual Studio 2019)| Build.BuildSelection |
|組建方案|**Ctrl + Shift + B**| Build.BuildSolution |
|取消|**Ctrl + Break**| Build.Cancel |
|編譯|**Ctrl+F7**| Build.Compile |
|對解決方案執行程式碼分析|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> 類別檢視內容功能表

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|屬性|**Alt+Enter**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> 調試

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|套用程式碼變更|**Alt+F10**| Debug.ApplyCodeChanges |
|附加至進程|**Ctrl + Alt + P**| Debug.AttachtoProcess |
|自動|**Ctrl + Alt + V、A**| Debug.Autos |
|全部中斷|**Ctrl + Alt + Break**| Debug.BreakAll |
|中斷點|**Ctrl + Alt + B**| Debug.Breakpoints |
|呼叫堆疊|**Ctrl + Alt + C**| Debug.CallStack |
|刪除所有中斷點|**Ctrl + Shift + F9**| Debug.DeleteAllBreakpoints |
|啟動|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|反組譯碼|**Ctrl + Alt + D**| Debug.Disassembly |
|Dom explorer|**Ctrl + Alt + V、D**| Debug.DOMExplorer |
|啟用中斷點|**Ctrl + F9**| Debug.EnableBreakpoint |
|例外狀況|**Ctrl + Alt + E**| Debug.Exceptions |
|函數中斷點|**Ctrl+K、B** (Visual Studio 2019)<br />**Ctrl** +**B** (Visual Studio 2017) | Debug.FunctionBreakpoint |
|移至上一個呼叫或 IntelliTrace 事件|**Ctrl+Shift+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|開始診斷|**Alt + F5**| Debug.Graphics.StartDiagnostics |
|立即|**Ctrl + Alt + I**| Debug.Immediate |
|IntelliTrace 呼叫|**Ctrl+Alt+Y、T**| Debug.IntelliTraceCalls |
|IntelliTrace 事件|**Ctrl+Alt+Y、F**| Debug.IntelliTraceEvents |
|JavaScript 主控台|**Ctrl + Alt + V、C**| Debug.JavaScriptConsole |
|本機|**Ctrl + Alt + V、L**| Debug.Locals |
|進程組合|**Ctrl + 5**| Debug.LocationToolbar.ProcessCombo |
|堆疊框架下拉式方塊|**Ctrl + 7**| Debug.LocationToolbar.StackFrameCombo |
|執行緒組合|**Ctrl + 6**| Debug.LocationToolbar.ThreadCombo |
|切換目前線程的旗標狀態|**Ctrl + 8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|切換標示的執行緒|**Ctrl + 9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|記憶體1|**Ctrl+Alt+M、1**| Debug.Memory1 |
|記憶體2|**Ctrl+Alt+M、2**| Debug.Memory2 |
|記憶體3|**Ctrl+Alt+M、3**| Debug.Memory3 |
|記憶體4|**Ctrl+Alt+M、4**| Debug.Memory4 |
|單元|**Ctrl+Alt+U**| Debug.Modules |
|平行堆疊|**Ctrl + Shift + D、S**| Debug.ParallelStacks |
|平行監看式1|**Ctrl+Shift+D、1**| Debug.ParallelWatch1 |
|平行監看2|**Ctrl+Shift+D、2**| Debug.ParallelWatch2 |
|平行監看式3|**Ctrl+Shift+D、3**| Debug.ParallelWatch3 |
|平行監看4|**Ctrl+Shift+D、4**| Debug.ParallelWatch4 |
|處理序|**Ctrl + Alt + Z**| Debug.Processes |
|快速監看|**Shift+F9** 或 **Ctrl+Alt+Q**| Debug.QuickWatch |
|重新附加至進程|**Shift+Alt+P**| ReattachtoProcess |
|重新整理 >windowsapp|**Ctrl + Shift + R**| Debug.RefreshWindowsapp |
|暫存器|**Ctrl + Alt + G**| Debug.Registers |
|重新啟動|**Ctrl+Shift+F5**| Debug.Restart |
|執行至游標處|**Ctrl + F10**| Debug.RunToCursor |
|設定下一個陳述式|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|在 code map 上顯示呼叫堆疊|**Ctrl + Shift + '**| Debug.ShowCallStackonCodeMap |
|顯示下一個陳述式|**Alt + Num** *| Debug.ShowNextStatement |
|開始|**F5**| Debug.Start |
|啟動 windows phone 應用程式分析|**Alt + F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|啟動但不進行調試|**Ctrl + F5**| Debug.StartWithoutDebugging |
|逐步執行|**F11**| Debug.StepInto |
|逐步執行目前的進程|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|逐步執行特定|**Shift + Alt + F11**| Debug.StepIntoSpecific |
|跳出|**Shift + F11**| Debug.StepOut |
|跳出目前的進程|**Ctrl+Shift+Alt+F11**| Debug.StepOutCurrentProcess |
|逐程序|在進行調試時， **F10** (：執行不進入動作的步驟) | Debug.StepOver |
|逐程序|在不進行偵錯工具時， **F10** (：開始偵錯工具，並在使用者程式碼的第一行停止) | Debug.StepOver |
|不進入目前的進程|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|停止偵錯|**Shift + F5**| Debug.StopDebugging |
|停止效能分析|**Shift+Alt+F2**| Debug.StopPerformanceAnalysis |
|工作|**Ctrl + Shift + D、K**| Debug.Tasks |
|執行緒|**Ctrl + Alt + H**| Debug.Threads |
|切換中斷點|**F9**| Debug.ToggleBreakpoint |
|切換反組解碼|**Ctrl + F11**| Debug.ToggleDisassembly |
|監看式 1|**Ctrl + Alt + W、1**| Debug.Watch1 |
|觀賞2|**Ctrl + Alt + W、2**| Debug.Watch2 |
|觀賞3|**Ctrl + Alt + W、3**| Debug.Watch3 |
|觀賞4|**Ctrl + Alt + W、4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> 偵錯工具內容功能表

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|刪除|**Alt + F9、D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|移至反組解碼|**Alt+F9、A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|移至原始程式碼|**Alt+F9、S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> 診斷中樞

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|停止收集|**Ctrl + Alt + F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> 編輯

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|複製|**Ctrl + C**<br /><br /> 或<br /><br /> **Ctrl + Ins**| Edit.Copy |
|剪下|**Ctrl + X**<br /><br /> 或<br /><br /> **Shift + Delete**| Edit.Cut |
|迴圈剪貼簿環形|**Ctrl + Shift + V**<br /><br /> 或<br /><br /> **Ctrl+Shift+Ins**| Edit.CycleClipboardRing |
|刪除|**刪除**| Edit.Delete |
|重複|**Ctrl+D**| Edit.Duplicate |
|Find|**Ctrl + F**| Edit.Find |
|尋找所有參考|**Shift + F12**| Edit.FindAllReferences |
|檔案中尋找|**Ctrl + Shift + F**| Edit.FindinFiles |
|尋找下一個|**F3**| Edit.FindNext |
|尋找下一個選取的|**Ctrl + F3**| Edit.FindNextSelected |
|尋找上一個|**Shift + F3**| Edit.FindPrevious |
|尋找上一個選取的|**Ctrl + Shift + F3**| Edit.FindPreviousSelected |
|產生方法|**Ctrl+K、Ctrl+M**| Edit.GenerateMethod |
|移至|**Ctrl + G**| Edit.GoTo |
|移至全部|**Ctrl+,** 或 **Ctrl+T**| Edit.GoToAll |
|移至宣告|**Ctrl+F12**| Edit.GoToDeclaration |
|移至定義|**F12**| Edit.GoToDefinition |
|前往成員|**Ctrl+1、Ctrl+M** 或 **Ctrl+1、M** 或 **Alt+\\**| Edit.GoToMember |
|移至下一個位置|**F8** (錯誤清單或 [輸出] 視窗中的下一個錯誤)| Edit.GoToNextLocation |
|移至上一個位置|**Shift+F8** (錯誤清單或 [輸出] 視窗中的上一個錯誤)| Edit.GoToPrevLocation |
|插入程式碼片段|**Ctrl + K、Ctrl + X**| Edit.InsertSnippet |
|向下移動控制項|**Ctrl + 向下鍵**| Edit.MoveControlDown |
|將控制項向下移動格線|**向下箭號**| Edit.MoveControlDownGrid |
|左移控制項|**Ctrl+向左鍵**| Edit.MoveControlLeft |
|移動控制項左方方格|**向左鍵**| Edit.MoveControlLeftGrid |
|向右移動控制項|**Ctrl+向右鍵**| Edit.MoveControlRight |
|移動控制項右格線|**向右鍵**| Edit.MoveControlRightGrid |
|向上移動控制項|**Ctrl + 向上鍵**| Edit.MoveControlUp |
|移動控制項格線|**向上箭號**| Edit.MoveControlUpGrid |
|下一個書籤|**Ctrl + K、Ctrl + N**| Edit.NextBookmark |
|資料夾中的下一個書簽|**Ctrl + Shift + K、Ctrl + Shift + N**| Edit.NextBookmarkInFolder |
|開啟檔案|**Ctrl+Shift+G** (開啟資料指標底下的檔案名稱)| Edit.OpenFile |
|貼上|**Ctrl + V**<br /><br /> 或<br /><br /> **Shift + Ins**| Edit.Paste |
|上一個書籤|**Ctrl + K、Ctrl + P**| Edit.PreviousBookmark |
|資料夾中的前一個書簽|**Ctrl + Shift + K、Ctrl + Shift + P**| Edit.PreviousBookmarkInFolder |
|快速尋找符號|**Shift+Alt+F12**| Edit.QuickFindSymbol |
|取消復原|**Ctrl + Y**<br /><br /> 或<br /><br /> **Ctrl + Shift + Z**<br /><br /> 或<br /><br /> **Shift+Alt+退格鍵**| Edit.Redo |
|重新整理遠端參考|**Ctrl + Shift + J**| Edit.RefreshRemoteReferences |
|取代|**Ctrl + H**| Edit.Replace |
|檔案中取代|**Ctrl + Shift + H**| Edit.ReplaceinFiles |
|全選|**Ctrl + A**| Edit.SelectAll |
|選取下一個控制項|**Tab**| Edit.SelectNextControl |
|選取先前的控制項|**Shift + Tab**| Edit.SelectPreviousControl |
|顯示磚方格|**Enter**| Edit.ShowTileGrid |
|調整控制項大小|**Ctrl+Shift+向下鍵**| Edit.SizeControlDown |
|將控制項向下調整格線|**Shift + 向下鍵**| Edit.SizeControlDownGrid |
|左邊的大小控制項|**Ctrl+Shift+向左鍵**| Edit.SizeControlLeft |
|大小控制項左方方格|**Shift + 向左鍵**| Edit.SizeControlLeftGrid |
|大小控制許可權|**Ctrl + Shift + 向右鍵**| Edit.SizeControlRight |
|大小控制右方格|**Shift + 向右鍵**| Edit.SizeControlRightGrid |
|調整控制項大小|**Ctrl+Shift+向上鍵**| Edit.SizeControlUp |
|調整控制項的大小|**Shift + 向上鍵**| Edit.SizeControlUpGrid |
|停止搜尋|**Alt + F3、S**| Edit.StopSearch |
|環繞|**Ctrl + K、Ctrl + S**| Edit.SurroundWith |
|復原|**Ctrl + Z**<br /><br /> 或<br /><br /> **Alt + 倒退鍵**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> 編輯器內容功能表

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|中斷點條件|**Alt + F9、C**| EditorCoNtextMenus. CodeWindow. BreakpointConditions |
|中斷點編輯標籤|**Alt + F9、L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|顯示專案|**Ctrl + '**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|執行|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|移至 view|**Ctrl+M、Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|切換標頭程式碼檔案|**Ctrl+K、Ctrl+O** (字母 'O')| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|檢視呼叫階層|**Ctrl+K、Ctrl+T**<br /><br /> 或<br /><br /> **Ctrl+K、T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> 檔

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|結束|**Alt + F4**| File.Exit |
|新增檔案|**Ctrl + N**| File.NewFile |
|新增專案|**Ctrl + Shift + N**| File.NewProject |
|新網站|**Shift+Alt+N**| File.NewWebSite |
|開啟檔案|**Ctrl+O** (字母 'O')| File.OpenFile |
|開啟專案|**Ctrl+Shift+O** (字母 'O')| File.OpenProject |
|開啟網站|**Shift+Alt+O** (字母 'O')| File.OpenWebSite |
|列印|**Ctrl + P**| File.Print |
|全部儲存|**Ctrl + Shift + S**| File.SaveAll |
|儲存選取的專案|**Ctrl + S**| File.SaveSelectedItems |
|在瀏覽器中檢視|**Ctrl + Shift + W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> 説明

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|新增和移除說明內容|**Ctrl + Alt + F1**| Help.AddandRemoveHelpContent |
|F1 說明|**F1**| Help.F1Help |
|View 說明|**Ctrl + F1**| Help.ViewHelp |
|視窗說明|**Shift + F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> 負載測試

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|跳至計數器窗格|**Ctrl+R、Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> 其他操作功能表

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|新增圖表|**插入**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> 專案

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|加入現有專案|**Shift + Alt + A**| Project.AddExistingItem |
|新增項目|**Ctrl + Shift + A**| Project.AddNewItem |
|類別嚮導|**Ctrl+Shift+X**| Project.ClassWizard |
|覆寫|**Ctrl+Alt+Ins**| Project.Override |
|預覽變更|**Alt+;** 然後 **Alt+C**| Project.Previewchanges |
|發佈選取的檔案|**Alt+;** 然後 **Alt+P**| Project.Publishselectedfiles |
|從伺服器取代選取的檔案|**Alt+;** 然後 **Alt+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a> 專案及解決方案操作功能表

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|下移|**Alt + 向下鍵**| ProjectandSolutionContextMenus.Item.MoveDown |
|上移|**Alt+向上箭**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> 重 構

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|封裝欄位|**Ctrl+R、Ctrl+E**| Refactor.EncapsulateField |
|擷取介面|**Ctrl+R、Ctrl+I**| Refactor.ExtractInterface |
|擷取方法|**Ctrl+R、Ctrl+M**| Refactor.ExtractMethod |
|移除參數|**Ctrl+R、Ctrl+V**| Refactor.RemoveParameters |
|重新命名|**Ctrl+R、Ctrl+R**| Refactor.Rename |
|重新排列參數|**Ctrl+R、Ctrl+O** (字母 'O')| Refactor.ReorderParameters |

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> 方案總管

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|開啟檔案篩選|**Ctrl+[**、**O** (字母 'O')<br /><br /> 或<br /><br /> **Ctrl+[**、**Ctrl+O** (字母 'O')| SolutionExplorer.OpenFilesFilter |
|暫止的變更篩選|**Ctrl + [**、 **P**<br /><br /> 或<br /><br /> **Ctrl + [**、 **Ctrl + P**| SolutionExplorer.PendingChangesFilter |
|與使用中檔同步|**Ctrl + [**、 **S**<br /><br /> 或<br /><br /> **Ctrl + [**、 **Ctrl + S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team"></a><a name="bkmk_team"></a> 團隊

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|移至 git 分支|**Ctrl+0** (零)、**Ctrl+N**<br /><br /> 或<br /><br /> **Ctrl+0、N**| Team.Git.GoToGitBranches |
|移至 git 變更|**Ctrl+0** (零)、**Ctrl+G**<br /><br /> 或<br /><br /> **Ctrl+0、G**| Team.Git.GoToGitChanges |
|移至 git 認可|**Ctrl+0** (零)、**Ctrl+O** (字母 'O')<br /><br /> 或<br /><br /> **Ctrl+0、O**| Team.Git.GoToGitCommits |
|Team explorer 搜尋|**Ctrl + '**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Team Foundation 內容功能表

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|移至組建|**Ctrl+0** (零)、**Ctrl+B**<br /><br /> 或<br /><br /> **Ctrl+0、B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|前往 connect|**Ctrl+0** (零)、**Ctrl+C**<br /><br /> 或<br /><br /> **Ctrl+0、C**| TeamFoundationContextMenus.Commands.GoToConnect |
|移至檔|**Ctrl+0** (零)、**Ctrl+D**<br /><br /> 或<br /><br /> **Ctrl+0、D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|前往首頁|**Ctrl+0** (零)、**Ctrl+H**<br /><br /> 或<br /><br /> **Ctrl+0、H**| TeamFoundationContextMenus.Commands.GoToHome |
|前往 [我的工作]|**Ctrl+0** (零)、**Ctrl+M**<br /><br /> 或<br /><br /> **Ctrl+0、M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|移至暫止的變更|**Ctrl+0** (零)、**Ctrl+P**<br /><br /> 或<br /><br /> **Ctrl+0、P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|移至報表|**Ctrl+0** (零)、**Ctrl+R**<br /><br /> 或<br /><br /> **Ctrl+0、R**| TeamFoundationContextMenus.Commands.GoToReports |
|移至 [設定]|**Ctrl+0** (零)、**Ctrl+S**<br /><br /> 或<br /><br /> **Ctrl+0、S**| TeamFoundationContextMenus.Commands.GoToSettings |
|前往 web 存取|**Ctrl+0** (零)、**Ctrl+A**<br /><br /> 或<br /><br /> **Ctrl+0、A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|移至工作專案|**Ctrl+0** (零)、**Ctrl+W**<br /><br /> 或<br /><br /> **Ctrl+0、W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test"></a><a name="bkmk_test"></a> 測試

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|使用自動程式碼 ui 測試產生器|**Ctrl + \\ 、ctrl + C**| Test.UseCodedUITestBuilder |
|使用現有的動作記錄|**Ctrl + \\ 、ctrl + A**| Test.UseExistingActionRecording |

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> 測試總管

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|所有測試的 Debug|**Ctrl+R、Ctrl+A**| TestExplorer.DebugAllTests |
|在內容中進行所有測試的調試|**Ctrl + R、Ctrl + T**| TestExplorer.DebugAllTestsInContext |
|上次執行的調試|**Ctrl + R、D**| TestExplorer.DebugLastRun |
|重複上一次執行|**Ctrl + R、L**| TestExplorer.RepeatLastRun |
|執行所有測試|**Ctrl + R、A**| TestExplorer.RunAllTests |
|在內容中執行所有測試|**Ctrl + R、T**| TestExplorer.RunAllTestsInContext |
|顯示測試瀏覽器|**Ctrl + E、T**| TestExplorer.ShowTestExplorer |
|開啟索引標籤|**Ctrl + E、L**| LiveUnitTesting.OpenTab |
|程式碼涵蓋範圍結果|**Ctrl+E、C**| CodeCoverageResults |

### <a name="tools"></a><a name="bkmk_tools"></a> 工具

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|附加至處理序|**Ctrl + Alt + P**| Tools.AttachtoProcess |
|程式碼片段管理員|**Ctrl + K、Ctrl + B**| Tools.CodeSnippetsManager |
|強制 gc|**Ctrl+Shift+Alt+F12、Ctrl+Shift+Alt+F12**| Tools.ForceGC |

### <a name="view"></a><a name="bkmk_view"></a> 視圖

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|所有視窗|**Shift+Alt+M**| View.AllWindows |
|架構總管|**Ctrl + \\ 、ctrl + R**| View.ArchitectureExplorer |
|一層|**Alt+向左鍵** (不同於文字編輯器中 View.NavigateBackward 的功能)| View.Backward |
|書簽視窗|**Ctrl + K、Ctrl + W**| View.BookmarkWindow |
|流覽下一個|**Ctrl + Shift + 1**| View.BrowseNext |
|流覽上一個|**Ctrl + Shift + 2**| View.BrowsePrevious |
|呼叫階層|**Ctrl + Alt + K**| View.CallHierarchy |
|類別視圖|**Ctrl + Shift + C**| View.ClassView |
|類別視圖前往搜尋下拉式方塊|**Ctrl+K、Ctrl+V**| View.ClassViewGoToSearchCombo |
|程式碼定義視窗|**Ctrl + \\ 、D**<br /><br /> 或<br /><br /> **Ctrl + \\ 、ctrl + D**| View.CodeDefinitionWindow |
|命令視窗|**Ctrl+Alt+A**| View.CommandWindow |
|資料來源|**Shift+Alt+D**| View.DataSources |
|檔大綱|**Ctrl + Alt + T**| View.DocumentOutline |
|編輯標籤|**F2**| View.EditLabel |
|錯誤清單|**Ctrl + \\ 、E**<br /><br /> 或<br /><br /> **Ctrl + \\ 、ctrl + E**| View.ErrorList |
|F# Interactive|**Ctrl + Alt + F**| View.F#Interactive |
|尋找符號結果|**Ctrl+Alt+F12**| View.FindSymbolResults |
|轉寄|**Alt+向右鍵** (不同於文字編輯器中 View.NavigateForward 的功能)| View.Forward |
|向前流覽內容|**Ctrl + Shift + 7**| View.ForwardBrowseContext |
|全螢幕|**Shift + Alt + Enter**| View.FullScreen |
|向後導覽|**Ctrl +-**| View.NavigateBackward |
|向前流覽|**Ctrl + Shift +-**| View.NavigateForward |
|下一個錯誤|**Ctrl + Shift + F12**| View.NextError |
|通知|**Ctrl+W、N**<br /><br /> 或<br /><br /> **Ctrl+W、Ctrl+N**| View.Notifications |
|物件瀏覽器|**Ctrl + Alt + J**| View.ObjectBrowser |
|物件瀏覽器移至搜尋下拉式方塊|**Ctrl+K、Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|輸出|**Ctrl+Alt+O** (字母 'O')| View.Output |
|Pop 流覽內容|**Ctrl+Shift+8** (僅限 C++)| View.PopBrowseContext |
|屬性視窗|**F4**| View.PropertiesWindow |
|「屬性頁」|**Shift+F4**| View.PropertyPages |
|資源檢視|**Ctrl + Shift + E**| View.ResourceView |
|伺服器 explorer|**Ctrl+Alt+S**| View.ServerExplorer |
|顯示智慧標籤|**Shift + Alt + F10**<br /><br /> 或<br /><br /> **Ctrl +。**| View.ShowSmartTag |
|方案總管|**Ctrl + Alt + L**| View.SolutionExplorer |
|SQL 伺服器物件瀏覽器|**Ctrl + \\ 、ctrl + S**| View.SQLServerObjectExplorer |
|工作清單|**Ctrl + \\ 、T**<br /><br /> 或<br /><br /> **Ctrl + \\ 、ctrl + T**| View.TaskList |
|TFS team explorer|**Ctrl + \\ 、ctrl + M**| View.TfsTeamExplorer |
|工具箱|**Ctrl + Alt + X**| View.Toolbox |
|UML 模型瀏覽器|**Ctrl + \\ 、ctrl + U**| View.UMLModelExplorer |
|查看程式碼|**F7**| View.ViewCode |
|檢視表設計工具|**Shift+F7**| View.ViewDesigner |
|網頁瀏覽器|**Ctrl + Alt + R**| View.WebBrowser |
|放大|**Ctrl + Shift +。**| View.ZoomIn |
|縮小|**Ctrl + Shift +、**| View.ZoomOut |
|顯示測試瀏覽器|**Ctrl + E、T**| TestExplorer.ShowTestExplorer |

### <a name="window"></a><a name="bkmk_window"></a> 視窗

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|啟動文件視窗|**Esc**| Window.ActivateDocumentWindow |
|將索引標籤新增至選取範圍|**Ctrl+Shift+Alt+空格鍵**| Window.AddTabtoSelection |
|關閉文件視窗|**Ctrl + F4**| Window.CloseDocumentWindow |
|關閉工具視窗|**Shift + Esc**| Window.CloseToolWindow |
|保持 tab 開啟|**Ctrl+Alt+Home**| Window.KeepTabOpen |
|移至巡覽列|**Ctrl+F2**| Window.MovetoNavigationBar |
|下一個文件視窗|**Ctrl + F6**| Window.NextDocumentWindow |
|下一個文件視窗導覽|**Ctrl + Tab**| Window.NextDocumentWindowNav |
|下一個窗格|**Alt + F6**| Window.NextPane |
|下一個分割窗格|**F6**| Window.NextSplitPane |
|下一個 Tab 點|**Ctrl+Alt+PgDn**<br /><br /> 或<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|下一個索引標籤並新增至選取範圍|**Ctrl+Shift+Alt+PgDn**| Window.NextTabandAddtoSelection |
|Next tool window nav|**Alt + F7**| Window.NextToolWindowNav |
|上一個文件視窗|**Ctrl + Shift + F6**| Window.PreviousDocumentWindow |
|上一個文件視窗 nav|**Ctrl + Shift + Tab**| Window.PreviousDocumentWindowNav |
|上一個窗格|**Shift + Alt + F6**| Window.PreviousPane |
|上一個分割窗格|**Shift + F6**| Window.PreviousSplitPane |
|上一個 Tab 點|**Ctrl+Alt+PgUp**<br /><br /> 或<br /><br /> **Ctrl+PgUp**| Window.PreviousTab |
|上一個索引標籤並新增至選取範圍|**Ctrl+Shift+Alt+PgUp**| Window.PreviousTabandAddtoSelection |
|上一個工具視窗 nav|**Shift + Alt + F7**| Window.PreviousToolWindowNav |
|快速啟動|**Ctrl+Q**| Window.QuickLaunch |
|快速啟動先前的類別|**Ctrl + Shift + Q**| Window.QuickLaunchPreviousCategory |
|顯示停駐功能表|**Alt +-**| Window.ShowDockMenu |
|顯示 Ex 的 MDI 檔案清單|**Ctrl + Alt + 向下鍵**| Window.ShowEzMDIFileList |
|Solution explorer 搜尋|**Ctrl +;**| Window.SolutionExplorerSearch |
|視窗搜尋|**Alt + '**| Window.WindowSearch |

### <a name="azure"></a><a name="bkmk_windowsazure"></a> 蔚藍

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|重試行動服務腳本作業|**Ctrl + Num \* 、ctrl + R**| WindowsAzure.RetryMobileServiceScriptOperation |
|顯示行動服務腳本錯誤詳細資料|**Ctrl + Num \* 、ctrl + D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

## <a name="context-specific-shortcuts"></a>特定內容的快捷方式


### <a name="adonet-entity-data-model-designer"></a>ADO.NET 實體資料模型設計工具

此內容的特定快速鍵如下：

|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|Down|**Alt + 向下鍵**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|向下5|**Alt+PgDn**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|置底|**Alt+End**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|置頂|**Alt + 首頁**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Up|**Alt+向上箭**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|向上5|**Alt+PgUp**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|重新命名|**Ctrl+R、R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|從圖表移除|**Shift+Del**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|實體資料模型瀏覽器|**Ctrl + 1**| View.EntityDataModelBrowser |
|實體資料模型對應詳細資料|**Ctrl + 2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>類別圖表

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|摺疊|**號**| ClassDiagram.Collapse |
|展開|**Num +**| ClassDiagram.Expand |
|刪除|**Ctrl+Del**| Edit.Delete |
|展開折迭基底類型清單|**Shift+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|流覽至棒糖|**Shift+Alt+L**| Edit.NavigateToLollipop |
|從圖表移除|**刪除**| Edit.RemovefromDiagram |
|查看程式碼|**Enter**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>自動程式碼 UI 測試編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|將參考複製到剪貼簿|**Ctrl + C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|插入延遲前|**Ctrl + Alt + D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|全部尋找|**Shift+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|找出 ui 控制項|**Ctrl + Shift + L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|移動程式碼|**Ctrl + Alt + C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|分割為新方法|**Ctrl + Shift + T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>資料集編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|插入資料行|**插入**| OtherContextMenus.ColumnContext.InsertColumn |
|Column|**Ctrl + L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>差異檢視器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|忽略修剪空白字元|**Ctrl + \\ 、ctrl + 空格鍵**| Diff.IgnoreTrimWhitespace |
|內嵌視圖|**Ctrl + \\ 、ctrl + 1**| Diff.InlineView |
|僅限左方視圖|**Ctrl + \\ 、ctrl + 3**| Diff.LeftOnlyView |
|[下一項差異]|**F8**| Diff.NextDifference |
|[前一項差異]|**Shift + F8**| Diff.PreviousDifference |
|僅限右視圖|**Ctrl + \\ 、ctrl + 4**| Diff.RightOnlyView |
|並排顯示|**Ctrl + \\ 、ctrl + 2**| Diff.SideBySideView |
|從左至右切換|**Ctrl + \\ 、ctrl + Tab**| Diff.SwitchBetweenLeftAndRight |
|同步處理視圖切換|**Ctrl+\\、Ctrl+向下鍵**| Diff.SynchronizeViewToggle |
|加入註解|**Ctrl+Shift+K**| EditorContextMenus.CodeWindow.AddComment |
|編輯本機檔案|**Ctrl + Shift + P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>DOM 總管

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|重新整理|**F5**| DOMExplorer.Refresh |
|選取項目|**Ctrl + B**| DOMExplorer.SelectElement |
|顯示版面配置|**Ctrl + Shift + I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>F# Interactive

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|取消互動式評估|**Ctrl + Break**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>圖形文件編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|新增節點|**插入**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|這兩項相依性|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|傳入的相依性|**我**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|連出相依性|**輸出**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|新增批註|**Ctrl+Shift+K**<br /><br /> 或<br /><br /> **Ctrl+E、C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|移除|**刪除**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|重新命名|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>圖形診斷

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|捕捉框架|無| Debug.Graphics.CaptureFrame |
|將圖元選取範圍下移|**Shift + Alt + 向下鍵**| Graphics.MovePixelSelectionDown |
|將圖元選取範圍向左移動|**Shift + Alt + 向左鍵**| Graphics.MovePixelSelectionLeft |
|將圖元選取範圍右移|**Shift + Alt + 向右鍵**| Graphics.MovePixelSelectionRight |
|將圖元選取範圍向上移動|**Shift+Alt+向上鍵**| Graphics.MovePixelSelectionUp |
|縮放至實際大小|**Shift+Alt+0** (零)| Graphics.ZoomToActualSize |
|縮放至視窗大小|**Shift+Alt+9**| Graphics.ZoomToFitInWindow |
|放大|**Shift + Alt + =**| Graphics.ZoomIn |
|縮小|**Shift + Alt +-**| Graphics.ZoomOut |

### <a name="html-editor"></a>HTML 編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|移至控制器|**Ctrl+M、Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view"></a>HTML 編輯器設計檢視

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|向下移動控制項|**Ctrl + 向下鍵**| Edit.MoveControlDown |
|向上移動控制項|**Ctrl + 向上鍵**| Edit.MoveControlUp |
|粗體|**Ctrl + B**| Format.Bold |
|轉換成超連結|**Ctrl + L**| Format.ConverttoHyperlink |
|插入書簽|**Ctrl + Shift + L**| Format.InsertBookmark |
|斜體|**Ctrl+I**| Format.Italic |
|Underline|**Ctrl + U**| Format.Underline |
|新增內容頁面|**Ctrl+M、Ctrl+C**| Project.AddContentPage |
|左邊的資料行|**Ctrl + Alt + 向左鍵**| Table.ColumntotheLeft |
|右邊的資料行|**Ctrl+Alt+向右鍵**| Table.ColumntotheRight |
|上方的資料列|**Ctrl+Alt+向上鍵**| Table.RowAbove |
|以下資料列|**Ctrl + Alt + 向下鍵**| Table.RowBelow |
|.Net 非視覺化控制項|**Ctrl + Shift + N**| View.ASP.NETNonvisualControls |
|編輯 master|**Ctrl + M、Ctrl + M**| View.EditMaster |
|下一個視圖|**Ctrl+PgDn**| View.NextView |
|顯示智慧標籤|**Shift + Alt + F10**| View.ShowSmartTag |
|視圖標記|**Shift+F7**| View.ViewMarkup |
|上一個 Tab 點|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="html-editor-source-view"></a>HTML 編輯器原始碼檢視

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|移至控制器|**Ctrl+M、Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |
|下一個視圖|**Ctrl+PgDn**| View.NextView |
|同步處理視圖|**Ctrl+Shift+Y**| View.SynchronizeViews |
|檢視表設計工具|**Shift+F7**| View.ViewDesigner |
|上一個 Tab 點|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="layer-diagram"></a>分層圖

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|刪除|**Shift + Delete**| Edit.Delete |

### <a name="managed-resources-editor"></a>Managed 資源編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|編輯資料格|**F2**| Edit.EditCell |
|移除|**刪除**| Edit.Remove |
|移除資料列|**Ctrl + Delete**| Edit.RemoveRow |
|選取 [取消]|**ESC 鍵**| Edit.SelectionCancel |
|音訊|**Ctrl + 4**| Resources.Audio |
|檔案|**Ctrl + 5**| Resources.Files |
|圖示|**Ctrl + 3**| Resources.Icons |
|映像|**Ctrl + 2**| Resources.Images |
|其他|**Ctrl + 6**| Resources.Other |
|字串|**Ctrl + 1**| Resources.Strings |

### <a name="merge-editor-window"></a>合併編輯器視窗

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|將焦點設定在左視窗|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|設定結果視窗的焦點|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|將焦點設定在右視窗|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Microsoft SQL Server Data Tools，結構描述比較

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|SSDT 架構比較比較|**Shift+Alt+C**| SQL.SSDTSchemaCompareCompare |
|SSDT 架構比較產生腳本|**Shift+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|SSDT 架構比較下一次變更|**Shift + Alt +。**| SQL.SSDTSchemaCompareNextChange |
|SSDT 架構比較先前的變更|**Shift + Alt +、**| SQL.SSDTSchemaComparePreviousChange |
|SSDT 架構比較停止|**Alt + Break**| SQL.SSDTSchemaCompareStop |
|SSDT 架構比較寫入更新|**Shift+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Microsoft SQL Server Data Tools，資料表設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|展開萬用字元|**Ctrl+R、E**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+E**| SQL.ExpandWildcards |
|完整限定名稱|**Ctrl+R、Q**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+Q**| SQL.FullyqualifyNames |
|移至架構|**Ctrl+R、M**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+M**| SQL.MovetoSchema |
|重新命名|**F2**<br /><br /> 或<br /><br /> **Ctrl+R、R**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Shift+Alt+PgDn**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Microsoft SQL Server Data Tools，T-SQL 編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|使用偵錯工具執行|**Alt + F5**| SQL.ExecuteWithDebugger |
|展開萬用字元|**Ctrl+R、E**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+E**| SQL.ExpandWildcards |
|完整限定名稱|**Ctrl+R、Q**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+Q**| SQL.FullyqualifyNames |
|移至架構|**Ctrl+R、M**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+M**| SQL.MovetoSchema |
|重新命名|**F2**<br /><br /> 或<br /><br /> **Ctrl+R、R**<br /><br /> 或<br /><br /> **Ctrl+R、Ctrl+R**| SQL.Rename |
|T SQL 編輯器取消查詢|**Alt + Break**| SQL.TSqlEditorCancelQuery |
|T SQL 編輯器執行查詢|**Ctrl + Shift + E**| SQL.TSqlEditorExecuteQuery |
|T SQL 編輯器結果為檔案|**Ctrl+D、F**| SQL.TSqlEditorResultsAsFile |
|T SQL 編輯器的結果視為格線|**Ctrl+D、G**| SQL.TSqlEditorResultsAsGrid |
|T SQL 編輯器的結果做為文字|**Ctrl+D、T**| SQL.TSqlEditorResultsAsText |
|T SQL 編輯器顯示預估計畫|**Ctrl+D、E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL 編輯器切換執行計畫|**Ctrl+D、A**| SQL.TSqlEditorToggleExecutionPlan |
|T SQL 編輯器切換結果窗格|**Ctrl+D、R**| SQL.TSqlEditorToggleResultsPane |
|T SQL 編輯器複製查詢|**Ctrl + Alt + N**|SQL。TSqlEditorCloneQuery |
|T SQL 編輯器資料庫下拉式方塊|**Shift+Alt+PgDn**|SQL。TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Microsoft SQL Server Data Tools，T-SQL PDW 編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|T SQL 編輯器取消查詢|**Alt + Break**| SQL.TSqlEditorCancelQuery |
|T SQL 編輯器執行查詢|**Ctrl + Shift + E**| SQL.TSqlEditorExecuteQuery |
|T SQL 編輯器結果為檔案|**Ctrl+D、F**| SQL.TSqlEditorResultsAsFile |
|T SQL 編輯器的結果視為格線|**Ctrl+D、G**| SQL.TSqlEditorResultsAsGrid |
|T SQL 編輯器的結果做為文字|**Ctrl+D、T**| SQL.TSqlEditorResultsAsText |
|T SQL 編輯器顯示預估計畫|**Ctrl+D、E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL 編輯器切換執行計畫|**Ctrl+D、A**| SQL.TSqlEditorToggleExecutionPlan |
|T SQL 編輯器切換結果窗格|**Ctrl+D、R**| SQL.TSqlEditorToggleResultsPane |
|T SQL 編輯器複製查詢|**Ctrl + Alt + N**|SQL。TSqlEditorCloneQuery |
|T SQL 編輯器複製查詢|**Shift+Alt+PgDn**|SQL。TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Page Inspector

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|最小化|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>查詢設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|取消取出資料|**Ctrl + T**| QueryDesigner.CancelRetrievingData |
|準則|**Ctrl + 2**| QueryDesigner.Criteria |
|圖表|**Ctrl + 1**| QueryDesigner.Diagram |
|執行 SQL。|**Ctrl + R**| QueryDesigner.ExecuteSQL |
|Goto 資料列|**Ctrl + G**| QueryDesigner.GotoRow |
|聯結模式|**Ctrl + Shift + J**| QueryDesigner.JoinMode |
|結果|**Ctrl + 4**| QueryDesigner.Results |
|Sql|**Ctrl + 3**| QueryDesigner.SQL |

### <a name="query-results"></a>查詢結果

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|查詢結果的新資料列|**Alt+End**| SQL.QueryResultsNewRow |
|查詢結果重新整理|**Shift+Alt+R**| SQL.QueryResultsRefresh |
|查詢結果停止|**Alt + Break**| SQL.QueryResultsStop |

### <a name="report-designer"></a>報表設計師

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|中斷線|**Enter**| Edit.BreakLine |
|左邊的字元|**向左鍵**| Edit.CharLeft |
|字元左方擴充|**Shift + 向左鍵**| Edit.CharLeftExtend |
|右移字元|**向右鍵**| Edit.CharRight |
|字元右延伸|**Shift + 向右鍵**| Edit.CharRightExtend |
|插入索引標籤|**Tab**| Edit.InsertTab |
|向下捲動一行|**向下箭號**| Edit.LineDown |
|行向下擴充|**Shift + 向下鍵**| Edit.LineDownExtend |
|向上捲動一行|**向上箭號**| Edit.LineUp |
|行向上擴充|**Shift + 向上鍵**| Edit.LineUpExtend |
|向下移動控制項|**Ctrl + 向下鍵**| Edit.MoveControlDown |
|左移控制項|**Ctrl+向左鍵**| Edit.MoveControlLeft |
|向右移動控制項|**Ctrl+向右鍵**| Edit.MoveControlRight |
|向上移動控制項|**Ctrl + 向上鍵**| Edit.MoveControlUp |
|選取 [取消]|**Esc**| Edit.SelectionCancel |
|調整控制項大小|**Ctrl+Shift+向下鍵**| Edit.SizeControlDown |
|左邊的大小控制項|**Ctrl+Shift+向左鍵**| Edit.SizeControlLeft |
|大小控制許可權|**Ctrl + Shift + 向右鍵**| Edit.SizeControlRight |
|調整控制項大小|**Ctrl+Shift+向上鍵**| Edit.SizeControlUp |
|靠左 Tab|**Shift + Tab**| Edit.TabLeft |
|報表資料|**Ctrl + Alt + D**| View.ReportData |

### <a name="sequence-diagram"></a>順序圖表

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|流覽至程式碼|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|刪除|**Shift+Del**| Edit.Delete |

### <a name="settings-designer"></a>設定設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|編輯資料格|**F2**| Edit.EditCell |
|移除資料列|**Ctrl + Delete**| Edit.RemoveRow |
|選取 [取消]|**Esc**| Edit.SelectionCancel |
|查看程式碼|**F7**| View.ViewCode |

### <a name="solution-explorer"></a>方案總管

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|Page inspector 中的 View|**Ctrl+K、Ctrl+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer"></a>Team Explorer

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|刪除|**刪除**| Edit.Delete |
|重新命名|**F2**| File.Rename |
|移至 team explorer 導覽|**Alt + 首頁**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|移至 team explorer 下一節內容|**Alt + 向下鍵**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|移至 team explorer 頁面內容|**Alt+0** (零)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|移至 team explorer 上一節內容|**Alt+向上箭**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|移至 team explorer 區段1內容|**Alt+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|移至 team explorer 區段2內容|**Alt+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|移至 team explorer 第3節內容|**Alt+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|移至 team explorer 第4節內容|**Alt+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|移至 team explorer 第5節內容|**Alt+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|移至 team explorer 第6節內容|**Alt+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|移至 team explorer 第7節內容|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|移至 team explorer 第8節內容|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|移至 team explorer 第9節內容|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Team explorer 向後導覽|**Alt + 向左鍵**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Team explorer 向前導覽|**Alt + 向右鍵**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|TFS 內容我的工作頁面建立複製 wi-fi|**Shift+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|TFS 內容我的工作頁面新增連結的 wi-fi|**Shift+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|重新整理|**F5**| View.Refresh |

### <a name="test-explorer"></a>測試總管

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|開啟測試|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>文字編輯器

此內容的特定快速鍵如下：


| 命令 | 鍵盤快速鍵 |命令 ID|
|-|-|-|
|中斷線| **Enter**<br /><br /> 或<br /><br /> **Shift+Enter** | Edit.BreakLine |
|左邊的字元| **向左鍵** | Edit.CharLeft |
|字元左方擴充| **Shift + 向左鍵** | Edit.CharLeftExtend |
|Char left 擴充資料行| **Shift + Alt + 向左鍵** | Edit.CharLeftExtendColumn |
|右移字元| **向右鍵** | Edit.CharRight |
|字元右延伸| **Shift + 向右鍵** | Edit.CharRightExtend |
|Char right 擴充資料行| **Shift + Alt + 向右鍵** | Edit.CharRightExtendColumn |
|清除書籤| **Ctrl + K、Ctrl + L** | Edit.ClearBookmarks |
|折迭所有大綱| **Ctrl + M、Ctrl + A** | Edit.CollapseAllOutlining |
|折迭目前區域| **Ctrl + M、Ctrl + S** | Edit.CollapseCurrentRegion |
|折迭標記| **Ctrl+M、Ctrl+T** | Edit.CollapseTag |
|折迭至定義| **Ctrl+M、Ctrl+O** (字母 'O') | Edit.CollapseToDefinitions |
|縮小選取範圍| **Shift + Alt +-** | Edit.ContractSelection |
|批註選取範圍| **Ctrl + K、Ctrl + C** | Edit.CommentSelection |
|自動完成文字| **Ctrl + 空格鍵**<br /><br /> 或<br /><br /> **Alt + 向右鍵** | Edit.CompleteWord |
|複製參數提示| **Ctrl + Shift + Alt + C** | Edit.CopyParameterTip |
|減少篩選層級| **Alt +、** | Edit.DecreaseFilterLevel |
|向後刪除| **格**<br /><br /> 或<br /><br /> **Shift+退格鍵** | Edit.DeleteBackwards |
|刪除水準空白字元| **Ctrl + K、Ctrl +\\** | Edit.DeleteHorizontalWhiteSpace |
|檔結束| **Ctrl+End** | Edit.DocumentEnd |
|檔結束擴充| **Ctrl + Shift + End** | Edit.DocumentEndExtend |
|檔開始| **Ctrl+Home** | Edit.DocumentStart |
|檔開始延伸| **Ctrl + Shift + Home** | Edit.DocumentStartExtend |
|展開所有大綱| **Ctrl + M、Ctrl + X** | Edit.ExpandAllOutlining |
|展開目前的區域| **Ctrl + M、Ctrl + E** | Edit.ExpandCurrentRegion |
|展開選取範圍| **Shift + Alt + =** | Edit.ExpandSelection |
|展開選取範圍到包含區塊| **Shift + Alt +]** | Edit.ExpandSelectiontoContainingBlock |
|格式化文件| **Ctrl + K、Ctrl + D** | Edit.FormatDocument |
|格式選取項目| **Ctrl + K、Ctrl + F** | Edit.FormatSelection |
|全部移至| **Ctrl + T**<br /><br /> 或<br /><br /> **Ctrl +、** | Edit.GotoAll |
|Goto 大括弧| **Ctrl +]** | Edit.GotoBrace |
|Goto 大括弧延伸| **Ctrl + Shift +]** | Edit.GotoBraceExtend |
|移至最近| **Ctrl+T、R** | Edit.GotoRecent |
|移至檔案中的下一個問題| **Alt+PgDn** | Edit.GotoNextIssueinFile |
|移至檔案中的上一個問題| **Alt+PgUp** | Edit.GotoPreviousIssueinFile |
|隱藏選取| **Ctrl + M、Ctrl + H** | Edit.HideSelection |
|增加篩選層級| **Alt +。** | Edit.IncreaseFilterLevel |
|漸進式搜尋| **Ctrl+I** | Edit.IncrementalSearch |
|在所有相符的位置插入游標| **Shift + Alt +;** | Edit.InsertCaretsatAllMatching |
|插入下一個相符的插入號| **Shift + Alt +。** | Edit.InsertNextMatchingCaret |
|插入索引標籤| **Tab** | Edit.InsertTab |
|垂直線剪下| **Ctrl + L** | Edit.LineCut |
|行刪除| **Ctrl + Shift + L** | Edit.LineDelete |
|向下捲動一行| **向下箭號** | Edit.LineDown |
|行向下擴充| **Shift + 向下鍵** | Edit.LineDownExtend |
|行向下擴充資料行| **Shift + Alt + 向下鍵** | Edit.LineDownExtendColumn |
|行尾| **結束** | Edit.LineEnd |
|行尾延伸| **Shift+End** | Edit.LineEndExtend |
|行尾延伸資料行| **Shift + Alt + End** | Edit.LineEndExtendColumn |
|上面的行開啟| **Ctrl + Enter** | Edit.LineOpenAbove |
|行開啟| **Ctrl+Shift+Enter** | Edit.LineOpenBelow |
|行首| **首頁** | Edit.LineStart |
|行開始延伸| **Shift+Home** | Edit.LineStartExtend |
|行開始延伸資料行| **Shift + Alt + Home** | Edit.LineStartExtendColumn |
|換行| **Shift + Alt + T** | Edit.LineTranspose |
|向上捲動一行| **向上箭號** | Edit.LineUp |
|行向上擴充| **Shift + 向上鍵** | Edit.LineUpExtend |
|排行擴充資料行| **Shift+Alt+向上鍵** | Edit.LineUpExtendColumn |
|列出成員| **Ctrl + J** | Edit.ListMembers |
|設成小寫| **Ctrl + U** | Edit.MakeLowercase |
|設為大寫| **Ctrl + Shift + U** | Edit.MakeUppercase |
|將選取的行向下移| **Alt + 向下鍵** | Edit.MoveSelectedLinesDown |
|將選取的行向上移動| **Alt+向上箭** | Edit.MoveSelectedLinesUp |
|下一個反白顯示的參考| **Ctrl+Shift+向下鍵** | Edit.NextHighlightedReference |
|改寫模式| **插入** | Edit.OvertypeMode |
|向下捲動一頁| **PgDn** | Edit.PageDown |
|Page down 擴充| **Shift+PgDn** | Edit.PageDownExtend |
|向上捲動一頁| **PgUp** | Edit.PageUp |
|Page up 擴充| **Shift+PgUp** | Edit.PageUpExtend |
|參數資訊| **Ctrl+Shift+空格鍵** | Edit.ParameterInfo |
|貼上參數提示| **Ctrl + Shift + Alt + P** | Edit.PasteParameterTip |
|往回查看| **Ctrl + Alt +-** | Edit.PeekBackward |
|查看定義| **Alt+F12** | Edit.PeekDefinition |
|向前查看| **Ctrl + Alt + =** | Edit.PeekForward |
|上一個反白顯示的參考| **Ctrl+Shift+向上鍵** | Edit.PreviousHighlightedReference |
|快速諮詢| **Ctrl + K、Ctrl + I** | Edit.QuickInfo |
|反向遞增搜尋| **Ctrl + Shift + I** | Edit.ReverseIncrementalSearch |
|向下滾動行| **Ctrl + 向下鍵** | Edit.ScrollLineDown |
|向上滾動行| **Ctrl + 向上鍵** | Edit.ScrollLineUp |
|選取目前的單字| **Ctrl + W** | Edit.SelectCurrentWord |
|選取 [取消]| **ESC 鍵** | Edit.SelectionCancel |
|選取以上次返回| **Ctrl + =** | Edit.SelectToLastGoBack |
|顯示程式碼的鏡頭功能表| **Ctrl + K、Ctrl +\`** | Edit.ShowCodeLensMenu |
|顯示導覽功能表| **Alt +\`** | Edit.ShowNavigateMenu |
|停止隱藏目前的| **Ctrl + M、Ctrl + U** | Edit.StopHidingCurrent |
|停止大綱| **Ctrl + M、Ctrl + P** | Edit.StopOutlining |
|交換錨點| **Ctrl + K、Ctrl + A** | Edit.SwapAnchor |
|靠左 Tab| **Shift + Tab** | Edit.TabLeft |
|切換所有大綱| **Ctrl + M、Ctrl + L** | Edit.ToggleAllOutlining |
|切換書籤| **Ctrl + K、Ctrl + K** | Edit.ToggleBookmark |
|切換完成模式| **Ctrl+Alt+空格鍵** | Edit.ToggleCompletionMode |
|切換大綱展開| **Ctrl + M、Ctrl + M** | Edit.ToggleOutliningExpansion |
|切換工作清單快捷方式| **Ctrl + K、Ctrl + H** | Edit.ToggleTaskListShortcut |
|切換自動換行| **Ctrl+E、Ctrl+W** | Edit.ToggleWordWrap |
|取消選取專案的批註| **Ctrl + K、Ctrl + U** | Edit.UncommentSelection |
|視圖底部| **Ctrl+PgDn** | Edit.ViewBottom |
|視圖底部延伸| **Ctrl+Shift+PgDn** | Edit.ViewBottomExtend |
|視圖頂端| **Ctrl+PgUp** | Edit.ViewTop |
|視圖頂端擴充| **Ctrl+Shift+PgUp** | Edit.ViewTopExtend |
|視圖空白字元| **Ctrl + R、Ctrl + W** | Edit.ViewWhiteSpace |
|單字刪除到結尾| **Ctrl + Delete** | Edit.WordDeleteToEnd |
|Word 刪除以開始| **Ctrl + 倒退鍵** | Edit.WordDeleteToStart |
|下一字| **Ctrl+向右鍵** | Edit.WordNext |
|Word 下一步擴充| **Ctrl + Shift + 向右鍵** | Edit.WordNextExtend |
|Word 下一欄擴充資料行| **Ctrl+Shift+Alt+向右鍵** | Edit.WordNextExtendColumn |
|先前的 Word| **Ctrl+向左鍵** | Edit.WordPrevious |
|Word 先前的擴充| **Ctrl+Shift+向左鍵** | Edit.WordPreviousExtend |
|Word 先前的擴充資料行| **Ctrl+Shift+Alt+向左鍵** | Edit.WordPreviousExtendColumn |
|Word 換置| **Ctrl + Shift + T** | Edit.WordTranspose |
|以互動方式執行| **Alt+Enter** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|以互動方式執行行| **Alt + '** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Page inspector 中的 View| **Ctrl+K、Ctrl+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|TFS 批註移動下一個區域| **Alt+PgDn** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|TFS 批註移動先前的區域| **Alt+PgUp** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram"></a>UML 活動圖表

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|刪除|**Shift+Del**| Edit.Delete |

### <a name="uml-class-diagram"></a>UML 類別圖表

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|從模型中刪除|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-component-diagram"></a>UML 元件圖表

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|從模型中刪除|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>UML 使用案例圖表

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|從模型中刪除|**Shift+Del**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>VC 快速鍵編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|新加速器|**插入**| Edit.NewAccelerator |
|輸入的下一個索引鍵|**Ctrl + W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>VC 對話方塊編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|向下移動控制項|**向下箭號**| Edit.MoveControlDown |
|左移控制項|**向左鍵**| Edit.MoveControlLeft |
|向右移動控制項|**向右鍵**| Edit.MoveControlRight |
|向上移動控制項|**向上箭號**| Edit.MoveControlUp |
|左邊滾動資料行|**Ctrl+向左鍵**| Edit.ScrollColumnLeft |
|向右滾動資料行|**Ctrl+向右鍵**| Edit.ScrollColumnRight |
|向下滾動行|**Ctrl + 向下鍵**| Edit.ScrollLineDown |
|向上滾動行|**Ctrl + 向上鍵**| Edit.ScrollLineUp |
|調整控制項大小|**Shift + 向下鍵**| Edit.SizeControlDown |
|左邊的大小控制項|**Shift + 向左鍵**| Edit.SizeControlLeft |
|大小控制許可權|**Shift + 向右鍵**| Edit.SizeControlRight |
|調整控制項大小|**Shift + 向上鍵**| Edit.SizeControlUp |
|靠上對齊|**Ctrl+Shift+向下鍵**| Format.AlignBottoms |
|對齊中心|**Shift + F9**| Format.AlignCenters |
|靠左對齊|**Ctrl+Shift+向左鍵**| Format.AlignLefts |
|垂直對齊|**F9**| Format.AlignMiddles |
|調整許可權|**Ctrl + Shift + 向右鍵**| Format.AlignRights |
|對齊頂端|**Ctrl+Shift+向上鍵**| Format.AlignTops |
|按鈕底部|**Ctrl + B**| Format.ButtonBottom |
|按鈕右移|**Ctrl + R**| Format.ButtonRight |
|水準置中|**Ctrl + Shift + F9**| Format.CenterHorizontal |
|垂直置中|**Ctrl + F9**| Format.CenterVertical |
|檢查助憶鍵|**Ctrl + M**| Format.CheckMnemonics |
|內容大小|**Shift+F7**| Format.SizetoContent |
|跨越的空間|**Alt + 向右鍵**<br /><br /> 或<br /><br /> **Alt + 向左鍵**| Format.SpaceAcross |
|空間減少|**Alt+向上箭**<br /><br /> 或<br /><br /> **Alt + 向下鍵**| Format.SpaceDown |
|定位順序|**Ctrl+D**| Format.TabOrder |
|測試對話方塊|**Ctrl + T**| Format.TestDialog |
|切換輔助線|**Ctrl + G**| Format.ToggleGuides |

### <a name="vc-image-editor"></a>VC 影像編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|噴槍工具|**Ctrl + A**| Image.AirbrushTool |
|筆刷工具|**Ctrl + B**| Image.BrushTool |
|複製和大綱選取專案|**Ctrl + Shift + U**| Image.CopyandOutlineSelection |
|繪製不透明|**Ctrl + J**| Image.DrawOpaque |
|橢圓形工具|**Alt + P**| Image.EllipseTool |
|清除工具|**Ctrl + Shift + I**| Image.EraseTool |
|填滿橢圓形工具|**Ctrl + Shift + Alt + P**| Image.FilledEllipseTool |
|填滿矩形工具|**Ctrl + Shift + Alt + R**| Image.FilledRectangleTool |
|實心圓角矩形工具|**Ctrl+Shift+Alt+W**| Image.FilledRoundedRectangleTool |
|填滿工具|**Ctrl + F**| Image.FillTool |
|水準翻轉|**Ctrl + H**| Image.FlipHorizontal |
|垂直翻轉|**Shift+Alt+H**| Image.FlipVertical |
|較大筆刷|**Ctrl + =**| Image.LargerBrush |
|線條工具|**Ctrl + L**| Image.LineTool |
|放大工具|**Ctrl + M**| Image.MagnificationTool |
|放大|**Ctrl + Shift + M**| Image.Magnify |
|新增映射類型|**插入**| Image.NewImageType |
|下一色彩|**Ctrl +]**<br /><br /> 或<br /><br /> **Ctrl+向右鍵**| Image.NextColor |
|下一個右邊的色彩|**Ctrl + Shift +]**<br /><br /> 或<br /><br /> **Ctrl + Shift + 向右鍵**| Image.NextRightColor |
|空心橢圓形工具|**Shift+Alt+P**| Image.OutlinedEllipseTool |
|空心矩形工具|**Shift+Alt+R**| Image.OutlinedRectangleTool |
|空心圓角矩形工具|**Shift+Alt+W**| Image.OutlinedRoundedRectangleTool |
|鉛筆工具|**Ctrl+I**| Image.PencilTool |
|上一個色彩|**Ctrl + [**<br /><br /> 或<br /><br /> **Ctrl+向左鍵**| Image.PreviousColor |
|上一個右邊的色彩|**Ctrl + Shift + [**<br /><br /> 或<br /><br /> **Ctrl+Shift+向左鍵**| Image.PreviousRightColor |
|矩形選取工具|**Shift+Alt+S**| Image.RectangleSelectionTool |
|矩形工具|**Alt + R**| Image.RectangleTool |
|旋轉90度度|**Ctrl + Shift + H**| Image.Rotate90Degrees |
|圓角矩形工具|**Alt + W**| Image.RoundedRectangleTool |
|顯示格線|**Ctrl+Alt+S**| Image.ShowGrid |
|顯示磚方格|**Ctrl+Shift+Alt+S**| Image.ShowTileGrid |
|小型筆刷|**Ctrl +。**| Image.SmallBrush |
|較小筆刷|**Ctrl +-**| Image.SmallerBrush |
|文字工具|**Ctrl + T**| Image.TextTool |
|使用選取範圍作為筆刷|**Ctrl + U**| Image.UseSelectionasBrush |
|放大|**Ctrl + Shift +。**<br /><br /> 或<br /><br /> **Ctrl + 向上鍵**| Image.ZoomIn |
|縮小|**Ctrl + Shift +、**<br /><br /> 或<br /><br /> **Ctrl + 向下鍵**| Image.ZoomOut |

### <a name="vc-string-editor"></a>VC 字串編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|新字串|**插入**| Edit.NewString |

### <a name="view-designer"></a>檢視設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|取消取出資料|**Ctrl + T**| QueryDesigner.CancelRetrievingData |
|準則|**Ctrl + 2**| QueryDesigner.Criteria |
|圖表|**Ctrl + 1**| QueryDesigner.Diagram |
|執行 SQL。|**Ctrl + R**| QueryDesigner.ExecuteSQL |
|Goto 資料列|**Ctrl + G**| QueryDesigner.GotoRow |
|聯結模式|**Ctrl + Shift + J**| QueryDesigner.JoinMode |
|結果|**Ctrl + 4**| QueryDesigner.Results |
|Sql|**Ctrl + 3**| QueryDesigner.SQL |

### <a name="visual-studio"></a>Visual Studio

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|隱藏方法窗格|**Ctrl + 1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer"></a>Windows Form 設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|中斷線|**Enter**| Edit.BreakLine |
|左邊的字元|**向左鍵**| Edit.CharLeft |
|字元左方擴充|**Shift + 向左鍵**| Edit.CharLeftExtend |
|右移字元|**向右鍵**| Edit.CharRight |
|字元右延伸|**Shift + 向右鍵**| Edit.CharRightExtend |
|檔結束|**結束**| Edit.DocumentEnd |
|檔結束擴充|**Shift+End**| Edit.DocumentEndExtend |
|檔開始|**首頁**| Edit.DocumentStart |
|檔開始延伸|**Shift+Home**| Edit.DocumentStartExtend |
|插入索引標籤|**Tab**| Edit.InsertTab |
|向下捲動一行|**向下箭號**| Edit.LineDown |
|行向下擴充|**Shift + 向上鍵**| Edit.LineDownExtend |
|向上捲動一行|**向上箭號**| Edit.LineUp |
|行向上擴充|**Shift + 向下鍵**| Edit.LineUpExtend |
|向下移動控制項|**Ctrl + 向下鍵**| Edit.MoveControlDown |
|左移控制項|**Ctrl+向左鍵**| Edit.MoveControlLeft |
|向右移動控制項|**Ctrl+向右鍵**| Edit.MoveControlRight |
|向上移動控制項|**Ctrl + 向上鍵**| Edit.MoveControlUp |
|選取 [取消]|**ESC 鍵**| Edit.SelectionCancel |
|調整控制項大小|**Ctrl+Shift+向下鍵**| Edit.SizeControlDown |
|左邊的大小控制項|**Ctrl+Shift+向左鍵**| Edit.SizeControlLeft |
|大小控制許可權|**Ctrl + Shift + 向右鍵**| Edit.SizeControlRight |
|調整控制項大小|**Ctrl+Shift+向上鍵**| Edit.SizeControlUp |
|靠左 Tab|**Shift + Tab**| Edit.TabLeft |

### <a name="work-item-editor"></a>工作項目編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|建立工作專案的複本|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|重新整理工作專案|**F5**| Edit.RefreshWorkItem |
|新增連結工作專案|**Shift+Alt+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view"></a>工作項目查詢檢視

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|建立工作專案的複本|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|縮排|**Shift + Alt + 向右鍵**| Edit.Indent |
|凸排|**Shift + Alt + 向左鍵**| Edit.Outdent |
|新增連結工作專案|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|重新整理|**F5**| Team.Refresh |
|切換|**Shift+Alt+V**| Window.Toggle |

### <a name="work-item-results-view"></a>工作項目結果檢視

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|建立工作專案的複本|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|縮排|**Shift + Alt + 向右鍵**| Edit.Indent |
|凸排|**Shift + Alt + 向左鍵**| Edit.Outdent |
|前往下一個工作專案|**Shift+Alt+N**| Team.GotoNextWorkItem |
|移至上一個工作專案|**Shift+Alt+P**| Team.GotoPreviousWorkItem |
|新增連結工作專案|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|重新整理|**F5**| Team.Refresh |
|切換|**Shift+Alt+V**| Window.Toggle |

### <a name="workflow-designer"></a>工作流程設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|自動完成文字|**Ctrl+K、W**<br /><br /> 或<br /><br /> **Ctrl + K、Ctrl + W**<br /><br /> 或<br /><br /> **Ctrl + 空格鍵**<br /><br /> 或<br /><br /> **Alt + 向右鍵**| Edit.CompleteWord |
|減少篩選層級|**Alt +、**| Edit.DecreaseFilterLevel |
|增加篩選層級|**Alt +。**| Edit.IncreaseFilterLevel |
|列出成員|**Ctrl+K、L**<br /><br /> 或<br /><br /> **Ctrl + K、Ctrl + L**<br /><br /> 或<br /><br /> **Ctrl + J**| Edit.ListMembers |
|參數資訊|**Ctrl+K、P**<br /><br /> 或<br /><br /> **Ctrl + K、Ctrl + P**<br /><br /> 或<br /><br /> **Ctrl+Shift+空格鍵**| Edit.ParameterInfo |
|快速諮詢|**Ctrl+K、I**<br /><br /> 或<br /><br /> **Ctrl + K、Ctrl + I**| Edit.QuickInfo |
|摺疊|**Ctrl+E、Ctrl+C**<br /><br /> 或<br /><br /> **Ctrl+E、C**| WorkflowDesigner.Collapse |
|全部摺疊|或| WorkflowDesigner.CollapseAll |
|連線節點|**Ctrl+E、Ctrl+F**<br /><br /> 或<br /><br /> **Ctrl+E、F**| WorkflowDesigner.ConnectNodes |
|建立變數|**Ctrl+E、Ctrl+N**<br /><br /> 或<br /><br /> **Ctrl+E、N**| WorkflowDesigner.CreateVariable |
|全部展開|**Ctrl+E、Ctrl+X**<br /><br /> 或<br /><br /> **Ctrl+E、X**| WorkflowDesigner.ExpandAll |
|就地展開|**Ctrl+E、Ctrl+E**<br /><br /> 或<br /><br /> **Ctrl+E、E**| WorkflowDesigner.ExpandInPlace |
|移至父系|**Ctrl+E、Ctrl+P**<br /><br /> 或<br /><br /> **Ctrl+E、P**| WorkflowDesigner.GoToParent |
|移動焦點|**Ctrl+E、Ctrl+M**<br /><br /> 或<br /><br /> **Ctrl+E、M**| WorkflowDesigner.MoveFocus |
|流覽設計工具|**Ctrl+Alt+F6**| WorkflowDesigner.NavigateThroughDesigner |
|還原|**Ctrl+E、Ctrl+R**<br /><br /> 或<br /><br /> **Ctrl+E、R**| WorkflowDesigner.Restore |
|顯示隱藏引數設計工具|**Ctrl+E、Ctrl+A**<br /><br /> 或<br /><br /> **Ctrl+E、A**| WorkflowDesigner.ShowHideArgumentDesigner |
|顯示隱藏匯入設計工具|**Ctrl+E、Ctrl+I**<br /><br /> 或<br /><br /> **Ctrl+E、I**| WorkflowDesigner.ShowHideImportsDesigner |
|顯示隱藏總覽圖|**Ctrl+E、Ctrl+O** (字母 'O')<br /><br /> 或<br /><br /> **Ctrl+E、O**| WorkflowDesigner.ShowHideOverviewMap |
|顯示隱藏變數設計工具|**Ctrl+E、Ctrl+V**<br /><br /> 或<br /><br /> **Ctrl+E、V**| WorkflowDesigner.ShowHideVariableDesigner |
|切換選取範圍|**Ctrl+E、Ctrl+S**<br /><br /> 或<br /><br /> **Ctrl+E、S**| WorkflowDesigner.ToggleSelection |
|放大|**Ctrl+Num +**| WorkflowDesigner.ZoomIn |
|縮小|**Ctrl + Num-**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>XAML 設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|全部調整|**Ctrl + 0** (零) | Design.FitAll |
|顯示控點|**F9**| Design.ShowHandles |
|放大|**Ctrl + Alt + =**| Design.ZoomIn |
|縮小|**Ctrl + Alt +-**| Design.ZoomOut |
|設計工具選項|**Ctrl + Shift +;**|
|編輯文字|**F2**| Format.EditText |
|全部|**Ctrl + Shift + R**| Format.ResetLayout.All |
|執行專案程式碼|**Ctrl + F9**|
|只隱藏 (Blend) |**Ctrl + H**| Timeline.Hide (僅限混合) |
|僅鎖定 (Blend) |**Ctrl + L**| Timeline.Lock (僅限混合) |
|只顯示 (Blend) |**Ctrl + Shift + H**| Timeline.Show (僅限混合) |
|將 (Blend 解除鎖定) |**Ctrl + Shift + L**| Timeline.Unlock (僅限混合) |
|左邊緣下移|**Ctrl + Shift +、**| View.EdgeLeftMoveLeft |
|左邊緣右移|**Ctrl + Shift +。**| View.EdgeLeftMoveRight |
|Edge 向左移動|**Ctrl+Shift+Alt+,**| View.EdgeRightMoveLeft |
|Edge 右移右移|**Ctrl + Shift + Alt +。**| View.EdgeRightMoveRight |
|顯示內容標記功能表|**Ctrl + 空格鍵**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>XML (文字) 編輯器

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|啟動 XSLT 調試|**Alt + F5**| XML.StartXSLTDebugging |
|啟動 XSLT 而不進行調試|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>XML 結構描述設計工具

此內容的特定快速鍵如下：


|命令|鍵盤快速鍵|命令 ID|
|-|-|-|
|從下到上|**Alt+向上箭**| GraphView.BottomtoTop |
|由左至右|**Alt + 向右鍵**| GraphView.LefttoRight |
|由右至左|**Alt + 向左鍵**| GraphView.RighttoLeft |
|從上到下|**Alt + 向下鍵**| GraphView.ToptoBottom |
|從工作區移除|**刪除**| OtherContextMenus.GraphView.RemovefromWorkspace |
|顯示內容模型視圖|**Ctrl + 2**| XsdDesigner.ShowContentModelView |
|顯示圖形視圖|**Ctrl + 3**| XsdDesigner.ShowGraphView |
|顯示開始視圖|**Ctrl + 1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](reference/visual-studio-commands.md)
