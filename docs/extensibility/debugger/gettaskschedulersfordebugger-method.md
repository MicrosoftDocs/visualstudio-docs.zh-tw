---
title: GetTaskSchedulersForDebugger 方法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dc8e43629eab80dc3164813d0b8d0f380e8f86a
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231175"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
擷取的所有陣列<xref:System.Threading.Tasks.TaskScheduler>目前使用中的物件。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib (在*mscorlib.dll*)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```csharp  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>傳回值  
 所有陣列<xref:System.Threading.Tasks.TaskScheduler>且目前正在使用中的物件<xref:System.AppDomain>。  
  
## <a name="remarks"></a>備註  
 這個方法不是安全執行緒，以及您不應該使用它與其他執行個體同時<xref:System.Threading.Tasks.TaskScheduler>。 只在偵錯工具已暫止的其他所有執行緒時，請從 偵錯工具呼叫此方法。  
  
## <a name="see-also"></a>另請參閱  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)