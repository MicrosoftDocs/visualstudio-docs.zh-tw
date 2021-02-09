---
title: XSLT 偵錯工具視窗
description: 瞭解 XSLT 偵錯工具 UI 元件，以控制 XSLT 特定的偵錯工具行為，包括區域變數、輸出、中斷點、呼叫堆疊和監看式視窗。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e5d113718c2ecc73ad942dd58ddf92216fe6c83
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875116"
---
# <a name="debugger-user-interface-xslt"></a>偵錯工具使用者介面 (XSLT) 

本文描述偵錯工具視窗和對話方塊。 它只會討論具有 XSLT 特定的偵錯工具行為的使用者介面片段。

如需詳細資訊，請參閱 [偵錯工具使用者介面參考](../debugger/debugging-user-interface-reference.md)。

## <a name="locals-window"></a>[區域變數] 視窗

[本機] 視窗會顯示樣式表中定義之任何變數的相關資訊。 [本機] 視窗包含資訊的三個資料行：

**名稱**

此資料行包含目前範圍中所有區域變數的名稱。 節點集具有樹狀目錄控制項，您可以向下切入以查看其子資料夾。

**值**

此資料行顯示每個變數所包含的值。 屬性、處理指示、註解、文字及 CData 節點都顯示節點的文字值。 命名空間節點會顯示命名空間 URI。

**型別**

此資料行會識別 [ **名稱** ] 資料行中所列之每個變數的資料類型。

[本機] 視窗還顯示追蹤 XSLT 轉換內容之預先定義的內容變數。 下表說明 XSLT 偵錯工具使用之預先定義的內容變數。

|名稱|描述|
|-|-----------------|
|`last()`|內容大小。|
|`position()`|內容節點的位置或索引編號 (相對於內容大小)。|
|`self::node()`|內容節點的值。|

## <a name="output-window"></a>輸出視窗

[輸出] 視窗會顯示偵錯時發生的任何錯誤訊息或安全性例外狀況。 它也會顯示偵錯工具輸出。

## <a name="task-list"></a>工作清單

**工作清單** 會列出樣式表單中的所有編譯錯誤。 按兩下錯誤，即可將游標移至發生錯誤的程式行。

**工作清單** 包含 XSLT 檔中腳本區塊中發生的任何錯誤。

> [!NOTE]
> XSLT 偵錯工具沒有警告，因此它們永遠不會出現在 **工作清單** 中。

## <a name="breakpoints-window"></a>中斷點視窗

[中斷點] 視窗會顯示目前專案中的所有中斷點。 當視窗在檢視表中時如果加入中斷點，則視窗會自動更新以顯示新中斷點。

[中斷點] 視窗應與其他 Visual Studio 偵錯工具的作用方式相同。

## <a name="watch-window"></a>監看式視窗

[監看式] 視窗用於評估變數。 您還可變更變數的值。

[監看式] 視窗中顯示的變數是針對目前的內容 (呼叫堆疊上的最上層項目)。 如果您變更內容，則監看式視窗會更新，並顯示為該內容設定的變數。

## <a name="call-stack-window"></a>[呼叫堆疊] 視窗

[ **呼叫堆疊** ] 視窗是用來查看呼叫堆疊上的函式名稱、參數類型和參數值。 僅當進行偵錯的程式處於中斷狀態時，才會顯示呼叫堆疊資訊。

呼叫堆疊表示經歷 XSLT 執行的各種內容。 例如，如果從範本 "a" 到範本 "b" 的呼叫，範本 "a" 和範本 "b" 就會出現在 [ **呼叫堆疊** ] 視窗中，並在清單頂端顯示目前內容。 使用者可以查看目前執行的查詢。

如果範本在 XSLT 檔中沒有名稱，則會使用由 XSLT 處理器產生的名稱。

按一下非清單頂部的項目，會使用標準的綠色反白顯示及綠色箭頭，向檢視器表示 XSLT 執行分支所在的位置。

## <a name="quickwatch-dialog-box"></a>QuickWatch 對話方塊

[ **快速** 監看式] 對話方塊是用來評估 XPath 1.0 運算式。 內容節點 ([本機] 視窗中的 `self::node()` 節點) 提供 XPath 運算式執行的內容。 執行 XPath 運算式的結果會顯示於 [監看式] 視窗中。

下列清單描述 XPath 運算式評估的限制：

- 只允許內建 XPath 函式。

- 不允許內建 XSLT 函式 `document()` ，例如和 `key()` 。

- 不允許使用者定義函式。

如需詳細資訊，請參閱 [如何：評估 XPath 運算式](../xml-tools/how-to-evaluate-an-xpath-expression.md)。

## <a name="disassembly-window"></a>反組譯碼視窗

[反組譯碼] 視窗會顯示由 XSLT 編譯器產生的組譯程式碼。 此視窗的使用方式可以與所有其他 Visual Studio 反組譯碼視窗相同。

如需詳細資訊，請使用 [反組解碼 [] 視窗](../debugger/how-to-use-the-disassembly-window.md)。

## <a name="see-also"></a>另請參閱

- [偵錯 XSLT](../xml-tools/debugging-xslt.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [在 Visual Studio 的 [自動變數] 和 [區域變數] 視窗中檢查變數](../debugger/autos-and-locals-windows.md)
