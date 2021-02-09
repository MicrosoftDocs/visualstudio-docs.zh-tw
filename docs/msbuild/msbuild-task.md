---
title: MSBuild 工作 | Microsoft Docs
description: 瞭解 MSBuild 工作如何使用相同的 MSBuild 進程來建立另一個 MSBuild 專案的子專案。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8241188b484447f94c60aa0e0c9bf05e477dd39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878275"
---
# <a name="msbuild-task"></a>MSBuild 工作

從另一個 MSBuild 專案建立 MSBuild 專案。

## <a name="parameters"></a>參數

 下表說明 `MSBuild` 工作的參數。

| 參數 | Description |
|-----------------------------------| - |
| `BuildInParallel` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，同時也會建置 `Projects` 參數中指定的專案 (如果可能)。 預設為 `false`。 |
| `Projects` | 必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要建置的專案檔。 |
| `Properties` | 選擇性的 `String` 參數。<br /><br /> 作為全域屬性套用至子專案的屬性名稱/值組的分號分隔清單。 當您指定這個參數時，它在功能上相當於使用 [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md)建立時，設定具有 **-property** 參數的屬性。 例如：<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> 當您透過參數將屬性傳遞至專案時 `Properties` ，MSBuild 可能會建立專案的新實例，即使已經載入專案檔也一樣。 MSBuild 會為指定的專案路徑和一組唯一的全域屬性建立單一專案實例。 例如，此行為可讓您建立多個呼叫 *myproject.proj* 的 MSBuild 工作，在 Configuration=Release 的情況下，您會獲得單一的 *myproject.proj* 執行個體 (如果工作中未指定任何唯一屬性)。 如果您指定 MSBuild 尚未看見的屬性，MSBuild 會建立專案的新實例，該實例可以平行內建至專案的其他實例。 例如，Release 組態可以與 Debug 組態同時建置。|
| `RebaseOutputs` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，已建置的專案中目標輸出項目的相對路徑就會將其路徑調整為相對於呼叫的專案。 預設為 `false`。 |
| `RemoveProperties` | 選擇性的 `String` 參數。<br /><br /> 指定要移除的全域屬性組。 |
| `RunEachTargetSeparately` | 選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true` ，則 MSBuild 工作會一次叫用一次傳遞至 MSBuild 的清單中的每個目標，而不是同時叫用。 將此參數設定為 `true`，可保證即使先前叫用的目標失敗，還是會叫用後續的目標。 否則，建置錯誤便會停止叫用所有後續的目標。 預設為 `false`。 |
| `SkipNonexistentProjects` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，將會略過不存在於磁碟上的專案檔。 否則，這類專案將會造成錯誤。 |
|`SkipNonexistentTargets`|選擇性的 `Boolean` 參數。<br /><br /> 如果為，則會 `true` 略過存在但未包含命名的專案檔 `Targets` 。 否則，這類專案將會造成錯誤。 在 MSBuild 15.5 中引進。|
| `StopOnFirstFailure` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，則當其中一個專案無法建置時，將無法建置其他專案。 目前在 (使用多個處理器) 同時建置時不支援此功能。 |
| `TargetAndPropertyListSeparators` | 選擇性的 `String[]` 參數。<br /><br /> 指定目標和屬性的清單做為 `Project` 中繼資料。 處理之前將不會逸出分隔符號。 例如，%3B (逸出的 ';') 將會被視為是未逸出的 ';'。 |
| `TargetOutputs` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 傳回所有專案檔中建置目標的輸出。 只會傳回所指定目標的輸出，而非可能存在於這些目標所依存的任何輸出。<br /><br /> `TargetOutputs` 參數也會包含下列中繼資料：<br /><br /> -   `MSBuildSourceProjectFile`： MSBuild 專案檔，包含設定輸出的目標。<br />-   `MSBuildSourceTargetName`：設定輸出的目標。 **注意︰** 如果您想要分別找出每個專案檔或目標的輸出，請針對每個專案檔或目標個別執行 `MSBuild` 工作。 如果您只執行 `MSBuild` 工作一次來建置所有專案檔，即會將所有目標的輸出收集到一個陣列。 |
| `Targets` | 選擇性的 `String` 參數。<br /><br /> 指定要在專案檔中建置的一或多個目標。 請使用分號分隔目標名稱清單。 如果未在 `MSBuild` 工作中指定目標，即會建置專案檔中指定的預設目標。 **注意︰** 目標必須存在於所有的專案檔中。 如果沒有，就會發生建置錯誤。 |
| `ToolsVersion` | 選擇性的 `String` 參數。<br /><br /> 指定要在將建置中專案傳遞給此工作時使用 `ToolsVersion`。<br /><br /> 讓 MSBuild 工作建立專案，該專案的目標版本與專案中所指定的版本不同 .NET Framework。 有效值為 `2.0`、`3.0` 及 `3.5`。 預設值為 `3.5`。 |

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

 不同于使用 [Exec](../msbuild/exec-task.md) 工作來開始 *MSBuild.exe*，此工作會使用相同的 MSBuild 進程來建立子專案。 父組建和子組建之間能夠共用已經建置且可略過的目標清單。 這項工作也會更快，因為不會建立新的 MSBuild 進程。

 此工作不只會處理專案檔，也會處理方案檔。

 MSBuild 所需的任何設定，即使設定牽涉到遠端基礎結構 (例如埠、通訊協定、超時、重試等) ，也必須使用設定檔來設定為可設定的。 如果可能，應該能夠在 `MSBuild` 工作上指定組態項目做為工作參數。

 從 MSBuild 3.5 開始，方案專案現在會從它所建立的所有子專案中呈現 TargetOutputs。

## <a name="pass-properties-to-projects"></a>將屬性傳遞至專案

 在 msbuild 3.5 之前的 MSBuild 版本中，將不同的屬性集傳遞給 MSBuild 專案中所列的不同專案是一項挑戰。 如果您使用 [msbuild](../msbuild/msbuild-task.md)工作的 Properties 屬性，則它的設定會套用至所有正在建立的專案，除非您批次處理 [MSBuild](../msbuild/msbuild-task.md) 工作，並且有條件地針對專案清單中的每個專案提供不同的屬性。

 不過，MSBuild 3.5 提供兩個新的保留中繼資料專案：屬性和 AdditionalProperties，可讓您以彈性的方式，為使用 [MSBuild](../msbuild/msbuild-task.md)工作建立的不同專案傳遞不同的屬性。

> [!NOTE]
> 這些新的中繼資料專案僅適用于 [MSBuild](../msbuild/msbuild-task.md)工作的 Projects 屬性中所傳遞的專案。

## <a name="multi-processor-build-benefits"></a>多處理器組建的優點

 使用這個新中繼資料主要優點之一是發生在您於多處理器系統上同時建置專案時。 中繼資料可讓您將所有專案合併成單一 [MSBuild](../msbuild/msbuild-task.md) 工作呼叫，而不需要執行任何批次處理或條件式 MSBuild 工作。 而且當您只呼叫單一 [MSBuild](../msbuild/msbuild-task.md)工作時，[專案] 屬性中列出的所有專案都會以平行方式建立。 不過，只有在 `BuildInParallel=true` [MSBuild](../msbuild/msbuild-task.md)工作中有屬性時，才 (。 ) 如需詳細資訊，請參閱 [平行建立多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。

## <a name="properties-metadata"></a>Properties 中繼資料

 當指定時，Properties 中繼資料會覆寫工作的 Properties 參數，而 [AdditionalProperties](#additionalproperties-metadata) 中繼資料則會附加至該參數的定義。

 常見的案例是使用 [MSBuild](../msbuild/msbuild-task.md)工作建立多個方案檔時，只使用不同的組建設定。 您可能想要使用 Debug 組態來建置方案 a1，使用 Release 組態來建置方案 a2。 在 MSBuild 2.0 中，此專案檔看起來如下所示：

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

 不過，藉由使用屬性中繼資料，您可以簡化此動作以使用單一 [MSBuild](../msbuild/msbuild-task.md)工作，如下所示：

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

 請考慮下列案例：您使用 [MSBuild](../msbuild/msbuild-task.md)工作來建立兩個方案檔（兩者都使用發行設定），但使用的是使用 x86 架構，而另一個使用 ia64 架構。 在 MSBuild 2.0 中，您需要建立 [msbuild](../msbuild/msbuild-task.md)工作的多個實例：一個用來以 x86 架構的發行設定來建立專案，另一個則使用具有 ia64 架構的發行設定。 您的專案檔看起來如下：

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

 藉由使用 AdditionalProperties 中繼資料，您可以使用下列方法來簡化此動作以使用單一 [MSBuild](../msbuild/msbuild-task.md) 工作：

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
