---
title: TASK_STATE_FAULTED 欄位 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1db50b1b3fa2ca33bd6ab97500a10a6ad48021bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135678"
---
# <a name="taskstatefaulted-field"></a>TASK_STATE_FAULTED 欄位
工作因未處理的例外狀況而完成。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## <a name="remarks"></a>備註  
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位包含此值，<xref:System.Threading.Tasks.Task.Status%2A>屬性會傳回<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。  
  
## <a name="see-also"></a>另請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)