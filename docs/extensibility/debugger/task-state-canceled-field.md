---
title: TASK_STATE_CANCELED 欄位 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e5196b7a5b137e648c5ef35fa3f3bf13885b5e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="taskstatecanceled-field"></a>TASK_STATE_CANCELED 欄位
它已達到執行狀態，或確認其取消動作，並完成而沒有例外狀況之前，已取消工作。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## <a name="remarks"></a>備註  
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位包含此值，<xref:System.Threading.Tasks.Task.Status%2A>屬性會傳回<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。  
  
## <a name="see-also"></a>另請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)