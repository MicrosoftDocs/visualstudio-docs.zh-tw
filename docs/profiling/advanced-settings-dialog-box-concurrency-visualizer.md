---
title: 進階設定對話方塊 (並行視覺化檢視) | Microsoft Docs
description: 使用並行視覺化中的 [Advanced Settings] 來控制追蹤內容。 符號、Just My Code、緩衝處理等等有一些索引標籤。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0b58dfec2d0dd04f146c3a473736fa6911f194c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901252"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>進階設定對話方塊 (並行視覺化檢視)
使用並行視覺化檢視中的 [進階設定] 對話方塊，您可以控制收集追蹤的方式。  此對話方塊提供適用於符號、Just My Code、緩衝處理、篩選、CLR 事件、標記、提供者及檔案的索引標籤。

## <a name="symbols"></a>符號
 並行視覺化檢視會使用與 Visual Studio 偵錯工具相同的符號設定。 並行視覺化檢視會使用設定，來解析與效能資料相關聯的呼叫堆疊。  並行視覺化檢視會在處理追蹤時，存取設定頁面中所指定的符號伺服器。  透過網路存取此資料時，追蹤處理速度就會變慢。  若要降低解析符號所需的時間量，您可以本機快取符號。 如果已經下載符號，Visual Studio 將從本機快取中載入它們。

## <a name="just-my-code"></a>Just My Code
 根據預設，Just My Code 是 Visual Studio 中一組與目前方案建立關聯的 .*exe* 和 .*dll* 檔案。 當您使用 Just My Code 功能來篩選呼叫堆疊時，並行視覺化檢視就會評估這組檔案。 在 [Just My Code] 索引標籤中，您可以將包含 .*exe* 和 .*dll* 檔案的目錄新增至並行視覺化檢視針對 Just My Code 所使用的位置。

 在收集追蹤時，會將 .*exe* 和 .*dll* 檔案的路徑儲存於追蹤檔案中。  變更此設定不會影響任何先前收集的追蹤。

## <a name="buffering"></a>緩衝
 並行視覺化檢視會在收集追蹤時，使用Windows 事件追蹤 (ETW)。  ETW 會在儲存事件時使用各種緩衝區。  預設的 ETW 緩衝區設定並非適用所有案例，在某些情況下，可能會導致像是遺失事件等問題。  您可以使用 [緩衝] 索引標籤來設定 ETW 緩衝區設定。 如需詳細資訊，請參閱[事件追蹤](/windows/win32/etw/event-tracing-portal)和 [EVENT_TRACE_PROPERTIES 結構 (英文)](/windows/win32/api/evntrace/ns-evntrace-event_trace_properties)。

## <a name="filter"></a>篩選
 在 [篩選] 索引標籤上，您可以選取並行視覺化檢視所收集的事件集合。 選取事件子集會限制要在報表中顯示的資料類型、縮減每個追蹤的大小，並減少處理追蹤所需的時間。

### <a name="clr-events"></a>CLR 事件
 由 Common Language Runtime (CLR) 所產生的事件，讓並行視覺化檢視能夠解析 Managed 呼叫堆疊。  如果您停用 CLR 事件的收集，將縮減追蹤大小，但將無法解析部分呼叫堆疊。  如此一來，可能會對某些 CPU 執行緒活動進行不正確的分類。

### <a name="collect-for-native-processes"></a>針對原生處理序進行收集
 根據預設，由於通常不需針對原生處理器收集 CLR 事件，因此，只有在對 Managed 處理序進行程式碼剖析時，才會收集這類事件。  在某些情況下 (例如，當原生處理序裝載 CLR 時)，您可能必須針對原生處理序收集 CLR 事件。  如果是這種情況，請選取 [收集原生處理序] 核取方塊。

### <a name="disable-rundown-events"></a>停用取消事件
 CLR 會從下列兩個提供者產生事件︰執行階段和取消。  如果您想要收集 CLR 執行階段事件，但要避免收集取消事件，請選取 [停用取消事件] 核取方塊。  這可縮減因收集而產生的追蹤檔大小，但可能無法解析某些堆疊。 如需詳細資訊，請參閱 [CLR ETW 提供者](/dotnet/framework/performance/clr-etw-providers)。

