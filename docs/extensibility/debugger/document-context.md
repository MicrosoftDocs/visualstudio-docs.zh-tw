---
title: 檔內容 |Microsoft Docs
description: 瞭解 Visual Studio 偵錯工具中的檔內容，其代表原始程式檔中的位置，或程式碼內容之來源文件中的位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d19830346ea09731dde608e019109f61011cd60
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915527"
---
# <a name="document-context"></a>檔內容
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 調試中， *檔內容*：

- 表示原始檔案中的位置。 針對來源檔案可能不存在的語言，檔內容會識別檔中通常由執行時間環境產生的位置。 例如，腳本引擎可能會從腳本產生檔。 如需詳細資訊，請參閱 [檔位置](../../extensibility/debugger/document-position.md)。

- 描述對應至程式碼內容之來源文件中的位置。 符號處理常式會使用編譯器或解譯器所產生的資訊，將程式碼內容對應至檔內容。

- 是由 [IDebugDocumentCoNtext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) 介面所執行。

## <a name="see-also"></a>另請參閱
- [程式碼內容](../../extensibility/debugger/code-context.md)
- [符號提供者](../../extensibility/debugger/symbol-provider.md)
- [符號提供者介面](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
