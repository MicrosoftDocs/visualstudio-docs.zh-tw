---
title: GetTaskSchedulersForDebugger 方法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a2c657b7cef89871e17af442e41229c2fda0f4b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
擷取所有的陣列<xref:System.Threading.Tasks.TaskScheduler>目前使用中的物件。  
  
 **命名空間：**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
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
  
## <a name="see-also"></a>請參閱  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)