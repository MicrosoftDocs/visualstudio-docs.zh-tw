---
title: 任務類 - 內部成員 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712740"
---
# <a name="task-class---internal-members"></a>工作類別 ─ 內部成員
本文介紹了説明您實現自定義調試器的<xref:System.Threading.Tasks.Task?displayProperty=fullName>類的內部成員。 有關此類的一般資訊,<xref:System.Threading.Tasks.Task>請參閱參考文章。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問這些內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
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
|[SetNotificationForWaitCompletion 方法](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|設置或清除TASK_STATE_WAIT_COMPLETION_NOTIFICATION狀態位。|
|[NotifyDebuggerOfWaitCompletion 方法](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|占位符方法用作調試器的斷點目標。|

### <a name="fields"></a>欄位

|名稱|描述|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|表示要在物件中執行的代碼的<xref:System.Threading.Tasks.Task>委託。|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|存儲<xref:System.Threading.Tasks.Task>物件的其他屬性。|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|父屬性的<xref:System.Threading.Tasks.Task?displayProperty=fullName>備份欄位。|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|存儲有關<xref:System.Threading.Tasks.Task>物件當前狀態的資訊。|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|表示操作將使用的數據的物件。|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|屬性的<xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>後備欄位。|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|物件的下一個<xref:System.Threading.Tasks.Task>可用標識符。|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|指示任務在到達運行狀態之前已取消,或者任務確認其取消並無異常地完成。|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|指示任務正在運行。|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|指示任務由於未處理的異常而已完成。|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|指示任務成功完成執行。|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|指示任務已完成執行其委託,並隱式等待附加的子任務完成。|

## <a name="remarks"></a>備註
 以下內部方法對除錯器引擎很有用,因為它們標記了代碼執行的入口<xref:System.Threading.Tasks.Task>:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [.NET 框架的並行擴展內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
