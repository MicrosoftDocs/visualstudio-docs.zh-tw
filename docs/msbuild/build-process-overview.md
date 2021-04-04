---
title: MSBuild 如何建置專案
description: 瞭解 MSBuild 如何處理您的專案檔案，不論是從 Visual Studio 或從命令列或腳本叫用。
ms.custom: SEO-VS-2020
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bc7fe3898bec19b4eb0130e7279974823669e7f
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082535"
---
# <a name="how-msbuild-builds-projects"></a>MSBuild 如何建置專案

MSBuild 實際上如何運作？ 在本文中，您將瞭解 MSBuild 如何處理您的專案檔（不論是從 Visual Studio 叫用，還是從命令列或腳本叫用）。 瞭解 MSBuild 的運作方式可協助您更妥善地診斷問題，並更妥善地自訂您的組建流程。 本文描述組建流程，而且大部分都適用于所有專案類型。

完整的組建套裝程式含 [初始啟動](#startup)、 [評估](#evaluation-phase)和 [執行](#execution-phase) 建立專案的目標和工作。 除了這些輸入之外，外部匯入也會定義組建程式的詳細資料，包括 [標準匯入](#standard-imports) （例如 *Microsoft* ），以及方案或專案層級的 [使用者可](#user-configurable-imports) 設定匯入。

## <a name="startup"></a>啟動

您可以透過 *Microsoft.Build.dll* 中的 msbuild 物件模型，或直接在命令列上叫用可執行檔，或在腳本中叫用可執行檔（例如在 CI 系統中），從 Visual Studio 叫用 msbuild。 無論是哪一種情況，會影響組建進程的輸入都會包含專案檔 (或 Visual Studio) 的內部專案物件，可能是方案檔、環境變數，以及命令列參數或其物件模型對等專案。 在啟動階段，您可以使用命令列選項或物件模型對等專案來設定 MSBuild 設定，例如設定記錄器。 使用或參數在命令列上設定的屬性 `-property` `-p` 會設定為全域屬性，這會覆寫任何會在專案檔中設定的值，即使稍後會讀取專案檔也是一樣。

接下來的章節是關於輸入檔，例如解決方案檔或專案檔。

### <a name="solutions-and-projects"></a>方案和專案

MSBuild 實例可能包含一個專案，或許多專案作為解決方案的一部分。 方案檔不是 MSBuild XML 檔案，但 MSBuild 會將它解讀為知道針對指定的設定和平臺設定所需要建立的所有專案。 當 MSBuild 處理這個 XML 輸入時，就是所謂的解決方案組建。 它有一些可擴充點可讓您在每個方案組建中執行某些工作，但由於此組建與個別專案組建的個別執行不同，因此，方案組建中的屬性或目標定義設定與每個專案組建都有關。

您可以在 [自訂解決方案組建](customize-your-build.md#customize-the-solution-build)時，瞭解如何擴充解決方案組建。

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio 組建與 MSBuild.exe 組建的比較

當您在 Visual Studio 中建立專案時，會有一些顯著的差異，也就是當您直接叫用 MSBuild 時，可以透過 MSBuild 可執行檔，或是當您使用 MSBuild 物件模型來啟動組建時。 Visual Studio 管理 Visual Studio 組建的專案組建順序;它只會在個別的專案層級呼叫 MSBuild，當它執行時，會有幾個布林值屬性 (`BuildingInsideVisualStudio` `BuildProjectReferences`) ，這會大幅影響 MSBuild 的用途。 在每個專案中，執行都會與透過 MSBuild 叫用時相同，但參考的專案會發生差異。 在 MSBuild 中，需要參考的專案時，實際上會發生組建;也就是說，它會執行工作和工具，並產生輸出。 當 Visual Studio 組建找到參考的專案時，MSBuild 只會傳回所參考專案的預期輸出;它可讓 Visual Studio 控制這些其他專案的建立。 Visual Studio 決定組建順序，並視需要在 MSBuild 中個別呼叫 () ，全都完全以 Visual Studio 的控制項為依據。

另一個差異是當使用方案檔叫用 MSBuild 時，MSBuild 會剖析方案檔、建立標準的 XML 輸入檔、評估它，然後以專案的形式執行它。 方案組建會在任何專案之前執行。 從 Visual Studio 建立時，不會發生這種情況;MSBuild 永遠看不到方案檔。 因此， (使用之前的解決方案組建自訂 *。名稱名稱* 和 *之後。[名稱名稱* ]) 只適用于 MSBuild.exe 或物件模型驅動，而不是 Visual Studio 的組建。

### <a name="project-sdks"></a>專案 SDK

MSBuild 專案檔案的 SDK 功能相當新。 在這項變更之前，專案檔會明確匯入為特定專案類型定義組建流程的 *.targets* 和 *. .props* 檔案。

.NET Core 專案會匯入適當的 .NET SDK 版本。 請參閱總覽、 [.Net Core 專案 sdk](/dotnet/core/project-sdk/overview)和 [屬性](/dotnet/core/project-sdk/msbuild-props)的參考。

## <a name="evaluation-phase"></a>評估階段

本節將討論如何處理和剖析這些輸入檔，以產生記憶體中的物件，以判斷將建立的內容。

評估階段的目的是要根據輸入 XML 檔案和本機環境，在記憶體中建立物件結構。 評估階段包含六個傳遞，可處理輸入檔（例如專案 XML 檔案或），以及匯入的 XML 檔案（一般以 *. .props* 或 *.targets* 檔案命名），這取決於它們主要是設定屬性或定義組建目標。 每個階段都會建立記憶體內建物件的一部分，稍後用於執行階段以建立專案，但在評估階段中不會發生實際的組建動作。 在每個階段中，會依其出現的順序來處理專案。

評估階段中的階段如下所示：

- 評估環境變數
- 評估匯入和屬性
- 評估專案定義
- 評估專案
- 評估 [UsingTask](usingtask-element-msbuild.md) 元素
- 評估目標

這些行程的順序有很大的影響，而且在自訂專案檔時必須知道。 請參閱 [屬性和專案評估順序](comparing-properties-and-items.md#property-and-item-evaluation-order)。

### <a name="evaluate-environment-variables"></a>評估環境變數

在這個階段中，會使用環境變數來設定對等的屬性。 例如，PATH 環境變數可做為屬性 `$(PATH)` 。 從命令列或腳本執行時，命令環境會如往常般使用，而從 Visual Studio 執行時，則會使用 Visual Studio 啟動時生效的環境。

### <a name="evaluate-imports-and-properties"></a>評估匯入和屬性

在這個階段中，會讀取整個輸入 XML，包括專案檔和整個匯入鏈。 MSBuild 會建立記憶體中的 XML 結構，以代表專案的 XML 和所有匯入的檔案。 目前不在目標中的屬性會進行評估和設定。

因為 MSBuild 在其進程中提早讀取所有的 XML 輸入檔，所以在建立程式期間對這些輸入進行的任何變更都不會影響目前的組建。

任何目標以外的屬性會以不同于目標內的屬性來處理。 在這個階段中，只會評估在任何目標之外定義的屬性。

因為屬性會在屬性傳遞中依序處理，所以輸入中任何點的屬性都可以存取之前出現在輸入中的屬性值，而不是稍後顯示的屬性。

因為屬性會在評估專案之前處理，所以您無法在屬性傳遞的任何部分期間存取任何專案的值。 

### <a name="evaluate-item-definitions"></a>評估專案定義

在這個階段中，會解釋 [專案定義](item-definitions.md) ，並建立這些定義的記憶體中標記法。

### <a name="evaluate-items"></a>評估專案

在目標內定義的專案，處理方式會與任何目標外部的專案不同。 在這個階段中，會處理任何目標外部的專案及其相關聯的中繼資料。  專案定義所設定的中繼資料會由專案的中繼資料設定覆寫。 因為專案是依其出現的順序來處理，所以您可以參考先前定義過的專案，而不是稍後顯示的專案。 由於專案通過是在屬性通過之後，因此，如果在任何目標之外定義任何屬性，專案就可以存取任何屬性，而不論屬性定義是否稍後出現。

### <a name="evaluate-usingtask-elements"></a>評估 `UsingTask` 元素

在這個階段中，會讀取 [UsingTask](usingtask-element-msbuild.md) 元素，並宣告工作以供稍後在執行階段使用。

### <a name="evaluate-targets"></a>評估目標

在這個階段中，會在記憶體中建立所有目標物件結構，以準備執行。 不會發生實際的執行。 

## <a name="execution-phase"></a>執行階段

在執行階段中，會排序並執行目標，並執行所有工作。 但是首先，在目標中定義的屬性和專案會以其出現的順序在單一階段中進行評估。 處理的順序與處理不在目標中的屬性和專案有何不同：首先是所有屬性，然後再以個別的行程進行所有的專案。 目標中的屬性和專案的變更，可以在其變更的目標之後觀察到。

### <a name="target-build-order"></a>目標組建順序

在單一專案中，目標會循序執行。 中央問題是如何判斷要在其中建立所有專案的順序，以便將相依性用來依正確順序建立目標。  

目標群組建順序是由在 `BeforeTargets` `DependsOnTargets` `AfterTargets` 每個目標上使用、和屬性來決定。 如果先前的目標修改了這些屬性中所參考的屬性，則未來目標的順序可能會受到影響。

排序的規則會在 [判斷目標群組建順序](target-build-order.md#determine-the-target-build-order)中描述。 此處理程式是由包含要建立之目標的堆疊結構所決定。 此工作頂端的目標會開始執行，如果它相依于其他任何東西，則這些目標會推送至堆疊的頂端，並開始執行。  當沒有任何相依性的目標時，它會執行到完成，而且其父目標會繼續。

### <a name="project-references"></a>專案參考

MSBuild 可以採用的程式碼路徑有兩種：一般的路徑，如下一節所述的圖形選項。

個別專案會透過專案來指定其對其他專案的相依性 `ProjectReference` 。 當堆疊頂端的專案開始建立時，它會達到目標執行所在的位置，也就 `ResolveProjectReferences` 是一般目標檔案中定義的標準目標。

`ResolveProjectReferences` 使用專案的輸入來叫用 MSBuild 工作 `ProjectReference` ，以取得輸出。 `ProjectReference`專案會轉換成本機專案，例如 `Reference` 。 當執行時間開始處理參考的專案時，目前專案的 MSBuild 執行階段會暫停 (評估階段會視需要) 執行。 只有在您開始建立相依專案之後，才會建立參考的專案，如此就會建立建立專案的樹狀結構。

Visual Studio 可讓您在方案 ( .sln) 檔案中建立專案相依性。 這些相依性是在方案檔中指定，而且只有在建立方案或在 Visual Studio 內建立時才會遵守。 如果您建立單一專案，則會忽略這種類型的相依性。 解決方案參考會由 MSBuild 轉換成 `ProjectReference` 專案，之後則會以相同的方式處理。

### <a name="graph-option"></a>Graph 選項

如果您指定 (或) 的圖形組建參數 `-graphBuild` `-graph` ，則 `ProjectReference` 會成為 MSBuild 所使用的第一級概念。 MSBuild 將剖析所有專案並建立組建順序圖形（專案的實際相依性圖形），然後進行往返以判斷組建順序。 如同個別專案中的目標，MSBuild 可確保參考的專案會在其相依的專案之後建立。

## <a name="parallel-execution"></a>平行執行

如果使用多處理器支援 (`-maxCpuCount` 或 `-m` 切換) ，msbuild 會建立節點，也就是使用可用 CPU 核心的 msbuild 進程。 每個專案都會提交至可用的節點。 在節點內，個別的專案組建會以序列方式執行。

您可以藉由設定布林 <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> 值變數（根據 MSBuild 中的屬性值設定），來啟用平行執行的工作 `$(BuildInParallel)` 。 針對啟用平行執行的工作，工作排程器會管理節點並將工作指派給節點。

請參閱 [使用 MSBuild 平行建立多個專案](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>標準匯入

*.Props* 和 *microsoft* 通常會在 SDK 樣式專案中明確或隱含地匯入 .net 專案檔 (，) 並位於 Visual Studio 安裝的 *MSBuild\Current\bin* 資料夾中。 C + + 專案有自己的 imports 階層：請參閱 [c + + 專案的 MSBuild 內部](/cpp/build/reference/msbuild-visual-cpp-overview)。

*.Props* 檔案會設定您可以覆寫的預設值。 它會在專案檔的開頭明確或隱含地) 匯入 (。 如此一來，您的專案設定就會出現在預設值之後，讓它們覆寫這些設定。

*Microsoft 一般 .targets* 檔案和它所匯入的目標檔案會定義 .net 專案的標準組建進程。 它也提供您可用來自訂群組建的擴充點。

在執行中，CurrentVersion 是一種精簡型包裝函 *式，可* 匯入 *。* 此檔案包含標準屬性的設定，並定義定義組建進程的實際目標。 `Build`目標是在這裡定義的，但其實是空的。 但是， `Build` 目標包含 `DependsOnTargets` 屬性，此屬性會指定組成實際組建步驟的個別目標，也就是、 `BeforeBuild` `CoreBuild` 和 `AfterBuild` 。 `Build`目標定義如下：

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

`BeforeBuild` 和 `AfterBuild` 是延伸點。 這些專案在 *CurrentVersion* 中是空的，但專案可以提供自己的目標，以及必須在 `BeforeBuild` `AfterBuild` 主要組建處理常式之前或之後執行的工作。 `AfterBuild` 是在無 op 目標之前執行， `Build` 因為 `AfterBuild` 會出現在目標的屬性中，但會出現在 `DependsOnTargets` `Build` 之後 `CoreBuild` 。

`CoreBuild`目標包含組建工具的呼叫，如下所示：

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

下表描述這些目標;某些目標只適用于特定的專案類型。

| 目標 | 描述 |
|--------|-------------|
| BuildOnlySettings | 實際組建的設定，而不是在 Visual Studio 于專案載入時叫用 MSBuild。 |
| PrepareForBuild | 準備組建的必要條件 |
| >prebuildevent.bat | 專案的擴充點，用來定義要在組建之前執行的工作 |
| ResolveProjectReferences | 分析專案相依性並建立參考的專案 |
| ResolveAssemblyReferences| 尋找參考的元件。 |
| ResolveReferences | 由 `ResolveProjectReferences` 和 `ResolveAssemblyReferences` 來尋找所有相依性 |
| PrepareResources | 處理資源檔 |
| ResolveKeySource| 解析用來簽署元件的強式名稱金鑰，以及用來簽署 [ClickOnce](../deployment/clickonce-security-and-deployment.md) 資訊清單的憑證。 |
| 編譯 | 叫用編譯器 |
| ExportWindowsMDFile | 從編譯器產生的 WinMDModule 檔案產生 [WinMD](/uwp/winrt-cref/winmd-files) 檔案。 |
| UnmanagedUnregistration | 移除/清除先前組建中的 [COM Interop](/dotnet/standard/native-interop/cominterop) 登錄專案 |
| GenerateSerializationAssemblies | 使用 [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe)產生 XML 序列化元件。|
| CreateSatelliteAssemblies | 為資源中的每個唯一文化特性建立一個附屬元件。 |
| 產生資訊清單 | 產生 [ClickOnce](../deployment/clickonce-security-and-deployment.md) 應用程式和部署資訊清單或原生資訊清單。 |
| GetTargetPath | 傳回包含此專案之組建產品 (可執行檔或元件) 的專案，其中包含中繼資料。 |
| PrepareForRun | 將組建輸出複製到最終目錄（如果已變更的話）。 |
| UnmanagedRegistration | 設定[COM Interop](/dotnet/standard/native-interop/cominterop)的登錄專案 |
| IncrementalClean | 移除先前組建中所產生但未在目前組建中產生的檔案。 這是 `Clean` 在累加式組建中進行工作的必要動作。 |
| PostBuildEvent | 專案的擴充點，可定義組建之後要執行的工作 |

上表中的許多目標都是在特定語言的匯入中找到，例如， *Microsoft. CSharp. 目標*。 此檔案會定義 c # .NET 專案特有的標準組建程式中的步驟。 例如，它包含 `Compile` 實際呼叫 c # 編譯器的目標。

## <a name="user-configurable-imports"></a>使用者可設定的匯入

除了標準匯入，您還可以新增數個匯入來自訂群組建流程。

- *.Props*
- *Directory.Build.targets*

這些檔案是由其下任何子資料夾中任何專案的標準匯入所讀取。 這通常是用來控制解決方案中所有專案的設定解決方案層級，但在檔案系統中也可能較高，最多可達磁片磁碟機的根目錄。

*.Props* 檔案是由 *.props* 匯入，因此專案檔中可使用定義于其中的屬性。 您可以在專案檔中重新定義它們，以根據每個專案自訂值。 在專案檔之後，會讀取 *目錄. 組建* 檔案。 它通常包含目標，但您也可以在這裡定義不想要個別專案重新定義的屬性。

## <a name="customizations-in-a-project-file"></a>專案檔中的自訂

Visual Studio 在 **方案總管**、[ **屬性** ] 視窗或 **專案屬性** 中進行變更時，會更新專案檔，但是您也可以直接編輯專案檔來進行自己的變更。

您可以藉由在專案檔中設定 MSBuild 屬性（在專案的本機設定）或上一節中所述的方式來設定許多組建行為，方法是建立 *.props* 檔案，以針對專案和方案的整個資料夾設定全域屬性。 針對命令列上的臨機操作組建或腳本，您也可以使用 `/p` 命令列上的選項來設定 MSBuild 特定調用的屬性。 如需您可以設定之屬性的相關資訊，請參閱 [一般 MSBuild 專案屬性](common-msbuild-project-properties.md) 。

## <a name="next-steps"></a>下一步

MSBuild 進程除了此處所述以外的其他數個擴充點。 請參閱 [自訂您的組建](customize-your-build.md)。 以及 [如何延伸 Visual Studio 組建進程](how-to-extend-the-visual-studio-build-process.md)。

## <a name="see-also"></a>另請參閱

[MSBuild](msbuild.md)
