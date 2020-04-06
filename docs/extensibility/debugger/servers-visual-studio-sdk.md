---
title: 伺服器(可視化工作室 SDK) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712888"
---
# <a name="servers-visual-studio-sdk"></a>伺服器 (Visual Studio SDK)
在除錯器架構結構中,*伺服器*:

- 是埠和埠供應商的容器,將埠和埠供應商與會話調試管理器 (SDM) 和調試引擎進行通信。

- 可以按名稱標識自身,並枚舉其埠和埠供應商。

- 由[IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)介面表示,該介面僅由 Visual Studio 實現(運行的 Visual Studio 的每個實例的伺服器的一個實例)。

## <a name="see-also"></a>另請參閱
- [連接埠](../../extensibility/debugger/ports.md)
- [港口供應商](../../extensibility/debugger/port-suppliers.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
