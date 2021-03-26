---
title: 事件描述 |Microsoft Docs
description: 瞭解事件的類型，以及其使用的原因。 每種類型的事件都有特定用途。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd8c6dbb4eddfcffa779b70b17819bf5e92c0c45
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096963"
---
# <a name="event-descriptions"></a>事件描述
每種類型的事件都有特定用途。

## <a name="events-and-the-reasons-for-their-use"></a>事件及其使用的原因

|事件|描述|
|-----------|-----------------|
|開機檔案事件|當 debug engine (DE) 希望 IDE 開啟或將檔帶入前景時發生。|
|中斷點系結或中斷點錯誤事件|在系結中斷點或中斷點無法系結時傳送，而且會傳回錯誤。|
|中斷點未系結事件|系結的中斷點從程式碼解除系結時發生。|
|可以停止事件|傳送至 IDE，以判斷使用者是否想要在程式碼中的指定點停止。|
|中斷點事件|當遇到程式碼或資料中斷點時發生。|
|檔文字事件|在檔中的文字變更時發生。 這些事件不會透過方法傳送 `IDebugEventCallBack2::Event` 。|
|引擎建立事件|在第一次建立引擎時傳送。|
|進入點事件|在正在進行調試的程式執行其初始化程式碼並到達其第一個使用者進入點時傳送。|
|例外狀況事件|當執行中的程式到達例外狀況時傳送。|
|運算式評估完成事件|在非同步運算式評估完成時傳送。|
|尋找符號事件|每次需要要求使用者尋找模組的符號時傳送。|
|載入完成事件|只有在初始程式載入完成，而且第一個程式碼即將在程式中執行時，才會傳送。|
|訊息事件|傳送訊息給使用者時傳送。|
|模組載入事件|在載入或卸載新模組時傳送。|
|輸出字串事件|當程式寫入偵錯工具輸出時傳送。|
|建立和終結事件|傳送來宣佈進程、程式、屬性、會話和執行緒的建立或終結，讓 Visual Studio IDE 可以追蹤正在進行偵錯工具的狀態。|
|逐步完成事件|在步驟完成時傳送。|
|執行緒名稱變更事件|當使用者變更執行緒的名稱時傳送。|
|程式名稱變更事件|當使用者變更程式名稱時傳送。|

## <a name="see-also"></a>另請參閱
- [傳送事件](../../extensibility/debugger/sending-events.md)
