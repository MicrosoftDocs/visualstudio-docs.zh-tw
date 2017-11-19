---
title: "IDebugStopCompleteEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
偵錯引擎 (DE) 可以傳送這個選擇性事件工作階段的偵錯管理員 (SDM) 當程式已停止。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 這是新的介面的[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]。 先前的版本不支援非同步停止。  
  
 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)SDM 中多處理序或多個程式的情況下呼叫。 當一種程式會將停止事件傳送至 SDM 時，SDM 要求太停止其他程式。  
  
 它用來以非同步方式通知程式已停止 SDM。 這可用於解譯器偵錯引擎有時沒有程式碼執行所在的偵錯程式內，因此[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)不同步完成。 如果偵錯引擎要採用此非同步通知時，它必須傳回`S_ASYNC_STOP`從[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll