---
title: Spy + + 工具列 |Microsoft Docs
description: 瞭解 Spy + + 工具列中出現在功能表列底下的使用者介面元素。 若要顯示或隱藏工具列，請按一下 [View] 功能表上的 [工具列]。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: af6db0f367c73804197ef35d0b3734d68f15a332
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903525"
---
# <a name="spy-toolbar"></a>Spy++ 工具列
工具列會出現在 Spy + + 的功能表列下方。 若要顯示或隱藏工具列，請按一下 [ **View** ] 功能表上的 [ **工具列**]。

 工具列上提供下列控制項。

## <a name="uielement-list"></a>UIElement 清單

|按鈕|效果|
|------------|------------|
|![Spy&#43;&#43; Windows 按鈕](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|顯示系統中視窗和控制項的樹狀檢視。 如需詳細資訊，請參閱 [Windows View](../debugger/windows-view.md)。|
|![Spy&#43;&#43; 進程按鈕](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|顯示系統中進程的樹狀檢視。 如需詳細資訊，請參閱 [進程視圖](../debugger/processes-view.md)。|
|![Spy&#43;&#43; 執行緒按鈕](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|顯示系統中線程的樹狀檢視。 如需詳細資訊，請參閱 [執行緒視圖](../debugger/threads-view.md)。|
|![Spy&#43;&#43; 訊息按鈕](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|建立視窗來顯示視窗訊息，並開啟 [ **訊息選項** ] 對話方塊，讓您可以選取要顯示其訊息的視窗，也可以選取 [其他選項]。 如需詳細資訊，請參閱 [訊息查看](../debugger/messages-view.md)。|
|![Spy&#43;&#43; 開機記錄按鈕](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|啟動訊息記錄，並顯示訊息串流。 只有當 [ **訊息** ] 視窗是使用中視窗時，才能使用這個控制項。 如需詳細資訊，請參閱 [如何：啟動和停止訊息記錄顯示](../debugger/how-to-start-and-stop-the-message-log-display.md)。|
|![Spy&#43;&#43; 停止記錄按鈕](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|停止訊息記錄和訊息資料流程的顯示。 只有當 [ **訊息** ] 視窗是使用中視窗時，才能使用這個控制項。 如需詳細資訊，請參閱 [如何：啟動和停止訊息記錄顯示](../debugger/how-to-start-and-stop-the-message-log-display.md)。|
|![Spy&#43;&#43; 記錄檔選項按鈕](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|顯示 [ [訊息選項](../debugger/message-options-dialog-box.md) ] 對話方塊。 使用此對話方塊來選取要進行流覽的視窗和訊息類型。 只有當 [ **訊息** ] 視窗是使用中視窗時，才能使用這個控制項。|
|![Spy&#43;&#43; 清除記錄按鈕](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|清除 [活動 **訊息** ] 視窗的內容。 只有當 [ **訊息** ] 視窗是使用中視窗時，才能使用這個控制項。|
|![Spy&#43;&#43; 尋找視窗按鈕](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|開啟 [ [尋找視窗](../debugger/find-window-dialog-box.md) ] 對話方塊，此對話方塊可讓您設定視窗搜尋準則，以及顯示內容或訊息。 如需詳細資訊，請參閱 [如何：使用 Finder 工具](../debugger/how-to-use-the-finder-tool.md)。|
|![Spy&#43;&#43; 尋找第一個視窗按鈕](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|在目前的視圖中搜尋相符的視窗、進程、執行緒或訊息。|
|![Spy&#43;&#43; 尋找下一個視窗按鈕](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|在目前的視圖中搜尋下一個相符的視窗、進程、執行緒或訊息。 只有當有效的搜尋結果不是唯一時，才能使用此控制項 (和相關的功能表命令) 。 例如，當您使用視窗控制碼做為視窗樹狀結構中的搜尋準則時，它會產生唯一的結果，因為視窗樹狀結構中只有一個視窗具有該控制碼;在此實例中， **找不到 [下一步]** 。|
|![Spy&#43;&#43; 尋找上一個視窗按鈕](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|在目前的視圖中搜尋先前相符的視窗、進程、執行緒或訊息。 只有當有效的搜尋結果不是唯一時，才能使用此控制項 (和相關的功能表命令) 。 例如，當您使用視窗控制碼做為視窗樹狀結構中的搜尋準則時，它會產生唯一的結果，因為視窗樹狀結構中只有一個視窗具有該控制碼;在此實例中， **找不到 [上一步** ]。|
|![Spy&#43;&#43; Property Explorer 按鈕](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|顯示在 Windows view 中選取之視窗的屬性。|
|![Spy&#43;&#43; 重新整理按鈕](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|重新整理系統檢視。|

## <a name="see-also"></a>另請參閱
- [使用 Spy++](../debugger/using-spy-increment.md)
- [Spy++ 檢視](../debugger/spy-increment-views.md)
- [Spy++ 參考](../debugger/spy-increment-reference.md)