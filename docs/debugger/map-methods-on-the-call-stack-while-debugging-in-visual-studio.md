---
title: 建立呼叫堆疊的視覺導覽圖 |Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9fe3471f7165cf48f62dee3ca657e78fbfafd273
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837395"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-in-visual-studio-enterprise"></a>在 Visual Studio Enterprise 中偵錯時建立的視覺效果的對應呼叫堆疊
建立 code map 以視覺方式追蹤呼叫堆疊，當您偵錯。 您可以在對應圖上做筆記，追蹤程式碼的執行狀況，以便專注於尋找 Bug。

 您需要下列項目：

-   [Visual Studio 企業版](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

-   您可以偵錯，例如 Visual C#、 Visual Basic、 c + +、 JavaScript 或 X + + 的程式碼

以下是快速查看 code map:

 ![使用 code map 上的呼叫堆疊偵錯](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

 請參閱：

- [影片： 可以使用 Code Map 偵錯工具整合 (Channel 9) 以視覺化方式偵錯](http://go.microsoft.com/fwlink/?LinkId=293418)

- [對應呼叫堆疊](#MapStack)

- [附註解的程式碼](#MakeNotes)

- [下一個呼叫堆疊更新對應圖](#UpdateMap)

- [將相關程式碼加入至對應](#AddRelatedCode)

- [使用地圖尋找 bug](#FindBugs)

- [問與答](#QA)

  如需命令和使用 code map 時，您可以使用的動作的詳細資訊，請參閱 <<c0> [ 瀏覽和重新整理 code map](../modeling/browse-and-rearrange-code-maps.md)。

##  <a name="MapStack"></a> 對應呼叫堆疊

1.  開始偵錯。 (鍵盤： **F5**)

2.  您的應用程式進入中斷模式或是您逐步執行函式之後，請選擇**Code Map**。 (鍵盤： **Ctrl** + **Shift** + **`**)

     ![選擇 開始對應堆疊呼叫 Code Map](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")

     目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：

     ![請參閱在 code map 上的呼叫堆疊](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     當您繼續偵錯時，對應會自動更新。 請參閱[以下一個呼叫堆疊更新對應圖](#UpdateMap)。

##  <a name="MakeNotes"></a> 附註解的程式碼
 新增註解，以追蹤程式碼中的情況。 若要加入新的一行的註解，請按**Shift + Return**。

 ![新增堆疊呼叫 code map 上的註解](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> 下一個呼叫堆疊更新對應圖
 執行應用程式到下一個中斷點或逐步執行函式。 對應圖中就會加入新的呼叫堆疊。

 ![更新 code map，包含下一個呼叫堆疊](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

##  <a name="AddRelatedCode"></a> 將相關程式碼加入至對應
 現在您已經有對應-什麼接下來？ 如果您正在使用 Visual C# 或 Visual Basic 中，新增項目，例如欄位、 屬性和其他方法，來追蹤程式碼中的情況。

 按兩下某個方法以查看它的程式碼定義，或使用方法的捷徑功能表 (鍵盤： 選取的方法，在地圖，然後按**F12**)

 ![移至 code map 上方法的程式碼定義](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 在對應圖上加入您要追蹤的項目。

 ![顯示堆疊呼叫 code map 上的方法中的欄位](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
>  根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。 雖然這很有用，您可以簡化對應圖關閉這項功能會使用**包含父代**按鈕，在 [對應] 工具列中，或按下**CTRL**當您新增的項目。

 ![在堆疊呼叫 code map 上的方法相關的欄位](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

 您可以在這裡輕鬆查看哪些方法使用相同的欄位。 最新加入的項目會以綠色顯示。

 繼續建置對應圖來查看更多程式碼。

 ![請參閱使用欄位的方法： 堆疊呼叫 code map](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![堆疊呼叫 code map 使用欄位的方法](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> 使用地圖尋找 bug
 視覺化程式碼可協助您更快速找到 Bug。 例如，假設您正在調查繪圖程式中的 bug。 當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。

 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：

 ![新增其他堆疊呼叫 code map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。 這或許可以解釋為什麼`undo`立即無法運作。

 在修正 Bug 並繼續執行程式之後，對應圖會加入從 `undo` 到 `Repaint` 的新呼叫：

 ![在 code map 上新增新方法的呼叫堆疊](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

##  <a name="QA"></a> 問與答

- **並非所有的呼叫會顯示在地圖上。為什麼？**

   根據預設，只有您的程式碼會出現在對應圖上。 若要查看外部程式碼，它在中開啟**呼叫堆疊**視窗：

   ![顯示外部程式碼，使用 [呼叫堆疊] 視窗](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")

   或關閉**啟用 Just My Code**在 Visual Studio 偵錯選項：

   ![顯示外部程式碼，使用 [選項] 對話方塊](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

- **變更對應會影響到程式碼嗎？**

   變更對應圖不會影響以任何方式的程式碼。 請放心地重新命名、移動或移除對應圖上的任何項目。

- **此訊息表示什麼: 「 圖表可能根據舊版程式碼 」？**

   從您上次更新對應圖之後，程式碼可能已經變更。 例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。 關閉訊息，然後先嘗試重建方案後再更新對應圖。

- **我要如何控制地圖的版面配置？**

   開啟**版面配置**map 工具列上的功能表：

  -   變更預設的版面配置。

  -   若要停止自動重新整理對應，請關閉**偵錯時自動配置**。

  -   若要新增項目時，重新排列盡可能對應，請關閉**累加配置**。

- **可以與其他人共用對應嗎？**

   您可以匯出對應圖，傳送給其他人 (如果您有 Microsoft Outlook)，也可以將它儲存到方案中，以便將它簽入 Team Foundation 版本控制。

   ![共用堆疊呼叫 code map 與他人](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")

- **如何停止自動加入新的呼叫堆疊的對應？**

   選擇![按鈕&#45;顯示呼叫堆疊 code map 上自動](../debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") map 工具列上。 若要手動新增至對應的目前呼叫堆疊，請按**Ctrl** + **Shift** + **`**。

   偵錯時，將現有的呼叫堆疊，在地圖上反白顯示對應圖會繼續。

- **項目圖示和箭號的意義為何？**

   若要取得項目的相關詳細資訊，請將滑鼠指標移並查看項目的工具提示。 您也可以看看**圖例**若要深入了解每個圖示的意義。

   ![堆疊呼叫 code map 上的圖示代表什麼意思？](../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")

  請參閱：

- [對應呼叫堆疊](#MapStack)

- [附註解的程式碼](#MakeNotes)

- [下一個呼叫堆疊更新對應圖](#UpdateMap)

- [將相關程式碼加入至對應](#AddRelatedCode)

- [使用地圖尋找 bug](#FindBugs)

## <a name="see-also"></a>另請參閱
 [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)[使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)[尋找潛在的問題，使用程式碼對應分析器](../modeling/find-potential-problems-using-code-map-analyzers.md)[瀏覽和重新整理 code map](../modeling/browse-and-rearrange-code-maps.md)