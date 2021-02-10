---
title: CPU 和 Windows 計數器 | Microsoft Docs
description: CPU (硬體) 和 Windows (軟體) 計數器會提供效能資料。 瞭解如何加以查看，以及如何從中收集資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3553106c9c2bea0d4d4c24b2e51b59e4fcf42722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956057"
---
# <a name="cpu-and-windows-counters"></a>CPU 和 Windows 計數器

Visual Studio 分析工具可讓您收集由作業系統 (Windows 計數器) 所產生的效能資料，以及處理器單元 (CPU 計數器) 所產生的效能資料。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="windows-counters"></a>Windows 計數器

Windows 計數器是 Windows 診斷基礎結構的一部分，提供作業系統或應用程式、服務或驅動程式的效能資訊。 Windows 計數器取決於目前電腦的設定，可能無法在其他電腦上使用。 在分析資料檔案中，收集到的 Windows 效能計數器會做為分析標記，然後可以用來篩選檢視和報表。

## <a name="cpu-counters"></a>CPU 計數器

CPU 計數器是儲存硬體相關事件計數的電腦 CPU 功能。 當您使用檢測分析方法收集 CPU 計數器資料時，資料會附加至函式和模組的資料。 您可以使用檢測方法收集多個 CPU 計數器。 當您使用取樣方法時，則是選取一個計數器用來做為要取樣的事件。

效能計數器與 CPU 相關。 不同的 CPU 型號和版本可能會有明顯不同的組態設定，卻啟用相同的效能計數器。 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 分析工具的可攜式事件會將一些常用的效能計數器與特定處理器分離，可讓您收集或取樣一般的效能事件。

當您使用分析工具時如果想要計算特定事件，例如，L2 快取遺漏，可以在該事件傳送者建置效能工作階段。 您可以在任何 CPU 上使用 L2 快取執行這項操作。 效能工作階段可以在平台之間移動而無需修改。

Visual Studio 分析工具會繼續支援特定平台的特定事件。 例如，Pentium 4 平台的開發人員可能想要計算 NetBurst 架構特定的事件。 此事件不可攜，但開發人員仍然可在特定平台上特定效能工作階段使用。

## <a name="portable-and-platform-events"></a>可攜式和平台事件

可攜式事件是一組不屬於特定處理器的 CPU 計數器。 其他所有的 CPU 計數器都稱為平台事件，在各種平台上可能不支援。

 可移植和平臺事件的計數器都定義于中。*xml* 檔案，其中會提供與計數器相關的特定值。 不同 CPU 有多個檔案，因為 (例如) Intel 和 AMD 的 CPU 資料不同。 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 分析工具使用此資訊對使用者顯示適當的計數器 (可攜式和平台) 進行效能度量。

### <a name="portable-events"></a>可攜式事件

可攜式事件包含下列事件︰

**一般事件**

|活動名稱|事件描述|
|----------------|-----------------------|
|Instructions Retired|表示直到事件完成已執行的指令數目。|
|Non Halted Cycles|表示處理器只在這些循環未停止 (例如正在等候 I/O)。|

**前端事件**

|活動名稱|事件描述|
|----------------|-----------------------|
|ITLB Misses|表示導致遺漏的指令轉譯旁觀緩衝區查閱數。|

**分支事件**

|活動名稱|事件描述|
|----------------|-----------------------|
|Branches Retired|表示直到事件完成已執行的分支指令數目。|
|Mis-predicted Branches|表示因為處理器預測不正確的路徑而錯估的分支。 錯估的分支會影響效能，因為處理器必須捨棄所有完成的工作，然後要在正確的路徑上重新啟動。|

**記憶體事件︰**

|活動名稱|事件描述|
|----------------|-----------------------|
|L2 Cache Read Misses|表示第二個層級快取讀取遺漏的數目。|
|L2 Cache Read References|表示第二個層級快取讀取參考的數目。 包括載入遺漏和讀取擁有權 (RFO) 的遺漏和叫用。|

## <a name="view-available-counters"></a>檢視可用的計數器

您可以在 Visual Studio IDE 或 [命令提示字元] 視窗中，列出可用的 CPU 計數器。

### <a name="visual-studio-ui"></a>Visual Studio UI

若要在 Visual Studio IDE 中列出電腦上可用的計數器，您必須在 [效能總管] 中開啟分析工具效能工作階段。

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>檢視目前平台支援的所有 CPU 計數器清單

1. 在效能總管中，以滑鼠右鍵按一下效能會話，然後按一下 [ **屬性**]。

2. 執行下列其中一個動作：

   - 按一下 [取樣]，然後從 [樣本] 事件清單選取 [效能計數器]。 CPU 計數器會列在 [可用的效能計數器] 中。

      **注意** 按一下 [取消] 可回到前一個取樣組態。

     -或-

   - 選取 [CPU 計數器]，然後選取 [收集 CPU 計數器]。 CPU 計數器會列在 [可用的計數器] 中。

      **注意** 按一下 [ **取消** ] 以返回先前的計數器集合設定。

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>檢視目前平台支援的 Windows 計數器清單

1. 在效能總管中，以滑鼠右鍵按一下效能會話，然後按一下 [ **屬性**]。

2. 按一下 [Windows 計數器]。

3. 選取 [收集 Windows 計數器]。

4. 從 [計數器分類] 清單中，選取計數器群組。 群組的 Windows 計數器會顯示在清單方塊中。

     **注意：** 按一下 [取消] 可回到前一個計數器收集組態。

### <a name="command-line"></a>命令列

使用 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具，您可以從命令列列出電腦上可用的 CPU 計數器。

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>檢視目前平台支援的 CPU 計數器清單

1. 開啟 [命令提示字元] 視窗。

2. 類型

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd/querycounters**

     其中 *\<Visual Studio Performance Tools Directory>* 是 Visual Studio 安裝之 [效能工具] 目錄的路徑。 若要取得效能工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。

## <a name="see-also"></a>另請參閱

- [概觀](../profiling/overviews-performance-tools.md)
- [如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)
- [如何：收集 CPU 計數器資料](../profiling/how-to-collect-cpu-counter-data.md)
- [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)
