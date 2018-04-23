---
title: 文件內容 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f97df9bc3c0a40a44379ba37f1b36d79cffb74e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="document-context"></a>文件內容
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯，**文件內容**:  
  
-   表示原始程式檔中的位置。 對於在原始程式檔可能不存在的語言，文件內容會識別通常是由執行階段環境產生的文件中的位置。 例如，指令碼引擎可能會產生從指令碼的文件。 如需詳細資訊，請參閱[文件位置](../../extensibility/debugger/document-position.md)。  
  
-   描述對應至程式碼內容的來源文件中的位置。 符號處理常式會將程式碼內容對應至文件內容中，使用由編譯器或解譯器所產生的資訊。  
  
-   由實作[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼內容](../../extensibility/debugger/code-context.md)   
 [符號提供者](../../extensibility/debugger/symbol-provider.md)   
 [符號提供者介面](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)