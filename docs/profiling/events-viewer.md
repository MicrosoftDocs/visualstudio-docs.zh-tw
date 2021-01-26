---
title: 事件檢視器 |Microsoft Docs
description: 深入瞭解一般事件檢視器，可協助您更妥善地診斷您的應用程式在 Visual Studio profiler 內的執行狀況。
ms.custom: SEO-VS-2020
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 6aef8e72f416923aa647a8b3a412ee701ece18dd
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801399"
---
# <a name="events-viewer"></a>事件檢視器

一般事件檢視器會透過事件清單顯示應用程式活動，例如模組載入、執行緒啟動和系統組態。 此視圖可協助您更妥善地診斷您的應用程式在 Visual Studio profiler 中的執行情況。

## <a name="setup"></a>安裝程式

1. 選取 **Alt + F2** 以開啟 Visual Studio 中的效能分析工具。

1. 選取 [ **事件檢視器]** 核取方塊。

   ![已選取 [事件檢視器] 核取方塊](../profiling/media/eventsviewerselected.png "已選取 [事件檢視器] 核取方塊")

1. 選取 [ **開始** ] 按鈕以執行工具。

1. 當工具開始執行之後，請流覽案例來分析您的應用程式。 然後選取 [ **停止收集** ] 或關閉應用程式以查看您的資料。

   ![顯示停止收集的視窗](../profiling/media/stopcollectioneventsviewer.png "顯示停止收集的視窗")

如需如何讓工具更有效率的詳細資訊，請參閱 [優化程式碼剖析設定](../profiling/optimize-profiler-settings.md)。

## <a name="understand-your-data"></a>瞭解您的資料

![事件檢視器追蹤](../profiling/media/eventviewertrace.png "事件檢視器追蹤")

|資料行名稱|描述|
|----------|---------------------|
|Provider Name|事件來源|
|活動名稱|依其提供者指定的事件|
|Text|事件提供者、事件名稱和識別碼的描述|
|時間戳記 (ms) |當事件發生時|
|提供者 Guid|事件提供者的識別碼|
|事件識別碼|事件的識別碼|
|處理序識別碼|發生事件的進程 (已知的) |
|處理序名稱|正在執行的進程名稱|
|執行緒識別碼|事件發生所在之執行緒的識別碼 (如果已知) |

如果預設遺失任何資料行，請在其中一個現有的資料行標頭上按一下滑鼠右鍵，然後選取您要加入的資料行。

![將資料行加入至事件檢視器](../profiling/media/eventvieweraddcolumns.png "將資料行加入至事件檢視器")

當您選取事件時，[ **其他屬性** ] 視窗隨即出現。 [**通用屬性**] 會顯示將針對任何事件顯示的屬性清單。 承載 **屬性** 會顯示事件的特定屬性。 針對某些事件，您也可以查看 **堆疊**。

![顯示堆疊的事件檢視器](../profiling/media/eventviewerstacks.png "顯示堆疊的事件檢視器")

## <a name="organize-your-data"></a>組織您的資料

除了 **文字** 資料行以外的所有資料行都可以排序。

![事件檢視器追蹤](../profiling/media/eventviewertrace.png "事件檢視器追蹤")

事件檢視器一次最多會顯示20000個事件。 若要將焦點放在感興趣的事件，您可以選取事件篩選器來篩選事件的顯示。 您也可以查看每個提供者發生事件總數的百分比。 將滑鼠停留在單一事件篩選器上，以查看顯示下列專案的工具提示：

- 事件名稱
- 提供者
- GUID
- 事件總數的百分比
- 事件計數

![事件檢視器事件篩選器](../profiling/media/eventviewereventfilter.png "事件檢視器事件篩選器")

提供者篩選器會顯示每個提供者發生事件總數的百分比。 將滑鼠停留在單一提供者上，以查看類似的工具提示，其中包含提供者名稱、事件總數百分比和事件計數。

![事件檢視器提供者篩選](../profiling/media/eventviewerproviderfilter.png "事件檢視器提供者篩選")
