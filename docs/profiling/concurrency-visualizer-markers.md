---
title: 並行視覺化檢視中的標記 | Microsoft Docs
description: 深入瞭解並行視覺化中的標記。 標記是代表應用程式所產生之事件的圖示。 有三種類型：旗標、訊息和範圍。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fab8108e15f3cbaf81130c2ce8533d00f2a23c7e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720991"
---
# <a name="concurrency-visualizer-markers"></a>並行視覺化檢視標記
在並行視覺化檢視中，標記是代表應用程式中事件的圖示。  一般而言，應用程式會產生這些事件，以指定應用程式中的階段或發生次數。  應用程式或程式庫和應用程式使用的執行階段，可以產生事件。

## <a name="kinds-of-markers"></a>標記類型
 並行視覺化檢視使用三種類型的標記來表示應用程式事件︰旗標、訊息和範圍。

1. 使用 *旗標* 可指出應用程式中有趣的時間點。  例如，您可以使用旗標來表示變數值已達到特定的閾值或表示擲回例外狀況。

2. *訊息* 也可標記時間點，但是您可以使用它追蹤記錄檔樣式。  例如，您現在可以在訊息呼叫中包裝傾印到記錄檔的內容以便追蹤，並在並行視覺化檢視中檢視。 您也可以使用並行視覺化檢視將此資料匯出至 CSV 檔案。

3. *範圍* 代表應用程式中一個時間間隔，例如其中一個階段。

## <a name="marker-linkage-to-threads"></a>執行緒標記連結
 產生標記的每個執行緒都有不同的時間軸通道。  負責產生標記事件的執行緒識別碼會顯示在標記通道的描述旁邊。  標記通道左邊顯示的識別碼符合目前處理序中另一個執行緒的 ID。

## <a name="marker-importance"></a>標記重要性
 標記可以有其中一種四種重要性層級︰低、標準、高和重要。  您可以根據重要性層級篩選標記的來源。  例如，如果您只想看到來自特定來源有一般或重要重要性的標記，您可以在[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)對話方塊中設定篩選。 標記的重要性會顯示在其工具提示和[標記報告](../profiling/markers-report.md)中。

## <a name="marker-category"></a>標記分類
 標記分類表示一組來自相同來源的標記事件。  並行視覺化檢視使用色彩來區別不同分類的旗標和範圍。 您可以設定並行視覺化檢視以使用分類來篩選來自特定事件提供者的標記事件。  使用 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊可設定篩選。

## <a name="known-sources-of-markers"></a>已知的標記來源
 只要提供者符合某些限制式，任何 ETW 提供者都可以產生標記。 您可以設定並行視覺化檢視來接聽其他事件來源的標記。 預設會接聽這些事件來源︰

- [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)

- [工作平行程式庫 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [資料流程](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [平行 LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [並行執行階段](/cpp/parallel/concrt/concurrency-runtime)

- [情節標記支援](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  您可以使用 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊中的 [標記] 索引標籤，控制各種來源的標記是否顯示在並行視覺化檢視中，您可以依照重要性和類別篩選標記。

## <a name="markers-from-eventsource"></a>來自 EventSource 的標記
 並行視覺化檢視也可以顯示 EventSource 事件。  如需詳細資訊，請參閱[將 EventSource 事件顯示為標記](../profiling/visualizing-eventsource-events-as-markers.md)。

## <a name="see-also"></a>另請參閱
- [旗標標記](../profiling/flag-markers.md)
- [訊息標記](../profiling/message-markers.md)
- [範圍標記](../profiling/span-markers.md)
- [將 EventSource 事件顯示為標記](../profiling/visualizing-eventsource-events-as-markers.md)