---
title: 直接附加至程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc78234b31b98865f1779dd65d743d4196f9cbf5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903272"
---
# <a name="attach-directly-to-a-program"></a>直接附加至程式
想要在已執行的進程中，對程式進行偵錯工具的使用者，通常會遵循此流程：

1. 在 IDE 中，從 [**工具**] 功能表中選擇 [ **Debug 進程**] 命令。

    [處理序]**** 對話方塊隨即出現。

2. 選擇進程，然後按一下 [**附加**] 按鈕。

    [**附加至進程**] 對話方塊隨即出現，列出電腦上安裝的所有 debug Engine （DEs）。

3. 指定用來對所選進程進行程式的 DEs，然後按一下 **[確定]**。

   Debug 封裝會啟動一個「debug」會話，並將 DEs 清單傳遞給它。 接著，debug 會話會將這份清單連同回呼函式傳遞給選取的進程，然後要求進程列舉其執行中的程式。

   以程式設計方式回應使用者要求時，debug 封裝會具現化會話 debug manager （SDM），並將選取的 DEs 清單傳遞給它。 除了清單，debug 封裝也會將 SDM 傳遞至[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面。 Debug 封裝會藉由呼叫[IDebugProcess2：： Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)，將 DEs 清單傳遞至選取的進程。 然後，SDM 會在埠上呼叫[IDebugProcess2：： EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) ，以列舉在進程中執行的程式。

   從這裡開始，每個 debug engine 都會附加至程式，就像在[啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)所述，有兩個例外。

   為了提高效率，會將用來與 SDM 共用位址空間的 DEs 進行分組，讓每個 DE 都有一組要附加的程式。 在此情況下， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)會呼叫[IDebugEngine2：： attach](../../extensibility/debugger/reference/idebugengine2-attach.md) ，並將它傳遞至要附加至的程式陣列。

   第二個例外狀況是由「解除附加至已在執行的程式所傳送的啟動事件」通常不會包含進入點事件。

## <a name="see-also"></a>另請參閱
- [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
