---
title: TASK_STATE_RAN_TO_COMPLETION 欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f7d5f05a077e5243d5de52c210ae65dbfe3b2850
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428023"
---
# <a name="task_state_ran_to_completion-field"></a>TASK_STATE_RAN_TO_COMPLETION 欄位
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

工作已成功完成執行。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **元件：** mscorlib.dll) 中的 mscorlib (  
  
 因為您無法從 .NET Framework 存取此內部成員，所以會在) 的通用中繼語言中提供下列語法 (。  
  
## <a name="syntax"></a>語法  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## <a name="remarks"></a>備註  
 如果 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 欄位包含此值，則 <xref:System.Threading.Tasks.Task.Status%2A> 屬性會傳回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> 。  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