### <a name="sample-events"></a>取樣事件
 您可以使用取樣事件來收集與執行緒執行相關聯的呼叫堆疊。 針對在目前處理序中執行的執行緒，大約每毫秒會收集這些事件一次。 如果您停用取樣事件的收集，就能縮減所收集的追蹤大小，但您無法檢視任何與執行緒執行相關聯的呼叫堆疊。

### <a name="gpu-events"></a>GPU 事件
 GPU 事件是 DirectX 所產生的事件。 如果您停用 GPU 事件的收集，就會縮減所收集的追蹤大小，但您無法在 [使用率] 檢視中檢視任何 GPU 活動，或在 [執行緒] 檢視中檢視 DirectX 引擎活動。

### <a name="file-io-events"></a>檔案 I/O 事件
 檔案 I/O 事件表示代表目前的處理序存取磁碟。  如果您停用檔案 I/O 事件，就會縮減追蹤的大小，但 [執行緒] 檢視將不會報告任何有關磁碟通道或磁碟作業的資訊。

## <a name="markers"></a>標記
 在 [標記] 索引標籤中，您可以設定一組 ETW 提供者，以便在並行視覺化檢視中顯示為標記。  您也可以根據重要性層級和 ETW 類別來篩選標記集合。  如果您使用[並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md) 並使用您自己的標記提供者，則可在此處註冊該提供者，讓它能夠出現在 [執行緒] 檢視中。

### <a name="add-a-new-provider"></a>新增新的提供者
 如果您的程式碼使用[並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md) 或遵循 <xref:System.Diagnostics.Tracing.EventSource> 慣例產生 ETW 事件，您可以在這個對話方塊中註冊這些事件，藉以在並行視覺化檢視中檢視它們。

 在 [ **名稱** ] 欄位中，輸入描述提供者所產生之事件種類的名稱。  在 [GUID] 欄位中，輸入與此提供者相關聯的 GUID (GUID 會與每個 ETW 提供者產生關聯)。

 (選擇性) 您可以指定是否要根據類別或重要性層級，篩選出來自此提供者的事件。  您可以使用類別欄位，根據並行視覺化檢視 SDK 類別進行篩選。  若要這樣做，請輸入以逗號分隔的類別字串或類別範圍。  這會指定要在目前提供者中顯示的事件類別。  如果您新增 <xref:System.Diagnostics.Tracing.EventSource> 提供者，就能使用 [類別] 欄位，依 ETW 關鍵字來篩選。  由於關鍵字是位元遮罩，因此，您能使用以逗號分隔的整數字串來指定要在遮罩中設定哪些位元。 例如，"1,2" 會設定第一個和第二個位元，而這會轉譯為十進位的 6。

 您可以使用重要性層級清單來篩選出重要性或 ETW 層級小於指定值的事件。

### <a name="configure-an-existing-provider"></a>設定現有的提供者
 若要編輯與現有提供者相關聯的設定，在清單中選取它，然後選擇 [編輯提供者] 按鈕。  您可以變更名稱、GUID 和篩選設定。

### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>篩選出並行視覺化檢視報表的標記資料
 如果您不想要讓特定提供者的資料出現在未來的追蹤中，請清除您想要移除之提供者旁邊的核取方塊。

## <a name="files"></a>檔案
 在 [檔案] 索引標籤上，您可以指定每次收集追蹤時要儲存追蹤檔的目錄。  並行視覺化檢視會針對它所收集的每個追蹤產生四個檔案：

- 核心模式的事件追蹤記錄 (ETL) 檔案 (<em>.</em>kernel.etl*)

- 使用者模式的事件追蹤記錄檔案 (<em>.</em>user.etl*)

- 並行視覺化檢視的資料檔案 (<em>.</em>CVData*)

- 並行視覺化檢視的追蹤檔案 (<em>.</em>CVTrace*)

  這兩個 ETL 檔案會儲存原始追蹤資料，而這兩個並行視覺化檢視檔案會儲存已處理的資料。  在處理追蹤之後，通常不會用到原始的 ETL 檔案。  選取 [分析後刪除事件追蹤記錄 (ETL) 檔案] 核取方塊，可減少儲存在磁碟上的追蹤資料量。

## <a name="see-also"></a>另請參閱
- [僅自己的程式碼](../profiling/just-my-code-threads-view.md)
- [並行視覺化標記](../profiling/concurrency-visualizer-markers.md)