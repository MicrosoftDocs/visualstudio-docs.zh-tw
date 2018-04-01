---
title: IDebugProgramNameChangedEvent2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 6
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 92cab263f6f19b719ee6452b93b6cb53ba7efd1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
程式的名稱變更時傳送的偵錯引擎 (DE) 從工作階段的偵錯管理員 (SDM)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來的程式名稱已變更的報表。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取**IDebugEvent2**介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立和傳送此報告程式的名稱變更的事件物件。 DE 使用來傳送此事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。 自訂連接埠供應商傳送此事件，使用我的介面。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll