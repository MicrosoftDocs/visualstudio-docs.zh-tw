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
ms.openlocfilehash: b1ddb8bdbc913a72791144d5e9d29d206712a3d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594418"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio 整合 (MSBuild)
Visual Studio 會裝載 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ，用於載入及建置 Managed 專案。 由於 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 是負責處理專案，因此幾乎任何 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 格式的專案都可以成功地用在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中，即使專案是用不同的工具撰寫，而且含有自訂的建置處理序，也不會有問題。

 本文將針對 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 裝載部分，描述在自訂您想要在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中載入和建置的專案與 *.targets* 檔時所應考慮的幾個特定層面。 這些內容將可幫助您確定像是 IntelliSense 和偵錯等 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 功能在自訂專案中能夠正常運作。

 如需有關 C++ 專案的資訊，請參閱[專案檔](/cpp/build/reference/project-files)。

## <a name="project-file-name-extensions"></a>專案檔副檔名
 *MSBuild.exe* 能夠辨認任何副檔名符合 *.\*proj* 模式的專案檔， 但是， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 只能辨認這些專案副檔名的一部分，這些專案副檔名會決定載入專案所使用的特定語言專案系統。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 並沒有中性語言的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案系統。

 例如，[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案系統可以載入 *.csproj* 檔案，但是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 卻無法載入 *.xxproj* 檔案。 對於任意語言的原始程式檔來說，其專案檔都必須使用與 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案檔相同的副檔名，才能夠載入至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中。

## <a name="well-known-target-names"></a>已知的目標名稱
 按一下 **中的 [建置]** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令，將會執行專案中的預設目標。 通常這個目標也是命名為 `Build`。 如果選擇 [ **重建** ] 或 [ **清除** ] 命令，將會嘗試執行專案中相同名稱的目標。 如果按一下 [ **發行** ]，則會執行專案中命名為 `PublishOnly` 的目標。

## <a name="configurations-and-platforms"></a>組態和平台
 組態會以根據 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 項目 (包含 `PropertyGroup` 屬性 (Attribute)) 分組之屬性 (Property) 的 `Condition` 專案表示。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會查看這些條件以建立要顯示的專案組態與平台清單。 若要成功地擷取這份清單，條件必須具有類似下列的格式：

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會查看 `PropertyGroup`、 `ItemGroup`、 `Import`、屬性和項目的條件，以便建立這份清單。

## <a name="additional-build-actions"></a>其他建置動作
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可以讓您利用 [檔案屬性] 視窗的 [建置動作] 屬性，變更專案中檔案的項目類型名稱。 **Compile**、**EmbeddedResource**、**Content** 和 **None** 項目類型名稱會一直列在這個功能表中，另外還會列出專案中既有的其他項目類型名稱。 若要確保自訂的項目類型名稱都會一直列在這個功能表中，您可以將其名稱加入至名為 `AvailableItemName`的項目類型中。 例如，如果在專案檔中加入下列程式碼，就會將自訂類型 **JScript** 加入至所有會匯入此類型之專案的這個功能表中：

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> 有些項目類型名稱是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中特有的，但是沒有列在這個下拉式清單中。

## <a name="in-process-compilers"></a>同處理序編譯器
 如果可能，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會嘗試使用同處理序 (In-Process) 版本的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器來提升效能 （不適用於 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]）。若要讓此作業正常運作，必須符合下列條件：

- 專案的目標中必須有一個名為 `Vbc` 的工作供 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案使用。

- 這個工作的 `UseHostCompilerIfAvailable` 參數必須設定為 true。

## <a name="design-time-intellisense"></a>設計階段 IntelliSense
 若要在組建產生輸出組件之前取得 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的 IntelliSense 支援，必須符合下列條件：

- 必須要有一個名為 `Compile`的目標。

- `Compile` 目標或此目標的其中一個相依性必須呼叫專案的編譯器工作，例如 `Csc` 或 `Vbc`。

- `Compile` 目標或此目標的其中一個相依性必須讓編譯器接收 IntelliSense 的所有必要參數，特別是所有參考。

- 必須符合[同處理序編譯器](#in-process-compilers)一節中所列的條件。

## <a name="build-solutions"></a>建置方案
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中，方案檔和專案建置順序是由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 本身來控制。 在命令列上使用 *msbuild.exe* 建置方案時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會剖析方案檔並排列專案建置的順序。 在這兩種情況下都會依據相依性順序個別建置專案，而且不會走訪專案對專案間的參考。 相反地，使用 *msbuild.exe* 建置個別專案時，則會周遊專案對專案間的參考。

 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中進行建置時，會將 `$(BuildingInsideVisualStudio)` 屬性設定為 `true`。 您可以在專案或 *.targets* 檔案中使用這個屬性，使建置以不同的方式運作。

## <a name="display-properties-and-items"></a>顯示屬性和項目
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 能夠辨認某些屬性名稱和值。 例如，在專案中下列屬性會使 [ **Windows 應用程式** ] 出現在 [ **專案設計工具** ] 的 [ **應用程式類型**] 方塊中。

```xml
<OutputType>WinExe</OutputType>
```

 屬性值可以在 [ **專案設計工具** ] 中進行編輯並且儲存在專案檔中。 如果以手動編輯方式為屬性指定了無效值， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在載入專案時將會顯示一個警告訊息，並以預設值取代無效值。

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 知道某些屬性的預設值， 所以，除非這些屬性不是使用預設值，否則不會保存在專案檔中。

 具有任意名稱的屬性不會顯示在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中。 若要修改 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中的任意屬性，必須在 XML 編輯器中開啟專案檔，然後以手動方式編輯屬性。 如需詳細資訊，請參閱本主題稍後的[在 Visual Studio 中編輯專案檔](#edit-project-files-in-visual-studio)一節。

 根據預設，在專案中以任意項目類型名稱定義的項目會顯示在 [方案總管] 中的專案節點下方。 若要隱藏項目，請將 `Visible` 中繼資料設定為 `false`。 例如，下列項目將會參與建置處理序，但是不會顯示在 [方案總管] 中。

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

 根據預設，在檔案中宣告並匯入至專案的項目不會顯示出來。 在建置處理序期間所建立的項目永遠不會顯示在 [方案總管] 中。

## <a name="conditions-on-items-and-properties"></a>項目和屬性的條件
 在組建期間，必須確實遵守所有的條件。

 在決定要顯示的屬性值時， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會以不同的方式來評估它認為與組態相關的屬性以及它認為與組態無關的屬性。 如果是它認為與組態相關的屬性， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 就會適當地設定 `Configuration` 和 `Platform` 屬性，並且指示 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 重新評估專案。 如果是它認為與組態無關的屬性，則不會決定條件的評估方式。

 在決定項目是否要顯示在 [方案總管] 中時，一律會忽略項目的條件運算式。

## <a name="debugging"></a>偵錯
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 必須正確定義 `OutputPath`、 `AssemblyName`和 `OutputType` 屬性，才能找到並啟動輸出組件以及連接到偵錯工具。 如果建置處理序未能使編譯器產生 *.pdb* 檔，將會無法連接到偵錯工具。

## <a name="design-time-target-execution"></a>設計階段目標執行
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在載入專案時，會嘗試執行具有特定名稱的目標， 這些目標包括 `Compile`、`ResolveAssemblyReferences`、`ResolveCOMReferences`、`GetFrameworkPaths` 與 `CopyRunEnvironmentFiles`。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會執行這些目標，以便能初始化編譯器以提供 IntelliSense、初始化偵錯工具，以及解析顯示在 [方案總管] 中的參考。 如果沒有這些目標，專案仍然可以正常載入和建置，但是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的設計階段功能將無法全部正常運作。

## <a name="edit-project-files-in-visual-studio"></a>在 Visual Studio 中編輯專案檔
 若要直接編輯 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案，可以在 Visual Studio XML 編輯器中開啟專案檔。

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>若要在 Visual Studio 中卸載和編輯專案檔

1. 在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **卸載專案**]。

     專案便會標記為 [ **(無法使用)** ]。

2. 在方案總管中，開啟無法使用之專案的捷徑功能表，然後選擇 [編輯 \<專案檔>]。

     專案檔隨即在 [Visual Studio XML 編輯器] 中開啟。

3. 編輯、儲存，然後關閉專案檔。

4. 在 [ **方案總管**] 中，開啟無法使用之專案的捷徑功能表，然後選擇 [ **重新載入專案**]。

## <a name="intellisense-and-validation"></a>IntelliSense 和驗證
 使用 XML 編輯器編輯專案檔時，IntelliSense 和驗證是由 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 結構描述檔驅動。 這些都會安裝在結構描述快取中，您可以在 *\<Visual Studio 安裝目錄>\Xml\Schemas\1033\MSBuild* 中找到。

 核心 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 類型是在 *Microsoft.Build.Core.xsd* 中定義的，而 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用的通用類型則是在 *Microsoft.Build.CommonTypes.xsd* 中定義的。 若要自訂結構描述，讓自訂的項目類型名稱、屬性和工作都能夠使用 IntelliSense 和驗證，您可以編輯 *Microsoft.Build.xsd*，或是建立自己的結構描述 (內含 CommonTypes 或 Core 結構描述)。 如果已經建立了自己的結構描述，必須使用 [ **屬性** ] 視窗引導 XML 編輯器找到它。

## <a name="edit-loaded-project-files"></a>編輯已載入的專案檔
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會快取專案檔以及專案檔所匯入之檔案的內容。 如果您編輯的是已載入的專案檔， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 將會自動提示您重新載入專案，才能使變更生效。 但是，如果您編輯的是已載入專案所匯入的檔案，就不會出現重新載入的提示，您必須以手動方式將專案卸載，然後再重新載入，才能使變更生效。

## <a name="output-groups"></a>輸出群組
 在 *Microsoft.Common.targets* 中定義的數個目標名稱結尾為 `OutputGroups` 或 `OutputGroupDependencies`。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會呼叫這些目標以取得專案輸出的特定清單。 例如，`SatelliteDllsProjectOutputGroup` 目標會建立一份清單，列出組建將要建立的所有附屬組件。 使用這些輸出群組的功能包括發行、部署以及專案對專案間的參考。 沒有定義輸出群組的專案仍然可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]載入和建置，但是有些功能可能無法正常運作。

