---
title: 分析 .NET 物件的記憶體使用量 |Microsoft Docs
description: 查看您的應用程式所使用的記憶體數量，以及使用 .NET 物件組態工具配置最多記憶體的程式碼路徑。
ms.custom: SEO-VS-2020
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 4c0d8b02f867797317ff762e7a23bec042f93318
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801498"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>使用 .NET 物件組態工具來分析記憶體使用量

您可以看到應用程式使用的記憶體數量，以及使用 .NET 物件組態工具配置最多記憶體的程式碼路徑。

執行工具之後，您就可以看到要設定物件的函式執行路徑。 然後，您可以追蹤回佔用最多記憶體的呼叫樹狀結構的根。

## <a name="setup"></a>安裝程式

1. 選取 **Alt + F2** 以開啟 Visual Studio 中的效能分析工具。

1. 選取 [ **.Net 物件配置追蹤** ] 核取方塊。

   ![已選取 Dotnet 物件配置追蹤工具](../profiling/media/dotnetalloctoolselected.png "已選取 Dotnet 物件配置追蹤工具")

1. 選取 [ **開始** ] 按鈕以執行工具。

1. 工具開始執行之後，請完成您想要在應用程式中進行分析的案例。 然後選取 [ **停止收集** ] 或關閉應用程式以查看您的資料。

   ![顯示停止收集的視窗](../profiling/media/stopcollectionlighttheme.png "顯示停止收集的視窗")

1. 選取 [ **配置** ] 索引標籤。顯示類似下列螢幕擷取畫面的視窗內容。

   ![[配置] 索引標籤](../profiling/media/allocationview.png "[配置] 索引標籤")

您現在可以分析物件的記憶體配置。

在收集期間，追蹤工具可能會使已分析的應用程式變慢。 如果追蹤工具或應用程式的效能很慢，而且您不需要追蹤每個物件，您可以調整取樣率。 若要這樣做，請在 [分析工具] 摘要頁面中，選取追蹤工具旁的齒輪符號。

![Dotnet 組態工具的設定](../profiling/media/dotnetallocsettings.png "Dotnet 組態工具的設定")

將取樣率調整為您想要的速率。 這項變更有助於在收集和分析期間加速您的應用程式效能。

![調整的取樣率](../profiling/media/adjustedsamplingratedotnetalloctool.png "調整的取樣率")

如需如何讓工具更有效率的詳細資訊，請參閱 [優化 Profiler 設定](../profiling/optimize-profiler-settings.md)。

## <a name="understand-your-data"></a>瞭解您的資料

![Dotnet 組態工具的圖形](../profiling/media/graphdotnetalloc.png "Dotnet 組態工具的圖形")

在上圖中，上圖顯示應用程式中的即時物件數目。 底部 **物件差異** 圖顯示應用程式物件的百分比變更。 紅色橫條表示垃圾收集發生的時間。

![Dotnet 配置時間的篩選圖形](../profiling/media/graphdotnetalloctimefiltered.png "Dotnet 配置時間的篩選圖形")

您可以篩選表格式資料，只顯示指定時間範圍的活動。 您也可以放大或移出圖形。

### <a name="allocation"></a>配置

![已展開配置視圖](../profiling/media/allocationexpandedlight.png "已展開配置視圖")

配置視圖會顯示 **配置** 記憶體的物件位置，以及這些物件所配置的記憶體數量。

- [ **類型** ] 資料行是佔用記憶體之類別和結構的清單。 按兩下類型可將其 backtrace 視為反向呼叫樹狀結構。 在 [ **配置** 視圖] 中，您可以看到所選類別中佔用記憶體的專案。

- [ **配置** ] 資料行會顯示在特定配置類型或函數中佔用記憶體的物件數目。 此資料行只會出現在 **配置**、**呼叫樹狀結構****和函** 式視圖中。

- 預設不會顯示 **(位元組)** 資料行的 **位元組** 和平均大小。 若要顯示這些專案，請以滑鼠右鍵按一下 [ **類型** **] 或 [** 配置] 資料行，然後選取 [ **位元組** ] 和 [ **平均大小] (位元組])** 選項將它們新增至圖表。 

   這兩個數據行類似于 **總 (配置)** 和 **(自助配置)**，只不過它們會顯示所耗用的記憶體數量，而不是佔用記憶體的物件數目。 這些欄位只會出現在 **配置** 視圖中。

- [ **模組名稱** ] 資料行會顯示包含正在呼叫之函數或進程的模組。

