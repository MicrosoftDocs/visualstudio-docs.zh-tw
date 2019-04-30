---
title: 事件描述 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5a1567cc7f5d3f6072b47fda1aacd32f69cb672
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889716"
---
# <a name="event-descriptions"></a>事件描述
事件的每個類型都有特定的用途。

## <a name="events-and-the-reasons-for-their-use"></a>事件和其使用的原因

|Event - 事件|描述|
|-----------|-----------------|
|啟用文件事件|偵錯引擎 (DE) 想要開啟或文件帶到前景 IDE 時發生。|
|繫結的中斷點或中斷點錯誤事件|當中斷點繫結或當中斷點無法繫結，而且會傳回錯誤時，就會傳送。|
|未繫結的中斷點事件|從程式碼會繫結的中斷點解除繫結時發生。|
|可以停止事件|若要判斷使用者是否想要停止程式碼中的指定點在傳送至 IDE。|
|中斷點事件|發生時叫用程式碼或資料中斷點。|
|文件文字事件|文件中的文字變更時，就會發生。 這些事件不會透過傳送`IDebugEventCallBack2::Event`方法。|
|引擎會建立事件|第一次建立引擎時，就會傳送。|
|項目點事件|當正在進行偵錯的程式已執行其初始化程式碼，並達到其第一個使用者進入點時，就會傳送。|
|例外狀況事件|當執行中的程式會觸發例外狀況時，就會傳送。|
|運算式評估完成事件|非同步運算式評估完成時傳送。|
|尋找符號的事件|每當 DE 需要要求使用者尋找符號的模組，就會傳送。|
|載入完成事件|傳送只有初始程式載入完畢，並且在即將執行的程式中的第一個程式碼。|
|訊息事件|當訊息傳送給使用者時，就會傳送。|
|模組載入事件|當新的模組會載入或卸載時，就會傳送。|
|輸出字串的事件|程式會寫入偵錯輸出時傳送。|
|建立和終結事件|傳送至宣佈的建立或遭到破壞的程序、 程式、 內容、 講習會以及執行緒，讓 Visual Studio IDE 可追蹤的偵錯的程式的狀態。|
|步驟完成事件|步驟已完成時傳送。|
|執行緒名稱變更事件|當使用者變更執行緒的名稱時，就會傳送。|
|程式名稱變更事件|當使用者變更程式的名稱時，就會傳送。|

## <a name="see-also"></a>另請參閱
- [傳送事件](../../extensibility/debugger/sending-events.md)