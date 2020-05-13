---
title: 文件上下文 |微軟文件
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
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738915"
---
# <a name="document-context"></a>文件內容
除[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]錯中,*文件中文 :*

- 表示源檔中的位置。 對於源檔案可能不存在的語言,文檔上下文標識通常由執行時環境生成的文件中的位置。 例如,腳本引擎可能從腳本生成文檔。 有關詳細資訊,請參考[文件位置](../../extensibility/debugger/document-position.md)。

- 描述源文件中對應於代碼上下文的位置。 符號處理程式使用編譯器或解釋器生成的信息將代碼上下文映射到文檔上下文。

- 由[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面實現。

## <a name="see-also"></a>另請參閱
- [代碼內容](../../extensibility/debugger/code-context.md)
- [符號提供者](../../extensibility/debugger/symbol-provider.md)
- [符號提供者介面](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)
