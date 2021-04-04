---
title: 工作撰寫 | Microsoft Docs
description: 瞭解如何建立您自己的工作，以提供在 MSBuild 組建處理常式期間執行的程式碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0db9504404142e5bfdd17a66471820ddad790130
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214547"
---
# <a name="task-writing"></a>工作撰寫

提供在建置流程期間執行之程式碼的工作。 工作是包含在目標中。 MSBuild 包含一般工作的程式庫，您也可以建立自己的工作。 如需 MSBuild 隨附工作程式庫的詳細資訊，請參閱工作 [參考](../msbuild/msbuild-task-reference.md)。

## <a name="tasks"></a>工作

 工作的範例包括 [複製](../msbuild/copy-task.md)，這會複製一或多個檔案（ [MakeDir](../msbuild/makedir-task.md)），其中會建立目錄和 [Csc](../msbuild/csc-task.md)，以編譯 c # 原始程式碼檔。 每個工作都會實作為 .NET 類別，此類別會實作 <xref:Microsoft.Build.Framework.ITask> 介面，此介面定義於 *Microsoft.Build.Framework.dll* 組件中。

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

 如果您在工作類別上建立 .NET 屬性，則工作在執行時，也可以接收來自專案檔的輸入。 MSBuild 會在呼叫工作的方法之前立即設定這些屬性 `Execute` 。 若要建立字串屬性，請使用下列工作碼：

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

 如果專案即將執行工作，MSBuild 必須知道如何找出包含工作類別的元件。 工作是使用 [UsingTask 元素 (MSBuild) ](../msbuild/usingtask-element-msbuild.md)註冊。

 「MSBuild 檔案 *」是一個* 專案檔，其中包含 `UsingTask` 註冊 MSBuild 所提供之所有工作的元素清單。 組建每個專案時，都會自動包含此檔案。 如果在 *Microsoft* 中註冊的工作也會在目前的專案檔中註冊，則會優先使用目前的專案檔。也就是說，您可以使用具有相同名稱的工作來覆寫預設工作。

> [!TIP]
> 您可以藉由查看 *Microsoft* 的內容，查看 MSBuild 提供的工作清單。

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

## <a name="how-msbuild-invokes-a-task"></a>MSBuild 如何叫用工作

當叫用工作時，MSBuild 會先具現化工作類別，然後針對專案檔中的 task 專案所設定的工作參數，呼叫該物件的屬性 setter。 如果工作專案未指定參數，或在元素中指定的運算式評估為空字串，則不會呼叫屬性 setter。

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

只 `Input3` 會呼叫的 setter。

工作不應該相依于參數屬性 setter 調用的任何相對順序。

### <a name="task-parameter-types"></a>工作參數類型

MSBuild 會以原生方式處理型別 `string` 、和的屬性 `bool` `ITaskItem` `ITaskItem[]` 。 如果工作接受不同類型的參數，MSBuild 會叫 <xref:System.Convert.ChangeType%2A> 用以從 (轉換， `string` 並將所有屬性和專案參考展開) 至目的地類型。 如果任何輸入參數的轉換失敗，MSBuild 會發出錯誤，而且不會呼叫工作的 `Execute()` 方法。

## <a name="example-1"></a>範例 1

### <a name="description"></a>描述

下列 c # 類別示範衍生自 <xref:Microsoft.Build.Utilities.Task> helper 類別的工作。 此工作會傳回 `true`，指出是否成功。

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

## <a name="example-2"></a>範例 2

### <a name="description"></a>描述

下列 c # 類別示範執行介面的工作 <xref:Microsoft.Build.Framework.ITask> 。 此工作會傳回 `true`，指出是否成功。

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

## <a name="example-3"></a>範例 3

### <a name="description"></a>描述

這個 c # 類別會示範衍生自 <xref:Microsoft.Build.Utilities.Task> helper 類別的工作。 它具有必要的字串屬性，會引發所有已註冊記錄器顯示的事件。

### <a name="code"></a>程式碼

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs" id="Snippet1":::

## <a name="example-4"></a>範例 4

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

- [工作參考](../msbuild/msbuild-task-reference.md)
