---
title: IDebugProgramDestroyEventFlags2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6b57206159ce00fbb79e9f9af1a6353588df76c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
可讓偵錯引擎，將覆寫預設行為[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 偵錯工作階段結束時。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作這個介面是由偵錯引擎。 它可用於主機，可能會建立並終結多個程式的處理序存留期。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugProgramDestroyEventFlags2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|擷取程式旗標會終結。|  
  
## <a name="remarks"></a>備註  
 預設行為[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 是以返回設計模式之後，所有的程式已送出程式損毀事件。 此介面可讓偵錯引擎變更該行為。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll