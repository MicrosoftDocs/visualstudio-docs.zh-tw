---
title: TaskScheduler 類別-內部成員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427a84b3dcda0471f5ec9d71883a5a8e859bb92d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176692"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler 類別 - 內部成員
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題說明 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 可協助您執行自訂偵錯工具之類別的內部成員。 如需此類別的一般資訊，請參閱 <xref:System.Threading.Tasks.TaskScheduler> 參考主題。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **元件：** mscorlib.dll) 中的 mscorlib (  
  
 因為您無法從 .NET Framework 存取這些內部成員，所以會以一般中繼語言 () 的 CIL 來提供下列語法。  
  
## <a name="syntax"></a>語法  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|名稱|描述|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|捕獲所有排程工作的陣列。|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|抓取目前作用中之所有物件的陣列 <xref:System.Threading.Tasks.TaskScheduler> 。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [.NET Framework 適用的平行擴充內部資訊](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
