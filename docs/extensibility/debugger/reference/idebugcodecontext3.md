---
title: IDebugCodeContext3 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 451e61ab7d6f74c83898987cdbecad2a9e13b06c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
擴充[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)介面，以擷取模組和處理序的介面。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎所實作且由[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯封裝。  
  
## <a name="methods"></a>方法  
 除了上`IDebugCodeContext2`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|擷取的偵錯模組介面的參考。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|擷取偵錯處理序的介面的參考。|  
  
## <a name="remarks"></a>備註  
 這是選擇性但通常不需要實作的介面。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll