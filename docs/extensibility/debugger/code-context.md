---
title: 程式碼內容 |Microsoft Docs
description: 瞭解 Visual Studio 偵錯工具中的程式碼內容，描述程式碼中程式在中斷點停止時所存在的位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e3bd252990e52f4ecaede0cc5026067b28434bc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905718"
---
# <a name="code-context"></a>程式碼內容
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具中，程式 **代碼** 內容：

- 在程式碼中提供程式碼位置的抽象概念， (DE) 。 在現今大部分的執行時間架構中，可以將程式碼內容視為程式指令資料流程中的位址。 針對非傳統語言（程式碼可能不會以指示表示），程式碼內容可能會以其他方式表示。

- 描述您正在進行偵錯工具之執行資料流程中的目前位置。

- 只有當程式在中斷點停止時才存在。

- 具有相關聯的檔內容。

- 是由 [IDebugCodeCoNtext2](../../extensibility/debugger/reference/idebugcodecontext2.md) 介面所執行。

## <a name="see-also"></a>另請參閱
- [檔內容](../../extensibility/debugger/document-context.md)
- [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
