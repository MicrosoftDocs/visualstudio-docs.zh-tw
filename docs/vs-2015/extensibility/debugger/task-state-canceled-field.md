---
title: TASK_STATE_CANCELED 欄位 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9dccdeb9ebec3ce99557cb554ae3f19be3a7d12
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730931"
---
# <a name="taskstatecanceled-field"></a>TASK_STATE_CANCELED 欄位
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

已達到執行中狀態，或認可其取消作業，然後完成而沒有例外狀況前，已取消工作。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## <a name="remarks"></a>備註  
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位會包含此值，請<xref:System.Threading.Tasks.Task.Status%2A>屬性會傳回<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)

