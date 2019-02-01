---
title: 訊息標記 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c7a173bf0b7f5b3dc2187c0c8574819b2317a9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804023"
---
# <a name="message-markers"></a>訊息標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

訊息標記表示記錄檔輸出。 訊息是由特定執行緒在特定時間發出的字串。 您可以將訊息匯出成文字檔，以便與其他工具搭配使用。 您可以將指標放在並行視覺化檢視中的訊息上，以檢視訊息字串。 您可以檢視在[標記報告](../profiling/markers-report.md)中檢視所有訊息標記。  下圖顯示訊息標記。  
  
## <a name="message-aggregation-markers"></a>訊息彙總標記  
 有時多個訊息發生的位置太靠近並行視覺化檢視中的另一個標記，以至於無法個別繪製。 發生這種情況時，會顯示一個表示基礎訊息的灰色「訊息彙總標記」。 當您將指標放在這些圖示的其中一個時，工具提示會顯示所代表基礎訊息的數目。 若要檢視訊息，請予以放大。  如果您縮放到最大後仍然出現彙總標記，您可以在[標記報告](../profiling/markers-report.md)中檢視基礎訊息。  
  
## <a name="see-also"></a>請參閱  
 [並行視覺化檢視標記](../profiling/concurrency-visualizer-markers.md)   
 [並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md)
