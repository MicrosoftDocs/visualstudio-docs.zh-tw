---
title: 埠供應商 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738290"
---
# <a name="port-suppliers"></a>埠供應商
在偵錯工具架構中， *埠供應商*：

- 包含在伺服器上，並提供對該伺服器之要求的埠。

- 可以從包含的伺服器加入和移除埠。

- 可以列舉所有提供給伺服器的埠。

- 是以 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 介面表示，此介面透過登錄向 Visual Studio 註冊。 您可以藉由呼叫 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)來取得這個介面。

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供預設埠供應商和預設通訊埠。 如果需要執行自訂埠，也需要執行自訂埠供應商來提供這些自訂埠。

## <a name="see-also"></a>另請參閱
- [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [連接埠](../../extensibility/debugger/ports.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
