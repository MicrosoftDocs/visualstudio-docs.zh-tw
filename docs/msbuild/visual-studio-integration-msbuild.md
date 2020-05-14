---
title: Visual Studio 整合 (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631194"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio 整合 (MSBuild)

Visual Studio 託管 MSBuild 以載入和生成託管專案。 由於 MSBuild 負責該專案，因此幾乎任何 MSBuild 格式的專案都可以在 Visual Studio 中成功使用，即使該專案是由不同的工具創作的，並且具有自訂的生成過程。

 本文介紹了 Visual Studio 的 MSBuild 託管的特定方面，在自訂專案和 *.targets*希望在 Visual Studio 中載入和構建的檔時應考慮這些方面。 這些將説明您確保 Visual Studio 功能（如 IntelliSense）和自訂專案的調試工作。

 有關C++專案的資訊，請參閱[專案檔案](/cpp/build/reference/project-files)。

## <a name="project-file-name-extensions"></a>專案檔副檔名

 *MSBuild.exe*可識別與模式匹配的任何專案檔案名擴展*名\*。普羅傑*. 但是，Visual Studio 僅識別這些專案檔案名副檔名的子集，該副檔名確定將載入專案的語言特定專案系統。 Visual Studio 沒有基於語言的 MSBuild 專案系統。

 例如，C# 專案系統載入 *.csproj*檔，但 Visual Studio 無法載入 *.xxproj*檔。 以任意語言獲取原始檔案的專案檔案必須使用與 Visual Basic 或 C# 專案檔案相同的副檔名才能在 Visual Studio 中載入。

## <a name="well-known-target-names"></a>已知的目標名稱

 按一下 Visual Studio 中的 **"生成**"命令將在專案中執行預設目標。 通常這個目標也是命名為 `Build`。 如果選擇 [ **重建** ] 或 [ **清除** ] 命令，將會嘗試執行專案中相同名稱的目標。 如果按一下 [ **發行** ]，則會執行專案中命名為 `PublishOnly` 的目標。

## <a name="configurations-and-platforms"></a>組態和平台

 配置在 MSBuild 專案中由分組在包含`PropertyGroup``Condition`屬性的元素中的屬性工作表示。 Visual Studio 查看這些條件，以便創建要顯示的專案配置和平臺的清單。 若要成功地擷取這份清單，條件必須具有類似下列的格式：

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio 會查看`PropertyGroup`、`ItemGroup`屬性`Import`和項元素上的條件。

## <a name="additional-build-actions"></a>其他建置動作

 Visual Studio 允許您使用 **"檔案屬性**"視窗的**生成操作**屬性更改專案中檔的項類型名稱。 **Compile**、**EmbeddedResource**、**Content** 和 **None** 項目類型名稱會一直列在這個功能表中，另外還會列出專案中既有的其他項目類型名稱。 若要確保自訂的項目類型名稱都會一直列在這個功能表中，您可以將其名稱加入至名為 `AvailableItemName`的項目類型中。 例如，如果在專案檔中加入下列程式碼，就會將自訂類型 **JScript** 加入至所有會匯入此類型之專案的這個功能表中：

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> 某些專案類型名稱是 Visual Studio 的專用名稱，但在此下拉清單中未列出。

## <a name="in-process-compilers"></a>同處理序編譯器

 如果可能，Visual Studio 將嘗試使用 Visual Basic 編譯器的進程中版本來提高性能。 （不適用於 C#。要正常工作，必須滿足以下條件：

- 在專案的目標中，必須有一個為 Visual Basic`Vbc`專案命名的任務。

- 這個工作的 `UseHostCompilerIfAvailable` 參數必須設定為 true。

## <a name="design-time-intellisense"></a>設計階段 IntelliSense

 要在生成生成輸出程式集之前在 Visual Studio 中獲得 IntelliSense 支援，必須滿足以下條件：

- 必須要有一個名為 `Compile`的目標。

- `Compile` 目標或此目標的其中一個相依性必須呼叫專案的編譯器工作，例如 `Csc` 或 `Vbc`。

- `Compile` 目標或此目標的其中一個相依性必須讓編譯器接收 IntelliSense 的所有必要參數，特別是所有參考。

- 必須滿足[進程內編譯器](#in-process-compilers)部分中列出的條件。

## <a name="build-solutions"></a>建置解決方案

 在 Visual Studio 中，解決方案檔和專案生成順序由 Visual Studio 本身控制。 在命令列上使用*msbuild.exe*構建解決方案時，MSBuild 會分析解決方案檔並命令專案生成。 在這兩種情況下都會依據相依性順序個別建置專案，而且不會走訪專案對專案間的參考。 相反，當使用*msbuild.exe*構建單個專案時，將遍歷專案引用。

 在 Visual Studio 內構建`$(BuildingInsideVisualStudio)`時，屬性`true`設置為 。 這可用於專案或 *.target*檔，使生成的行為不同。

## <a name="display-properties-and-items"></a>顯示屬性和項目

 Visual Studio 可識別某些屬性名稱和值。 例如，在專案中下列屬性會使 [ **Windows 應用程式** ] 出現在 [ **專案設計工具** ] 的 [ **應用程式類型**] 方塊中。

```xml
<OutputType>WinExe</OutputType>
```

 屬性值可以在 [ **專案設計工具** ] 中進行編輯並且儲存在專案檔中。 如果通過手動編輯為此類屬性指定無效值，則 Visual Studio 將在載入專案時顯示警告，並將無效值替換為預設值。

 Visual Studio 瞭解某些屬性的預設值。 所以，除非這些屬性不是使用預設值，否則不會保存在專案檔中。

 具有任意名稱的屬性不會在視覺化工作室中顯示。 要修改 Visual Studio 中的任意屬性，必須在 XML 編輯器中打開專案檔案並手動編輯它們。 如需詳細資訊，請參閱本主題稍後的[在 Visual Studio 中編輯專案檔](#edit-project-files-in-visual-studio)一節。

 預設情況下，在具有任意專案類型名稱的專案中定義的項顯示在其專案節點下的 **"解決方案資源管理器"** 中。 若要隱藏項目，請將 `Visible` 中繼資料設定為 `false`。 例如，以下專案將參與生成過程，但不會顯示在**解決方案資源管理器**中。

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> 對於`Visible`C++專案 **，解決方案資源管理器**將忽略中繼資料。 即使設置為`Visible`false，也始終顯示專案。

 根據預設，在檔案中宣告並匯入至專案的項目不會顯示出來。 在生成過程中創建的項永遠不會顯示在**解決方案資源管理器**中。

## <a name="conditions-on-items-and-properties"></a>項目和屬性的條件

 在組建期間，必須確實遵守所有的條件。

 確定要顯示的屬性值時，Visual Studio 認為與配置相關的屬性的計算方式與它認為獨立于配置的屬性不同。 對於它認為與配置相關的屬性，Visual Studio`Configuration`會`Platform`適當地設置 和 屬性，並指示 MSBuild 重新評估專案。 如果是它認為與組態無關的屬性，則不會決定條件的評估方式。

 為了確定專案是否應顯示在**解決方案資源管理器**中，始終忽略項的條件運算式。

## <a name="debugging"></a>偵錯

 為了查找和啟動輸出程式集並附加調試器，Visual Studio 需要屬性`OutputPath`，`AssemblyName`並`OutputType`正確定義。 如果生成過程未導致編譯器生成 *.pdb*檔，則調試器將無法附加。

## <a name="design-time-target-execution"></a>設計階段目標執行

 Visual Studio 嘗試在載入專案時使用某些名稱執行目標。 這些目標包括 `Compile`、`ResolveAssemblyReferences`、`ResolveCOMReferences`、`GetFrameworkPaths` 與 `CopyRunEnvironmentFiles`。 Visual Studio 運行這些目標，以便可以初始化編譯器以提供 IntelliSense，可以初始化調試器，並解析解決方案資源管理器中顯示的引用。 如果這些目標不存在，專案將正確載入和生成，但 Visual Studio 中的設計時體驗將不能完全正常運行。

## <a name="edit-project-files-in-visual-studio"></a>在 Visual Studio 中編輯專案檔

 要直接編輯 MSBuild 專案，可以在 Visual Studio XML 編輯器中打開專案檔案。

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>若要在 Visual Studio 中卸載和編輯專案檔

1. 在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **卸載專案**]。

     專案便會標記為 [ **(無法使用)**]。

2. 在方案總管**** 中，開啟無法使用之專案的捷徑功能表，然後選擇 [編輯 \<專案檔>]****。

     專案檔隨即在 [Visual Studio XML 編輯器] 中開啟。

3. 編輯、儲存，然後關閉專案檔。

4. 在 [ **方案總管**] 中，開啟無法使用之專案的捷徑功能表，然後選擇 [ **重新載入專案**]。

## <a name="intellisense-and-validation"></a>IntelliSense 和驗證

 當使用 XML 編輯器編輯專案檔案時，IntelliSense 和驗證由 MSBuild 架構檔驅動。 這些安裝在架構緩存中，可在*\<視覺化工作室安裝目錄中找到>\Xml_Schemas_1033_MSBuild*。

 核心 MSBuild 類型在*Microsoft*中定義。 *Microsoft.Build.CommonTypes.xsd* 要自訂架構，以便對自訂專案類型名稱、屬性和任務進行 IntelliSense 和驗證，可以編輯*Microsoft.Build.xsd*，或者創建自己的架構，其中包括通用類型或核心架構。 如果已經建立了自己的結構描述，必須使用 [ **屬性** ] 視窗引導 XML 編輯器找到它。

## <a name="edit-loaded-project-files"></a>編輯已載入的專案檔

 Visual Studio 緩存專案檔案和專案檔案導入的檔的內容。 如果編輯載入的專案檔案，Visual Studio 將自動提示您重新載入專案，以便更改生效。 但是，如果您編輯的是已載入專案所匯入的檔案，就不會出現重新載入的提示，您必須以手動方式將專案卸載，然後再重新載入，才能使變更生效。

## <a name="output-groups"></a>輸出群組

 *在 Microsoft.Common.target*中定義的多個目標的名稱`OutputGroups`以`OutputGroupDependencies`或 結尾。 Visual Studio 調用這些目標來獲取專案輸出的特定清單。 例如，`SatelliteDllsProjectOutputGroup` 目標會建立一份清單，列出組建將要建立的所有附屬組件。 使用這些輸出群組的功能包括發行、部署以及專案對專案間的參考。 不定義它們的專案將在 Visual Studio 中載入和生成，但某些功能可能無法正常工作。

## <a name="reference-resolution"></a>參考解析

 參考解析是使用儲存於專案檔中參考項目以找到實際組件的程序。 Visual Studio 必須觸發引用解析度，以便在 **"屬性"** 視窗中顯示每個引用的詳細屬性。 下列清單會說明三種參考類型及其解析方式。

- 組件參考：

   專案系統使用已知名稱 `ResolveAssemblyReferences`呼叫目標。 這個目標應該以項目類型名稱 `ReferencePath`來產生項目。 每一個產生的項目都會包含完整參考路徑的項目規格 (即項目的 `Include` 屬性值)。 除了下列這些新的中繼資料以外，項目應該傳遞輸入項目中的所有中繼資料：

  - `CopyLocal`，指出是否要將組件複製到輸出資料夾中，可設定為 true 或 false。

  - `OriginalItemSpec`，包含參考的原始項目規格。

  - `ResolvedFrom`，如果是從 .NET Framework 目錄解析，則設定為 "{TargetFrameworkDirectory}"。

- COM 參考：

   專案系統使用已知名稱 `ResolveCOMReferences`呼叫目標。 這個目標應該以項目類型名稱 `ComReferenceWrappers`來產生項目。 對於 COM 參考而言，每一個項目都應該有包含完整 Interop 組件路徑的項目規格。 除了名稱為 `CopyLocal` 的新中繼資料 (指出是否要將組件複製到輸出資料夾中，可設定為 true 或 false) 以外，這些項目應該傳遞輸入項目中的所有中繼資料。

- 原生參考：

   專案系統使用已知名稱 `ResolveNativeReferences`呼叫目標。 這個目標應該以項目類型名稱 `NativeReferenceFile`來產生項目。 除了名為 `OriginalItemSpec`的新的中繼資料 (包含參考的原始項目規格) 以外，項目應該傳遞輸入項目中的所有中繼資料。

## <a name="performance-shortcuts"></a>效能捷徑

 如果使用 Visual Studio IDE 開始調試（通過選擇 F5 鍵或在功能表列上選擇**調試** > **開始調試**）或生成專案（例如，**生成** > **生成解決方案**），則生成過程使用快速更新檢查來提高性能。 在某些情況下，自訂組建會建立輪流建置的檔案，此時快速更新檢查就無法正確識別變更的檔案。 需要更完整更新檢查的專案可以藉由設定環境變數 `DISABLEFASTUPTODATECHECK=1`關閉快速檢查。 或者，專案可以在專案中或專案匯入的檔案中將此設為 MSBuild 屬性。

 快速更新檢查並不適用 Visual Studio 中的定期組建，而且專案的建置方式就如同您在命令提示字元中叫用組建一般。

## <a name="see-also"></a>另請參閱

- [如何：擴展視覺化工作室構建過程](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [從 IDE 中啟動組建](../msbuild/starting-a-build-from-within-the-ide.md)
- [登錄 .NET Framework 的延伸模組](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)
- [屬性元素 （MSBuild）](../msbuild/property-element-msbuild.md)
- [目標元素 （MSBuild）](../msbuild/target-element-msbuild.md)
- [Csc 工作](../msbuild/csc-task.md)
- [Vbc 任務](../msbuild/vbc-task.md)
