---
title: 伺服器 (Visual Studio SDK) |Microsoft Docs
description: 本文說明 Visual Studio 中偵錯工具架構中伺服器的定義和角色。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99f6c634053df9191ac419c8ee450dc99cf62c7c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902120"
---
# <a name="servers-visual-studio-sdk"></a>伺服器 (Visual Studio SDK)
在偵錯工具架構中， *伺服器*：

- 是埠和埠供應商的容器，並將埠和埠供應商傳遞給會話 debug manager (SDM) 和偵錯工具引擎。

- 可以依名稱識別其本身，並列舉其埠和埠供應商。

- 是以 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) 介面表示，它只會由 Visual Studio 針對執行) 之 Visual Studio 的每個實例 (一個伺服器實例。

## <a name="see-also"></a>另請參閱
- [連接埠](../../extensibility/debugger/ports.md)
- [埠供應商](../../extensibility/debugger/port-suppliers.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
