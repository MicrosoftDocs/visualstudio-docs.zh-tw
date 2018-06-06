---
title: 在 Visual Studio 中進行偵錯時對應呼叫堆疊上的方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 111a1180f694b57a4e5ae013a41128a4a7e9e9f5
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748682"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>在 Visual Studio 中進行偵錯時對應呼叫堆疊上的方法
建立 code map 以視覺方式追蹤呼叫堆疊偵錯時。 您可以在對應圖上做筆記，追蹤程式碼的執行狀況，以便專注於尋找 Bug。

 ![使用 Code Map 上的堆疊呼叫來偵錯](../debugger/media/debuggermap_overview.png)

 您需要下列項目：

-   [Visual Studio 企業版](https://www.visualstudio.com/downloads/download-visual-studio-vs)

-   您可以偵錯，例如 Visual C#、 Visual Basic、 c + +、 JavaScript 或 X + + 的程式碼

 請參閱：

-   [影片： 視覺化方式偵錯使用 Code Map 偵錯工具整合 (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

-   [對應呼叫堆疊](#MapStack)

-   [做有關程式碼的筆記](#MakeNotes)

-   [使用下一個呼叫堆疊更新對應](#UpdateMap)

-   [將相關程式碼加入至對應](#AddRelatedCode)

-   [使用對應圖尋找 bug](#FindBugs)

-   [問與答](#QA)

 如需命令和使用 code map 時，您可以使用的動作的詳細資訊，請參閱[瀏覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

##  <a name="MapStack"></a> 對應呼叫堆疊

1.  開始偵錯。 (鍵盤： **F5**)

2.  您的應用程式進入中斷模式或是您逐步執行函式之後，請選擇**Code Map**。 (鍵盤： **Ctrl** + **Shift** + **`**)

     ![選擇 [Code Map] 開始對應堆疊呼叫](../debugger/media/debuggermap_choosecodemap.png)

     目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：

     ![查看 Code Map 上的堆疊呼叫](../debugger/media/debuggermap_seeundocallstack.png)

     當您繼續偵錯時，對應會自動更新。 請參閱[下一個呼叫堆疊更新對應圖](#UpdateMap)。

##  <a name="MakeNotes"></a> 做有關程式碼的筆記
 加入註解以追蹤程式碼中的情況。 若要加入新的一行的註解，請按**Shift + Return**。

 ![為 Code Map 上的堆疊呼叫加入註解](../debugger/media/debuggermap_addcomment.png)

##  <a name="UpdateMap"></a> 使用下一個呼叫堆疊更新對應
 執行應用程式到下一個中斷點或逐步執行函式。 對應圖中就會加入新的呼叫堆疊。

 ![使用下一個堆疊呼叫來更新 Code Map](../debugger/media/debuggermap_addclearcallstack.png)

##  <a name="AddRelatedCode"></a> 將相關程式碼加入至對應
 現在您已經有對應的什麼接下來？ 如果您使用 C# 或 Visual Basic，加入項目，例如欄位、 屬性和其他方法，以追蹤程式碼中的情況。

 按兩下某個方法以查看它的程式碼定義，或使用方法的捷徑功能表 (鍵盤： 選取的方法上的地圖和按**F12**)

 ![移至 Code Map 上方法的程式碼定義](../debugger/media/debuggermap_gotocodedefinition.png)

 在對應圖上加入您要追蹤的項目。

 ![顯示堆疊呼叫 Code Map 上的方法中的欄位](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
>  根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。 雖然這很有用，您可以簡化對應圖關閉此功能使用**包含父代**按鈕對應工具列上，或按**CTRL**當您將加入的項目。

 ![與堆疊呼叫 Code Map 上的方法相關的欄位](../debugger/media/debuggermap_showedfields.png)

 您可以在這裡輕鬆查看哪些方法使用相同的欄位。 最新加入的項目會以綠色顯示。

 繼續建置對應圖來查看更多程式碼。

 ![查看使用欄位的方法：堆疊呼叫 Code Map](../debugger/media/debuggermap_findallreferences.png)

 ![堆疊呼叫 Code Map 上使用欄位的方法](../debugger/media/debuggermap_foundallreferences.png)

##  <a name="FindBugs"></a> 使用對應圖尋找 bug
 視覺化程式碼可協助您更快速找到 Bug。 例如，假設您正在調查繪圖程式中的 bug。 當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。

 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：

 ![將其他堆疊呼叫加入至 Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。 這或許可以解釋為什麼`undo`立即無法運作。

 在修正 Bug 並繼續執行程式之後，對應圖會加入從 `undo` 到 `Repaint` 的新呼叫：

 ![為 Code Map 上的堆疊呼叫新增方法呼叫](../debugger/media/debuggermap_addnewcallforrepaint.png)

##  <a name="QA"></a> 問與答

-   **並非所有的呼叫會顯示在地圖上。為什麼？**

     根據預設，只有您的程式碼會出現在對應圖上。 若要查看外部程式碼，它在開啟**呼叫堆疊**視窗：

     ![使用 [呼叫堆疊] 視窗來顯示外部程式碼](../debugger/media/debuggermap_callstackmenu.png)

     或關閉**啟用 Just My Code**在 Visual Studio 偵錯選項：

     ![使用 [選項] 對話方塊來顯示外部程式碼](../debugger/media/debuggermap_debugoptions.png)

-   **變更對應圖是否會影響程式碼？**

     變更對應圖不會影響任何方式中的程式碼。 請放心地重新命名、移動或移除對應圖上的任何項目。

-   **此訊息什麼: 「 圖表可能會根據較舊版本的程式碼 」？**

     從您上次更新對應圖之後，程式碼可能已經變更。 例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。 關閉訊息，然後先嘗試重建方案後再更新對應圖。

-   **我要如何控制地圖的版面配置？**

     開啟**配置**map 工具列上的功能表：

    -   變更預設的版面配置。

    -   若要停止自動重新排列對應，請關閉**偵錯時自動配置**。

    -   若要新增項目時，重新排列盡可能對應，請關閉**累加配置**。

-   **可以與其他人共用對應圖？**

     您可以匯出對應圖，傳送給其他人 (如果您有 Microsoft Outlook)，也可以將它儲存到方案中，以便將它簽入 Team Foundation 版本控制。

     ![與其他人共用堆疊呼叫 Code Map](../debugger/media/debuggermap_sharewithothers.png)

-   **如何避免加入新的呼叫堆疊會自動讓對應圖？**

     選擇![按鈕&#45;顯示呼叫堆疊 code map 上自動](../debugger/media/debuggermap_automaticupdateicon.gif)map 工具列上。 若要手動新增至對應的目前呼叫堆疊，請按**Ctrl** + **Shift** + **`**。

     地圖會繼續偵錯時，反白顯示在地圖上現有的呼叫堆疊。

-   **項目圖示和箭號代表什麼？**

     若要取得項目的詳細資訊，請將滑鼠指標移並查看項目的工具提示。 您也可以查看**圖例**若要了解每個圖示的意義。

     ![呼叫堆疊 Code Map 上的圖示代表什麼意思？](../debugger/media/debuggermap_showlegend.png)

 請參閱：

-   [對應呼叫堆疊](#MapStack)

-   [做有關程式碼的筆記](#MakeNotes)

-   [使用下一個呼叫堆疊更新對應](#UpdateMap)

-   [將相關程式碼加入至對應](#AddRelatedCode)

-   [使用對應圖尋找 bug](#FindBugs)

## <a name="see-also"></a>另請參閱

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)
- [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)
- [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
