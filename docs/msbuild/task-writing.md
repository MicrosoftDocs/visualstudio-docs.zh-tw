---
title: "工作撰寫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 建立工作"
  - "MSBuild, 寫入工作"
  - "工作, 為 MSBuild 建立"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 工作撰寫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

提供程式碼的工作，這些程式碼會在建置程序中執行。  工作包含在目標中。  常見工作的程式庫會隨 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供，您也可以自行建立工作。  如需隨 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供之工作程式庫的詳細資訊，請參閱 [Task Reference](../msbuild/msbuild-task-reference.md)。  
  
## 工作  
 工作的例子包括複製一個或多個檔案的 [Copy](../msbuild/copy-task.md)、建立目錄的 [MakeDir](../msbuild/makedir-task.md)，以及編譯 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 原始程式碼檔的 [Csc](../msbuild/csc-task.md)。  每一個工作都會實作為 .NET 類別，而這個類別再實作 Microsoft.Build.Framework.dll 組件中定義的 <xref:Microsoft.Build.Framework.ITask> 介面。  
  
 實作工作的方法有兩種：  
  
-   直接實作 <xref:Microsoft.Build.Framework.ITask> 介面。  
  
-   從 Helper 類別 <xref:Microsoft.Build.Utilities.Task> 衍生您的類別，該 Helper 類別是在 Microsoft.Build.Utilities.dll 組件中定義的。  工作會實作 ITask 並提供某些 ITask 成員的預設實作。  此外，記錄也較為容易。  
  
 在這兩種情況中，您都必須在類別中加入名為 `Execute` 的方法，這是在工作執行時呼叫的方法。  這個方法不會採用任何參數，但會傳回 `Boolean` 值：如果工作成功為 `true`，工作失敗則為 `false`。  在下列程式碼中，示範了不執行任何動作但會傳回 `true` 的工作。  
  
```  
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
  
 下列專案檔會執行這項工作：  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 如果您在工作類別上建立 .NET 屬性，則當工作執行時，也可以接收來自專案檔的輸入。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會先設定這些屬性，並緊接著呼叫工作的 `Execute` 方法。  若要建立字串屬性，請使用工作程式碼如下：  
  
```  
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
  
 下列專案檔會執行這項工作並將 `MyProperty` 設為指定的值：  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## 註冊工作  
 如果專案要執行工作，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 必須知道如何找到包含工作類別的組件。  工作是使用 [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md) 註冊的。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 檔案 Microsoft.Common.Tasks 是一個專案檔，其中包含 `UsingTask` 項目清單，負責註冊 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 隨附的所有工作。  每次建置專案時，就會自動加入這個檔案。  如果已在 Microsoft.Common.Tasks 中註冊的工作同時也在目前專案檔中註冊，則目前專案檔具有優先權，也就是說，您可以用自己擁有的同名工作覆寫預設工作。  
  
> [!TIP]
>  您可以檢視 Microsoft.Common.Tasks 的內容，查看 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 隨附的工作清單。  
  
## 從工作引發事件  
 如果工作是從 <xref:Microsoft.Build.Utilities.Task> Helper 類別衍生，則可使用 <xref:Microsoft.Build.Utilities.Task> 類別的下列任何 Helper 方法，來引發任何已註冊記錄器將攔截及顯示的事件：  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 如果您的工作直接實作 <xref:Microsoft.Build.Framework.ITask>，您仍可以引發這類事件，但必須使用 IBuildEngine 介面。  在下列程式碼中，示範了實作 ITask 並引發自訂事件的工作：  
  
```  
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
  
## 需要設定工作參數  
 您可以將特定工作屬性標記為「必要項」\(Required\)，如此任何執行工作的專案檔都必須設定這些屬性的值，否則建置會失敗。  請將 `[Required]` 屬性 \(Attribute\) 套用至工作中的 .NET 屬性 \(Property\)，如下所示：  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` 屬性是由 <xref:Microsoft.Build.Framework> 命名空間中的 <xref:Microsoft.Build.Framework.RequiredAttribute> 所定義。  
  
## 範例  
  
### 描述  
 下面這個 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別示範從 <xref:Microsoft.Build.Utilities.Task> Helper 類別衍生的工作。  這項工作會傳回 `true`，表示該工作成功。  
  
### 程式碼  
  
```  
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
  
## 範例  
  
### 描述  
 下面這個 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別示範實作 <xref:Microsoft.Build.Framework.ITask> 介面的工作。  這項工作會傳回 `true`，表示該工作成功。  
  
### 程式碼  
  
```  
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
  
## 範例  
  
### 描述  
 這個 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別示範從 <xref:Microsoft.Build.Utilities.Task> Helper 類別衍生的工作。  它擁有必要的字串屬性，而且會引發所有已註冊記錄器顯示的事件。  
  
### 程式碼  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## 範例  
  
### 描述  
 在下列程式碼中，示範了叫用上一個範例工作 SimpleTask3 的專案檔。  
  
### 程式碼  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)