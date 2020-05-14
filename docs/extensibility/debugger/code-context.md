---
title: 代碼上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739159"
---
# <a name="code-context"></a>代碼內容
除[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]錯中,**程式碼中 , 程式碼中**:

- 提供調試引擎 (DE) 已知的代碼中位置的抽象。 對於當今的大多數運行時體系結構,可以將代碼上下文視為程式指令流中的位址。 對於代碼可能由指令表示的非傳統語言,程式碼上下文可能通過其他某種方式表示。

- 描述正在調試的程式的執行流中的當前位置。

- 僅當程式在斷點停止時才存在。

- 具有關聯的文檔上下文。

- 由[IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)介面實現。

## <a name="see-also"></a>另請參閱
- [文件內容](../../extensibility/debugger/document-context.md)
- [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)
