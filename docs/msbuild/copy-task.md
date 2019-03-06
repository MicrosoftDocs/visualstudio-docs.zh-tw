---
title: Copy 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d996aa0c16c67cfdda23a1ecb63adcbb32d02b15
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596291"
---
# <a name="copy-task"></a>Copy 工作
將檔案複製到檔案系統上的新位置。

## <a name="parameters"></a>參數
下表說明 `Copy` 工作的參數。

|參數|說明|
|---------------|-----------------|
|`CopiedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已成功複製的項目。|
|`DestinationFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要將來源檔案複製到其中的檔案清單。 此清單與 `SourceFiles` 參數中指定的清單應該是一對一對應。 也就是，會將 `SourceFiles` 中指定的第一個檔案複製到 `DestinationFiles` 中指定的第一個位置，依此類推。|
|`DestinationFolder`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要將檔案複製至其中的目錄。 這必須是目錄，而非檔案。 如果目錄不存在，即會自動建立。|
|`OverwriteReadOnlyFiles`|選擇性的 `Boolean` 參數。<br /><br /> 即使已將檔案標示為唯讀檔案，還是會覆寫它們|
|`Retries`|選擇性的 `Int32` 參數。<br /><br /> 指定如果所有先前的嘗試均失敗，要嘗試複製多少次。 預設值為零。<br /><br /> **注意：** 使用重試，可以為建置流程中的同步處理問題設定遮罩。|
|`RetryDelayMilliseconds`|選擇性的 `Int32` 參數。<br /><br /> 指定任何必要重試之間的延遲。 預設值為 RetryDelayMillisecondsDefault 引數，其會傳遞至 CopyTask 建構函式。|
|`SkipUnchangedFiles`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會略過複製來源與目的地之間未變更的檔案。 如果檔案具有相同的大小和相同的上次修改時間，`Copy` 工作即會將檔案視為未變更。 <br /><br /> **注意：** 如果您將此參數設為 `true`，您應該在包含目標上使用相依性分析，因為只有在來源檔案的上次修改時間比目的地檔案的上次修改時間還新時，才會執行此工作。|
|`SourceFiles`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要複製的檔案。|
|`UseHardlinksIfPossible`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即會針對複製的檔案建立永久連結，而非複製檔案。|

## <a name="warnings"></a>警告
系統會記錄警告，包括：

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>備註
您必須指定 `DestinationFolder` 或 `DestinationFiles` 參數，但不能同時指定這兩者。 如果同時指定這兩者，工作即會失敗，並記錄錯誤。

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例
下列範例會將 `MySourceFiles` 項目集合中的項目複製到資料夾 *c:\MyProject\Destination*。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFolder="c:\MyProject\Destination"
        />
    </Target>

</Project>
```

## <a name="example"></a>範例
下列範例示範如何進行遞迴複製。 此專案會以遞迴方式將所有檔案從 *c:\MySourceTree* 中複製到 *c:\MyDestinationTree*，同時保有目錄結構。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
