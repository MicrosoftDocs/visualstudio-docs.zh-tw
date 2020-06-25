---
title: 分析 .NET 物件的記憶體使用量 |Microsoft Docs
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f7ec98f8d17465e95369eb6e2ecd88051f8daa59
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330452"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>使用 .NET 物件組態工具分析記憶體使用量

您可以查看您的應用程式所使用的記憶體數量，以及使用 .NET 物件組態工具配置最多記憶體的程式碼路徑。

執行此工具之後，您可以看到正在設定物件的函式執行路徑。 然後，您可以追蹤回到佔用最多記憶體的呼叫樹狀結構的根目錄。

## <a name="setup"></a>安裝程式

1. 選取 [ **Alt + F2** ] 以在 Visual Studio 中開啟效能分析工具。

1. 選取 [ **.Net 物件配置追蹤**] 核取方塊。

   ![已選取 Dotnet 物件配置追蹤工具](../profiling/media/dotnetalloctoolselected.png "已選取 Dotnet 物件配置追蹤工具")

1. 選取 [**開始**] 按鈕以執行工具。

1. 工具開始執行之後，請完成您想要在應用程式中分析的案例。 然後選取 [**停止收集**] 或關閉您的應用程式，以查看您的資料。

   ![顯示停止收集的視窗](../profiling/media/stopcollectionlighttheme.png "顯示停止收集的視窗")

1. 選取 [**配置**] 索引標籤。顯示類似下列螢幕擷取畫面的視窗內容。

   ![[配置] 索引標籤](../profiling/media/allocationview.png "[配置] 索引標籤")

您現在可以分析物件的記憶體配置。

在收集期間，追蹤工具可能會使分析的應用程式變慢。 如果追蹤工具或應用程式的效能變慢，而且您不需要追蹤每個物件，您可以調整取樣率。 若要這麼做，請選取 [分析工具] [摘要] 頁面中追蹤工具旁邊的齒輪符號。

![Dotnet 組態工具的設定](../profiling/media/dotnetallocsettings.png "Dotnet 組態工具的設定")

將取樣率調整為您想要的速率。 這項變更有助於加快您的應用程式在收集和分析期間的效能。

![已調整的取樣率](../profiling/media/adjustedsamplingratedotnetalloctool.png "已調整的取樣率")

如需如何讓工具更有效率的詳細資訊，請參閱[優化 Profiler 設定](../profiling/optimize-profiler-settings.md)。

## <a name="understand-your-data"></a>瞭解您的資料

![Dotnet 組態工具的圖形](../profiling/media/graphdotnetalloc.png "Dotnet 組態工具的圖形")

在先前的圖形化視圖中，最上方的圖表會顯示應用程式中的即時物件數目。 底部**物件差異**圖表會顯示應用程式物件的百分比變更。 紅色橫條代表發生垃圾收集的時間。

![Dotnet 配置時間的篩選圖形](../profiling/media/graphdotnetalloctimefiltered.png "Dotnet 配置時間的篩選圖形")

您可以篩選表格式資料，只顯示指定時間範圍內的活動。 您也可以放大或縮小圖形。

### <a name="allocation"></a>配置

![配置視圖已展開](../profiling/media/allocationexpandedlight.png "配置視圖已展開")

[**配置**] 視圖會顯示正在配置記憶體的物件位置，以及這些物件所配置的記憶體數量。

- [ **類型**] 資料   行是佔用記憶體的類別和結構清單。 按兩下類型，將其 backtrace 為反向呼叫樹狀結構。 在 [**配置**] 視圖中，您可以看到所選類別中佔用記憶體的專案。

- [ **配置**]   欄位會顯示在特定配置類型或函式中佔用記憶體的物件數目。 此資料行只會出現在 [**配置**]、[ **呼叫樹狀結構**] 和 [ **函數**]   視圖中。

-  **Bytes**   預設不會顯示 [位元組] 和 [ **平均大小（位元組）**] 資料   行。 若要顯示它們，請以滑鼠右鍵按一下 [ **類型**] 或 [配置] 資料    **Allocations**   行，然後選取 [**位元組**]   和 [ **平均大小（位元組）**]   選項，將它們加入圖表中。 

   這兩個數據行與 **[總（配置）** ] 和 **[本身（配置）**] 相似，不同之處在于它們會顯示佔用的記憶體數量，而不是佔用記憶體的物件數目。 這些資料行只會出現在**配置**視圖中。

- [ **模組名稱**] 資料行會   顯示模組，其中包含正在呼叫的函式或進程。

