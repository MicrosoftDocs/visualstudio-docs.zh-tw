---
title: GetScheduledTasksForDebugger 方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4ac6fa753be7672f1e698bda231bd11217c10d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152729"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger 方法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取所有排定工作的陣列。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>傳回值  
 所有排程工作的陣列。 每項工作正在執行，或已完成執行。  
  
## <a name="remarks"></a>備註  
 這個方法不是安全執行緒，並不應與其他執行個體同時<xref:System.Threading.Tasks.TaskScheduler>它時，應該呼叫從偵錯工具只偵錯工具已暫止所有其他執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)
