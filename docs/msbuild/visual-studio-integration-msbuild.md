---
title: Visual Studio 整合 (MSBuild)
titleSuffix: ''
description: 瞭解 Visual Studio 如何以 MSBuild 格式來裝載專案，即使這些專案是由不同的工具所撰寫，並有自訂的組建程式。
ms.custom: seodec18, SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ff8f195b6d77aeab9a01a6f3f6262f4024de1153
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951650"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio 整合 (MSBuild)

Visual Studio 裝載 MSBuild 以載入和建立 managed 專案。 因為 MSBuild 負責專案，所以即使專案是由不同的工具所撰寫並且具有自訂的組建流程，也可以成功地在 Visual Studio 中使用 MSBuild 格式的任何專案。

 本文說明在自訂您想要在 Visual Studio 中載入和建立的專案和 *.targets* 檔案時，Visual Studio 的 MSBuild 裝載的特定層面。 這些將可協助您確保 Visual Studio 的功能（例如 IntelliSense 和偵錯工具）適用于您的自訂專案。

 如需 c + + 專案的詳細資訊，請參閱 [專案](/cpp/build/reference/project-files)檔。

## <a name="project-file-name-extensions"></a>專案檔副檔名

 *MSBuild.exe* 會辨識符合模式的任何專案檔名稱延伸 *。 \*proj*。 不過，Visual Studio 只能辨識這些專案副檔名的子集，以決定將載入專案的特定語言專案系統。 Visual Studio 沒有以語言中立的 MSBuild 為基礎的專案系統。

 例如，c # 專案系統載入 *.csproj* 檔案，但 Visual Studio 無法載入 *xxproj* 檔案。 任意語言的原始程式檔專案檔必須使用與 Visual Basic 或 c # 專案檔相同的副檔名，才能在 Visual Studio 中載入。

## <a name="well-known-target-names"></a>已知的目標名稱

 按一下 Visual Studio 中的 [ **組建** ] 命令，將會執行專案中的預設目標。 通常這個目標也是命名為 `Build`。 如果選擇 [ **重建** ] 或 [ **清除** ] 命令，將會嘗試執行專案中相同名稱的目標。 如果按一下 [ **發行** ]，則會執行專案中命名為 `PublishOnly` 的目標。

## <a name="configurations-and-platforms"></a>組態和平台

 在 MSBuild 專案中，設定會以包含屬性之元素中群組的屬性來表示 `PropertyGroup` `Condition` 。 Visual Studio 會查看這些條件以建立要顯示的專案設定和平臺清單。 若要成功地擷取這份清單，條件必須具有類似下列的格式：

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio 會查看 `PropertyGroup` 、 `ItemGroup` 、 `Import` 、屬性和專案元素的條件，以達到此目的。

## <a name="additional-build-actions"></a>其他建置動作

 Visual Studio 可讓您使用 [**檔案屬性**] 視窗的 [**建立動作**] 屬性，來變更專案中檔案的專案類型名稱。 **Compile**、**EmbeddedResource**、**Content** 和 **None** 項目類型名稱會一直列在這個功能表中，另外還會列出專案中既有的其他項目類型名稱。 若要確保自訂的項目類型名稱都會一直列在這個功能表中，您可以將其名稱加入至名為 `AvailableItemName`的項目類型中。 例如，如果在專案檔中加入下列程式碼，就會將自訂類型 **JScript** 加入至所有會匯入此類型之專案的這個功能表中：

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> 某些專案類型名稱是 Visual Studio 特殊的，但未列在此下拉式清單中。

