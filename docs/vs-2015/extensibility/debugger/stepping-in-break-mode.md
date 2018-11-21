---
title: 在中斷模式中逐步執行 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4400bcbecce322185ec514e6d05ac9a37e27fdde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749089"
---
# <a name="stepping-in-break-mode"></a>在中斷模式中逐步執行
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明偵錯工具處於中斷模式，且必須逐步執行程式碼時發生的處理程序：  
  
## <a name="stepping-process"></a>逐步執行程序  
  
1.  呼叫[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)具有[STEPKIND](../../extensibility/debugger/reference/stepkind.md)並[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)執行之步驟的引數。  
  
2.  完成步驟後，傳送[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)為停止事件。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)

