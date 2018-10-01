---
title: 終止程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6092e7f393eb973980cfca123264326aa0b2388b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496573"
---
# <a name="terminating-a-program"></a>終止程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[終止程式](https://docs.microsoft.com/visualstudio/extensibility/debugger/terminating-a-program)。  
  
以下是一個執行緒的單一程式終止的描述。  
  
## <a name="termination-process"></a>終止程序  
  
1.  DE 傳送[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)的有效[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)。  
  
2.  DE 傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)的有效[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)。  
  
 IDE 會進入設計模式。 執行階段環境呼叫的偵錯引擎[IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)來移除連接埠的程式。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)

