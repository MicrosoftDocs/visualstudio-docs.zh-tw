---
title: MSBuild 工作 | Microsoft Docs
ms.date: 07/30/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab54c5c523c833be60ef4b5d5088b6217a3111a5
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072576"
---
# <a name="msbuild-task"></a>MSBuild 工作

從另一個 MSBuild 專案生成 MSBuild 專案。

## <a name="parameters"></a>參數

 下表說明 `MSBuild` 工作的參數。

| 參數 | 描述 |
|-----------------------------------| - |
| `BuildInParallel` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，同時也會建置 `Projects` 參數中指定的專案 (如果可能)。 預設值為 `false`。 |
| `Projects` | 必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要建置的專案檔。 |
| `Properties` | 選擇性的 `String` 參數。<br /><br /> 作為全域屬性套用至子專案的屬性名稱/值組的分號分隔清單。 指定此參數時,它在功能上等效於使用[*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md)生成時具有 **-屬性**開關的設置屬性。 例如：<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> 當您通過`Properties`參數將屬性傳遞給專案時,MSBuild 可能會創建專案的新實例,即使專案檔已載入。 MSBuild 為給定的專案路徑和一組唯一的全域屬性創建單個專案實例。 例如，此行為可讓您建立多個呼叫 *myproject.proj* 的 MSBuild 工作，在 Configuration=Release 的情況下，您會獲得單一的 *myproject.proj* 執行個體 (如果工作中未指定任何唯一屬性)。 如果指定 MSBuild 尚未看到的屬性,MSBuild 將創建專案的新實例,該實例可以與專案的其他實例並行生成。 例如，Release 組態可以與 Debug 組態同時建置。|
| `RebaseOutputs` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，已建置的專案中目標輸出項目的相對路徑就會將其路徑調整為相對於呼叫的專案。 預設值為 `false`。 |
| `RemoveProperties` | 選擇性的 `String` 參數。<br /><br /> 指定要移除的全域屬性組。 |
| `RunEachTargetSeparately` | 選擇性的 `Boolean` 參數。<br /><br /> 如果`true`,MSBuild 任務將調用清單中每個目標一次傳遞給 MSBuild,而不是同時傳遞一個目標。 將此參數設定為 `true`，可保證即使先前叫用的目標失敗，還是會叫用後續的目標。 否則，建置錯誤便會停止叫用所有後續的目標。 預設值為 `false`。 |
| `SkipNonexistentProjects` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，將會略過不存在於磁碟上的專案檔。 否則，這類專案將會造成錯誤。 |
|`SkipNonexistentTargets`|選擇性的 `Boolean` 參數。<br /><br /> 如果`true`,將跳過存在但不包含命名的`Targets`專案 檔。 否則，這類專案將會造成錯誤。 在 MSBuild 15.5 中介紹。|
| `StopOnFirstFailure` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，則當其中一個專案無法建置時，將無法建置其他專案。 目前在 (使用多個處理器) 同時建置時不支援此功能。 |
| `TargetAndPropertyListSeparators` | 選擇性的 `String[]` 參數。<br /><br /> 指定目標和屬性的清單做為 `Project` 中繼資料。 處理之前將不會逸出分隔符號。 例如，%3B (逸出的 ';') 將會被視為是未逸出的 ';'。 |
| `TargetOutputs` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 傳回所有專案檔中建置目標的輸出。 只會傳回所指定目標的輸出，而非可能存在於這些目標所依存的任何輸出。<br /><br /> `TargetOutputs` 參數也會包含下列中繼資料：<br /><br /> -   `MSBuildSourceProjectFile`:包含設定輸出的目標的 MSBuild 專案檔。<br />-   `MSBuildSourceTargetName`：設定輸出的目標。 **注意︰** 如果您想要分別找出每個專案檔或目標的輸出，請針對每個專案檔或目標個別執行 `MSBuild` 工作。 如果您只執行 `MSBuild` 工作一次來建置所有專案檔，即會將所有目標的輸出收集到一個陣列。 |
| `Targets` | 選擇性的 `String` 參數。<br /><br /> 指定要在專案檔中建置的一或多個目標。 請使用分號分隔目標名稱清單。 如果未在 `MSBuild` 工作中指定目標，即會建置專案檔中指定的預設目標。 **注意︰** 目標必須存在於所有的專案檔中。 如果沒有，就會發生建置錯誤。 |
| `ToolsVersion` | 選擇性的 `String` 參數。<br /><br /> 指定要在將建置中專案傳遞給此工作時使用 `ToolsVersion`。<br /><br /> 使 MSBuild 任務能夠生成針對 .NET 框架的不同版本的專案,而不是專案中指定的版本。 有效值為 `2.0`、`3.0` 及 `3.5`。 預設值為 `3.5`。 |

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單,請參閱[工作延伸基項](../msbuild/taskextension-base-class.md)。

 與使用[Exec 工作](../msbuild/exec-task.md)啟動*MSBuild.exe*不同,此任務使用相同的 MSBuild 過程來生成子專案。 父組建和子組建之間能夠共用已經建置且可略過的目標清單。 此任務也更快,因為未創建新的 MSBuild 進程。

 此工作不只會處理專案檔，也會處理方案檔。

 MSBuild 使專案能夠同時生成所需的任何配置,即使配置涉及遠端基礎結構(例如,埠、協定、超時、重試等),也必須使用配置檔進行配置。 如果可能，應該能夠在 `MSBuild` 工作上指定組態項目做為工作參數。

 從 MSBuild 3.5 開始,解決方案專案現在顯示它構建的所有子專案中的目標輸出。

