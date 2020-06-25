---
title: MSBuild 如何建立專案
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3c1cdc4738f60301435932b3700f14377f12172
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290199"
---
# <a name="how-msbuild-builds-projects"></a>MSBuild 如何建立專案

MSBuild 實際上如何運作？ 在本文中，您將瞭解 MSBuild 如何處理您的專案檔，不論是從 Visual Studio 叫用，或是從命令列或腳本叫用。 瞭解 MSBuild 的運作方式可協助您更有效地診斷問題，並更有效地自訂您的組建流程。 本文描述組建程式，而且大部分都適用于所有專案類型。

完整的組建套裝程式含[初始啟動](#startup)、[評估](#evaluation-phase)和[執行](#execution-phase)建立專案的目標和工作。 除了這些輸入之外，外部匯入也會定義組建進程的詳細資料，包括[標準匯入](#standard-imports)（例如*Microsoft* ），以及解決方案或專案層級的[使用者可](#user-configurable-imports)設定匯入。

## <a name="startup"></a>啟動

MSBuild 可以透過*Microsoft.Build.dll*中的 msbuild 物件模型，或直接在命令列上叫用可執行檔，或是在 CI 系統中的腳本中，從 Visual Studio 叫用。 不論是哪一種情況，都會影響組建進程的輸入，包括專案檔（或 Visual Studio 的專案物件），可能是方案檔、環境變數、命令列參數或其物件模型對等專案。 在啟動階段，會使用命令列選項或物件模型對等專案來設定 MSBuild 設定，例如設定記錄器。 使用或參數在命令列上設定的屬性 `-property` `-p` 會設定為全域屬性，這會覆寫專案檔中所設定的任何值，即使稍後會讀取專案檔也一樣。

下一節是關於輸入檔，例如方案檔或專案檔。

### <a name="solutions-and-projects"></a>方案和專案

MSBuild 實例可能包含一個專案，或多個專案做為方案的一部分。 方案檔不是 MSBuild XML 檔案，但 MSBuild 會將它解讀成知道必須針對指定的設定和平臺設定建立的所有專案。 當 MSBuild 處理此 XML 輸入時，它稱為「方案組建」。 它有一些可擴充的點，可讓您在每個解決方案組建執行某個專案，但由於此組建與個別的專案組建分開執行，因此，解決方案組建中的屬性或目標定義設定不會與每個專案組建相關。

您可以在[自訂方案組建](customize-your-build.md#customize-the-solution-build)中瞭解如何擴充解決方案組建。

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio 組建和 MSBuild.exe 組建

當您透過 MSBuild 可執行檔，或當您使用 MSBuild 物件模型來啟動組建時，Visual Studio 與中的專案建立時，會有一些顯著的差異。 Visual Studio 管理 Visual Studio 組建的專案組建順序;它只會在個別專案層級呼叫 MSBuild，而當它執行時，會設定幾個布林值屬性（ `BuildingInsideVisualStudio` `BuildProjectReferences` ），以大幅影響 MSBuild 的作用。 在每個專案中，執行與透過 MSBuild 叫用時相同，但會與參考的專案產生差異。 在 MSBuild 中，需要參考的專案時，實際上會發生組建;也就是說，它會執行工作和工具，並產生輸出。 當 Visual Studio 組建找到參考的專案時，MSBuild 只會從參考的專案傳回預期的輸出;它可讓 Visual Studio 控制這些其他專案的建立。 Visual Studio 會分別決定組建順序和 MSBuild 的呼叫（視需要），完全在 Visual Studio 的控制項底下。

當使用方案檔叫用 MSBuild 時，會發生另一個差異，MSBuild 會剖析方案檔、建立標準的 XML 輸入檔、評估它，然後以專案的形式執行它。 方案組建會在任何專案之前執行。 從 Visual Studio 建立時，不會發生任何情況;MSBuild 永遠不會看到方案檔。 因此，解決方案組建自訂（使用*before）。解決方案名稱. .sln.* 和*after。解決方案名稱 .sln*）僅適用于已驅動的 MSBuild.exe 或物件模型，而不是 Visual Studio 的組建。

### <a name="project-sdks"></a>專案 SDK

MSBuild 專案檔的 SDK 功能相對較新。 在此變更之前，專案檔會明確匯入定義特定專案類型之組建進程的 *.targets*和 *. .props*檔案。

.NET Core 專案會匯入適用的 .NET SDK 版本。 請參閱總覽、 [.Net Core 專案 sdk](/dotnet/core/project-sdk/overview)和[屬性](/dotnet/core/project-sdk/msbuild-props)參考。

## <a name="evaluation-phase"></a>評估階段

本節討論如何處理和剖析這些輸入檔案，以產生記憶體中的物件，以判斷將會建立哪些內容。

評估階段的目的是要根據輸入 XML 檔案和本機環境，在記憶體中建立物件結構。 評估階段包含五個處理輸入檔（例如專案 XML 檔案或）和匯入的 XML 檔案（通常命名為 *. .props*或 *.targets*檔案），視其主要是設定屬性或定義組建目標而定。 每個階段都會建立部分記憶體中的物件，稍後在執行時間中用來建立專案，但在評估階段中不會發生實際的組建動作。 在每個階段中，專案會依其出現的順序進行處理。

評估階段中的階段如下所示：

- 評估環境變數
- 評估匯入和屬性
- 評估專案定義
- 評估專案
- 評估[UsingTask](usingtask-element-msbuild.md)元素
- 評估目標

這些階段的順序會有明顯的影響，而且在自訂專案檔時一定要知道。 請參閱[屬性和專案評估順序](comparing-properties-and-items.md#property-and-item-evaluation-order)。

### <a name="evaluate-environment-variables"></a>評估環境變數

在此階段中，會使用環境變數來設定對等的屬性。 例如，PATH 環境變數可做為屬性 `$(PATH)` 。 從命令列或腳本執行時，會使用命令環境做為正常，而當您從 Visual Studio 執行時，會使用 Visual Studio 啟動時生效的環境。

### <a name="evaluate-imports-and-properties"></a>評估匯入和屬性

在此階段中，會讀取整個輸入 XML，包括專案檔案和整個匯入鏈。 MSBuild 會建立記憶體中的 XML 結構，代表專案的 XML 和所有匯入的檔案。 目前不在目標中的屬性會進行評估和設定。

由於 MSBuild 會提早讀取其進程中所有的 XML 輸入檔，因此在建立程式期間對這些輸入進行的任何變更，都不會影響目前的組建。

任何目標外的屬性會以不同于目標內的屬性來處理。 在此階段中，只會評估在任何目標外部定義的屬性。

因為屬性會依序在屬性傳遞中進行處理，所以在輸入中任何時間點的屬性都可以存取先前出現在輸入中的屬性值，而不是稍後出現的屬性。

因為屬性會在評估專案之前進行處理，所以您無法在屬性傳遞的任何部分期間存取任何專案的值。 

### <a name="evaluate-item-definitions"></a>評估專案定義

在此階段中，會解讀[專案定義](item-definitions.md)，並建立這些定義的記憶體中標記法。

### <a name="evaluate-items"></a>評估專案

在目標內定義的專案會與任何目標外的專案以不同的方式處理。 在此階段中，會處理任何目標外的專案及其相關聯的中繼資料。  專案定義所設定的中繼資料會由專案上的中繼資料設定覆寫。 因為專案會依其出現的順序進行處理，所以您可以參考稍早定義的專案，但不是稍後顯示的專案。 因為專案通過是在屬性通過之後，所以如果在任何目標外部定義，專案就可以存取任何屬性，而不論稍後是否出現屬性定義。

### <a name="evaluate-usingtask-elements"></a>評估 `UsingTask` 元素

在此階段中，會讀取[UsingTask](usingtask-element-msbuild.md)元素，並宣告工作以供稍後在執行時間使用。

### <a name="evaluate-targets"></a>評估目標

在此階段中，會在記憶體中建立所有目標物件結構，以準備執行。 實際執行不會發生。 

## <a name="execution-phase"></a>執行階段

在執行階段中，目標會進行排序和執行，並執行所有工作。 但是首先，在目標內定義的屬性和專案會依其出現的順序在單一階段中進行評估。 處理的順序與不在目標中的屬性和專案的處理方式不同：在個別的階段中，所有屬性都會先，然後是所有專案。 對目標內的屬性和專案所做的變更，可以在變更目標之後觀察到。

### <a name="target-build-order"></a>目標組建順序

在單一專案中，目標會以序列循序執行。 中央問題在於如何判斷要在中建立所有專案的順序，以便使用相依性依正確順序建立目標。  

目標群組建順序是由在 `BeforeTargets` `DependsOnTargets` `AfterTargets` 每個目標上使用、和屬性所決定。 如果較舊的目標修改了這些屬性中所參考的屬性，則後續目標的順序可能會在執行較舊的目標期間受到影響。

排序的規則會在[判斷目標群組建順序](target-build-order.md#determine-the-target-build-order)中加以說明。 此程式是由包含要建立之目標的堆疊結構所決定。 此工作頂端的目標會開始執行，如果它相依于其他任何專案，則這些目標會推送至堆疊的頂端，並開始執行。  當沒有任何相依性的目標時，它會執行至完成，並繼續其父系目標。

### <a name="project-references"></a>專案參考

MSBuild 可以採用兩種程式碼路徑，這是正常的，如這裡所述，以及下一節所述的圖形選項。

個別專案會透過專案來指定其對其他專案的相依性 `ProjectReference` 。 當堆疊頂端的專案開始建立時，它會到達目標執行的點，也就 `ResolveProjectReferences` 是在一般目標檔案中定義的標準目標。

`ResolveProjectReferences`使用專案的輸入叫用 MSBuild 工作 `ProjectReference` 以取得輸出。 `ProjectReference`專案會轉換成本機專案（例如） `Reference` 。 當執行時間開始處理參考的專案時，目前專案的 MSBuild 執行時間會暫停（評估階段會在必要時先完成）。 只有在您開始建立相依專案之後，才會建立參考的專案，因此這會建立專案的樹狀結構。

Visual Studio 允許在方案檔（.sln）中建立專案相依性。 相依性是在方案檔中指定，而且只有在建立方案時，或在 Visual Studio 內建立時才會遵守。 如果您建立單一專案，就會忽略這種類型的相依性。 MSBuild 會將解決方案參考轉換成 `ProjectReference` 專案，之後會以相同的方式處理。

### <a name="graph-option"></a>圖表選項

如果您指定圖形組建參數（ `-graphBuild` 或 `-graph` ）， `ProjectReference` 會成為 MSBuild 所使用的第一級概念。 MSBuild 會剖析所有專案，並建立組建順序圖形，也就是專案的實際相依性圖形，接著會進行遍歷以判斷組建順序。 如同個別專案中的目標，MSBuild 會確保參考的專案會在其相依專案之後建立。

## <a name="parallel-execution"></a>平行執行

如果使用多處理器支援（ `-maxCpuCount` 或 `-m` 參數），msbuild 會建立節點，這是使用可用 CPU 核心的 msbuild 進程。 每個專案都會提交至可用的節點。 在節點內，個別的專案組建會以序列循序執行。

藉由設定布林變數 <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> （根據 MSBuild 中的屬性值來設定），可以啟用平行執行的工作 `$(BuildInParallel)` 。 針對平行執行所啟用的工作，工作排程器會管理節點，並將工作指派給節點。

請參閱[使用 MSBuild 平行建立多個專案](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>標準匯入

*.Props*和*microsoft*一般都是由 .net 專案檔（在 SDK 樣式專案中明確或隱含）匯入，而且位於 Visual Studio 安裝的*MSBuild\Current\bin*資料夾中。 C + + 專案有自己的匯入階層;請參閱[c + + 專案的 MSBuild 內部](/cpp/build/reference/msbuild-visual-cpp-overview)。

*.Props*檔案會設定您可以覆寫的預設值。 它會在專案檔的開頭匯入（明確或隱含）。 如此一來，您專案的設定就會出現在預設值之後，使其覆寫它們。

*Microsoft Common .targets*檔案及其匯入的目標檔案會定義 .net 專案的標準組建程式。 它也會提供可用來自訂群組建的擴充點。

在執行中， *Microsoft 一般的目標*是一個會匯入*CurrentVersion*的精簡型包裝函式。 此檔案包含標準屬性的設定，並定義定義組建進程的實際目標。 此 `Build` 目標定義于此處，但實際上本身是空的。 不過， `Build` 目標 `DependsOn` 會包含屬性，以指定組成實際組建步驟的個別目標，也就是 `BeforeBuild` 、 `CoreBuild` 和 `AfterBuild` 。 `Build`目標定義如下：

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild`和 `AfterBuild` 是擴充點。 它們在*CurrentVersion*檔案中是空的，但專案可以提供自己的 `BeforeBuild` 目標，以及 `AfterBuild` 需要在主要組建程式之前或之後執行的工作。 `AfterBuild`會在無 op 目標之前執行， `Build` 因為 `AfterBuild` 會出現在目標的 `DependsOn` 屬性中 `Build` ，但會出現在之後 `CoreBuild` 。

`CoreBuild`目標包含對組建工具的呼叫，如下所示：

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

下表描述這些目標;某些目標僅適用于特定專案類型。

| 目標 | 說明 |
|--------|-------------|
| BuildOnlySettings | 僅適用于實際組建，而不是在 Visual Studio 的專案載入上叫用 MSBuild 時的設定。 |
| PrepareForBuild | 準備建立的必要條件 |
| PreBuildEvent | 專案的擴充點，用來定義要在組建之前執行的工作 |
| ResolveProjectReferences | 分析專案相依性並建立參考的專案 |
| ResolveAssemblyReferences| 尋找參考的元件。 |
| ResolveReferences | 包含 `ResolveProjectReferences` 和 `ResolveAssemblyReferences` 以尋找所有相依性 |
| PrepareResources | 處理資源檔 |
| ResolveKeySource| 解析用來簽署元件的強式名稱金鑰，以及用來簽署[ClickOnce](../deployment/clickonce-security-and-deployment.md)資訊清單的憑證。 |
| 編譯 | 叫用編譯器 |
| ExportWindowsMDFile | 從編譯器所產生的 WinMDModule 檔案產生[WinMD](/uwp/winrt-cref/winmd-files)檔案。 |
| UnmanagedUnregistration | 移除/清除前一個組建中的[COM Interop](/dotnet/standard/native-interop/cominterop)登錄專案 |
| GenerateSerializationAssemblies | 使用[sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe)產生 XML 序列化元件。|
| CreateSatelliteAssemblies | 為資源中的每個唯一文化特性建立一個附屬元件。 |
| 產生資訊清單 | 產生[ClickOnce](../deployment/clickonce-security-and-deployment.md)應用程式和部署資訊清單或原生資訊清單。 |
| GetTargetPath | 傳回專案，其中包含此專案的組建產品（可執行檔或元件），以及中繼資料。 |
| PrepareForRun | 將組建輸出複製到最終目錄（如果已變更）。 |
| UnmanagedRegistration | 設定[COM Interop](/dotnet/standard/native-interop/cominterop)的登錄專案 |
| IncrementalClean | 移除在先前組建中產生但未在目前組建中產生的檔案。 這是 `Clean` 在累加式組建中進行工作的必要動作。 |
| Postbuildevent.bat | 專案的擴充點，定義要在組建之後執行的工作 |

上表中的許多目標都是在語言特定的匯入（例如， *Microsoft CSharp. .targets*）中找到。 這個檔案會定義 c # .NET 專案特定的標準組建程式中的步驟。 例如，它包含 `Compile` 實際呼叫 c # 編譯器的目標。

## <a name="user-configurable-imports"></a>使用者可設定的匯入

除了標準匯入以外，您還可以新增數個匯入，以自訂群組建進程。

- *.Props*
- *Directory.Build.targets*

這些檔案是由其底下任何子資料夾中任何專案的標準匯入所讀取。 這通常是在設定的解決方案層級上，用於控制解決方案中的所有專案，但也可以在檔案系統中更高的時間，直到磁片磁碟機的根目錄為止。

*.Props*會匯入 *.props*檔案，因此在專案檔中可使用其中定義的屬性。 它們可以在專案檔中重新定義，以根據每個專案自訂值。 *目錄. 組建 .targets*檔案會在專案檔之後讀入。 它通常包含目標，但您也可以定義不想要個別專案重新定義的屬性。

## <a name="customizations-in-a-project-file"></a>專案檔中的自訂

當您在 [**方案總管**]、[**屬性**] 視窗或 [**專案屬性**] 中進行變更時，Visual Studio 更新專案檔，但您也可以直接編輯專案檔來進行變更。

藉由在專案的專案檔中設定 MSBuild 屬性，或在上一節中所述，您可以藉由建立 *.props*檔案來設定多個組建行為，以針對專案和方案的整個資料夾設定全域屬性。 對於命令列或腳本上的臨機操作組建，您也可以在 `/p` 命令列上使用選項，以設定 MSBuild 的特定調用的屬性。 如需您可以設定之屬性的相關資訊，請參閱[一般 MSBuild 專案屬性](common-msbuild-project-properties.md)。

## <a name="next-steps"></a>後續步驟

MSBuild 進程有其他幾個擴充點，而不是此處所述。 請參閱[自訂您的組建](customize-your-build.md)。 以及[如何擴充 Visual Studio 的組建進程](how-to-extend-the-visual-studio-build-process.md)。

## <a name="see-also"></a>另請參閱

[Msbuild.exe](msbuild.md)