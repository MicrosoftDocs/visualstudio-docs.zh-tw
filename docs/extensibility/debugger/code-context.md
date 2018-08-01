---
title: 程式碼內容 |Microsoft Docs
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
ms.openlocfilehash: 31b1f3d91fd44308c1737f8066c13af730454abe
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203341"
---
# <a name="code-context"></a>程式碼內容
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯**程式碼內容**:  
  
-   提供偵錯引擎 (DE) 已知的抽象概念的程式碼中的位置。 適用於大部分的執行階段架構現在，程式碼內容可以視為該應用程式的指令資料流中的位址。 對於非傳統任務為語言，其中程式碼不可能呈現的指示，程式碼內容都可以透過其他方式來表示。  
  
-   描述您在偵錯的程式的執行資料流中目前的位置。  
  
-   存在僅當程式已停止於中斷點。  
  
-   具有相關聯的文件內容。  
  
-   由實作[IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [文件內容](../../extensibility/debugger/document-context.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)