這些資料行都可以排序。 針對 [ **類型**] 和 [**模組名稱**] 資料行，您可以依字母順序以遞增或遞減順序排序專案。 針對 **Allocations**[配置]、[**位元組**]   和 **[平均大小（位元組）**]，您可以藉由增加或減少數值來排序專案。

#### <a name="symbols"></a>符號

下列符號會出現在 [**配置**]、[**呼叫樹狀結構**] 和 [**函數**] 索引標籤中：

- 實![值型別符號](../profiling/media/valuetypeicon.png "實值型別符號")-實值型別，例如整數

- 實值型別![集合符號](../profiling/media/valuetypecollectionicon.png "實數值型別集合符號")-值型別集合，例如整數的陣列

- ![參考](../profiling/media/referencetypeicon.png "參考型別符號")型別符號-類似字串的參考型別

- ![參考型別集合符號](../profiling/media/referencetypecollectionicon.png "參考型別集合符號")-如字串陣列的參考型別集合

### <a name="call-tree"></a>呼叫樹狀結構

![呼叫樹狀檢視](../profiling/media/calltreelight.png "呼叫樹狀檢視")

[ **呼叫樹**   視圖] 會顯示函式執行路徑，其中包含配置大量記憶體的物件。

- [ **函數名稱**] 資料行會顯示函式的   進程或名稱，其中包含配置記憶體的物件。 顯示是以您要檢查的節點層級為基礎。
- [ **總計（配置）** ] 和 [ **總大小（位元組）**] 資料行會   顯示已配置的物件數目，以及函式和其所呼叫之所有其他函數所使用的記憶體數量。
- [**自我（配置）** ] 和 [**自我大小（位元組）** ] 資料行會顯示已配置的物件數目，以及單一選取的函式或配置類型所使用的記憶體數量。
- [**平均大小（位元組）** ] 資料行會顯示與 [配置 **] 視圖中**相同的資訊。
- [ **模組名稱**] 資料行會   顯示模組，其中包含正在呼叫的函式或進程。

   ![已展開的最忙碌路徑](../profiling/media/hotpathlight.png "已展開的最忙碌路徑")

- [**展開**最忙碌路徑] 按鈕會反白顯示函數執行路徑，其中包含許多正在配置記憶體的物件。 此演算法會從您選取的節點開始，並反白顯示最多配置的路徑，引導您進行調查。
- [**顯示**最忙碌路徑] 按鈕會顯示或隱藏火焰符號，指出哪些節點是最忙碌路徑的一部分。

### <a name="functions"></a>函數

![函數視圖](../profiling/media/functionslight.png "函數視圖")

[**函數**] 視圖會顯示配置記憶體的進程、模組和函式。

- [**名稱**] 資料行會將進程顯示為最高層級節點。 [進程] 底下是模組，而 [模組] 下則是函數。
- 這些資料行顯示的資訊與**配置**和**呼叫樹**視圖中的相同。

   - **總計（配置）**
   - **自我（配置）**
   - **總大小 (位元組)**
   - **自我大小（位元組）**
   - **平均大小（位元組）**

### <a name="collection"></a>集合

![集合視圖](../profiling/media/collectionlight.png "集合視圖")

[**集合**] 視圖會顯示垃圾收集期間收集或保留的物件數目。 此視圖也會顯示圓形圖，可依類型將所收集和不被回收的物件視覺化。

- [**收集**的資料行] 會顯示垃圾收集行程收集的物件數目。
- [已**存活**] 資料行會顯示在執行垃圾收集行程之後，被回收的物件數目。

### <a name="filtering-tools"></a>篩選工具

[**配置]、[****呼叫樹狀**] 和 [函式] Views 全都包含 [**顯示 Just My Code** **] 和 [** **顯示機器碼**選項] 和 [篩選] 方塊。

- **顯示 Just My Code**將系統、架構和其他 nonuser 程式碼折迭為 **[外部程式碼]** 框架，讓您可以只專注于您的程式碼。 如需詳細資訊，請參閱[使用 Just My Code 的 Debug 使用者程式碼](../debugger/just-my-code.md)。
- [**顯示原生程式碼**] 會顯示分析目標內的機器碼，而且可以包含 nonuser 程式碼。
- 使用 [篩選] 方塊，您可以根據您提供的值來篩選 [**名稱**] 或 [函式**名稱**] 資料行。 在方塊中輸入字串值。 然後，資料表只會顯示包含該字串的類型。
