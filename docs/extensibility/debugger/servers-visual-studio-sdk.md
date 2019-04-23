---
title: 伺服器 (Visual Studio SDK) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ec28d0d9202bfd72d31e95c53038dd1fa475e9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111775"
---
# <a name="servers-visual-studio-sdk"></a>伺服器 (Visual Studio SDK)
在偵錯工具架構中， *server*:

- 是一個容器的連接埠和連接埠提供者和通訊連接埠和連接埠提供者的工作階段偵錯管理員 (SDM) 和偵錯引擎。

- 可以依名稱、 識別自己，並列舉其連接埠和連接埠提供者。

- 由[IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)介面，只藉由 Visual Studio （Visual Studio 執行的每個執行個體的伺服器的一個執行個體）。

## <a name="see-also"></a>另請參閱
- [連接埠](../../extensibility/debugger/ports.md)
- [連接埠提供者](../../extensibility/debugger/port-suppliers.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)