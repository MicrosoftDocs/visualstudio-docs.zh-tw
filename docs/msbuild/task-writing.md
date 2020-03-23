---
title: 工作撰寫 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cbcf47ec83e1b900ba94ab3842c2cfa63fdcc5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631832"
---
# <a name="task-writing"></a>工作撰寫

提供在建置流程期間執行之程式碼的工作。 工作是包含在目標中。 MSBuild 包含典型任務庫，您還可以創建自己的任務。 有關 MSBuild 中包含的任務庫的詳細資訊，請參閱[任務引用](../msbuild/msbuild-task-reference.md)。

## <a name="tasks"></a>工作

 任務的示例包括複製一個或多個檔案複製的[Copy](../msbuild/copy-task.md)、創建目錄的[MakeDir](../msbuild/makedir-task.md)和編譯 C# 原始程式碼檔的[Csc](../msbuild/csc-task.md)。 每個工作都會實作為 .NET 類別，此類別會實作 <xref:Microsoft.Build.Framework.ITask> 介面，此介面定義於 *Microsoft.Build.Framework.dll* 組件中。

 實作工作時有兩種方法可供使用：

- 直接實作 <xref:Microsoft.Build.Framework.ITask> 介面。

- 從協助程式類別 <xref:Microsoft.Build.Utilities.Task> 衍生您的類別，此協助程式類別定義於 *Microsoft.Build.Utilities.dll* 組件中。 工作會實作 ITask 並提供部分 ITask 成員的預設實作。 此外，記錄會更容易。

這兩種情況都必須在您的類別中新增名為 `Execute` 的方法，這是工作執行時所呼叫的方法。 這個方法不採用任何參數，並會傳回 `Boolean` 值：如果工作成功為 `true`，如果失敗為 `false`。 下例示範的工作不執行任何動作，並會傳回 `true`。

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 下列專案檔會執行此工作：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 如果您在工作類別上建立 .NET 屬性，則工作在執行時，也可以接收來自專案檔的輸入。 MSBuild 在調用任務`Execute`的方法之前立即設置這些屬性。 若要建立字串屬性，請使用下列工作碼：

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 下列專案檔會執行此工作，並將 `MyProperty` 設定成指定值：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>註冊工作

 如果專案要運行任務，MSBuild 必須知道如何查找包含任務類的程式集。 使用[UsingTask 元素 （MSBuild）](../msbuild/usingtask-element-msbuild.md)註冊任務。

 MSBuild 檔*Microsoft.Common.Tasks*是一個專案檔案，其中包含註冊`UsingTask`MSBuild 提供的所有任務的元素清單。 組建每個專案時，都會自動包含此檔案。 如果在*Microsoft.Common.Tasks*中註冊的任務也在當前專案檔案中註冊，則當前專案檔案優先;也就是說，您可以使用具有相同名稱自己的任務來覆蓋預設任務。

> [!TIP]
> 通過查看*Microsoft.Common.Tasks*的內容，可以查看 MSBuild 附帶的任務的清單。

## <a name="raise-events-from-a-task"></a>從工作引發事件

 如果您的工作衍生自 <xref:Microsoft.Build.Utilities.Task> 協助程式類別，您可以對 <xref:Microsoft.Build.Utilities.Task> 類別使用下列任一 helper 方法，引發要被攔截且由任何已註冊記錄器顯示的事件：

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 如果您的工作直接實作 <xref:Microsoft.Build.Framework.ITask>，您仍會引發這類事件，但必須使用 IBuildEngine 介面。 下例示範的工作會實作 ITask 並引發自訂事件：

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>要求設定工作參數

 您可將某些工作屬性標記為「必要」，讓所有執行工作的專案檔都必須設定這些屬性值，否則組建會失敗。 在您的工作中將 `[Required]` 屬性套用至 .NET 屬性，如下所示：

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 <xref:Microsoft.Build.Framework.RequiredAttribute> 在 <xref:Microsoft.Build.Framework> 命名空間中定義 `[Required]` 屬性。

## <a name="how-msbuild-invokes-a-task"></a>MSBuild 如何調用任務

調用任務時，MSBuild 首先具現化任務類，然後調用該物件的屬性設置器，用於在專案檔案中的任務元素中設置的任務參數。 如果任務元素未指定參數，或者如果元素中指定的運算式計算為空字串，則不調用屬性 setter。

例如，在專案中

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

僅調用 的`Input3`setter。

任務不應依賴于參數屬性設置器調用的任何相對順序。

### <a name="task-parameter-types"></a>任務參數類型

MSBuild`string`本機處理 類型 的屬性`bool`， `ITaskItem` `ITaskItem[]`和 。 如果任務接受不同類型的參數，MSBuild 將調用<xref:System.Convert.ChangeType%2A>從`string`（擴展所有屬性和項引用）轉換為目標型別。 如果任何輸入參數的轉換失敗，MSBuild 會發出錯誤，並且不調用任務`Execute()`的方法。

## <a name="example"></a>範例

### <a name="description"></a>描述

以下 C# 類演示了從<xref:Microsoft.Build.Utilities.Task>説明器類派生的任務。 此工作會傳回 `true`，指出是否成功。

### <a name="code"></a>程式碼

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example"></a>範例

### <a name="description"></a>描述

以下 C# 類演示了實現介面<xref:Microsoft.Build.Framework.ITask>的任務。 此工作會傳回 `true`，指出是否成功。

### <a name="code"></a>程式碼

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example"></a>範例

### <a name="description"></a>描述

此 C# 類演示派生自<xref:Microsoft.Build.Utilities.Task>説明器類的任務。 它具有必要的字串屬性，會引發所有已註冊記錄器顯示的事件。

### <a name="code"></a>程式碼

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下例示範的專案檔會叫用前一個範例的工作：SimpleTask3。

### <a name="code"></a>程式碼

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)
