---
title: 並行視覺化檢視中的標記 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43b6115c45f9583b90711ef030834da662106f08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704357"
---
# <a name="concurrency-visualizer-markers"></a>並行視覺化檢視中的標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在並行視覺化檢視中，標記是代表應用程式中事件的圖示。  一般而言，應用程式會產生這些事件，以指定應用程式中的階段或發生次數。  應用程式或程式庫和應用程式使用的執行階段，可以產生事件。  
  
## <a name="kinds-of-markers"></a>標記類型  
 並行視覺化檢視使用三種類型的標記來表示應用程式事件︰旗標、訊息和範圍。  
  
1. 使用*旗標*可指出應用程式中有趣的時間點。  例如，您可以使用旗標來表示變數值已達到特定的閾值或表示擲回例外狀況。  
  
2. *訊息*也可標記時間點，但是您可以使用它追蹤記錄檔樣式。  例如，您現在可以在訊息呼叫中包裝傾印到記錄檔的內容以便追蹤，並在並行視覺化檢視中檢視。 您也可以使用並行視覺化檢視將此資料匯出至 CSV 檔案。  
  
3. *範圍*代表應用程式中一個時間間隔，例如其中一個階段。  
  
## <a name="marker-linkage-to-threads"></a>執行緒標記連結  
 產生標記的每個執行緒都有不同的時間軸通道。  負責產生標記事件的執行緒識別碼會顯示在標記通道的描述旁邊。  標記通道左邊顯示的識別碼符合目前處理序中另一個執行緒的 ID。  
  
## <a name="marker-importance"></a>標記重要性  
 標記可以有其中一種四種重要性層級︰低、標準、高和重要。  您可以根據重要性層級篩選標記的來源。  例如，如果您只想看到來自特定來源有一般或重要重要性的標記，您可以在 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊中設定篩選。標記的重要性會顯示在其工具提示和[標記報告](../profiling/markers-report.md)中。  
  
## <a name="marker-category"></a>標記分類  
 標記分類表示一組來自相同來源的標記事件。  並行視覺化檢視使用色彩來區別不同分類的旗標和範圍。 您可以設定並行視覺化檢視以使用分類來篩選來自特定事件提供者的標記事件。  使用 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊可設定篩選。  
  
## <a name="known-sources-of-markers"></a>已知的標記來源  
 只要提供者符合某些限制式，任何 ETW 提供者都可以產生標記。 您可以設定並行視覺化檢視來接聽其他事件來源的標記。 預設會接聽這些事件來源︰  
  
- [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)  
  
- [工作平行程式庫 (TPL)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [資料流程](https://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [平行 LINQ (PLINQ)](https://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [並行執行階段](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [情節標記支援](https://msdn.microsoft.com/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](https://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  您可以使用 [[進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)] 對話方塊中的 [標記] 索引標籤，控制各種來源的標記是否顯示在並行視覺化檢視中，您可以依照重要性和類別篩選標記。  
  
## <a name="markers-from-eventsource"></a>來自 EventSource 的標記  
 並行視覺化檢視也可以顯示 EventSource 事件。  如需詳細資訊，請參閱[將 EventSource 事件顯示為標記](../profiling/visualizing-eventsource-events-as-markers.md)。  
  
## <a name="see-also"></a>另請參閱  
 [旗標標記](../profiling/flag-markers.md)   
 [訊息標記](../profiling/message-markers.md)   
 [範圍標記](../profiling/span-markers.md)   
 [將 EventSource 事件顯示為標記](../profiling/visualizing-eventsource-events-as-markers.md)
