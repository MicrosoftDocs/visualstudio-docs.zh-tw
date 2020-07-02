---
title: 通道 (執行緒檢視) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df93a87285bdf1172e75b63ed956c1aa978fc71e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545531"
---
# <a name="channels-threads-view"></a>通道 (執行緒檢視)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

並行視覺化檢視會顯示四種通道︰執行緒通道、磁碟通道、標記通道和 GPU 通道。  
  
## <a name="thread-channels"></a>執行緒通道  
 執行緒通道以不同色彩為每種執行緒顯示執行緒的狀態。 當您暫停在通道名稱時，會顯示指定執行緒的開始函式。 並行視覺化檢視會偵測幾種執行緒。 下表顯示最常見的種類。  
  
|Thread|描述|  
|-|-|  
|主執行緒|啟動應用程式的執行緒。|  
|背景工作執行緒|應用程式主執行緒所建立的執行緒。|  
|CLR 背景工作執行緒|背景工作執行緒是由通用語言執行平台 (CLR) 建立。|  
|偵錯工具協助程式|Visual Studio 偵錯工具所建立的背景工作執行緒。|  
|ConcRT 執行緒|Microsoft 並行執行階段所建立的執行緒。|  
|GDI 執行緒|GDIPlus 所建立的執行緒。|  
|OLE/RPC 執行緒|以 RPC 背景工作執行緒方式建立的執行緒。|  
|RPC 執行緒|以 RPC 執行緒方式建立的執行緒。|  
|Winsock 執行緒|以 Winsock 執行緒方式建立的執行緒。|  
|執行緒集區|CLR 執行緒集區所建立的執行緒。|  
  
## <a name="disk-channels"></a>磁碟通道  
 磁碟通道對應至電腦中的實體磁碟機。 因為系統上的每個實體磁碟機都有不同的通道進行讀取和寫入作業，所以每個磁碟機都有兩個通道。 磁碟編號對應置核心裝置名稱。 只有當磁碟有活動時，才會顯示磁碟通道。  
  
## <a name="marker-channels"></a>標記通道  
 標記通道對應至由應用程式以及所使用的程式庫所產生的事件。 例如，工作平行程式庫、平行模式程式庫和 C++ AMP 會產生顯示為標記的事件。 每個標記通道都與一個執行緒識別碼相關聯，執行緒識別碼顯示在通道的描述旁邊。 識別碼會識別產生事件的執行緒。 通道的描述包含產生事件之 Windows 事件追蹤 (ETW) 提供者的名稱。 如果通道顯示來自[並行視覺化檢視 SDK](../profiling/concurrency-visualizer-sdk.md) 的事件，也會顯示系列名稱。  
  
## <a name="gpu-channels"></a>GPU 通道  
 GPU 通道顯示系統上 DirectX 11 活動的相關資訊。  與圖形卡相關聯的每個 DirectX 引擎都有不同的通道。  個別區段代表處理 DMA 封包所花費的時間。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)
