---
title: ResolveAssemblyReference 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 ResolveAssemblyReference 工作，判斷相依于指定元件的所有元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveAssemblyReference
- MSBuild.ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects
- MSBuild.ResolveAssemblyReference.FoundConflict
- MSBuild.ResolveAssemblyRedirects.SuggestedRedirects
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveAssemblyReference task [MSBuild]
- MSBuild, ResolveAssemblyReference task
ms.assetid: 4d56d848-b29b-4dff-86a2-0a96c9e4a170
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9209fcffed9a15ce51e1aa079bd3efd5ff0bb384
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912649"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference 工作

判斷相依於指定組件的所有組件 (包含第二階與第 `n` 階的相依)。

## <a name="parameters"></a>參數

 下表說明 `ResolveAssemblyReference` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|選擇性的 `String[]` 參數。<br /><br /> 在解析參考時所使用的組件副檔名。 預設副檔名為 *.exe* 和 *.dll*。|
|`AllowedRelatedFileExtensions`|選擇性的 `String[]` 參數。<br /><br /> 搜尋彼此相關檔案時所使用的副檔名。 預設副檔名為 *.pdb* 和 *.xml*。|
|`AppConfigFile`|選擇性的 `String` 參數。<br /><br /> 指定要從中剖析和擷取 bindingRedirect 對應的 *app.config* 檔案。 若指定此參數， `AutoUnify` 參數必須是 `false`。|
|`Assemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定完整路徑和相依性必須受到識別的項目。 這些項目可以具有像是 "System" 的簡單名稱，或是類似 "System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" 的強式名稱。<br /><br /> 傳遞至這個參數的項目可以選擇性地擁有下列項目中繼資料：<br /><br /> -   `Private`： `Boolean` 值。 如果為 `true`，則在本機複製項目。 預設值是 `true`。<br />-   `HintPath`： `String` 值。 指定要作為參考的路徑和檔案名稱。 當在 `SearchPaths` 參數中指定 {HintPathFromItem} 時，就會使用此中繼資料。 預設值為空字串。<br />-   `SpecificVersion`： `Boolean` 值。 如果為 `true`，則在 `Include` 屬性中指定的確切名稱必須相符合。 如果為 `false`，則具有相同簡單名稱的任何組件都適用。 若未指定 `SpecificVersion` ，則工作會檢視項目 `Include` 屬性中的值。 若屬性是簡單名稱，則其行為會如同 `SpecificVersion` 為 `false`。 若屬性是強式名稱，則其行為會如同 `SpecificVersion` 為 `true`。<br />     搭配參考項目類型使用時， `Include` 屬性必須是組件的完整融合名稱才能受解析。 只有在融合完全符合 `Include` 屬性時，才會解析組件。<br />     當專案以 .NET Framework 版本作為目標，並以針對較高的 .NET Framework 版本所編譯的組件時作為參考時，只有將 `SpecificVersion` 設定為 `true`。<br />     當專案以設定檔作為目標，且以不在設定檔中的組件作為參考時，只有將 `SpecificVersion` 設定為 `true`。<br />-   `ExecutableExtension`： `String` 值。 如果有，則所解析的組件必須具有這個副檔名。 如果沒有，就會針對每個檢查過的目錄，將 *.dll* 視為第一個要採用的副檔名，接著是 *.exe*。<br />-   `SubType`： `String` 值。 只有含有空白 SubType 中繼資料的項目才會解析成完整的組件路徑。 含有非空白 SubType 中繼資料的項目都會被忽略。<br />-   `AssemblyFolderKey`： `String` 值。 舊版用途支援此中繼資料。 它會指定使用者定義的登錄機碼（例如 **hklm \\ \<VendorFolder>**），以便 `Assemblies` 用來解析元件參考。|
|`AssemblyFiles`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要尋找相依性的完整組件清單。<br /><br /> 傳遞至這個參數的項目可以選擇性地擁有下列項目中繼資料：<br /><br /> -   `Private`：選擇性的 `Boolean` 值。 如果為 true，則在本機複製項目。<br />-   `FusionName`：選擇性的 `String` 中繼資料。 指定此項目的簡單或強式名稱。 若此屬性存在，便可以節省時間，原因是不需要開啟組件檔案就能取得名稱。|
|`AutoUnify`|選擇性的 `Boolean` 參數。<br /><br /> 此參數會用於建置不能有一般 *App.Config* 檔案的組件，例如 DLL。<br /><br /> 當為 `true` 時，會自動將產生的相依性圖形視為有 *App.Config* 檔案傳遞至 AppConfigFile 參數。 此虛擬 *App.Config* 檔案的每個衝突元件集合都有 bindingRedirect 專案，因此會選擇最高版本的元件。 因此，將不會出現有關衝突組件的警告，因為每個衝突都已經獲得解決。<br /><br /> 如果為 `true`，每個不同的重新對應都將致使高優先權註解顯示新舊版本，且 `AutoUnify` 為 `true`。<br /><br /> 當為 `true` 時，則 AppConfigFile 參數必須為空白。<br /><br /> 如果為 `false`，則不會自動發生組件版本重新對應。 當有兩個版本的組件時，會發出警告。<br /><br /> 如果為 `false`，不同版本相同組件間的每個衝突都會致使高優先順序的註解。 這些註解後面都會接著單一警告。 此警告具有唯一的錯誤碼，且包含以下文字「找到不同版本的參考和相依組件之間的衝突」。<br /><br /> 預設值是 `false`。|
|`CandidateAssemblyFiles`|選擇性的 `String[]` 參數。<br /><br /> 指定要用於搜尋和解析處理序的組件清單。 傳遞至此參數的值必須是絕對檔案名稱或專案相關的檔案名稱。<br /><br /> 當 `SearchPaths` 參數將 {CandidateAssemblyFiles} 包含作為要考量的其中一個路徑時，就會考慮這個清單中的組件。|
|`CopyLocalDependenciesWhenParentReferenceInGac`|選擇性的 <xref:System.Boolean> 參數。<br /><br /> 如果為 true，表示要判斷是否應該在本機複製相依性，其中一項完成的檢查就是確認專案檔中的父參考是否已設定 Private 中繼資料。 若已設定，則會使用 Private  值做為相依性。<br /><br /> 若未設定中繼資料，則相依性會接受和父代參考相同的檢查。 其中一個檢查是為了查看參考是否在 GAC 中。 若參考在 GAC 中，則會假設其在目標電腦上的 GAC 中，因此不會在本機複製。 這只會套用於特定的參考，且不會套用於其相依性。<br /><br /> 例如，GAC 中專案檔的參考不會在本機複製，但其相依性因為不在 GAC 中所以會在本機複製。<br /><br /> 如果為 false，會檢查專案檔案的參考，以查看其是否在 GAC 中，且會視需要在本機複製。<br /><br /> 相依性會經過檢查以確認其是否位在 GAC 中，並確認專案檔中的父參考是否也位在 GAC 中。<br /><br /> 若來自專案檔案的父代參考在 GAC 中，就不會在本機複製相依性。<br /><br /> 不論此參數為 true 或 false，若有多個父代參考，且其中任何一個不在 GAC 中，則會在本機複製全部的父代參考。|
|`CopyLocalFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 傳回 `ResolvedFiles`、 `ResolvedDependencyFiles`、 `RelatedFiles`、 `SatelliteFiles`及 `ScatterFiles` 參數中的每個檔案，這些檔案具有值為 `CopyLocal` true `true`。|
|`FilesWritten`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含寫入磁碟的項目。|
|`FindDependencies`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，會找到相依性。 否則，只會找到主要參考。 預設值是 `true`。|
|`FindRelatedFiles`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true` 為，則會找到 *.pdb* 檔案和 *xml* 檔案等相關檔案。 預設值是 `true`。|
|`FindSatellites`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，會找到附屬組件。 預設值為 `true.`|
|`FindSerializationAssemblies`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，工作會搜尋序列化組件。 預設值是 `true`。|
|`FullFrameworkAssemblyTables`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定具有 "FrameworkDirectory" 中繼資料的項目，以建立可轉散發清單與特定架構目錄的關聯。 如果未建立關聯，則將記錄錯誤。 若未設定 FrameworkDirectory，解析組件參考 (RAR) 邏輯會使用目標 Framework 目錄。|
|`FullFrameworkFolders`|選擇性 <xref:System.String?displayProperty=fullName>`[]` 參數。<br /><br /> 指定包含 RedistList 目錄的資料夾。 此目錄代表指定用戶端設定檔的完整架構，例如：*%programfiles%\reference assemblies\microsoft\framework\v4.0*。|
|`FullTargetFrameworkSubsetNames`|選擇性的 `String[]` 參數。<br /><br /> 包含目標 Framework 子集的名稱清單。 若清單中的子集名稱符合 `TargetFrameworkSubset` 命名屬性中的其中一個名稱，則系統會在建置階段排除特定的目標 Framework 子集。|
|`IgnoreDefaultInstalledAssemblyTables`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則工作會搜尋並使用在 `TargetFrameworkDirectories`下的 *\RedistList* 目錄中找到的其他已安裝組件表格 (或「可轉散發清單」)。 預設值為 `false.`|
|`IgnoreDefaultInstalledAssemblySubsetTables`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則工作會搜尋並使用在 `TargetFrameworkDirectories`下的 *\SubsetList* 目錄中找到的其他已安裝組件子集表格 (或「子集清單」)。 預設值為 `false.`|
|`InstalledAssemblySubsetTables`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 包含 XML 檔案清單，這些 XML 檔案指定了預期要在目標子集上的組件。<br /><br /> 這份清單中的項目也可以選擇指定 "FrameworkDirectory" 中繼資料，以便讓 `InstalledAssemblySubsetTable`<br /><br /> 與特定架構目錄產生關聯。<br /><br /> 若只有一個 `TargetFrameworkDirectories` 元素，則會將這份清單中缺少 "FrameworkDirectory" 中繼資料的任何項目，視為已設定為傳遞至 `TargetFrameworkDirectories`的唯一值。|
|`InstalledAssemblyTables`|選擇性的 `String` 參數。<br /><br /> 包含 XML 檔案清單，這些 XML 檔案指定了預期要在目標電腦上安裝的組件。<br /><br /> 當設定 `InstalledAssemblyTables` 時，清單中較早版本的的組件會合併至列在 XML 中的較新版本。 此外，具有 InGAC = 'true' 設定的組件會被視為必要條件，而且除非明確覆寫，否則便會設定為 CopyLocal='false'。<br /><br /> 這份清單中的項目也可以選擇指定 "FrameworkDirectory" 中繼資料，以便讓 `InstalledAssemblyTable` 與特定架構目錄產生關聯。  不過，除非 Redist 名稱開頭如下，否則便會忽略這項設定：<br /><br /> "Microsoft-Windows-CLRCoreComp"。<br /><br /> 若只有一個 `TargetFrameworkDirectories` 元素，則會將這份清單中缺少 "FrameworkDirectory" 中繼資料的任何項目，視為已設定為傳遞<br /><br /> 至 `TargetFrameworkDirectories`的唯一值。|
|`LatestTargetFrameworkDirectories`|選擇性的 `String[]` 參數。<br /><br /> 指定目錄的清單，這些目錄包含電腦上可作為目標之最新版架構的可轉散發清單。 若未設定，則會使用為指定的目標架構識別碼而安裝在電腦上的最高架構。|
|`ProfileName`|選擇性的 `String` 參數。<br /><br /> -   指定要作為目標之 Framework 設定檔的名稱。 例如，用戶端、Web 或網路。|
|`RelatedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 包含相關的檔案，例如 XML 和 *.pdb* 檔案，這些檔案的基底名稱與參考相同。<br /><br /> 這個參數中列出的檔案可選擇性包含下列項目中繼資料：<br /><br /> -   `Primary`： `Boolean` 值。 如果為 `true`，則會使用 `Assemblies` 參數。 預設值為 `false`。<br />-   `CopyLocal`： `Boolean` 值。 表示是否將指定的參考複製到輸出目錄中。|
|`ResolvedDependencyFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 包含相依性的第 *n* 階路徑。 此參數不包括第一順序主要參考，其包含在 `ResolvedFiles` 參數中。<br /><br /> 這個參數中的項目可選擇性包含下列項目中繼資料：<br /><br /> -   `CopyLocal`： `Boolean` 值。 表示是否將指定的參考複製到輸出目錄中。<br />-   `FusionName`： `String` 值。 指定此相依性的名稱。<br />-   `ResolvedFrom`： `String` 值。 指定解析此檔案的來源常值搜尋路徑。|
|`ResolvedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 包含所有解析為完整路徑的主要參考清單。<br /><br /> 這個參數中的項目可選擇性包含下列項目中繼資料：<br /><br /> -   `CopyLocal`： `Boolean` 值。 表示是否將指定的參考複製到輸出目錄中。<br />-   `FusionName`： `String` 值。 指定此相依性的名稱。<br />-   `ResolvedFrom`： `String` 值。 指定解析此檔案的來源常值搜尋路徑。|
|`SatelliteFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 指定找到的任何附屬檔案。 如果讓此項目可以存在的參考或相依性為 CopyLocal = true，則這些檔案會是 CopyLocal = true。<br /><br /> 這個參數中的項目可選擇性包含下列項目中繼資料：<br /><br /> -   `CopyLocal`： `Boolean` 值。 表示是否將指定的參考複製到輸出目錄中。 如果讓此項目可以存在的參考或相依性具有值為 `true` 的 `CopyLocal` ，則此值為 `true`。<br />-   `DestinationSubDirectory`： `String` 值。 指定要將此項目複製到其中的相對目的地目錄。|
|`ScatterFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 包含與其中一個指定之組件相關聯的散佈檔案。<br /><br /> 這個參數中的項目可選擇性包含下列項目中繼資料：<br /><br /> -   `CopyLocal`： `Boolean` 值。 表示是否將指定的參考複製到輸出目錄中。|
|`SearchPaths`|必要的 `String[]` 參數。<br /><br /> 指定要搜尋的目錄或特殊位置，以找出磁碟上代表組件的檔案。 搜尋路徑的列示順序很重要。 對每個組件而言，都會從左至右搜尋路徑清單。 當找到代表組件的檔案時，此搜尋會停止並開始搜尋下一個組件。<br /><br /> 此參數接受以分號分隔的值清單，這些值可以是目錄路徑或下列清單的特殊常值：<br /><br /> -   `{HintPathFromItem}`：指定工作會檢查基底項目的 `HintPath` 中繼資料。<br />-   `{CandidateAssemblyFiles}`：指定工作會檢查透過 `CandidateAssemblyFiles` 參數傳遞的檔案。<br />-   `{Registry:`\<AssemblyFoldersBase>， \<RuntimeVersion> \<AssemblyFoldersSuffix> `}` ：指定工作會在登錄中指定的其他資料夾中搜尋。 應以要搜尋的登錄位置特定值取代 \<AssemblyFoldersBase>、\<RuntimeVersion> 和 \<AssemblyFoldersSuffix>。 常見目標中的預設規格是 {Registry:$(FrameworkRegistryBase), $(TargetFrameworkVersion), $(AssemblyFoldersSuffix), $(AssemblyFoldersExConditions)}。<br />-   `{AssemblyFolders}`：指定工作會使用 Visual Studio.NET 2003 的 finding-assemblies-from-registry 配置。<br />-   `{GAC}`：指定工作會在全域組件快取 (GAC) 中搜尋。<br />-   `{RawFileName}`：指定工作會將項目的 `Include` 值視為確切的路徑和檔案名稱。|
|`SerializationAssemblyFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 包含任何找到的 XML 序列化組件。 這些項目被標示為 CopyLocal = true 與造成此項目存在的相依性是 CopyLocal = true 互為充要條件。<br /><br /> `Boolean` 中繼資料 CopyLocal 表示是否將指定的參考複製到輸出目錄中。|
|`Silent`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，則不會記錄任何訊息。 預設值是 `false`。|
|`StateFile`|選擇性的 `String` 參數。<br /><br /> 指定檔名，表示要在該檔案中儲存這項工作的中繼建置狀態。|
|`SuggestedRedirects`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 不論 `AutoUnify` 屬性的值為何，都會包含每個不同衝突組件識別的一個項目。 包括每個發現的文化特性和 PKT，且其應用程式組態檔中沒有適合的 bindingRedirect 項目。<br /><br /> 每個項目都可選擇包含下列資訊：<br /><br /> -   `Include` 屬性：包含組件系列的完整名稱，其中版本欄位的值為 0.0.0.0。<br />-   `MaxVersion` 項目中繼資料：包含最大版本號碼。|
|`TargetedRuntimeVersion`|選擇性的 `String` 參數。<br /><br /> 指定要作為目標的執行階段版本，例如：2.0.57027 或 v2.0.57027。|
|`TargetFrameworkDirectories`|選擇性的 `String[]` 參數。<br /><br /> 指定目標 Framework 目錄的路徑。 在判斷所產生項目的 CopyLocal 狀態時，需要此參數。<br /><br /> 如果未指定這個參數，則產生的項目不會具有 `true` 的 CopyLocal 值，除非這些項目在其來源項目上明確具有`true` 的 `Private` 中繼資料值。|
|`TargetFrameworkMoniker`|選擇性的 `String` 參數。<br /><br /> 要監視的 TargetFrameworkMoniker (若有的話)。 這會用於進行記錄。|
|`TargetFrameworkMonikerDisplayName`|選擇性的 `String` 參數。<br /><br /> 要監視之 TargetFrameworkMoniker 的顯示名稱 (若有的話)。 這會用於進行記錄。|
|`TargetFrameworkSubsets`|選擇性的 `String[]` 參數。<br /><br /> 包含要在目標 Framework 目錄中搜尋之目標 Framework 子集名稱的清單。|
|`TargetFrameworkVersion`|選擇性的 `String` 參數。<br /><br /> 專案目標 Framework 版本。 預設值為空白，表示不根據目標 Framework 來篩選參考。|
|`TargetProcessorArchitecture`|選擇性的 `String` 參數。<br /><br /> 慣用的目標處理器架構。 用來解析全域組件快取 (GAC) 參考。<br /><br /> 此參數可以具有 `x86`、`IA64` 或 `AMD64` 的值。<br /><br /> 若此參數不存在，工作會先考慮使用符合目前正在執行之處理序架構的組件。 若找不到任何組件，則工作會考慮 GAC 中具有 `ProcessorArchitecture` 的 `MSIL` 值或不具有 `ProcessorArchitecture` 值的組件。|

## <a name="warnings"></a>警告

 將記錄下列警告：

- `ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects`

- `ResolveAssemblyReference.SuggestedRedirects`

- `ResolveAssemblyReference.FoundConflicts`

- `ResolveAssemblyReference.AssemblyFoldersExSearchLocations`

- `ResolveAssemblyReference.UnifiedPrimaryReference`

- `ResolveAssemblyReference.PrimaryReference`

- `ResolveAssemblyReference.UnifiedDependency`

- `ResolveAssemblyReference.UnificationByAutoUnify`

- `ResolveAssemblyReference.UnificationByAppConfig`

- `ResolveAssemblyReference.UnificationByFrameworkRetarget`

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
