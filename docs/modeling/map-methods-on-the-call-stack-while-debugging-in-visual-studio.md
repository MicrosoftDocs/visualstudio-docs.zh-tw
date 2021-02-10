---
title: 進行偵錯時對應呼叫堆疊上的方法
description: 瞭解如何建立 code map，以在進行偵錯工具時以視覺化方式追蹤呼叫堆疊。 此外，也請瞭解您可以在地圖上做筆記，以追蹤程式碼的執行狀況。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7196cf06e7d6bcde33bc1e4a6c5d0ebfac486576
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946484"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>在 Visual Studio 中進行偵錯時對應呼叫堆疊上的方法

在您偵錯時建立 Code Map 以視覺方式追蹤呼叫堆疊。 您可以在對應圖上做筆記，追蹤程式碼的執行狀況，以便專注於尋找 Bug。

 ![使用 Code Map 上的堆疊呼叫來偵錯](../debugger/media/debuggermap_overview.png)

 您將需要：

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- 您可以進行 debug 錯的程式碼，例如 Visual c #、Visual Basic、c + +、JavaScript 或 X + +

  請參閱：

- [影片：以視覺化方式使用 Code Map 偵錯工具整合 (Channel 9) ](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [對應呼叫堆疊](#MapStack)

- [製作程式碼的注意事項](#MakeNotes)

- [使用下一個呼叫堆疊更新對應](#UpdateMap)

- [將相關程式碼加入至地圖](#AddRelatedCode)

- [使用地圖尋找 bug](#FindBugs)

- [問與答](#QA)

  如需使用 code map 時可使用的命令和動作的詳細資訊，請參閱 [流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

## <a name="map-the-call-stack"></a><a name="MapStack"></a> 對應呼叫堆疊

1. 開始偵錯。  (鍵盤： **F5**) 

2. 當您的應用程式進入中斷模式或您逐步執行函式之後，請選擇 [ **Code Map**]。  (鍵盤： **Ctrl**  +  **Shift**  +  **`**) 

     ![選擇 [Code Map] 開始對應堆疊呼叫](../debugger/media/debuggermap_choosecodemap.png)

     目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：

     ![查看 Code Map 上的堆疊呼叫](../debugger/media/debuggermap_seeundocallstack.png)

     當您繼續偵錯時，對應會自動更新。 請參閱 [使用下一個呼叫堆疊更新對應](#UpdateMap)。

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> 製作程式碼的筆記

 新增批註以追蹤程式碼中發生的狀況。 若要在批註中加入新的一行，請按 **Shift + Return**。

 ![為 Code Map 上的堆疊呼叫加入註解](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> 以下一個呼叫堆疊更新地圖

 執行應用程式到下一個中斷點或逐步執行函式。 對應圖中就會加入新的呼叫堆疊。

 ![使用下一個堆疊呼叫來更新 Code Map](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> 將相關程式碼新增至地圖

 您現在已有對應，接下來該怎麼做？ 如果您使用 c # 或 Visual Basic，請加入專案（例如欄位、屬性和其他方法），以追蹤程式碼中發生的狀況。

 按兩下某個方法以查看它的程式碼定義，或使用方法的捷徑功能表  (鍵盤：選取地圖上的方法，然後按下 **F12**) 

 ![移至 Code Map 上方法的程式碼定義](../debugger/media/debuggermap_gotocodedefinition.png)

 在對應圖上加入您要追蹤的項目。

 ![顯示堆疊呼叫 Code Map 上的方法中的欄位](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> 根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。 雖然這很有用，但您可以使用 [對應] 工具列上的 [ **包含** 父系] 按鈕關閉這項功能，或在加入專案時按 **CTRL** 鍵，以保持簡單的對應。

 ![與堆疊呼叫 Code Map 上的方法相關的欄位](../debugger/media/debuggermap_showedfields.png)

 您可以在這裡輕鬆查看哪些方法使用相同的欄位。 最新加入的項目會以綠色顯示。

 繼續建置對應圖來查看更多程式碼。

 ![查看使用欄位的方法：堆疊呼叫 Code Map](../debugger/media/debuggermap_findallreferences.png)

 ![堆疊呼叫 Code Map 上使用欄位的方法](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> 使用地圖尋找 Bug

 視覺化程式碼可協助您更快速找到 Bug。 例如，假設您正在調查繪圖程式中的 bug。 當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。

 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：

 ![將其他堆疊呼叫加入至 Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。 這或許能解釋 `undo` 未立即執行的原因。

 在修正 Bug 並繼續執行程式之後，對應圖會加入從 `undo` 到 `Repaint` 的新呼叫：

 ![為 Code Map 上的堆疊呼叫新增方法呼叫](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> 問 & A

- **並非所有的呼叫都會出現在地圖上。為什麼？**

   根據預設，只有您的程式碼會出現在對應圖上。 若要查看外部程式碼，請在 [ **呼叫堆疊** ] 視窗中開啟它：

   ![使用 [呼叫堆疊] 視窗來顯示外部程式碼](../debugger/media/debuggermap_callstackmenu.png)

   或者，在 Visual Studio 調試選項中關閉 [ **啟用 Just My Code** ：

   ![使用 [選項] 對話方塊來顯示外部程式碼](../debugger/media/debuggermap_debugoptions.png)

- **變更對應圖是否會影響程式碼？**

   變更地圖不會以任何方式影響程式碼。 請放心地重新命名、移動或移除對應圖上的任何項目。

- **這則訊息表示「圖表可能是以較舊版本的程式碼為基礎」的意思：**

   從您上次更新對應圖之後，程式碼可能已經變更。 例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。 關閉訊息，然後先嘗試重建方案後再更新對應圖。

- **如何? 控制地圖的版面配置？**

   開啟地圖工具列上的 [ **版面** 配置] 功能表：

  - 變更預設的版面配置。

  - 若要停止自動重新排列對應，請 **在調試時關閉自動** 配置。

  - 若要在加入專案時盡可能地重新排列地圖，請關閉 [累加 **式版面** 配置]。

- **我是否可以和其他人共用對應圖？**

   如果您有 Microsoft Outlook，您可以匯出地圖、將它傳送給其他人，或是將它儲存到您的方案，以便將它簽入原始檔控制。

   ![與其他人共用堆疊呼叫 Code Map](../debugger/media/debuggermap_sharewithothers.png)

- **如何讓對應圖停止自動加入新的呼叫堆疊？**

   選擇 ![ [按鈕] &#45; 在地圖工具列上自動顯示 code map 上的呼叫堆疊 ](../debugger/media/debuggermap_automaticupdateicon.gif) 。 若要將目前的呼叫堆疊手動加入至地圖，請按下 **Ctrl**  +  **Shift**  +  **`** 。

   當您正在進行調試時，對應會繼續反白顯示對應上的現有呼叫堆疊。

- **項目圖示和箭號是什麼意思？**

   若要取得專案的詳細資訊，請將滑鼠指標移至該專案上方，並查看專案的工具提示。 您也可以查看 **圖例** ，以瞭解每個圖示的意義。

   ![堆疊呼叫 Code Map 上的圖示代表什麼意思？](../debugger/media/debuggermap_showlegend.png)

  請參閱：

- [對應呼叫堆疊](#MapStack)

- [製作程式碼的注意事項](#MakeNotes)

- [使用下一個呼叫堆疊更新對應](#UpdateMap)

- [將相關程式碼加入至地圖](#AddRelatedCode)

- [使用地圖尋找 bug](#FindBugs)

## <a name="see-also"></a>另請參閱

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)
- [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)
- [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
