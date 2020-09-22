---
title: Task 類別-內部成員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef0cd907c25a90ee90e3ed23a773d0ae8ba0ce1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838854"
---
# <a name="task-class---internal-members"></a>工作類別 - 內部成員
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題說明 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 可協助您執行自訂偵錯工具之類別的內部成員。 如需此類別的一般資訊，請參閱 <xref:System.Threading.Tasks.Task> 參考主題。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **元件：** mscorlib.dll) 中的 mscorlib (  
  
 因為您無法從 .NET Framework 存取這些內部成員，所以會以一般中繼語言 () 的 CIL 來提供下列語法。  
  
## <a name="syntax"></a>語法  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|名稱|描述|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion 方法](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|設定或清除 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 狀態位。|  
|[NotifyDebuggerOfWaitCompletion 方法](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|偵錯工具用來當做中斷點目標的預留位置方法。|  
  
### <a name="fields"></a>欄位  
  
|名稱|描述|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|表示要在物件中執行之程式碼的委派 <xref:System.Threading.Tasks.Task> 。|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|儲存物件的其他屬性 <xref:System.Threading.Tasks.Task> 。|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|父屬性的支援欄位 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 。|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|儲存物件目前狀態的相關資訊 <xref:System.Threading.Tasks.Task> 。|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|物件，表示動作將使用的資料。|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|屬性的支援欄位 <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> 。|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|物件的下一個可用識別碼 <xref:System.Threading.Tasks.Task> 。|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|指出工作在達到執行狀態之前已取消，或工作已確認其取消並完成，而沒有例外狀況。|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|指出工作正在執行。|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|指出工作因為未處理的例外狀況而完成。|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|表示工作已順利完成執行。|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|表示工作已完成執行它的委派，並隱含地等候附加的子工作完成。|  
  
## <a name="remarks"></a>備註  
 下列內部方法適用于偵錯工具引擎，因為它們會將進入程式 <xref:System.Threading.Tasks.Task> 代碼執行標記：  
  
- `Execute`  
  
- `ExecuteEntry`  
  
- `ExecuteWithThreadLocal`  
  
- `Finish`  
  
- `InnerInvoke`  
  
- `InternalWait`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework 適用的平行擴充內部資訊](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
