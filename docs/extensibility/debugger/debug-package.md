---
title: 除錯包 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739030"
---
# <a name="debug-package"></a>除錯套件
調試包在 Visual Studio 外殼中運行,並處理所有 UI。 它使用 Visual Studio 調試介面並與工作階段調試管理器 (SDM) 通信。

 通過 SDM 發送的中斷事件將調試器從運行模式切換到中斷模式,並將焦點更改為發生中斷的程式。 調試包跟蹤堆疊幀和線程從事件發送給它的資訊。

 調試包沒有語言或運行時環境依賴關係。 不需要實現或修改調試包。

 調試包由*vsdebug.dll*實現。

## <a name="see-also"></a>另請參閱
- [工作階段除錯管理員](../../extensibility/debugger/session-debug-manager.md)
- [堆疊幀](../../extensibility/debugger/stack-frames.md)
- [執行緒](../../extensibility/debugger/threads.md)
- [除錯器元件](../../extensibility/debugger/debugger-components.md)
