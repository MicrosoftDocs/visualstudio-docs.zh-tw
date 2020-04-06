---
title: 港口供應商 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738290"
---
# <a name="port-suppliers"></a>港口供應商
在除錯器架構結構中,*連接埠供應商*:

- 由伺服器控制,並應請求向該伺服器提供埠。

- 可以從包含的伺服器添加和刪除埠。

- 可以枚舉它提供給伺服器的所有埠。

- 由[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面表示,該介面通過註冊表在 Visual Studio 中註冊。 此介面可以通過調用[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)獲得。

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供預設埠供應商和預設埠。 如果需要實現自定義埠,還需要實施自定義埠供應商來提供這些自定義埠。

## <a name="see-also"></a>另請參閱
- [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [連接埠](../../extensibility/debugger/ports.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
