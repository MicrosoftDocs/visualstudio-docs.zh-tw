---
title: 程式碼內容 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197379"
---
# <a name="code-context"></a>程式碼內容
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯**程式碼內容**:  
  
- 提供偵錯引擎 (DE) 已知的抽象概念的程式碼中的位置。 適用於大部分的執行階段架構現在，程式碼內容可以視為該應用程式的指令資料流中的位址。 對於非傳統任務為語言，其中程式碼不可能呈現的指示，程式碼內容都可以透過其他方式來表示。  
  
- 描述正在偵錯之程式的執行資料流中目前的位置。  
  
- 存在僅當程式已停止於中斷點。  
  
- 具有相關聯的文件內容。  
  
- 由實作[IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [文件內容](../../extensibility/debugger/document-context.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
