---
title: 事件檢視器 |Microsoft Docs
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 4cba043d8300d47ae5ffba1c175a19fcfa2e65ed
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330329"
---
# <a name="events-viewer"></a>事件檢視器

[一般事件檢視器] 會透過事件清單（例如模組負載、執行緒啟動和系統設定）來顯示應用程式活動。 此視圖可協助您更有效地診斷應用程式在 Visual Studio profiler 中的執行狀況。

## <a name="setup"></a>安裝程式

1. 選取 [ **Alt + F2** ] 以在 Visual Studio 中開啟效能分析工具。

1. 選取 [**事件檢視器]** 核取方塊。

   ![已選取 [事件檢視器] 核取方塊](../profiling/media/eventsviewerselected.png "已選取 [事件檢視器] 核取方塊")

1. 選取 [**開始**] 按鈕以執行工具。

1. 工具開始執行之後，請在您的應用程式中進行分析的案例。 然後選取 [**停止收集**] 或關閉您的應用程式，以查看您的資料。

   ![顯示停止收集的視窗](../profiling/media/stopcollectioneventsviewer.png "顯示停止收集的視窗")

如需如何讓工具更有效率的詳細資訊，請參閱[優化程式碼剖析設定](../profiling/optimize-profiler-settings.md)。

## <a name="understand-your-data"></a>瞭解您的資料

![事件檢視器追蹤](../profiling/media/eventviewertrace.png "事件檢視器追蹤")

|資料行名稱|描述|
|----------|---------------------|
|Provider Name|事件來源|
|事件名稱|事件，如其提供者所指定|
|Text|提供者、事件名稱和事件識別碼的描述|
|時間戳記（毫秒）|事件發生時|
|提供者 Guid|事件提供者的識別碼|
|事件識別碼|事件的識別碼|
|處理序識別碼|發生事件的進程（如果已知）|
|處理序名稱|正在主動執行的進程名稱|
|執行緒識別碼|發生事件之來源執行緒的識別碼（如果已知）|

如果預設遺漏任何資料行，請以滑鼠右鍵按一下其中一個現有的資料行標頭，然後選取您要加入的資料行。

![將資料行新增至事件檢視器](../profiling/media/eventvieweraddcolumns.png "將資料行新增至事件檢視器")

當您選取事件時，[**其他屬性**] 視窗會隨即出現。 [**通用屬性**] 顯示將針對任何事件顯示的屬性清單。 裝載**屬性**會顯示事件特定的屬性。 針對某些事件，您也可以查看**堆疊**。

![顯示堆疊的事件檢視器](../profiling/media/eventviewerstacks.png "顯示堆疊的事件檢視器")

## <a name="organize-your-data"></a>組織您的資料

除了**文字**資料行以外的所有資料行都可排序。

![事件檢視器追蹤](../profiling/media/eventviewertrace.png "事件檢視器追蹤")

事件檢視器一次最多顯示20000個事件。 若要將焦點放在相關事件，您可以選取事件篩選器來篩選事件的顯示。 您也可以查看每個提供者發生的事件總數百分比。 將滑鼠停留在單一事件篩選器上，以查看顯示的工具提示：

- 事件名稱
- 提供者
- GUID
- 事件總數的百分比
- 事件計數

![事件檢視器事件篩選器](../profiling/media/eventviewereventfilter.png "事件檢視器事件篩選器")

提供者篩選器會顯示每個提供者發生的事件總數百分比。 將滑鼠停留在單一提供者上，以查看類似的工具提示，其中包含提供者名稱、事件總數百分比和事件計數。

![事件檢視器提供者篩選器](../profiling/media/eventviewerproviderfilter.png "事件檢視器提供者篩選器")