## <a name="reference-resolution"></a>參考解析
 參考解析是使用儲存於專案檔中參考項目以找到實際組件的程序。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 必須觸發參考解析，才能夠在 [ **屬性** ] 視窗中顯示每一個參考的屬性。 下列清單會說明三種參考類型及其解析方式。

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
 如果您使用 Visual Studio IDE 來啟動偵錯工具（選擇 F5 鍵或在功能表列上選擇 [ **Debug** ] > [**開始調試**程式]），或建立您的專案（例如**組建** > **組建方案**），則組建程式會使用快速更新檢查來改善效能。 在某些情況下，自訂組建會建立輪流建置的檔案，此時快速更新檢查就無法正確識別變更的檔案。 需要更完整更新檢查的專案可以藉由設定環境變數 `DISABLEFASTUPTODATECHECK=1`關閉快速檢查。 或者，專案可以在專案中或專案匯入的檔案中將此設為 MSBuild 屬性。

 快速更新檢查並不適用 Visual Studio 中的定期組建，而且專案的建置方式就如同您在命令提示字元中叫用組建一般。

## <a name="see-also"></a>請參閱
- [如何：擴充 Visual Studio 的組建進程](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [從 IDE 中啟動組建](../msbuild/starting-a-build-from-within-the-ide.md)
- [登錄 .NET Framework 的延伸模組](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property 項目 (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target 項目 (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc 工作](../msbuild/csc-task.md)
- [Vbc 工作](../msbuild/vbc-task.md)
