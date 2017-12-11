---
title: "工作撰寫 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: "19"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 0e71fcf69e5624e46261d49ebccc8c634492763a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="task-writing"></a>工作撰寫
提供在建置流程期間執行之程式碼的工作。 工作是包含在目標中。 一般工作程式庫會隨附於[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]，您也可以建立自己的工作。 如需隨附於 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的工作程式庫詳細資訊，請參閱[工作參考](../msbuild/msbuild-task-reference.md)。  
  
## <a name="tasks"></a>工作  
 工作範例包括複製一或多個檔案的 [Copy](../msbuild/copy-task.md)、建立目錄的 [MakeDir](../msbuild/makedir-task.md)，以及編譯 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 原始程式碼檔的 [Csc](../msbuild/csc-task.md)。 每項工作都會實作為 .NET 類別，此類別會實作 <xref:Microsoft.Build.Framework.ITask> 介面，此介面定義於 Microsoft.Build.Framework.dll 組件中。  
  
 實作工作時有兩種方法可供使用：  
  
-   直接實作 <xref:Microsoft.Build.Framework.ITask> 介面。  
  
-   從協助程式類別 <xref:Microsoft.Build.Utilities.Task> 衍生您的類別，此協助程式類別定義於 Microsoft.Build.Utilities.dll 組件中。 工作會實作 ITask 並提供部分 ITask 成員的預設實作。 此外，記錄會更容易。  
  
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
  
 如果您在工作類別上建立 .NET 屬性，則工作在執行時，也可以接收來自專案檔的輸入。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會先立即設定這些屬性，再呼叫工作的 `Execute` 方法。 若要建立字串屬性，請使用下列工作碼：  
  
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
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
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
  
## <a name="registering-tasks"></a>註冊工作  
 如果專案即將執行工作，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 必須知道如何找出包含工作類別的組件。 工作是使用 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md) 註冊。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 檔案 Microsoft.Common.Tasks 是專案檔案，包含 `UsingTask` 元素清單，這些元素會註冊所有隨附於 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的工作。 組建每個專案時，都會自動包含此檔案。 如果在 Microsoft.Common.Tasks 中註冊的工作也在目前的專案檔中註冊，則目前的專案檔有優先順序，亦即您可以使用自己的同名工作覆寫預設工作。  
  
> [!TIP]
>  檢視 Microsoft.Common.Tasks 的內容即可以查看 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所附的工作清單。  
  
## <a name="raising-events-from-a-task"></a>從工作引發事件  
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
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
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
  
## <a name="requiring-task-parameters-to-be-set"></a>需要設定工作參數  
 您可將某些工作屬性標記為「必要」，讓所有執行工作的專案檔都必須設定這些屬性值，否則組建會失敗。 在您的工作中將 `[Required]` 屬性套用至 .NET 屬性，如下所示：  
  
```csharp
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 <xref:Microsoft.Build.Framework.RequiredAttribute> 在 <xref:Microsoft.Build.Framework> 命名空間中定義 `[Required]` 屬性。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 以下 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別會示範衍生自 <xref:Microsoft.Build.Utilities.Task> 協助程式類別的工作。 此工作會傳回 `true`，指出是否成功。  
  
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
 以下 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別會示範實作 <xref:Microsoft.Build.Framework.ITask> 介面的工作。 此工作會傳回 `true`，指出是否成功。  
  
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
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
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
 此 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別會示範衍生自 <xref:Microsoft.Build.Utilities.Task> 協助程式類別的工作。 它具有必要的字串屬性，會引發所有已註冊記錄器顯示的事件。  
  
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
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)