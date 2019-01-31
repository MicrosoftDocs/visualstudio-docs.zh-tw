---
title: 建立呼叫堆疊的視覺導覽圖 |Microsoft Docs
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
ms.openlocfilehash: 087e8f850aa7d12a427924133f82f1e72c9c4bd3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959474"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>建立視覺效果的對應呼叫堆疊偵錯時 (C#，Visual Basic、 c + +、 JavaScript)

在您偵錯時建立 Code Map 以視覺方式追蹤呼叫堆疊。 您可以在地圖上做筆記來追蹤程式碼的執行狀況，以便專注於尋找 Bug。

如需逐步解說中，觀看此影片：[影片：使用 Code Map 偵錯工具整合 (Channel 9) 以視覺化方式進行偵錯](http://go.microsoft.com/fwlink/?LinkId=293418)

如需命令和動作，您可以使用 code map 的詳細資訊，請參閱 <<c0> [ 瀏覽和重新整理 code map](../modeling/browse-and-rearrange-code-maps.md)。

>[!IMPORTANT]
>您可以建立 code map 只有[Visual Studio Enterprise edition](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

以下是快速查看 code map:

 ![使用 code map 上的呼叫堆疊偵錯](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

##  <a name="MapStack"></a> 對應呼叫堆疊

1. 在 Visual Studio Enterprise 中C#，Visual Basic、 c + + 或 JavaScript 專案中，開始藉由選取偵錯**偵錯** > **開始偵錯**或按下**F5**.
   
1. 您的應用程式進入中斷模式或是您逐步執行函式之後，請選取**偵錯** > **Code Map**，或按**Ctrl**+**Shift**+**`**.

   目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：

   ![請參閱在 code map 上的呼叫堆疊](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

會自動隨著您繼續偵錯時，程式碼將對應更新。 變更地圖項目] 或 [版面配置，不會影響以任何方式的程式碼。 請放心地重新命名、移動或移除對應圖上的任何項目。

若要取得項目的詳細資訊，請將滑鼠停留並查看項目的工具提示。 您也可以選取**圖例**在工具列中，若要深入了解每個圖示的意義。

![程式碼地圖圖例](../debugger/media/debuggermap_showlegend.png "地圖圖例的程式碼")

>[!NOTE]
>訊息**圖表可能會根據較舊版本的程式碼**頂端的程式碼對應會代表您上次更新對應之後，可能已變更的程式碼。 例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。 關閉訊息，然後先嘗試重建方案後再更新對應圖。

## <a name="map-external-code"></a>將外部程式碼對應

根據預設，只有您的程式碼會出現在對應圖上。 若要在地圖上查看外部程式碼：
  
- 以滑鼠右鍵按一下**呼叫堆疊**視窗，然後選取**顯示外部程式碼**:
  
  ![顯示外部程式碼，使用 [呼叫堆疊] 視窗](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- 或者，您也可以取消選取**啟用 Just My Code** Visual Studio 中**工具**(或**偵錯**) >**選項** >  **偵錯**:
  
  ![顯示外部程式碼，使用 [選項] 對話方塊](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>控制地圖的版面配置

變更地圖的配置不會影響以任何方式的程式碼。 

若要控制地圖的版面配置，請選取**版面配置**map 工具列上的功能表。 

在 [**版面配置**] 功能表中，您可以：

-   變更預設的版面配置。
-   停止自動重新整理對應，取消選取**偵錯時自動配置**。
-   當您取消選取 新增項目，重新排列對應盡可能**累加配置**。

##  <a name="MakeNotes"></a> 製作程式碼的筆記

您可以加入註解，以追蹤程式碼中的情況。 

若要加入註解，以滑鼠右鍵按一下 code map，然後選取**編輯** > **新註解**，然後輸入註解。 

若要加入新的一行的註解，請按**Shift**+**Enter**。

 ![新增堆疊呼叫 code map 上的註解](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> 以下一個呼叫堆疊更新地圖

當您執行您的應用程式的下一個中斷點或步驟來執行函式，地圖會自動新增新的呼叫堆疊。

![更新 code map，包含下一個呼叫堆疊](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

若要停止從將新增新的呼叫堆疊會自動對應，請選取![顯示呼叫堆疊 code map 上自動](../debugger/media/debuggermap_automaticupdateicon.gif "顯示呼叫堆疊 code map 上自動")code map 工具列上。 地圖會繼續反白顯示現有的呼叫堆疊。 若要手動新增至對應的目前呼叫堆疊，請按**Ctrl**+**Shift**+**`**。 

##  <a name="AddRelatedCode"></a> 將相關程式碼新增至地圖

現在，您有一個對應，在C#或 Visual Basic 中，您可以新增欄位、 屬性和其他方法，來追蹤程式碼中的事情等項目。 

若要移到程式碼中方法的定義，按兩下的方法，在對應中，或選取它然後按**F12**，或以滑鼠右鍵按一下它，然後選取**移至定義**。

![移至 code map 上方法的程式碼定義](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

若要新增您想要追蹤到對應的項目，以滑鼠右鍵按一下方法並選取您想要追蹤的項目。最新加入的項目會以綠色顯示。

![在堆疊呼叫 code map 上的方法相關的欄位](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。 您可以關閉這項功能及開啟所選取**包含父代**按鈕在 code map 工具列上，或按**Ctrl**時新增項目。

![顯示堆疊呼叫 code map 上的方法中的欄位](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

繼續建置對應圖來查看更多程式碼。

 ![請參閱使用欄位的方法： 堆疊呼叫 code map](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![堆疊呼叫 code map 使用欄位的方法](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> 使用地圖尋找 Bug
 視覺化程式碼可協助您更快速找到 Bug。 例如，假設您正在調查繪圖應用程式中的 bug。 當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。

 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：

 ![新增其他堆疊呼叫 code map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。 這或許能解釋 `undo` 未立即執行的原因。

 修正 bug 後，當您繼續執行應用程式時，對應圖會加入新的呼叫，從`undo`至`Repaint`:

 ![在 code map 上新增新方法的呼叫堆疊](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>與其他人共用對應

您可以匯出對應、 與 Microsoft Outlook 傳送給其他人、 將它儲存到您的方案，並將它簽入版本控制。

若要共用或儲存對應，使用**共用**在 code map 工具列。 

![共用堆疊呼叫 code map 與他人](../debugger/media/debuggermap_sharewithothers.png "共用堆疊呼叫 code map 與其他人")

## <a name="see-also"></a>另請參閱
[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)

[使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)

[使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)

[瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