## <a name="in-process-compilers"></a>同處理序編譯器

 可能的話，Visual Studio 將嘗試使用 Visual Basic 編譯器的同進程版本，以提升效能。  (不適用於 c #。 ) 如此才能正確運作，必須符合下列條件：

- 在專案的目標中，必須有一個名 `Vbc` 為的工作 Visual Basic 專案。

- 這個工作的 `UseHostCompilerIfAvailable` 參數必須設定為 true。

## <a name="design-time-intellisense"></a>設計階段 IntelliSense

 若要在組建產生輸出元件之前 Visual Studio 取得 IntelliSense 支援，必須符合下列條件：

- 必須要有一個名為 `Compile`的目標。

- `Compile` 目標或此目標的其中一個相依性必須呼叫專案的編譯器工作，例如 `Csc` 或 `Vbc`。

- `Compile` 目標或此目標的其中一個相依性必須讓編譯器接收 IntelliSense 的所有必要參數，特別是所有參考。

- 必須符合同 [進程編譯器](#in-process-compilers) 區段中所列的條件。

## <a name="build-solutions"></a>建置解決方案

 在 Visual Studio 中，方案檔和專案建立順序是由 Visual Studio 本身所控制。 使用命令列上的 *msbuild.exe* 建立方案時，MSBuild 會剖析方案檔並排列專案組建的順序。 在這兩種情況下都會依據相依性順序個別建置專案，而且不會走訪專案對專案間的參考。 相反地，使用 *msbuild.exe* 建立個別專案時，會對專案對專案的參考進行往返。

 在 Visual Studio 內建立時，屬性 `$(BuildingInsideVisualStudio)` 會設定為 `true` 。 這可以在您的專案或 *.targets* 檔案中使用，使組建的行為不同。

## <a name="display-properties-and-items"></a>顯示屬性和項目

 Visual Studio 會辨識某些屬性名稱和值。 例如，在專案中下列屬性會使 [ **Windows 應用程式** ] 出現在 [ **專案設計工具** ] 的 [ **應用程式類型**] 方塊中。

```xml
<OutputType>WinExe</OutputType>
```

 屬性值可以在 [ **專案設計工具** ] 中進行編輯並且儲存在專案檔中。 如果手動編輯時，將這個屬性的值指定為無效，Visual Studio 將會在載入專案時顯示警告，並將不正確值取代為預設值。

 Visual Studio 瞭解某些屬性的預設值。 所以，除非這些屬性不是使用預設值，否則不會保存在專案檔中。

 具有任意名稱的屬性不會顯示在 Visual Studio 中。 若要在 Visual Studio 中修改任意屬性，您必須在 XML 編輯器中開啟專案檔，然後手動編輯。 如需詳細資訊，請參閱本主題稍後的[在 Visual Studio 中編輯專案檔](#edit-project-files-in-visual-studio)一節。

 專案中以任意專案類型名稱定義的專案預設會顯示在其專案節點下的 **方案總管** 中。 若要隱藏項目，請將 `Visible` 中繼資料設定為 `false`。 例如，下列專案將參與建立程式，但不會顯示在 **方案總管** 中。

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> `Visible`C + + 專案的 **方案總管** 會忽略中繼資料。 即使設為 false，也一律會顯示專案 `Visible` 。

 根據預設，在檔案中宣告並匯入至專案的項目不會顯示出來。 在建立程式期間建立的專案絕不會顯示在 **方案總管** 中。

## <a name="conditions-on-items-and-properties"></a>項目和屬性的條件

 在組建期間，必須確實遵守所有的條件。

 當您決定要顯示的屬性值時，Visual Studio 考慮設定相依的屬性會以不同于視為個別設定的屬性來評估。 對於它認為設定相依的屬性，Visual Studio `Configuration` `Platform` 適當地設定和屬性，並指示 MSBuild 重新評估專案。 如果是它認為與組態無關的屬性，則不會決定條件的評估方式。

 專案的條件運算式一律會被忽略，以決定是否應該在 **方案總管** 中顯示專案。

## <a name="debugging"></a>偵錯

 為了尋找並啟動輸出元件並附加偵錯工具，Visual Studio 需要屬性 `OutputPath` 、 `AssemblyName` 和 `OutputType` 正確定義。 如果組建進程未造成編譯器產生 *.pdb* 檔案，偵錯工具將無法附加。

## <a name="design-time-target-execution"></a>設計階段目標執行

 Visual Studio 在載入專案時，會嘗試使用特定名稱來執行目標。 這些目標包括 `Compile`、`ResolveAssemblyReferences`、`ResolveCOMReferences`、`GetFrameworkPaths` 與 `CopyRunEnvironmentFiles`。 Visual Studio 會執行這些目標，以便初始化編譯器以提供 IntelliSense、初始化偵錯工具，以及在方案總管中顯示的參考可以解決。 如果這些目標不存在，專案將會正確載入並建立，但 Visual Studio 中的設計階段體驗將無法完全運作。

## <a name="edit-project-files-in-visual-studio"></a>在 Visual Studio 中編輯專案檔

 若要直接編輯 MSBuild 專案，您可以在 Visual Studio XML 編輯器中開啟專案檔。

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>若要在 Visual Studio 中卸載和編輯專案檔

1. 在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **卸載專案**]。

     專案便會標記為 [ **(無法使用)**]。

2. 在 **方案總管** 中，開啟無法使用之專案的快捷方式功能表，然後選擇 [**編輯 \<Project File>**]。

     專案檔隨即在 [Visual Studio XML 編輯器] 中開啟。

3. 編輯、儲存，然後關閉專案檔。

4. 在 [ **方案總管**] 中，開啟無法使用之專案的捷徑功能表，然後選擇 [ **重新載入專案**]。

## <a name="intellisense-and-validation"></a>IntelliSense 和驗證

 使用 XML 編輯器編輯專案檔時，IntelliSense 和驗證是由 MSBuild 架構檔案所驅動。 這些會安裝在架構快取中，可在 *\<Visual Studio installation directory> \Xml\Schemas\1033\MSBuild* 中找到。

 核心 MSBuild 類型定義于 Microsoft.build.commontypes.xsd 中 *，Visual Studio* 所使用的一般類型會定義在 *.xsd* 中。 若要自訂架構，讓您擁有自訂專案類型名稱、屬性和工作的 IntelliSense 和 *驗證，您可以編輯 microsoft.build.commontypes.xsd* 或建立您自己的架構，其中包含或核心架構。 如果已經建立了自己的結構描述，必須使用 [ **屬性** ] 視窗引導 XML 編輯器找到它。

## <a name="edit-loaded-project-files"></a>編輯已載入的專案檔

 Visual Studio 快取專案檔的內容，以及專案檔所匯入的檔案。 如果您編輯載入的專案檔，Visual Studio 將會自動提示您重載專案，讓變更生效。 但是，如果您編輯的是已載入專案所匯入的檔案，就不會出現重新載入的提示，您必須以手動方式將專案卸載，然後再重新載入，才能使變更生效。

## <a name="output-groups"></a>輸出群組

 在 Microsoft 中定義的數個目標 *。 Common. .targets* 的名稱結尾為 `OutputGroups` 或 `OutputGroupDependencies` 。 Visual Studio 會呼叫這些目標以取得專案輸出的特定清單。 例如，`SatelliteDllsProjectOutputGroup` 目標會建立一份清單，列出組建將要建立的所有附屬組件。 使用這些輸出群組的功能包括發行、部署以及專案對專案間的參考。 未定義它們的專案會在 Visual Studio 載入並建立，但某些功能可能無法正常運作。

## <a name="reference-resolution"></a>參考解析

 參考解析是使用儲存於專案檔中參考項目以找到實際組件的程序。 Visual Studio 必須觸發參考解析，才能在 [ **屬性** ] 視窗中顯示每個參考的詳細屬性。 下列清單會說明三種參考類型及其解析方式。

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

 如果您使用 Visual Studio IDE，藉由選擇 F5 鍵或在功能表列上選擇 [ **Debug** 開始偵錯工具] 來啟動調試  >  程式 () 或建立專案 (例如，組建  >  **組建方案**) ，組建程式會使用快速更新檢查來改善效能。 在某些情況下，自訂組建會建立輪流建置的檔案，此時快速更新檢查就無法正確識別變更的檔案。 需要更完整更新檢查的專案可以藉由設定環境變數 `DISABLEFASTUPTODATECHECK=1`關閉快速檢查。 或者，專案可以在專案中或專案匯入的檔案中將此設為 MSBuild 屬性。

 快速更新檢查並不適用 Visual Studio 中的定期組建，而且專案的建置方式就如同您在命令提示字元中叫用組建一般。

## <a name="see-also"></a>另請參閱

- [如何：擴充 Visual Studio 組建進程](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [從 IDE 中啟動組建](../msbuild/starting-a-build-from-within-the-ide.md)
- [登錄 .NET Framework 的延伸模組](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)
- [MSBuild)  (Property 元素 ](../msbuild/property-element-msbuild.md)
- [MSBuild)  (目標元素 ](../msbuild/target-element-msbuild.md)
- [Csc 工作](../msbuild/csc-task.md)
- [Vbc 工作](../msbuild/vbc-task.md)
