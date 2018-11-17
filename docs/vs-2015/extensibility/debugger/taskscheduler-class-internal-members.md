---
title: TaskScheduler 類別-內部成員 |Microsoft Docs
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
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a0f1306463abc9b8f025453f8b259014ba5de10
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774896"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler 類別 - 內部成員
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題描述的內部成員<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>類別可協助您實作自訂的偵錯工具。 如需此類別的一般資訊，請參閱<xref:System.Threading.Tasks.TaskScheduler>參考主題。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|名稱|描述|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|擷取所有排定工作的陣列。|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|擷取的所有陣列<xref:System.Threading.Tasks.TaskScheduler>目前使用中的物件。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [.NET Framework 適用的平行擴充內部資訊](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

