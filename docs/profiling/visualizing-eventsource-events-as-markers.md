---
title: 將 EventSource 事件顯示為標記 | Microsoft Docs
description: 瞭解平行存取視覺化程式可以將 EventSource 事件顯示為標記，而您可以控制標記的顯示方式。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f8fadf9ef97717983c96226d81d43efada65e89
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723136"
---
# <a name="visualize-eventsource-events-as-markers"></a>將 EventSource 事件顯示為標記
並行視覺化檢視可以將 EventSource 事件顯示為標記，而您可以控制顯示標記的方式。 若要檢視 EventSource 標記，請使用 [進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 對話方塊，註冊 ETW 提供者 GUID。 並行視覺化檢視表示 EventSource 事件的預設慣例為[旗標標記](../profiling/flag-markers.md)、[延伸標記](../profiling/span-markers.md)及[訊息標記](../profiling/message-markers.md)。 您可以將自訂欄位加入至事件，來自訂 EventSource 事件的顯示方式 。 如需標記的詳細資訊，請參閱[並行視覺化檢視標記](../profiling/concurrency-visualizer-markers.md)。 如需 EventSource 事件的詳細資訊，請參閱 <xref:System.Diagnostics.Tracing>。

## <a name="default-visualization-of-eventsource-events"></a>EventSource 事件的預設視覺化
 根據預設，並行視覺化檢視會使用下列慣例來表示 EventSource 事件。

### <a name="marker-type"></a>標記類型

1. 有[作業碼 (Opcode)](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win:Start 或 win:Stop 的事件會分別視為延伸範圍的開始或結束。  無法顯示巢狀或重疊的延伸範圍。 無法顯示在一個執行緒開始但在另一個執行序結束的事件組合。

2. 其作業碼不是 win:Start，也非 win:Stop 的事件會視為標記旗標，除非其[層級 (Level)](/windows/desktop/WES/defining-severity-levels) (EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR 的欄位) 是 win:Verbose 或更高。

3. 在其他情況下，會將該事件視為一則訊息。

### <a name="importance"></a>重要性
 下表定義事件層級和標記重要性的對應方式。

|ETW 層級|並行視覺化檢視重要性|
|---------------|---------------------------------------|
|win:LogAlways|正常|
|win:Critical|重大|
|win:Error|重大|
|win:Warning|高|
|win:Informational|正常|
|win:Verbose|低|
|大於 win:verbose|低|

### <a name="series-name"></a>數列名稱
 用來當成序列名稱的事件工作名稱。 如果事件未定義任何工作，序列名稱為空白。

### <a name="category"></a>類別
 如果層級為 win:Critical 或 win:Error，則分類會是警示 (-1)。 否則，該分類為預設值 (0)。

### <a name="text"></a>Text
 如果事件定義為 printf 類型的格式化文字訊息，其會顯示為標記的描述。 否則，描述會是事件名稱和每個裝載欄位的值。

## <a name="customize-visualization-of-eventsource-events"></a>自訂 EventSource 事件的視覺化
 您可以將適當的欄位加入至事件，來自訂 EventSource 事件的顯示方式，如下列各節中所述。

### <a name="marker-type"></a>標記類型
 使用 `cvType` 欄位 (一個位元組)，來控制用來表示事件的標記類型。 以下是 cvType 的可用值︰

|cvType 值|產生的標記類型|
|------------------|---------------------------|
|0|訊息|
|1|延伸範圍開始|
|2|延伸範圍結束|
|3|旗標|
|所有其他的值|訊息|

### <a name="importance"></a>重要性
 您可以使用 `cvImportance` 欄位 (一個位元組)，來控制 EventSource 事件的重要性設定。 不過，建議您使用其層級來控制顯示的事件重要性。

|cvImportance 值|並行視覺化檢視重要性|
|------------------------|---------------------------------------|
|0|正常|
|1|重大|
|2|高|
|3|高|
|4|正常|
|5|低|
|所有其他的值|低|

### <a name="series-name"></a>數列名稱
 使用 `cvSeries` 事件欄位 (一個字串)，來控制並行視覺化檢視提供給 EventSource 事件的序列名稱。

### <a name="category"></a>類別
 使用 `cvCategory` 欄位 (一個位元組)，來控制並行視覺化檢視提供給 EventSource 事件的分類。

### <a name="text"></a>Text
 使用 `cvTextW` 欄位 (一個字串)，來控制並行視覺化檢視提供給 EventSource 事件的描述。

### <a name="spanid"></a>SpanID
 使用 cvSpanId 欄位 (一個整數)，來比對事件組合。 表示延伸範圍的每一組開始/停止事件都必須要有唯一的值。 一般而言，對於並行程式碼，這需要使用 <xref:System.Threading.Interlocked.Exchange%2A> 這類同步處理原始物件，以確保正確的索引鍵 (用於 CvSpanID 的值)。

> [!NOTE]
> 使用 SpanID 將延伸範圍巢狀化，不支援允許其在相同執行緒上部分重疊，或允許其在一個執行緒上開始並在另一個執行緒上結束。

## <a name="see-also"></a>另請參閱
- [並行視覺化標記](../profiling/concurrency-visualizer-markers.md)