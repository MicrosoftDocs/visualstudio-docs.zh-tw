---
title: GetTaskSchedulersForDebugger 方法 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d2bc798575cafbeb04837c3065d69b76ee872df
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490286"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[GetTaskSchedulersForDebugger 方法](https://docs.microsoft.com/visualstudio/extensibility/debugger/gettaskschedulersfordebugger-method)。  
  
擷取的所有陣列<xref:System.Threading.Tasks.TaskScheduler>目前使用中的物件。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>傳回值  
 所有陣列<xref:System.Threading.Tasks.TaskScheduler>且目前正在使用中的物件<xref:System.AppDomain>。  
  
## <a name="remarks"></a>備註  
 這個方法不是安全執行緒，並不應與其他執行個體同時<xref:System.Threading.Tasks.TaskScheduler>。 它應該呼叫偵錯工具中，只在偵錯工具已暫止的其他所有執行緒時。  
  
## <a name="see-also"></a>另請參閱  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)

