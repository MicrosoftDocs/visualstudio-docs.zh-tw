---
title: 建立呼叫堆疊的視覺效果地圖 |Microsoft Docs
ms.date: 11/26/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62fb77590a20b0e31648cab10f310851fd65820e
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180001"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>在調試過程中建立呼叫堆疊的視覺化地圖 (C#、Visual Basic、 C++、JavaScript)

在您偵錯時建立 Code Map 以視覺方式追蹤呼叫堆疊。 您可以在地圖上做筆記來追蹤程式碼的執行狀況，以便專注於尋找 Bug。

如需逐步解說, 請觀看這段影片:[影片：使用 Code Map 偵錯工具整合以視覺化方式進行偵錯工具 (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

如需可搭配 code map 使用之命令和動作的詳細資訊, 請參閱[流覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

>[!IMPORTANT]
>您只能在[Visual Studio Enterprise 版本](https://visualstudio.microsoft.com/downloads)中建立 code map。

以下是一個 Code Map 的快速流覽:

 ![在 code map 上使用呼叫堆疊進行調試]程式(../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="MapStack"></a> 對應呼叫堆疊

1. 在 Visual Studio Enterprise C# C++、Visual Basic、或 JavaScript 專案中, 選取 [ **Debug**  > **開始**] 或按**F5**來開始進行偵錯工具。

1. 當您的應用程式進入中斷模式或是您逐步執行函式之後, 請選取 [ **Debug**  >  **Code Map**], 或按**Ctrl** + **Shift** + **`** 。

   目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：

   ![請參閱 Code Map 上的呼叫堆疊](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

當您繼續進行偵錯工具時, Code Map 會自動更新。 變更對應專案或版面配置不會以任何方式影響程式碼。 請放心地重新命名、移動或移除對應圖上的任何項目。

若要取得專案的詳細資訊, 請將滑鼠停留在其上方, 並查看專案的工具提示。 您也可以在工具列中選取 [**圖例**], 以瞭解每個圖示所代表的意義。

![Code Map 圖例](../debugger/media/debuggermap_showlegend.png "Code Map 圖例")

>[!NOTE]
>此圖表可能會以 Code Map 頂端的**舊版程式碼為基礎**, 表示程式碼在您上次更新對應之後可能已變更。 例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。 關閉訊息，然後先嘗試重建方案後再更新對應圖。

## <a name="map-external-code"></a>對應外部程式碼

根據預設，只有您的程式碼會出現在對應圖上。 若要查看地圖上的外部程式碼:

- 以滑鼠右鍵按一下 [**呼叫堆疊**] 視窗, 然後選取 [**顯示外部程式碼**]:

  ![使用 [呼叫堆疊] 視窗顯示外部程式碼](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- 或者, 取消選取 [在 Visual Studio**工具**(或**Debug**) 中**啟用 Just My Code** ] >**選項** > 的**調試**:

  ![使用選項對話方塊顯示外部程式碼](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>控制地圖的版面配置

變更地圖的版面配置不會以任何方式影響程式碼。

若要控制地圖的版面配置, 請選取 [地圖] 工具列上的 [**版面**配置] 功能表。

在 [**版面**配置] 功能表中, 您可以:

- 變更預設的版面配置。
- 停止重新排列對應, 方法是在進行偵錯工具時取消選擇**自動版面**配置。
- 當您加入專案時, 請取消選擇 [**增量**配置], 盡可能少重新排列對應。

## <a name="MakeNotes"></a> 製作程式碼的筆記

您可以新增批註來追蹤程式碼中發生的狀況。

若要新增批註, 請以滑鼠右鍵按一下 Code Map 並選取 [**編輯** > **新批註**], 然後輸入批註。

若要在批註中加入新的一行, 請按**Shift** + **enter**鍵。

 ![將批註新增至 Code Map 上的呼叫堆疊](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> 以下一個呼叫堆疊更新地圖

當您執行應用程式到下一個中斷點或逐步執行函式時, 對應會自動加入新的呼叫堆疊。

![使用下一個呼叫堆疊更新 Code Map](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

若要停止對應自動加入新的呼叫堆疊, 請選取 [![在 Code Map 自動](../debugger/media/debuggermap_automaticupdateicon.gif "顯示 Code Map")上的呼叫堆疊] Code Map 工具列上的 [顯示呼叫堆疊]。 地圖會繼續反白顯示現有的呼叫堆疊。 若要手動新增至對應的目前呼叫堆疊，請按**Ctrl**+**Shift**+ **`** 。

## <a name="AddRelatedCode"></a> 將相關程式碼新增至地圖

現在您已有對應, 在或 Visual Basic C#中, 您可以加入欄位、屬性和其他方法等專案, 以追蹤程式碼中發生的情況。

若要移至程式碼中方法的定義, 請按兩下對應中的方法, 或選取它並按**F12**, 或以滑鼠右鍵按一下它, 然後選取 [**移至定義**]。

![移至 Code Map 上方法的程式碼定義](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

若要將您要追蹤的專案加入至地圖, 請以滑鼠右鍵按一下方法, 然後選取您要追蹤的專案。最新加入的項目會以綠色顯示。

與![呼叫堆疊上的方法相關的欄位 Code Map](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。 您可以選取 [Code Map] 工具列上的 [**包含父代**] 按鈕, 或在加入專案時按**Ctrl**鍵, 關閉和開啟這項功能。

![在呼叫堆疊上的方法中顯示欄位 Code Map](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

繼續建置對應圖來查看更多程式碼。

 ![請參閱使用欄位的方法: 呼叫堆疊 Code Map](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![在呼叫堆疊上使用欄位的方法 Code Map](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> 使用地圖尋找 Bug
 視覺化程式碼可協助您更快速找到 Bug。 例如, 假設您要調查繪圖應用程式中的 bug。 當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。

 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：

 ![將另一個呼叫堆疊新增至 Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。 這或許能解釋 `undo` 未立即執行的原因。

 修正錯誤並繼續執行應用程式之後, 對應會將新的呼叫從`undo`新增至: `Repaint`

 ![將新的方法呼叫加入至 Code Map 上的呼叫堆疊](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>與其他人共用地圖

您可以匯出對應、使用 Microsoft Outlook 將它傳送給其他人、將它儲存至您的方案, 然後將它簽入版本控制。

若要共用或儲存對應, 請使用 [Code Map] 工具列中的 [**共用**]。

![與其他人共用呼叫堆疊 Code Map](../debugger/media/debuggermap_sharewithothers.png "與其他人共用呼叫堆疊 Code Map")

## <a name="see-also"></a>另請參閱
[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)

[使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)

[使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)

[瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
