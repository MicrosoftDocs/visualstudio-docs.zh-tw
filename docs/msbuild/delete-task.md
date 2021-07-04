---
title: Delete 工作 | Microsoft Docs
description: 深入瞭解使用 MSBuild 刪除工作來刪除指定檔案的參數和考慮。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09945306a2260bed5b264d380dcea745ff3f7c07
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280422"
---
# <a name="delete-task"></a>Delete 工作

刪除指定的檔案。

## <a name="parameters"></a>參數

下表說明 `Delete` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`DeletedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定已成功刪除的檔案。|
|`Files`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要刪除的檔案。|
|`TreatErrorsAsWarnings`|選擇性的 `Boolean` 參數<br /><br /> 如果是 `true`，即會將錯誤記錄為警告。 預設值是 `false`。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

> [!WARNING]
> 當您在工作中使用萬用字元時，請務必小心 `Delete` 。 您可以使用或之類的運算式輕鬆地刪除錯誤的檔案， `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*` 尤其是當屬性評估為空字串時，此 `Files` 參數可以評估為磁片磁碟機的根目錄，並刪除超過您想要刪除的內容。

## <a name="example"></a>範例

下列範例會在您建立目標時刪除 *ConsoleApp1 檔案。* `DeleteDebugSymbolFile`

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

如果您需要追蹤已刪除的檔案，請 `TaskParameter` 使用專案名稱設定為，如下所示 `DeletedFiles` ：

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

您 `Delete` 可以建立要刪除的檔案， `ItemGroup` 並在上面執行工作，而不是直接在工作中使用萬用字元 `Delete` 。 但是，請務必 `ItemGroup` 小心地進行。 如果您在 `ItemGroup` 專案檔的最上層放置，它會在組建開始之前先評估，因此它不會包含組建程式中所建立的任何檔案。 因此，請將 `ItemGroup` 建立要在接近工作的目標中刪除之專案清單的 `Delete` 。 您也可以指定條件來檢查屬性不是空的，如此一來，就不會使用從磁片磁碟機根目錄開始的路徑建立專案清單。

工作 `Delete` 是用來刪除檔案。 如果您想要刪除目錄，請使用 [RemoveDir](removedir-task.md)。

此工作 `Delete` 不會提供刪除唯讀檔案的選項。 若要刪除唯讀檔案，您可以使用此工作 `Exec` 來執行 `del` 命令或對等專案，並提供可讓您刪除唯讀檔案的適當選項。 您必須注意輸入專案清單的長度，因為命令列上有長度限制，以及務必處理具有空格的檔案名，如此範例所示：

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

一般來說，在撰寫組建腳本時，請考慮您的刪除是否在邏輯上是作業的一部分 `Clean` 。 如果您需要將某些檔案設定為一般作業的一部分 `Clean` ，您可以將它們新增至 `@(FileWrites)` 清單，然後在下一步將其刪除 `Clean` 。 如果需要更多的自訂處理，請定義目標，並指定要執行它，方法是設定屬性 `BeforeTargets="Clean"` 或 `AfterTargets="Clean"` ，或是定義或目標的自訂版本 `BeforeClean` `AfterClean` 。 請參閱 [自訂您的組建](customize-your-build.md)。

## <a name="see-also"></a>另請參閱

- [RemoveDir 工作](removedir-task.md)
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
