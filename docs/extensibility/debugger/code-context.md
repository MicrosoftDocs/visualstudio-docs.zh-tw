---
title: 程式碼內容 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097831"
---
# <a name="code-context"></a>程式碼內容
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯，**程式碼內容**:  
  
-   已知的偵錯引擎 (DE)，提供抽象的程式碼中的位置。 大部分的執行階段架構，程式碼內容可以視為程式的指令資料流中的位址。 對於非語言，其中程式碼可能不由指示，程式碼內容都可以透過其他方式來表示。  
  
-   描述偵錯程式的執行資料流中目前的位置。  
  
-   存在僅當程式已停止於中斷點。  
  
-   有相關聯的文件內容。  
  
-   由實作[IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [文件內容](../../extensibility/debugger/document-context.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)