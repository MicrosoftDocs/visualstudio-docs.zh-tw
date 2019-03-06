---
title: 模組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f31e3760a0697be8c9fc80eb811c99df79d32b1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718907"
---
# <a name="modules"></a>模組
偵錯工具就架構而言，*模組*:

-   是一個實體容器的程式碼，例如可執行檔或 DLL。

-   可以重新載入其符號，並描述本身。 模組描述會顯示在 IDE 的 [模組] 視窗中。

-   由[IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)來描述模組的偵錯引擎所建立的介面。

## <a name="see-also"></a>另請參閱
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)