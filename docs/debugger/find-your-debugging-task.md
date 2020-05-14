---
title: 尋找您的偵錯工作
description: 確定可説明您調試應用的調試器功能
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302179"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>在視覺化工作室查找調試任務

如果您需要幫助將調試任務映射到相關視覺化工作室調試器的正確功能，請使用本文中提供的連結。 此處的工作清單包括常見任務，如暫停代碼以調試、檢查變數和向 **"輸出"** 視窗發送消息。 如果需要調試器功能的概述，請參閱[首先查看調試器](debugger-feature-tour.md)。

## <a name="pause-running-code"></a>暫停運行代碼

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>暫停運行代碼以檢查可能包含 Bug 的程式碼

設定中斷點。 有關詳細資訊，請參閱[使用中斷點](using-breakpoints.md)。

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>當應用達到特定狀態時暫停並檢查應用

嘗試條件中斷點以控制使用條件邏輯啟動中斷點的位置和時間。 有關詳細資訊，請參閱[中斷點條件](using-breakpoints.md#breakpoint-conditions)。

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>僅當特定物件的屬性或值發生更改時暫停代碼

對於C++，設置[資料中斷點](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)。 
::: moniker range=">= vs-2019"
對於使用 .NET Core 3 的應用，還可以設置[資料中斷點](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)。
::: moniker-end

否則，僅對於 C# 和 F#，可以使用[條件中斷點跟蹤物件識別碼。](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>在特定反覆運算時暫停迴圈內的代碼

使用**命中計數**作為條件設置中斷點。 有關詳細資訊，請參閱[命中計數](using-breakpoints.md#set-a-hit-count-condition)。

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>當您知道函數名稱但不知道函數名稱的位置時，在函數開始時暫停代碼

您可以使用函數中斷點執行此操作。 有關詳細資訊，請參閱[設置函數中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)。

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>在多個具有相同名稱的函數的開頭暫停代碼

當有多個具有相同名稱的函數（不同專案中的重載函數或函數）時，可以使用[函數中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)。

### <a name="manage-and-keep-track-of-your-breakpoints"></a>管理和跟蹤您的中斷點

使用 **"中斷點"** 視窗。 有關詳細資訊，請參閱[管理中斷點](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)。

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>引發特定處理或未處理的異常時暫停代碼並調試

儘管異常協助程式顯示發生錯誤的位置，但如果要暫停並調試特定錯誤，則可以[告訴調試器在引發異常時中斷](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)。

### <a name="set-a-breakpoint-from-the-call-stack"></a>從呼叫堆疊設置中斷點

如果要在"**呼叫堆疊"** 視窗中檢查執行流或查看函數時暫停和調試代碼，請參閱[在呼叫堆疊視窗中設置中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)。

### <a name="pause-code-at-a-specific-assembly-instruction"></a>在特定程式集指令處暫停代碼

可以通過[從"拆解"視窗設置中斷點](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)來執行此操作。

## <a name="execute-code"></a>執行代碼

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>瞭解在調試時要單一步驟代碼的命令

有關詳細資訊，請參閱[使用調試器導航代碼](navigating-through-code-with-the-debugger.md)。

## <a name="inspect-data"></a>檢查資料

### <a name="check-the-value-of-variables-while-running-your-app"></a>運行應用時檢查變數的值

使用[資料提示](view-data-values-in-data-tips-in-the-code-editor.md)將滑鼠懸停在變數[上或在"自動"和"區域變數"視窗中檢查變數](autos-and-locals-windows.md)。

### <a name="observe-the-changing-value-of-a-specific-variable"></a>觀察特定變數的變化值

在變數上設置監視。 有關詳細資訊，請參閱[在變數上設置監視](watch-and-quickwatch-windows.md)。

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>查看對於調試器視窗太長的字串

調試時打開內置[字串視覺化檢視](view-strings-visualizer.md)。

## <a name="configure-debugging"></a>設定偵錯

### <a name="customize-information-shown-in-the-debugger"></a>自訂調試器中顯示的資訊

您可能希望將物件類型以外的資訊顯示為不同調試器視窗中的值。 對於 C#、可視基本代碼、F# 和C++/CLI 代碼，請使用[調試器顯示](using-the-debuggerdisplay-attribute.md)屬性。 對於更高級的選項，還可以通過創建[自訂視覺化檢視](create-custom-visualizers-of-data.md)來自訂 UI。

對於本機C++，請使用[NatVis 框架](create-custom-views-of-native-objects.md)。

### <a name="configure-debugger-settings"></a>配置調試器設置

要配置調試器選項和調試器專案設置，請參閱[調試器設置和準備](debugger-settings-and-preparation.md)。

## <a name="additional-tasks"></a>其他工作

### <a name="fix-an-exception"></a>修復異常

請參閱[修復異常](write-better-code-with-visual-studio.md#fix-an-exception)。

### <a name="edit-code-during-a-debugging-session"></a>在調試會話期間編輯代碼

使用["編輯"並繼續](edit-and-continue.md)。 對於 XAML，請使用[XAML 熱重載入](../xaml-tools/xaml-hot-reload.md)。

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>在不修改代碼的情況下將消息發送到輸出視窗

設置追蹤點。 有關詳細資訊，請參閱[使用追蹤點](using-tracepoints.md)。

## <a name="view-the-order-in-which-functions-are-called"></a>查看調用函數的順序

請參閱[如何查看呼叫堆疊](how-to-use-the-call-stack-window.md)。

### <a name="debug-on-remote-machines"></a>在遠端電腦上調試

請參閱[遠端偵錯](remote-debugging.md)。

### <a name="debug-an-app-that-is-already-running"></a>調試已運行的應用

請參閱[附加到正在運行的進程](attach-to-running-processes-with-the-visual-studio-debugger.md)。

### <a name="debug-multithreaded-applications"></a>對多執行緒應用程式進行偵錯

請參閱[調試多執行緒應用程式](debug-multithreaded-applications-in-visual-studio.md)。

### <a name="fix-performance-issues"></a>修正效能問題

請參閱[首先查看分析工具](../profiling/profiling-feature-tour.md)