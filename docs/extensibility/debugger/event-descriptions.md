---
title: 活動描述 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738794"
---
# <a name="event-descriptions"></a>事件描述
每種類型的事件都有特定用途。

## <a name="events-and-the-reasons-for-their-use"></a>事件及其使用原因

|事件|描述|
|-----------|-----------------|
|啟用文件事件|當調試引擎 (DE) 希望 IDE 打開或將文檔帶到前台時發生。|
|斷點繫結或斷點錯誤事件|在綁定斷點或斷點無法綁定並返回錯誤時發送。|
|斷點未繫結事件|當綁定斷點從代碼中取消綁定時發生。|
|可以停止事件|發送到 IDE 以確定使用者是否要在代碼中的指定點停止。|
|斷點事件|當發生代碼或數據斷點時發生。|
|文件文字事件|當更改文件中的文本時發生。 這些事件不會通過方法`IDebugEventCallBack2::Event`發送。|
|引擎建立事件|首次創建引擎時發送。|
|入口點事件|當正在調試的程式已運行其初始化代碼並到達其第一個使用者入口點時發送。|
|異常事件|當正在運行的程式遇到異常時發送。|
|運算式計算完成事件|非同步運算完成後發送。|
|尋找符號事件|每當 DE 需要要求使用者查找模組的符號時,都會發送。|
|載入完整事件|僅當初始程式載入完成且第一個代碼即將在程式中運行時才發送。|
|訊息事件|向使用者發送消息時發送。|
|模組載入事件|載入或卸載新模組時發送。|
|輸出字串事件|程式寫入調試輸出時發送。|
|建立與銷毀事件|已發送以宣佈進程、程式、屬性、工作階段和線程的創建或銷毀,以便 Visual Studio IDE 可以追蹤正在除錯的程式的狀態。|
|步驟完成事件|步驟完成後發送。|
|執行緒名稱變更事件|當使用者更改線程的名稱時發送。|
|程式名稱變更事件|當使用者更改程式名稱時發送。|

## <a name="see-also"></a>另請參閱
- [傳送事件](../../extensibility/debugger/sending-events.md)
