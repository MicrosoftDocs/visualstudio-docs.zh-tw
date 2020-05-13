---
title: 終止程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712514"
---
# <a name="terminating-a-program"></a>終止程式
以下部分介紹使用一個線程終止單個程式。

## <a name="termination-process"></a>取消過程

1. DE 傳送[IDebugThread 破壞事件2,](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)帶有一個有效的[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)。

2. DE 發送具有有效[IDebug Program2](../../extensibility/debugger/reference/idebugprogram2.md)的[IDebug Program破壞事件2。](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

   IDE 進入設計模式。 除錯引擎或執行時環境調用[IDebugPortNotify2::刪除程式節點](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)以從埠中刪除程式。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
