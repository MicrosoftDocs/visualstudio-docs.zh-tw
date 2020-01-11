---
title: 進行偵錯時對應呼叫堆疊上的方法
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 43
author: MikeJo5000
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 414022e4e3c058826705845d57de62a9114fc821
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847513"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>在 Visual Studio 中進行偵錯時對應呼叫堆疊上的方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在偵錯時建立 Code Map 以視覺方式追蹤呼叫堆疊。 您可以在對應圖上做筆記，追蹤程式碼的執行狀況，以便專注於尋找 Bug。

 ![在 code map 上使用呼叫堆疊進行偵錯工具](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 您需要下列項目：

- [Visual Studio 企業版](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- 可以偵錯的程式碼，例如 Visual C# .NET、Visual Basic .NET、C++、JavaScript 或 X++

  請參閱：[影片：使用 Code Map 偵錯工具整合（Channel 9）以視覺化方式進行偵錯工具](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)•[對應呼叫堆疊](#MapStack)•[對程式碼進行附注](#MakeNotes)•[使用下一個呼叫堆疊更新對應](#UpdateMap)•[將相關程式碼加入至對應圖](#AddRelatedCode)•[使用對應來尋找 bug](#FindBugs) • [Q & A](#QA)

  如需您在處理 code map 時可使用的命令和動作的詳細資訊，請參閱[流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

## <a name="MapStack"></a> 對應呼叫堆疊

1. 開始偵錯。 （鍵盤： **F5**）

2. 當您的應用程式進入中斷模式，或您逐步執行函式之後，請選擇 [ **Code Map**]。 （鍵盤： **Ctrl** + **Shift** +  **`** ）

     ![選擇 Code Map 以開始對應呼叫堆疊](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：

     ![請參閱 Code Map 上的呼叫堆疊](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     當您繼續偵錯時，對應會自動更新。 請參閱[使用下一個呼叫堆疊更新對應](#UpdateMap)。

## <a name="MakeNotes"></a> 製作程式碼的筆記
 加入註解以追蹤程式碼中發生的狀況。 若要在批註中加入新的一行，請按**Shift + Return**。

 ![將批註新增至 Code Map 上的呼叫堆疊](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> 以下一個呼叫堆疊更新地圖
 執行應用程式到下一個中斷點或逐步執行函式。 對應圖中就會加入新的呼叫堆疊。

 ![使用下一個呼叫堆疊更新 Code Map](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> 將相關程式碼新增至地圖
 現在您已經有了對應圖，下一步要做什麼？ 如果您是使用 Visual C# .NET 或 Visual Basic .NET，請加入項目 (例如欄位、屬性及其他方法) 以追蹤程式碼中發生的情況。

 按兩下某個方法以查看它的程式碼定義，或使用方法的捷徑功能表 （鍵盤：選取地圖上的方法，然後按**F12**）

 ![移至 Code Map 上方法的程式碼定義](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 在對應圖上加入您要追蹤的項目。

 ![在呼叫堆疊上的方法中顯示欄位 Code Map](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> 根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。 雖然這很有用，但您可以使用 [對應] 工具列上的 [**包含**父系] 按鈕關閉這項功能，或在加入專案時按**CTRL 鍵**，讓對應保持簡單。

 ![與呼叫堆疊上的方法相關的欄位 Code Map](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 您可以在這裡輕鬆查看哪些方法使用相同的欄位。 最新加入的項目會以綠色顯示。

 繼續建置對應圖來查看更多程式碼。

 ![請參閱使用欄位的方法：呼叫堆疊 Code Map](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![在呼叫堆疊上使用欄位的方法 Code Map](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> 使用地圖尋找 Bug
 視覺化程式碼可協助您更快速找到 Bug。 例如，假設您正在調查繪圖程式中的 Bug。 當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。

 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：

 ![將另一個呼叫堆疊新增至 Code Map](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。 這或許可以解釋 `undo` 不會立即執行的原因。

 在修正 Bug 並繼續執行程式之後，對應圖會加入從 `undo` 到 `Repaint` 的新呼叫：

 ![將新的方法呼叫加入至 Code Map 上的呼叫堆疊](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> 問與答

- **並非所有的呼叫都會出現在對應上。因此?**

   根據預設，只有您的程式碼會出現在對應圖上。 若要查看外部程式碼，請在 [**呼叫堆疊**] 視窗中開啟它：

   ![使用 [呼叫堆疊] 視窗顯示外部程式碼](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   或在 Visual Studio 調試選項中關閉 [**啟用 Just My Code** ]：

   ![使用選項對話方塊顯示外部程式碼](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **變更對應是否會影響程式碼？**

   變更對應圖完全不會影響程式碼。 請放心地重新命名、移動或移除對應圖上的任何項目。

- **此訊息的意義是：「圖表可能是以舊版的程式碼為基礎」？**

   從您上次更新對應圖之後，程式碼可能已經變更。 例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。 關閉訊息，然後先嘗試重建方案後再更新對應圖。

- **如何? 控制地圖的版面配置嗎？**

   開啟 [對應] 工具列上的 [**版面**配置] 功能表：

  - 變更預設的版面配置。

  - 若要停止自動重新排列地圖，請**在進行調試時關閉自動版面**配置。

  - 若要在加入專案時盡可能少重新排列地圖，請關閉 [**增量**配置]。

- **我可以與其他人共用對應嗎？**

   您可以匯出對應圖，傳送給其他人 (如果您有 Microsoft Outlook)，也可以將它儲存到方案中，以便將它簽入 Team Foundation 版本控制。

   ![與其他人共用呼叫堆疊 Code Map](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **如何? 停止對應自動加入新的呼叫堆疊嗎？**

   選擇 [在地圖工具列上![自動顯示 Code Map 上的呼叫堆疊] 按鈕&#45; ](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") 。 若要以手動方式將目前的呼叫堆疊加入至地圖，請按**Ctrl** + **Shift** +  **`** 。

   在偵錯時，對應圖會繼續反白顯示對應圖上現有的呼叫堆疊。

- **專案圖示和箭號代表什麼意思？**

   若要取得某個項目的詳細資訊，請將滑鼠指標移至項目上方並查看項目的工具提示。 您也可以查看**圖例**，以瞭解每個圖示所代表的意義。

   ![呼叫堆疊上的圖示 Code Map 是什麼意思？](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  請參閱：[對應呼叫堆疊](#MapStack)•[對程式碼進行附注](#MakeNotes)•[使用下一個呼叫堆疊更新對應](#UpdateMap)•[將相關程式碼加入至對應圖](#AddRelatedCode)•[使用對應尋找 bug](#FindBugs)

## <a name="see-also"></a>請參閱
 [對應整個方案](../modeling/map-dependencies-across-your-solutions.md)的相依性[使用 code map 來對應用程式進行 debug](../modeling/use-code-maps-to-debug-your-applications.md) ，使用 Code Map 分析器[流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)來[尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)
