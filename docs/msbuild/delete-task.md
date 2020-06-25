---
title: Delete 工作 | Microsoft Docs
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eddb9804378a4c32de9d1b68f952bc715f32ffd6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288906"
---
# <a name="delete-task"></a>Delete 工作

刪除指定的檔案。

## <a name="parameters"></a>參數

下表說明 `Delete` 工作的參數。

|參數|說明|
|---------------|-----------------|
|`DeletedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定已成功刪除的檔案。|
|`Files`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要刪除的檔案。|
|`TreatErrorsAsWarnings`|選擇性的 `Boolean` 參數<br /><br /> 如果是 `true`，即會將錯誤記錄為警告。 預設值是 `false`。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱[TaskExtension 基類](../msbuild/taskextension-base-class.md)。

> [!WARNING]
> 當您使用萬用字元搭配工作時，請務必小心 `Delete` 。 您可以使用或之類的運算式輕鬆地刪除錯誤的檔案 `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*` ，特別是當屬性評估為空字串時，在這種情況下， `Files` 參數可以評估為磁片磁碟機的根目錄，而且刪除的次數比您想要刪除的還要多。

## <a name="example"></a>範例

下列範例會在您建立目標時，刪除檔案*MyApp. pdb。* `DeleteDebugSymbolFile`

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

如果您需要追蹤已刪除的檔案，請將設定 `TaskParameter` 為， `DeletedFiles` 並使用專案名稱，如下所示：

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

`Delete`請建立檔案 `ItemGroup` 的以刪除並執行該工作，而不是直接在工作中使用萬用字元 `Delete` 。 但是，請務必 `ItemGroup` 小心地放置。 如果您將放在 `ItemGroup` 專案檔的最上層，在組建開始之前，它會及早評估，因此不會包含任何在組建程式中建立的檔案。 因此，請在 `ItemGroup` 靠近工作的目標中，放入建立要刪除之專案清單的 `Delete` 。 您也可以指定條件來檢查屬性是否不是空的，這樣您就不會建立具有從磁片磁碟機根目錄開始之路徑的專案清單。

此工作適用 `Delete` 于刪除檔案。 如果您想要刪除目錄，請使用[RemoveDir](removedir-task.md)。

工作 `Delete` 不會提供刪除唯讀檔案的選項。 若要刪除唯讀檔案，您可以使用工作 `Exec` 來執行 `del` 命令或對等的，並使用適當的選項來啟用刪除唯讀檔案。 您必須注意輸入專案清單的長度，因為命令列上有長度限制，也請務必處理具有空格的檔案名，如下列範例所示：

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

一般來說，在撰寫組建腳本時，請考慮您的刪除是否為作業的邏輯部分 `Clean` 。 如果您需要設定一些要在正常作業中清除的檔案 `Clean` ，您可以將它們新增到清單中， `@(FileWrites)` 然後在下一步將它們刪除 `Clean` 。 如果需要更多自訂處理，請定義一個目標，並藉由設定屬性 `BeforeTargets="Clean"` 或 `AfterTargets="Clean"` ，或定義或目標的自訂版本來指定它要執行 `BeforeClean` `AfterClean` 。 請參閱[自訂您的組建](customize-your-build.md)。

## <a name="see-also"></a>另請參閱

- [RemoveDir 工作](removedir-task.md)
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