## <a name="pass-properties-to-projects"></a>將屬性傳遞至專案

 在 MSBuild 3.5 之前的 MSBuild 版本中,將不同的屬性集傳遞給 MSBuild 項中列出的不同專案具有挑戰性。 如果使用[MSBuild 工作的](../msbuild/msbuild-task.md)屬性,則其設置將應用於正在生成的所有專案,除非您批處理[了 MSBuild 任務](../msbuild/msbuild-task.md),並且有條件地為項清單中的每個專案提供了不同的屬性。

 但是,MSBuild 3.5 提供了兩個新的保留元數據項,屬性和附加屬性,它們為您提供了一種靈活的方式,用於使用[MSBuild 任務](../msbuild/msbuild-task.md)構建的不同項目傳遞不同的屬性。

> [!NOTE]
> 這些新中繼資料僅適用於[MSBuild 任務](../msbuild/msbuild-task.md)的專案屬性中傳遞的專案。

## <a name="multi-processor-build-benefits"></a>多處理器組建的優點

 使用這個新中繼資料主要優點之一是發生在您於多處理器系統上同時建置專案時。 中繼資料允許您將所有專案合併到單個[MSBuild 任務](../msbuild/msbuild-task.md)調用中,而無需執行任何批次處理或條件 MSBuild 任務。 當您只調用單個[MSBuild 任務](../msbuild/msbuild-task.md)時,專案屬性中列出的所有專案都將並行生成。 (但是,僅當`BuildInParallel=true`此屬性存在於[MSBuild 任務](../msbuild/msbuild-task.md)中時。有關詳細資訊,請參閱[並行產生多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。

## <a name="properties-metadata"></a>Properties 中繼資料

 當指定時，Properties 中繼資料會覆寫工作的 Properties 參數，而 [AdditionalProperties](#additionalproperties-metadata) 中繼資料則會附加至該參數的定義。

 常見方案是使用[MSBuild 任務](../msbuild/msbuild-task.md)構建多個解決方案檔,僅使用不同的生成配置。 您可能想要使用 Debug 組態來建置方案 a1，使用 Release 組態來建置方案 a2。 在 MSBuild 2.0 中,此專案檔如下所示:

> [!NOTE]
> 在下列範例中，"..." 代表其他方案檔。

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 但是,通過使用屬性元數據,可以簡化此項以使用單個[MSBuild 任務](../msbuild/msbuild-task.md),如下所示:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <Properties>Configuration=Debug</Properties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"/>
    </Target>
</Project>
```

 \- 或 -

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Debug"/>
    </Target>
</Project>
```

## <a name="additionalproperties-metadata"></a>AdditionalProperties 中繼資料

 請考慮以下方案,其中您將使用[MSBuild 任務](../msbuild/msbuild-task.md)構建兩個解決方案檔,這兩個解決方案檔都使用發佈配置,但一個使用 x86 體系結構,另一個使用 ia64 體系結構。 在 MSBuild 2.0 中,您需要創建[MSBuild 工作的](../msbuild/msbuild-task.md)多個實例:一個使用 x86 體系結構的發佈配置來構建專案,另一個使用帶有 ia64 體系結構的發佈配置。 您的專案檔看起來如下：

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 使用額外屬性中繼資料,可以使用以下功能簡化的資料以使用單個[MSBuild 工作](../msbuild/msbuild-task.md):

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <AdditionalProperties>Architecture=x86
              </AdditionalProperties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <AdditionalProperties>Architecture=ia64
              </AdditionalProperties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Release"/>
    </Target>
</Project>
```

## <a name="example"></a>範例

 下列範例會使用 `MSBuild` 工作來建置 `ProjectReferences` 項目集合所指定的專案。 所產生的目標輸出會儲存在 `AssembliesBuiltByChildProjects` 項目集合中。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ProjectReferences Include="*.*proj" />
    </ItemGroup>

    <Target Name="BuildOtherProjects">
        <MSBuild
            Projects="@(ProjectReferences)"
            Targets="Build">
            <Output
                TaskParameter="TargetOutputs"
                ItemName="AssembliesBuiltByChildProjects" />
        </MSBuild>
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
