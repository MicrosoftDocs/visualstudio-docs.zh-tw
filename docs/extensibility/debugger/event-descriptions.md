---
title: "事件描述 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6ec084c0d985ce5cc3cb0a886bd1fdcaf6cc3e54
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="event-descriptions"></a>事件描述
每種類型的事件有特定的用途。  
  
## <a name="events-and-the-reasons-for-their-use"></a>事件和其使用的原因  
  
|Event - 事件|描述|  
|-----------|-----------------|  
|啟用文件事件|偵錯引擎 (DE) 想要開啟或文件帶到前景 IDE 時，就會發生。|  
|繫結的中斷點或中斷點錯誤事件|傳送時的中斷點繫結或當中斷點無法繫結，而且會傳回錯誤。|  
|中斷點解除繫結事件|從程式碼的繫結的中斷點解除繫結時，則會發生。|  
|可以停止事件|若要判斷使用者是否想要在程式碼中的指定點停止傳送至 IDE。|  
|中斷點的事件|程式碼或資料叫用中斷點時，就會發生。|  
|文件文字事件|文件中的文字變更時發生。 這些事件不會透過傳送`IDebugEventCallBack2::Event`方法。|  
|引擎建立的事件|第一次建立引擎時，就會傳送。|  
|項目點事件|送出時已執行其初始化程式碼進行偵錯的程式，並達到其第一個使用者進入點。|  
|例外狀況事件|正在執行的程式遇到例外狀況時傳送。|  
|運算式評估完成事件|完成非同步的運算式評估時傳送。|  
|尋找符號事件|傳送每當 DE 必須要求使用者尋找模組的符號。|  
|載入完成事件|只有當初始程式負載已完成且第一個程式碼即將執行的程式中傳送。|  
|訊息事件|當訊息傳送給使用者時，就會傳送。|  
|模組載入事件|新的模組會載入或卸載時傳送。|  
|輸出字串事件|程式會將偵錯輸出時傳送。|  
|建立和終結事件|傳送通知的建立或處理程序、 程式、 屬性、 工作階段和執行緒的解構讓 Visual Studio IDE 可以追蹤的偵錯的程式的狀態。|  
|步驟完成事件|步驟已完成時傳送。|  
|執行緒名稱變更事件|當使用者變更執行緒的名稱時，就會傳送。|  
|程式名稱變更事件|當使用者變更程式的名稱時，就會傳送。|  
  
## <a name="see-also"></a>請參閱  
 [傳送事件](../../extensibility/debugger/sending-events.md)