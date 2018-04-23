---
title: GetTaskSchedulersForDebugger 方法 |Microsoft 文件
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
ms.openlocfilehash: d5d0b78a4f115d1ba07848db914289c35034d465
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
擷取所有的陣列<xref:System.Threading.Tasks.TaskScheduler>目前使用中的物件。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>傳回值  
 所有陣列<xref:System.Threading.Tasks.TaskScheduler>且目前正在使用中的物件<xref:System.AppDomain>。  
  
## <a name="remarks"></a>備註  
 這個方法不是安全執行緒，並不應與其他執行個體同時使用<xref:System.Threading.Tasks.TaskScheduler>。 它應從呼叫偵錯工具只在偵錯工具已經暫停所有其他執行緒時。  
  
## <a name="see-also"></a>另請參閱  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)