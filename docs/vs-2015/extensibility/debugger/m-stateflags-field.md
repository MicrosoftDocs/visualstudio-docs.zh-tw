---
title: m_stateFlags 欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ccf20ae5d3f009533f2000bc20ccdc347ef4015
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941107"
---
# <a name="mstateflags-field"></a>m_stateFlags 欄位
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

儲存的目前狀態的相關資訊<xref:System.Threading.Tasks.Task>物件。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## <a name="remarks"></a>備註  
 您通常會使用<xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName>屬性來存取這個值。  
  
 這個成員可以是下列值的任何組合：  
  
-   [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
