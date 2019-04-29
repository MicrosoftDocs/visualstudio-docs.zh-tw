---
title: Spy + + 工具列 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101b4ad50777f796a3de82127f6ce3253b26ccaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930800"
---
# <a name="spy-toolbar"></a>Spy++ 工具列
工具列會出現在功能表列，Spy + + 中。 若要顯示或隱藏工具列，請在**檢視**功能表上，按一下**工具列**。

 下列控制項可在工具列上。

## <a name="uielement-list"></a>UIElement 清單

|按鈕|作用|
|------------|------------|
|![Spy&#43; &#43; Windows 按鈕](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + （_w)")|顯示系統中的視窗和控制項的樹狀檢視。 如需詳細資訊，請參閱 < [Windows 檢視](../debugger/windows-view.md)。|
|![Spy&#43; &#43;按鈕會處理](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|顯示系統中的程序的樹狀結構檢視。 如需詳細資訊，請參閱 <<c0> [ 處理序檢視](../debugger/processes-view.md)。|
|![Spy&#43; &#43;執行緒按鈕](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|顯示樹狀檢視中的執行緒在系統中。 如需詳細資訊，請參閱 <<c0> [ 執行緒檢視](../debugger/threads-view.md)。|
|![Spy&#43; &#43;按鈕的訊息](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + 訊息 （_m)")|建立視窗以顯示視窗訊息，並開啟**訊息選項**對話方塊，讓您可以選取的視窗的訊息將會顯示，而且也選取 其他選項。 如需詳細資訊，請參閱 <<c0> [ 訊息檢視](../debugger/messages-view.md)。|
|![Spy&#43; &#43;啟動記錄檔 按鈕](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|啟動訊息記錄，並顯示訊息資料流。 此控制項是時才可使用**訊息**視窗是作用中視窗。 如需詳細資訊，請參閱[如何：啟動與停止訊息記錄顯示](../debugger/how-to-start-and-stop-the-message-log-display.md)。|
|![Spy&#43; &#43;停止記錄 按鈕](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|停止訊息記錄和顯示的訊息資料流。 此控制項是時才可使用**訊息**視窗是作用中視窗。 如需詳細資訊，請參閱[如何：啟動與停止訊息記錄顯示](../debugger/how-to-start-and-stop-the-message-log-display.md)。|
|![Spy&#43; &#43;記錄檔選項按鈕](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|顯示[訊息選項](../debugger/message-options-dialog-box.md) 對話方塊。 使用此對話方塊來選取視窗，然後訊息進行檢視的類型。 此控制項是時才可使用**訊息**視窗是作用中視窗。|
|![Spy&#43; &#43;清除記錄檔 按鈕](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|清除作用中的內容**訊息**視窗。 此控制項是時才可使用**訊息**視窗是作用中視窗。|
|![Spy&#43; &#43;尋找視窗 按鈕](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|會開啟[尋找視窗](../debugger/find-window-dialog-box.md)對話方塊中，可讓您設定視窗搜尋條件，並顯示屬性或訊息。 如需詳細資訊，請參閱[如何：使用搜尋工具](../debugger/how-to-use-the-finder-tool.md)。|
|![Spy&#43; &#43;尋找第一個視窗 按鈕](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|搜尋相符的視窗、 程序、 執行緒或訊息的目前檢視。|
|![Spy&#43; &#43;尋找下一個視窗 按鈕](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|會搜尋目前的檢視中的下一個相符的視窗、 程序、 執行緒或訊息。 不是唯一有效的搜尋結果時，此控制項 （與相關的功能表命令） 是可用。 例如，當您使用的視窗控制代碼與視窗樹狀目錄中的搜尋準則時，它會產生唯一的結果因為具有該控制代碼; 的視窗樹狀目錄中只有一個視窗在這種情況**尋找下一個**不提供。|
|![Spy&#43; &#43;尋找上一個視窗 按鈕](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|搜尋上一個相符的視窗、 程序、 執行緒或訊息的目前檢視。 不是唯一有效的搜尋結果時，此控制項 （與相關的功能表命令） 是可用。 例如，當您使用的視窗控制代碼與視窗樹狀目錄中的搜尋準則時，它會產生唯一的結果因為具有該控制代碼; 的視窗樹狀目錄中只有一個視窗在這種情況**找上一個**不提供。|
|![Spy&#43; &#43;屬性瀏覽器 按鈕](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|會顯示在 [Windows] 檢視中選取視窗的屬性。|
|![Spy&#43; &#43;重新整理 按鈕](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + （_r)")|重新整理的系統檢視表。|

## <a name="see-also"></a>另請參閱
- [使用 Spy++](../debugger/using-spy-increment.md)
- [Spy++ 檢視](../debugger/spy-increment-views.md)
- [Spy++ 參考](../debugger/spy-increment-reference.md)