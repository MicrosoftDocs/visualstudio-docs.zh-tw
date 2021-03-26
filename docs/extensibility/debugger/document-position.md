---
title: 檔位置 |Microsoft Docs
description: 瞭解 Visual Studio 偵錯工具中的檔位置如何在原始程式檔中提供 IDE 已知位置的抽象概念。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d14f9619059735aaecabf72adef248c69ed247e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097249"
---
# <a name="document-position"></a>檔位置
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 調試中， *檔位置*：

- 提供 IDE 已知的原始程式檔中的位置抽象概念。 在現今大部分的語言中，可以將檔位置視為原始程式檔中的位置。

- 描述來源文件中對 debug 引擎的位置。

- 是由 [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) 介面所執行。

## <a name="see-also"></a>另請參閱
- [程式碼內容](../../extensibility/debugger/code-context.md)
- [檔內容](../../extensibility/debugger/document-context.md)
- [符號提供者](../../extensibility/debugger/symbol-provider.md)
- [符號提供者介面](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
