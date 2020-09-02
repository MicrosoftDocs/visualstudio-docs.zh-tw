---
title: IDebugStopCompleteEvent2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546913"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

當程式停止時，debug engine (DE) 可以將這個選擇性事件傳送至會話 debug manager (SDM) 。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 這是的新介面 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 。 先前的版本不支援非同步停止。  
  
 多進程或多程式案例中的 SDM 會呼叫[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 。 當某個程式將停止事件傳送至 SDM 時，SDM 也會要求其他程式停止。  
  
 它是用來以非同步方式通知 SDM 程式已停止。 這對解譯器的偵測引擎很有用，在這種情況下，程式碼在偵錯工具中有時不會執行，所以無法同步完成 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 。 如果「debug engine」想要採用此非同步通知，它必須 `S_ASYNC_STOP` 從「 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)」回來。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll
