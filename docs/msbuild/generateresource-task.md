---
title: GenerateResource 工作 | Microsoft Docs
description: 使用 MSBuild GenerateResource 工作在 .txt 或 .resx 檔和 common language runtime 二進位 .resources 檔案之間轉換。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 810cbd4987277416b5be545603908d9818bff890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914759"
---
# <a name="generateresource-task"></a>GenerateResource 工作

在 *.txt* 與 *.resx* (XML 資源格式) 檔案，以及 Common Language Runtime 二進位 *.resources* 檔案 (可以內嵌在執行階段二進位可執行檔，或是編譯到附屬組件中) 之間轉換。 此工作一般用來將 *.txt* 或 *.resx* 檔轉換為 *.resources* 檔。 `GenerateResource` 工作的功能類似於 [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)。

## <a name="parameters"></a>參數

下表說明 `GenerateResource` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`AdditionalInputs`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 包含此工作所執行相依性檢查的其他輸入。 例如，專案與目標檔案通常應為輸入，如有所更新時，就會重新產生所有資源。|
|`EnvironmentVariables`|選擇性的 `String[]` 參數。<br /><br /> 指定環境變數的名稱/值組陣列，這些變數應該傳遞至衍生的 *resgen.exe*，除了 (或選擇性地覆寫一般環境區塊) 。|
|`ExcludedInputPaths`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定項目陣列，這會指定要在最新狀態檢查期間忽略所追蹤輸入的路徑。|
|`ExecuteAsTool`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true` 為，則會從適當的目標 framework 跨進程執行 *tlbimp.exe* 和 *aximp.exe* ，以產生必要的包裝函式元件。 此參數允許多目標的 `ResolveComReferences`。|
|`FilesWritten`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含寫入至磁碟的所有檔案名稱。 這包括快取檔案 (如果有的話)。 此參數對於 Clean 的實作很有用。|
|`MinimalRebuildFromTracking`|選擇性的 `Boolean` 參數。<br /><br /> 取得或設定參數，指定是否將使用追蹤式累加建置。 如果為 `true`，會開啟累加建置，否則會強制重建。|
|`NeverLockTypeAssemblies`|選擇性的 `Boolean` 參數。<br /><br /> 取得或設定布林值，這個值會指定是否要建立新的 [appdomain](/dotnet/api/system.appdomain) 來評估資源 (*.resx*) 檔 (true) 或只有在資源檔參考使用者的元件 (false) 時，才建立新的 [appdomain](/dotnet/api/system.appdomain) 。|
|`OutputResources`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定所產生檔案 (例如 *.resources* 檔案) 的名稱。 如果您未指定名稱，則會使用相符輸入檔案的名稱，並將所建立的 *.resources* 檔案放在包含輸入檔的目錄中。|
|`PublicClass`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，會建立強型別資源類別做為公用類別。|
|`References`|選擇性的 `String[]` 參數。<br /><br /> 要從中載入 *.resx* 檔案類型的參考。 *.resx* 檔案資料元素可能具有 .net 類型。 當讀取 *.resx* 檔案時，必須加以解析。 一般而言，使用標準型別載入規則即可順利解析。 如果您提供 `References` 中的組件，則會優先使用它們。<br /><br /> 強型別資源不需要此參數。|
|`SdkToolsPath`|選擇性的 `String` 參數。<br /><br /> 指定 SDK 工具（例如 *resgen.exe*）的路徑。|
|`Sources`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要轉換的項目。 傳遞給此參數的項目必須具有下列其中一個副檔名︰<br /><br /> -   .txt︰指定文字檔的副檔名以進行轉換。 文字檔只能包含字串資源。<br />-   .resx︰指定 XML 資源檔的副檔名以進行轉換。<br />-   .restext︰指定和 *.txt* 相同的格式。 如果您想要清楚地區分包含資源的原始程式檔和建置流程中的其他原始程式檔，這個不同的副檔名會很有用。<br />-   .resources︰指定資源檔的副檔名以進行轉換。|
|`StateFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定選擇性快取檔案的路徑，這個檔案可用來加速 *.resx* 輸入檔中連結的相依性檢查。|
|`StronglyTypedClassName`|選擇性的 `String` 參數。<br /><br /> 指定強型別資源類別的類別名稱。 如果未指定此參數，則會使用資源檔的基底名稱。|
|`StronglyTypedFilename`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定原始程式檔的檔案名稱。 如果未指定此參數，則會使用類別名稱做為基底檔案名稱，副檔名則依語言而定。 例如：*MyClass.cs*。|
|`StronglyTypedLanguage`|選擇性的 `String` 參數。<br /><br /> 指定當產生強型別資源的類別來源時所使用的語言。 此參數必須完全符合 CodeDomProvider 所使用的其中一種語言。 例如：`VB` 或 `C#`。<br /><br /> 藉由將值傳遞給此參數，您可以指示工作產生強型別資源。|
|`StronglyTypedManifestPrefix`|選擇性的 `String` 參數。<br /><br /> 指定要在產生的強型別資源類別來源中使用的資源命名空間或資訊清單前置詞。|
|`StronglyTypedNamespace`|選擇性的 `String` 參數。<br /><br /> 指定要為強型別資源產生的類別來源使用的命名空間。 如果未指定此參數，任何強型別資源都位在全域命名空間中。|
|`TLogReadFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀參數。<br /><br /> 取得代表讀取追蹤記錄檔的項目陣列。|
|`TLogWriteFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀參數。<br /><br /> 取得代表寫入追蹤記錄檔的項目陣列。|
|`ToolArchitecture`|選擇性的 <xref:System.String?displayProperty=fullName> 參數。<br /><br /> 用來判斷 *Tracker.exe* 是否需要用來產生 *ResGen.exe*。<br /><br /> 應可剖析為 <xref:Microsoft.Build.Utilities.ExecutableType> 列舉的成員。 如果為 `String.Empty`，請使用啟發學習法以判斷預設架構。 應可剖析為 Microsoft.Build.Utilities.ExecutableType 列舉的成員。|
|`TrackerFrameworkPath`|選擇性的 `String` 參數。<br /><br /> 指定包含 *FileTracker.dll* 之適當 .NET Framework 位置的路徑。<br /><br /> 如果設定，使用者必須負責確定其所傳遞的 *FileTracker.dll* 位符合他們想要使用之 *ResGen.exe* 的位位數。 如果未設定，工作會根據目前的 .NET Framework 版本決定適當的位置。|
|`TrackerLogDirectory`|選擇性的 `String` 參數。<br /><br /> 指定要用於放置執行此工作產生之追蹤記錄檔的中繼目錄。|
|`TrackerSdkPath`|選擇性的 `String` 參數。<br /><br /> 指定包含 *Tracker.exe* 之適當 Windows SDK 位置的路徑。<br /><br /> 如果設定，使用者必須負責確定其所傳遞的 *Tracker.exe* 位符合他們想要使用之 *ResGen.exe* 的位位數。 如果未設定，工作會根據目前的 Windows SDK 決定適當的位置。|
|`TrackFileAccess`|選擇性的 <xref:System.Boolean> 參數。<br /><br /> 如果為 true，會使用輸入檔的目錄來解析相對檔案路徑。|
|`UseSourcePath`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，會使用輸入檔的目錄來解析相對檔案路徑。|

## <a name="remarks"></a>備註

因為 *.resx* 檔案可能包含連至其他資源檔的連結，所以光是比較 *.resx* 和 *.resources* 檔案的時間戳記並不足以看出輸出是否為最新。 相反地，`GenerateResource` 工作會追蹤 *.resx* 檔案中的連結，以及檢查所連結檔案的時間戳記。 這表示，您不應該只在包含 `GenerateResource` 工作的目標上使用 `Inputs` 與 `Outputs` 屬性，因為這可能會略過原本應該要執行的工作。

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

當使用 MSBuild 4.0 處理以 .NET 3.5 為目標的專案時，可能會因為 x86 資源而建置失敗。 若要解決這個問題，您可以將目標建置為 AnyCPU 組件。

## <a name="example"></a>範例

下列範例會使用 `GenerateResource` 工作從 `Resx` 項目集合指定的檔案來產生 *.resources* 檔案。

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

工作 `GenerateResource` \<LogicalName> 會使用專案的中繼資料 \<EmbeddedResource> 來命名內嵌在元件中的資源。

假設組件名稱為 myAssembly，下列程式碼會產生名為 *someQualifier.someResource.resources* 的內嵌資源︰

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

如果沒有 \<LogicalName> 中繼資料，資源將會命名為 *MyAssembly. myResource。*  此範例僅適用於 Visual Basic 和 Visual C# 建置流程。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
