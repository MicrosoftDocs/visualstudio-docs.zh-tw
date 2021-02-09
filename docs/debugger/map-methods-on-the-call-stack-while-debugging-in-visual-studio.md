---
title: 建立呼叫堆疊的視覺地圖 |Microsoft Docs
description: 建立 code map，以在您進行偵錯工具時以視覺化方式追蹤呼叫堆疊。 在地圖上製作附注來追蹤程式碼的執行內容，讓您可以專注于尋找 bug。
ms.custom: SEO-VS-2020
ms.date: 11/26/2018
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9f047708383cdcf3cb8bc06ab2d835e2a2cf300
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893187"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>在 (c #、Visual Basic、c + +、JavaScript 的偵錯工具時，建立呼叫堆疊的視覺對應) 

在您偵錯時建立 Code Map 以視覺方式追蹤呼叫堆疊。 您可以在地圖上做筆記來追蹤程式碼的執行狀況，以便專注於尋找 Bug。

如需逐步解說中，觀看此影片：[影片：使用 Code Map 偵錯工具整合 (Channel 9) 以視覺化方式進行偵錯](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

如需可搭配 code map 使用的命令和動作詳細資訊，請參閱 [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

>[!IMPORTANT]
>您只能在 [Visual Studio Enterprise edition](https://visualstudio.microsoft.com/downloads)中建立 code map。

以下是 code map 的快速流覽：

 ![使用 Code Map 上的堆疊呼叫來偵錯](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="map-the-call-stack"></a><a name="MapStack"></a> 對應呼叫堆疊

1. 在 Visual Studio Enterprise c #、Visual Basic、c + + 或 JavaScript 專案中，選取 [ **Debug**  >  **開始調試** 程式] 或按 **F5** 來開始偵錯工具。

1. 當您的應用程式進入中斷模式或您逐步執行函式之後，請選取 [ **Debug**  >  **Code Map**]，或按 **Ctrl** + **Shift** + **`** 。

   目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：

   ![查看 Code Map 上的堆疊呼叫](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Code map 會在您繼續進行偵錯工具時自動更新。 變更對應專案或版面配置不會以任何方式影響程式碼。 請放心地重新命名、移動或移除對應圖上的任何項目。

若要取得專案的詳細資訊，請將滑鼠停留在其上方，並查看專案的工具提示。 您也可以在工具列中選取 [ **圖例** ]，以瞭解每個圖示的意義。

![Code Map 圖例](../debugger/media/debuggermap_showlegend.png "Code Map 圖例")

>[!NOTE]
>此圖表可能會以 code map 頂端的 **舊版程式碼為基礎** ，表示程式碼在您上次更新對應之後可能已變更。 例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。 關閉訊息，然後先嘗試重建方案後再更新對應圖。

## <a name="map-external-code"></a>對應外部程式碼

根據預設，只有您的程式碼會出現在對應圖上。 若要查看地圖上的外部程式碼：

- 在 [ **呼叫堆疊** ] 視窗中按一下滑鼠右鍵，然後選取 [ **顯示外部程式碼**]：

  ![使用 [呼叫堆疊] 視窗來顯示外部程式碼](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- 或者，取消選取 [在 Visual Studio **工具** 中 **啟用 Just My Code** ] (或 [ **Debug** ]) >**選項** 的  >  **調試**：

  ![使用 [選項] 對話方塊來顯示外部程式碼](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>控制地圖的版面配置

變更地圖的版面配置不會以任何方式影響程式碼。

若要控制地圖的版面配置，請選取 map 工具列上的 [ **版面** 配置] 功能表。

在 [ **版面** 配置] 功能表中，您可以：

- 變更預設的版面配置。
- 停止重新排列對應，方法是在偵錯工具取消停用 **自動版面** 配置。
- 當您加入專案時，重新整理地圖越少越好，方法是取消選擇 **增量** 配置。

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> 製作程式碼的筆記

您可以新增批註來追蹤程式碼中發生的狀況。

若要加入批註，請以滑鼠右鍵按一下 code map，然後選取 [**編輯**  >  **新批註**]，再輸入批註。

若要在批註中加入新的一行，請按 **Shift** + **鍵**。

 ![為 Code Map 上的堆疊呼叫加入註解](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> 以下一個呼叫堆疊更新地圖

當您執行應用程式到下一個中斷點或逐步執行函式時，地圖會自動加入新的呼叫堆疊。

![使用下一個堆疊呼叫來更新 Code Map](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

若要停止對應以自動加入新的呼叫堆疊，請選取 [在 code map 工具列上 ![自動顯示 code map 上的呼叫堆疊](../debugger/media/debuggermap_automaticupdateicon.gif "自動在 code map 上顯示呼叫堆疊") ]。 對應會繼續醒目提示現有的呼叫堆疊。 若要將目前的呼叫堆疊手動加入至地圖，請按下 **Ctrl** + **Shift** + **`** 。

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> 將相關程式碼新增至地圖

現在您已經有一個地圖，您可以在 c # 或 Visual Basic 中加入欄位、屬性和其他方法等專案，以追蹤程式碼中發生的狀況。

若要移至程式碼中方法的定義，請按兩下對應中的方法，或選取該方法並按下 **F12** 鍵，或以滑鼠右鍵按一下它，然後選取 [ **移至定義**]。

![移至 Code Map 上方法的程式碼定義](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

若要將您要追蹤的專案加入至地圖，請在方法上按一下滑鼠右鍵，然後選取您要追蹤的專案。最近新增的專案會以綠色顯示。

![與堆疊呼叫 Code Map 上的方法相關的欄位](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。 您可以選取 code map 工具列上的 [ **包含父代** ] 按鈕，或在加入專案時按 **Ctrl** 鍵，關閉並開啟此功能。

![顯示堆疊呼叫 Code Map 上的方法中的欄位](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

繼續建置對應圖來查看更多程式碼。

 ![查看使用欄位的方法：堆疊呼叫 Code Map](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![堆疊呼叫 Code Map 上使用欄位的方法](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> 使用地圖尋找 Bug
 視覺化程式碼可協助您更快速找到 Bug。 例如，假設您正在調查繪圖應用程式中的 bug。 當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。

 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：

 ![將其他堆疊呼叫加入至 Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。 這或許能解釋 `undo` 未立即執行的原因。

 修正錯誤並繼續執行應用程式之後，對應會將新的呼叫從新增 `undo` 至 `Repaint` ：

 ![為 Code Map 上的堆疊呼叫新增方法呼叫](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>與其他人共用地圖

您可以匯出地圖、使用 Microsoft Outlook 將它傳送給其他人、將它儲存到您的解決方案，然後將它簽入版本控制。

若要共用或儲存對應，請使用 code map 工具列上的 [ **共用** ]。

![與其他人共用堆疊呼叫 Code Map](../debugger/media/debuggermap_sharewithothers.png "與其他人共用堆疊呼叫 Code Map")

## <a name="see-also"></a>另請參閱
[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)

[使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)

[使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)

[瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
