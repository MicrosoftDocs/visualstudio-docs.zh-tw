---
title: 直接附加到程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739257"
---
# <a name="attach-directly-to-a-program"></a>直接附加到程式
希望在已執行的進程中除錯程式的使用者通常遵循此過程:

1. 在 IDE 中,從 **「工具**」功能表中選擇 **「調試過程」** 命令。

    [處理序]**** 對話方塊隨即出現。

2. 選擇一個進程,然後單擊「**附加」** 按鈕。

    將顯示 **「附加到行程**」對話框,列出電腦上安裝的所有除錯引擎 (DEs)。

3. 指定用於調試所選進程的 D,然後按下 **「 確定**」。

   除錯包啟動除錯工作階段並將 D 清單傳遞給它。 除錯工作階段反過來將此清單以及回調函數傳遞到所選進程,然後要求行程枚舉其正在運行的程式。

   在程式設計上,為了回應使用者請求,調試包實例化作業階段調試管理器 (SDM),並將所選 D 的清單傳遞給它。 與清單一起,調試包傳遞 SDM [IDebugEvent 回調2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面。 除錯包透過除除[IDebugProcess2::附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)將 D 選項清單傳遞給所選進程。 然後,SDM 調用埠上的[IDebugProcess2::enum程式](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)來枚舉進程中運行的程式。

   從此時開始,每個調試引擎都附加到一個程式,完全如[啟動后的附加](../../extensibility/debugger/attaching-after-a-launch.md)中詳細一樣,但有兩個例外。

   為提高效率,為與 SDM 共用位址空間而實現的 DE 進行了分組,以便每個 DE 都有一組要附加到的程式。 在這種情況下[,IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)調用[IDebugEngine2::附加](../../extensibility/debugger/reference/idebugengine2-attach.md)並傳遞要附加到的程序陣組。

   第二個異常是,DE 發送到已運行的程式的啟動事件通常不包括入口點事件。

## <a name="see-also"></a>另請參閱
- [啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
