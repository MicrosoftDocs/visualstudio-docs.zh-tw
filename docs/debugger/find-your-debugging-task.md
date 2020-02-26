---
title: 尋找您的偵錯工作
description: 識別可協助您對應用程式進行錯用的偵錯工具功能
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578776"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>在 Visual Studio 中尋找您的偵錯工具工作

如果您需要協助將您的偵錯工具對應至相關 Visual Studio 偵錯工具的正確功能，請使用本文中提供的連結。 此處的工作清單包含一般工作，例如暫停程式碼以進行偵錯工具、檢查變數，以及將訊息傳送至 [**輸出**] 視窗。 如果您需要偵錯工具功能的總覽，請參閱[第一次查看偵錯工具](debugger-feature-tour.md)。

## <a name="pause-running-code"></a>暫停執行中的程式碼

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>暫停執行中的程式碼，以檢查可能包含 bug 的程式程式碼

設定中斷點。 如需詳細資訊，請參閱[使用中斷點](using-breakpoints.md)。

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>當您的應用程式達到特定狀態時暫停並加以檢查

請嘗試條件式中斷點，以控制使用條件式邏輯啟動中斷點的位置和時機。 如需詳細資訊，請參閱[中斷點條件](using-breakpoints.md#breakpoint-conditions)。

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>只有當特定物件的屬性或值變更時，才暫停程式碼

針對C++，設定[資料中斷點](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)。 
::: moniker range=">= vs-2019"
針對使用 .NET Core 3 的應用程式，您也可以設定[資料中斷點](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)。
::: moniker-end

否則，僅C#適用F#于和，您可以[使用條件式中斷點追蹤物件識別碼](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)。

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>在特定反復專案中暫停迴圈內部的程式碼

使用 [叫用**計數**] 做為條件來設定中斷點。 如需詳細資訊，請參閱[計數](using-breakpoints.md#set-a-hit-count-condition)。

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>當您知道函式名稱但不是它的位置時，在函式的開頭暫停程式碼

您可以使用函式中斷點來執行此動作。 如需詳細資訊，請參閱設定函式[中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)。

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>在具有相同名稱的多個函式開頭暫停程式碼

當您有多個具有相同名稱的函式時（在不同的專案中有多載函式或函數），您可以使用函式[中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)。

### <a name="manage-and-keep-track-of-your-breakpoints"></a>管理和持續追蹤您的中斷點

使用 [**中斷點**] 視窗。 如需詳細資訊，請參閱[管理中斷點](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)。

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>當擲回特定的已處理或未處理的例外狀況時暫停程式碼和偵錯工具

雖然例外狀況協助程式會顯示發生錯誤的位置，但如果您想要暫停和偵測特定的錯誤，您可以[指示偵錯工具](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)在擲回例外狀況時中斷。

### <a name="set-a-breakpoint-from-the-call-stack"></a>從呼叫堆疊設定中斷點

如果您想要在檢查執行流程或在 [**呼叫堆疊**] 視窗中查看函式時暫停和偵錯工具代碼，請參閱在[[呼叫堆疊] 視窗中設定中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)。

### <a name="pause-code-at-a-specific-assembly-instruction"></a>在特定的元件指令暫停程式碼

您可以從 [反組解碼[] 視窗設定中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)來執行這項操作。

## <a name="execute-code"></a>執行程式碼

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>瞭解在偵錯工具中逐步執行程式碼的命令

如需詳細資訊，請參閱[使用偵錯工具流覽程式碼](navigating-through-code-with-the-debugger.md)。

## <a name="inspect-data"></a>檢查資料

### <a name="check-the-value-of-variables-while-running-your-app"></a>在執行您的應用程式時檢查變數的值

使用[資料提示](view-data-values-in-data-tips-in-the-code-editor.md)將滑鼠停留在變數上，或[在 [自動變數] 和 [區域變數] 視窗中檢查變數](autos-and-locals-windows.md)。

### <a name="observe-the-changing-value-of-a-specific-variable"></a>觀察特定變數的變更值

在變數上設定監看式。 如需詳細資訊，請參閱[在變數上設定監看](watch-and-quickwatch-windows.md)式。

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>查看偵錯工具視窗太長的字串

在進行調試時，開啟內建的[字串視覺化檢視](view-strings-visualizer.md)。

## <a name="configure-debugging"></a>設定偵錯

### <a name="customize-information-shown-in-the-debugger"></a>自訂偵錯工具中顯示的資訊

在不同的偵錯工具視窗中，您可能會想要顯示物件類型以外的資訊做為值。 針對C#、Visual Basic、 F#和C++/Cli 程式碼，請使用[DebuggerDisplay](using-the-debuggerdisplay-attribute.md)屬性。 如需更多的選項，您也可以建立[自訂的視覺化](create-custom-visualizers-of-data.md)程式來自訂 UI。

若為C++原生，請使用[NatVis 架構](create-custom-views-of-native-objects.md)。

### <a name="configure-debugger-settings"></a>設定偵錯工具設定

若要設定偵錯工具選項和偵錯工具專案設定，請參閱[偵錯工具設定和準備](debugger-settings-and-preparation.md)。

## <a name="additional-tasks"></a>其他工作

### <a name="fix-an-exception"></a>修正例外狀況

請參閱[修正例外](write-better-code-with-visual-studio.md#fix-an-exception)狀況。

### <a name="edit-code-during-a-debugging-session"></a>在偵錯工具期間編輯程式碼

使用 [[編輯後繼續](edit-and-continue.md)]。 若是 XAML，請使用[Xaml 熱重載](../xaml-tools/xaml-hot-reload.md)。

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>將訊息傳送至 [輸出] 視窗而不修改程式碼

設定追蹤點。 如需詳細資訊，請參閱[使用追蹤點](using-tracepoints.md)。

## <a name="view-the-order-in-which-functions-are-called"></a>查看函數的呼叫順序

請參閱[如何觀看呼叫堆疊](how-to-use-the-call-stack-window.md)。

### <a name="debug-on-remote-machines"></a>在遠端電腦上進行調試

請參閱[遠端偵錯](remote-debugging.md)。

### <a name="debug-an-app-that-is-already-running"></a>對已在執行中的應用程式進行 Debug

請參閱[附加至正在執行的進程](attach-to-running-processes-with-the-visual-studio-debugger.md)。

### <a name="debug-multithreaded-applications"></a>對多執行緒應用程式進行偵錯

請參閱[Debug 多執行緒應用程式](debug-multithreaded-applications-in-visual-studio.md)。

### <a name="fix-performance-issues"></a>修正效能問題

請參閱程式碼[剖析工具的第一看](../profiling/profiling-feature-tour.md)