所有這些資料行都可以排序。 針對 [ **類型** ] 和 [ **模組名稱** ] 資料行，您可以依字母順序排序專案（以遞增或遞減順序排序）。 針對配置、**位元組** 和 **平均大小 (位元組)**，您可以藉由增加或減少 **數值來排序** 專案。

#### <a name="symbols"></a>符號

下列符號會出現在 [ **配置**]、[ **呼叫樹狀結構**] 和 [ **函數** ] 索引標籤中：

- ![數值型別符號](../profiling/media/valuetypeicon.png "數值型別符號") -實數值型別，例如整數

- 實![數值型別集合符號](../profiling/media/valuetypecollectionicon.png "數值型別集合符號")-數值型別集合，例如整數陣列

- ![參考型別符號](../profiling/media/referencetypeicon.png "參考型別符號") -參考型別，例如 string

- ![參考型別集合符號](../profiling/media/referencetypecollectionicon.png "參考型別集合符號") -類型集合，例如字串陣列

### <a name="call-tree"></a>呼叫樹狀結構

![呼叫樹狀檢視](../profiling/media/calltreelight.png "呼叫樹狀檢視")

[ **呼叫樹** 視圖] 會顯示包含物件配置大量記憶體的函式執行路徑。

- [函式 **名稱** ] 欄會顯示函式的進程或名稱，其中包含可配置記憶體的物件。 顯示是以您正在檢查的節點層級為基礎。
- **總 (配置)** 和 **(位元組總計) 位元組** 會顯示已配置的物件數目，以及函式和其所呼叫之所有其他函數所使用的記憶體數量。
- **自我 (配置)** 和 **(位元組)** 資料行顯示已配置的物件數目，以及單一所選函數或配置類型所使用的記憶體數量。
- **平均大小 (位元組)** 資料行 **顯示的資訊與配置視圖中** 的資訊相同。
- [ **模組名稱** ] 資料行會顯示包含正在呼叫之函數或進程的模組。

   ![展開的最忙碌路徑](../profiling/media/hotpathlight.png "展開的最忙碌路徑")

- [ **展開** 最忙碌路徑] 按鈕會反白顯示包含許多正在配置記憶體之物件的函數執行路徑。 此演算法會從您選取的節點開始，並反白顯示最多配置的路徑，引導您進行調查。
- [ **顯示** 最忙碌路徑] 按鈕會顯示或隱藏火焰符號，指出哪些節點是最忙碌路徑的一部分。

### <a name="functions"></a>函式

![函數視圖](../profiling/media/functionslight.png "函數視圖")

[ **函數** ] 視圖會顯示正在配置記憶體的進程、模組和函式。

- [ **名稱** ] 資料行會將進程顯示為最高層級的節點。 程式底下的模組是模組，而下的模組是函式。
- 這些資料行所顯示的資訊與 **配置** 和 **呼叫樹** 視圖中的資訊相同：

  - **總 (配置)**
  - **自助 (配置)**
  - **總大小 (位元組)**
  - **(位元組的自我大小)**
  - **平均大小 (位元組)**

### <a name="collection"></a>集合

![集合視圖](../profiling/media/collectionlight.png "集合視圖")

[ **收集** 視圖] 會顯示垃圾收集期間收集或保留的物件數目。 此視圖也會顯示圓形圖，以依類型將收集和存活的物件視覺化。

- [ **收集** 的資料行] 會顯示垃圾收集行程收集的物件數目。
- 未被回收的資料行會顯示在執行垃圾收集行程之後， **被回收的** 物件數目。

### <a name="filtering-tools"></a>篩選工具

[配置]、[**呼叫樹狀結構**] 和 [**函數**] 視圖都 **包含 [****顯示 Just My Code** ] 和 [**顯示原生程式碼** 選項] 和 [篩選] 方塊。

- **顯示 Just My Code** 將系統、架構和其他 nonuser 程式碼折迭為 **[外部程式碼]** 畫面格，讓您可以只專注于您的程式碼。 如需詳細資訊，請參閱 [使用 Just My Code 來處理使用者程式碼](../debugger/just-my-code.md)。
- **顯示原生程式碼** 會在分析目標內顯示原生程式碼，並可包含 nonuser 程式碼。
- 您可以使用 [篩選] 方塊，根據您提供的值篩選 [ **名稱** ] 或 [函式 **名稱** ] 資料行。 在方塊中輸入字串值。 然後，資料表只會顯示包含該字串的類型。
