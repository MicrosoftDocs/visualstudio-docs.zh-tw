---
description: Visual c + + 專案系統用於 .vcxproj 檔案。
title: Visual c + + 專案擴充性
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc538402ae39753f14a3bccd8bcd17ddb0081078
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221232"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio c + + 專案系統擴充性和工具組整合

Visual c + + 專案系統用於 .vcxproj 檔案。 它是以 [Visual Studio Common Project System (CPS) ](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) 為基礎，並提供額外的 c + + 專屬擴充點，可讓您輕鬆地整合新工具組、組建架構和目標平臺。

## <a name="c-msbuild-targets-structure"></a>C + + MSBuild 目標結構

所有的 .vcxproj 檔案都會匯入這些檔案：

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

這些檔案本身只會定義。 相反地，他們會根據這些屬性值匯入其他檔案：

- `$(ApplicationType)`

   範例： Windows Store、Android、Linux

- `$(ApplicationTypeRevision)`

   這必須是有效的版本字串，格式為主要. 次要 [.... a.............。

   範例：1.0、10.0.0。0

- `$(Platform)`

   基於歷史原因，名為 "Platform" 的組建架構。

   範例： Win32、x86、x64、ARM

- `$(PlatformToolset)`

   範例： v140、v141、v141_xp、llvm

這些屬性值指定根資料夾下的資料夾名稱 `$(VCTargetsPath)` ：

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*應用程式類型*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*平臺*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*平臺*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

`$(VCTargetsPath)` \\ 如果是空的，則會使用 [*平臺*] \\ 資料夾 `$(ApplicationType)` ，適用于 Windows 桌面專案。

### <a name="add-a-new-platform-toolset"></a>新增平臺工具組

若要加入新的工具組（例如，現有 Win32 平臺的 "MyToolset"），請在 [平臺 `$(VCTargetsPath)` *\\ \\ Win32 \\ PlatformToolsets \\*] 下建立 MyToolset 資料夾，然後在其中建立工具組 *。 .props* 和 *工具組 .targets* 檔案。

*PlatformToolsets* 下的每個資料夾名稱都會出現在 [**專案屬性**] 對話方塊中，做為指定平臺的可用 **平臺工具** 組，如下所示：

![專案屬性頁對話方塊中的平臺工具組屬性](media/vc-project-extensibility-platform-toolset-property.png "專案屬性頁對話方塊中的平臺工具組屬性")

在此工具組支援的每個現有平臺資料夾中，建立類似的 *MyToolset* 資料夾和工具組。 *.props* 和 *工具組 .targets* 檔案。

### <a name="add-a-new-platform"></a>新增平臺

若要加入新的平臺（例如 "MyPlatform"），請在平臺 `$(VCTargetsPath)` *\\ \\* 下建立 MyPlatform 資料夾，並在其中建立 *.props*、 *platform. .props* 和 *platform .targets* 檔案。 也請建立 `$(VCTargetsPath)` *\\ 平臺 \\* <strong><em>MyPlatform</em></strong> *\\ PlatformToolsets \\* 資料夾，並在其中建立至少一個工具組。

[ *平臺* ] 資料夾底下的所有資料夾名稱 `$(ApplicationType)` ， `$(ApplicationTypeRevision)` 會在 IDE 中顯示為專案的可用 **平臺** 選項。

![[新增專案平臺] 對話方塊中的新平臺選擇](media/vc-project-extensibility-new-project-platform.png "[新增專案平臺] 對話方塊中的新平臺選擇")

### <a name="add-a-new-application-type"></a>新增應用程式類型

若要加入新的應用程式類型， 請在 [ `$(VCTargetsPath)` *\\ 應用程式 \\ 類型*] 下建立 MyApplicationType 資料夾，並在其中建立 *預設 .props* 檔案。 至少需要一個應用程式類型的修訂，因此也請建立 `$(VCTargetsPath)` *\\ 應用程式類型 \\ MyApplicationType \\ 1.0* 資料夾，並在其中建立 *.props* 檔案。 您也應該建立一個 `$(VCTargetsPath)` *\\ ApplicationType \\ MyApplicationType \\ 1.0 \\* platform 資料夾，並在其中建立至少一個平臺。

`$(ApplicationType)` 和 `$(ApplicationTypeRevision)` 屬性不會顯示在使用者介面中。 這些專案會在專案範本中定義，而且無法在專案建立之後變更。

## <a name="the-vcxproj-import-tree"></a>.Vcxproj 匯入樹狀結構

Microsoft c + + .props 和目標檔案的簡化匯入樹狀結構如下所示：

> `$(VCTargetsPath)`\\ *.Props。* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\ *.Props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\*預設值* \\ \* 。*.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*應用程式類型* \\ `$(ApplicationType)` \\*預設值。 .props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*應用程式* \\ `$(ApplicationType)` \\ 類型 `$(ApplicationTypeRevision)` \\*預設值。 .props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*應用程式* \\ `$(ApplicationType)` \\ 類型 `$(ApplicationTypeRevision)` \\ \\ `$(Platform)` 平臺 \\ *.Props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\*預設值* \\ \* 。*.props*

Windows 桌面專案未定義 `$(ApplicationType)` ，因此只會匯入

> `$(VCTargetsPath)`\\ *.Props。* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\ *.Props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\*預設值* \\ \* 。*.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ `$(Platform)` 平臺 \\ *.Props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\*預設值* \\ \* 。*.props*

我們將使用 `$(_PlatformFolder)` 屬性來保存 `$(Platform)` 平臺資料夾位置。 這個屬性是

> `$(VCTargetsPath)`\\*平臺*\\`$(Platform)`

適用于 Windows 桌面應用程式，以及

> `$(VCTargetsPath)`\\*應用程式* \\ `$(ApplicationType)` \\ 類型 `$(ApplicationTypeRevision)` \\*平臺*\\`$(Platform)`

適用于其他專案。

.Props 檔案會依下列順序匯入：

> `$(VCTargetsPath)`\\ *.Props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. .props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ *.Props。* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* 。*.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\*工具組. .props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* 。*.props*

目標檔案會依下列順序匯入：

> `$(VCTargetsPath)`\\*Microsoft .Cpp* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft .Cpp. 目前的目標* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. 目標* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft .Cpp* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* 。*目標* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\*工具組。目標* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* 。*目標*

如果您需要為工具組定義一些預設屬性，您可以將檔案新增至適當的 ImportBefore 和 ImportAfter 資料夾。

## <a name="author-toolsetprops-and-toolsettargets-files"></a>撰寫工具組. .props 和工具組 .targets 檔案

*工具組. .props* 和 *工具組 .targets* 檔案可以完全掌控在使用此工具組時，在組建期間發生的狀況。 它們也可以控制可用的偵錯工具，其中一些 IDE 使用者介面，例如 [ **屬性頁** ] 對話方塊中的內容，以及一些其他專案行為的層面。

雖然工具組可以覆寫整個組建程式，但通常您只想要讓工具組修改或新增一些組建步驟，或使用不同的組建工具，做為現有組建程式的一部分。 為了達成此目標，您的工具組可以匯入一些常見的 .props 和目標檔案。 根據您想要的工具組執行的動作，這些檔案可能有助於作為匯入或作為範例使用：

- `$(VCTargetsPath)`\\*CppCommon*

  這個檔案會定義原生組建程式的主要部分，也會匯入：

  - `$(VCTargetsPath)`\\*CppBuild*

  - `$(VCTargetsPath)`\\*BuildSteps*

  - `$(MSBuildToolsPath)`\\*Microsoft. 一般目標*

- `$(VCTargetsPath)`\\ *.Props。*

   為使用 Microsoft 編譯器和目標視窗的工具組設定預設值。

- `$(VCTargetsPath)`\\*WindowsSDK. .props*

   此檔案會決定 Windows SDK 位置，並針對以 Windows 為目標的應用程式定義一些重要屬性。

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>使用預設 c + + 組建程式來整合工具組特定目標

預設的 c + + 組建進程定義于 *CppCommon* 中。 目標不會呼叫任何特定的組建工具;他們會指定主要的組建步驟、順序和相依性。

C + + 組建有三個主要步驟，以下列目標表示：

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

因為每個組建步驟可以獨立執行，所以在一個步驟中執行的目標無法依賴在不同步驟中執行的目標中所定義的專案群組和屬性。 此部門允許某些組建效能優化。 雖然預設不會使用，但仍建議您採用這種分隔。

在每個步驟內執行的目標都是由這些屬性所控制：

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

每個步驟也都有屬性之前和之後。

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

如需每個步驟中所包含之目標的範例，請參閱 *CppBuild* 檔：

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

如果您查看目標，例如 `_ClCompile` ，您會看到它們本身不會直接執行任何動作，而是取決於其他目標，包括 `ClCompile` ：

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` 和其他組建工具特定目標定義為 *CppBuild* 中的空目標：

```xml
<Target Name="ClCompile"/>
```

因為 `ClCompile` 目標是空的，除非工具組覆寫它，否則不會執行實際的組建動作。 工具組目標可以覆寫 `ClCompile` 目標，也就是在匯 `ClCompile` 入 *CppBuild* 之後，可以包含其他定義：

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

儘管其名稱是在 Visual Studio 執行跨平臺支援之前建立的，但 `ClCompile` 目標不需要呼叫 CL.exe。 它也可以使用適當的 MSBuild 工作來呼叫 Clang、gcc 或其他編譯器。

`ClCompile`目標不應該有任何相依性，但必須要有 `SelectClCompile` 單一檔案編譯命令才能在 IDE 中運作的相依性。

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>要在工具組目標中使用的 MSBuild 工作

若要叫用實際的組建工具，目標必須呼叫 MSBuild 工作。 有一個基本的 [Exec](../msbuild/exec-task.md) 工作，可讓您指定要執行的命令列。 不過，組建工具通常有許多選項、輸入。 和輸出可追蹤增量組建，因此對它們具有特殊工作會更有意義。 例如，工作會將 `CL` MSBuild 屬性轉譯成 CL.exe 參數、將它們寫入回應檔中，然後呼叫 CL.exe。 它也會追蹤所有輸入和輸出檔案，以供稍後的累加組建之用。 如需詳細資訊，請參閱 [增量組建和最](#incremental-builds-and-up-to-date-checks)新的檢查。

Microsoft.Cpp.Common.Tasks.dll 會執行下列工作：

- `BSCMake`

- `CL`

- `ClangCompile` (clang-gcc 交換器) 

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (例如 Exec，但使用輸入和輸出追蹤) 

- `SetEnv`

- `GetOutOfDateItems`

如果您的工具與現有的工具執行相同的動作，而且具有類似命令列參數 (clang-cl 和 CL do) ，您可以針對兩者使用相同的工作。

如果您需要為組建工具建立新的工作，可以從下列選項中選擇：

1. 如果您很少使用這項工作，或如果您的組建不太需要幾秒鐘的時間，您可以使用 MSBuild 「內嵌」工作：

   - Xaml 工作 (自訂群組建規則) 

     如需 Xaml 工作宣告的其中一個範例，請參閱 `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml* 以及其使用方式，請參閱 `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm*。

   - [程式碼工作](../msbuild/msbuild-inline-tasks.md)

1. 如果您想要更好的工作效能，或只需要更複雜的功能，請使用一般的 MSBuild 工作 [撰寫](../msbuild/task-writing.md) 流程。

   如果工具命令列並未列出工具的所有輸入和輸出（如 `CL` 、 `MIDL` 和 `RC` 案例），而且如果您想要自動輸入和輸出檔案追蹤以及建立 tlog 檔案，請從類別衍生您的工作 `Microsoft.Build.CPPTasks.TrackedVCToolTask` 。 目前，在有基本 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) 類別的檔時，類別的詳細資料並沒有範例或檔 `TrackedVCToolTask` 。 如果這是特別感興趣的，請將您的語音新增至 [開發人員群體](https://aka.ms/feedback/suggest?space=62)上的要求。

## <a name="incremental-builds-and-up-to-date-checks"></a>增量組建和最新的檢查

預設的 MSBuild 累加式組建目標使用 `Inputs` 和 `Outputs` 屬性。 如果您指定它們，MSBuild 只會在任何輸入具有比所有輸出較新的時間戳記時，才會呼叫目標。 由於來源檔案通常會包含或匯入其他檔案，而組建工具會根據工具選項產生不同的輸出，因此很難在 MSBuild 目標中指定所有可能的輸入和輸出。

為了管理這個問題，c + + 組建使用不同的技術來支援累加組建。 大部分的目標都不會指定輸入和輸出，因此在組建期間一律會執行。 依目標呼叫的工作會將所有輸入和輸出的相關資訊，寫入至副檔名為 tlog 的 *tlog* 檔案中。 稍後的組建會使用 tlog 檔案來檢查已變更的內容，以及需要重建的內容，以及最新的內容。 在 IDE 中，tlog 檔案也是預設組建最新檢查的唯一來源。

若要判斷所有輸入和輸出，原生工具工作會使用 tracker.exe 和 MSBuild 提供的 [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) 類別。

Microsoft.Build.CPPTasks.Common.dll 定義 `TrackedVCToolTask` 公用抽象基類。 大部分的原生工具工作都是衍生自這個類別。

從 Visual Studio 2017 update 15.8 開始，您可以使用 `GetOutOfDateItems` 在 Microsoft.Cpp.Common.Tasks.dll 中執行的工作，為具有已知輸入和輸出的自訂目標產生 tlog 檔案。
或者，您也可以使用工作來建立它們 `WriteLinesToFile` 。 如需範例，請參閱 `_WriteMasmTlogs` `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm* 中的目標。

## <a name="tlog-files"></a>tlog 檔案

有三種類型的 tlog 檔案： *讀取*、 *寫入* 和 *命令列*。 讀取和寫入。 tlog 檔案是由累加組建和 IDE 中的最新檢查所使用。 命令列。 tlog 檔案只會用於累加式組建中。

MSBuild 提供這些 helper 類別來讀取和寫入 tlog 檔案：

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata)類別可以用來存取讀取和寫入的 tlog 檔案，以及識別比輸出新的輸入，或是遺漏輸出。 它會在最新的檢查中使用。

命令列。 tlog 檔案包含組建中使用之命令列的相關資訊。 它們只會用於累加組建，而不是最新的檢查，因此內部格式是由產生它們的 MSBuild 工作所決定。

### <a name="read-tlog-format"></a>Read. tlog 格式

*讀取* (的 tlog 檔案。 \* 讀取 ... \*tlog) 包含來源檔案及其相依性的相關資訊。

行開頭的插入號 (**^**) 表示一或多個來源。 共用相同相依性的來源會以分隔號 (**\|**) 分隔。

相依性檔案會列在來源之後，每個都在自己的行上。 所有檔案名都是完整路徑。

例如，假設您在 *F： \\ test \\ ConsoleApplication1 \\ ConsoleApplication1* 中找到您的專案來源。 如果您的原始程式檔（ *Class1*）包含下列內容：

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

然後， *CL. 1.. 1... 1.*

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

不需要在大寫的情況下寫入檔案名，而是一些工具的便利性。

### <a name="write-tlog-format"></a>寫入. tlog 格式

*寫入* 。 tlog (\* 寫入。 \*) 檔案的 tlog 會連接來源和輸出。

行開頭的插入號 (**^**) 表示一或多個來源。 多個來源以分隔號分隔 (**\|**) 。

來源所建立的輸出檔案應該列在來源之後，每個都在自己的行上。 所有檔案名都必須是完整路徑。

例如，針對具有額外原始程式檔 *Class1* 的簡單 ConsoleApplication 專案，則 *連結. 1.. 1.. 1.* . a。

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>設計階段組建

在 IDE 中，.vcxproj projects 會使用一組 MSBuild 目標來取得專案的其他資訊，並重新產生輸出檔。 其中有些目標僅用於設計階段組建中，但其中有許多是用於一般組建和設計階段組建中。

如需設計階段組建的一般資訊，請參閱適用于 [設計階段組建](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)的 CPS 檔集。 本檔僅部分適用于 Visual c + + 專案。

`CompileDesignTime` `Compile` 針對 .vcxproj 專案，設計階段組建檔中所述的和目標絕對不會執行。 Visual c + +. .vcxproj projects 使用不同的設計階段目標來取得 IntelliSense 資訊。

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense 資訊的設計階段目標

.Vcxproj 專案中使用的設計階段目標是在 `$(VCTargetsPath)` \\ *DesignTime* 中定義。

`GetClCommandLines`目標會收集 IntelliSense 的編譯器選項：

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` -僅限設計階段目標，設計階段組建初始化所需。 除此之外，這些目標會停用一些一般組建功能來改善效能。

- `ComputeCompileInputsTargets` –一組修改編譯器選項和專案的目標。 這些目標會在設計階段和一般組建中執行。

目標會呼叫工作 `CLCommandLine` 來建立要用於 IntelliSense 的命令列。 同樣地，即使它的名稱，它也可以處理 CL 選項，但是也可以處理 Clang 和 gcc 選項。 編譯器參數的類型是由屬性所控制 `ClangMode` 。

目前，即使在 Clang 模式中，工作所產生的命令列 `CLCommandLine` 一律會使用 CL 切換 () ，因為它們比較容易剖析 IntelliSense 引擎。

如果您要加入在編譯之前執行的目標（無論是一般或設計階段），請確定它不會中斷設計階段組建或影響效能。 測試目標最簡單的方式是開啟開發人員命令提示字元，然後執行此命令：

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

此命令會產生詳細的組建記錄 *檔，也* 就是結尾有目標和工作的效能摘要。

請務必 `Condition ="'$(DesignTimeBuild)' != 'true'"` 在所有只對一般組建有意義的作業中使用，而不是針對設計階段組建使用。

### <a name="design-time-targets-that-generate-sources"></a>產生來源的設計階段目標

*桌面原生專案預設會停用這項功能，而且在快取的專案上目前不支援此功能*。

如果已 `GeneratorTarget` 針對專案專案定義中繼資料，則當載入專案時，以及變更原始程式檔時，會自動執行此目標。

::: moniker range="vs-2017"

比方說，若要從 .xaml 檔案自動產生 .cpp 或 .h 檔案， `$(VSInstallDir)` \\ *MSBuild* \\ *microsoft* \\ *WindowsXaml* \\ *v 15.0* 會 \\ \* \\ 定義這些實體，如下所示：

::: moniker-end

::: moniker range=">=vs-2019"

比方說，若要從 .xaml 檔案自動產生 .cpp 或 .h 檔案， `$(VSInstallDir)` \\ *MSBuild* \\ *microsoft* \\ *WindowsXaml* \\ *v 16.0* 會 \\ \* \\ 定義這些實體，如下所示：

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

若要使用 `Task.HostObject` 來取得原始程式檔的未儲存內容，應針對 .pkgdef 中的指定專案，將目標和工作註冊為 [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) ：

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual Studio IDE 中的 visual c + + 專案擴充性

Visual c + + 專案系統是以 [VS 專案系統](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)為基礎，並使用其擴充點。 不過，專案階層的執行是 Visual c + + 特有的，而不是以 CPS 為基礎，因此階層擴充性限制為專案專案。

### <a name="project-property-pages"></a>專案屬性頁

如需一般的設計資訊，請參閱 [適用于 VC + + 專案的架構多目標](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/)。

簡單來說，您在 c + + 專案的 [ **專案屬性** ] 對話方塊中看到的屬性頁面是由 *規則* 檔所定義。 規則檔會指定屬性頁面上要顯示的一組屬性，以及它們在專案檔中的儲存方式和位置。 規則檔案是使用 Xaml 格式的 .xml 檔案。 用來序列化它們的類型會在 [XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes)中說明。 如需在專案中使用規則檔的詳細資訊，請參閱 [屬性頁 XML 規則](/cpp/build/reference/property-page-xml-files)檔。

規則檔案必須加入至 `PropertyPageSchema` 專案群組：

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` 中繼資料會限制規則可見度，也就是由規則類型所控制，且可以有下列其中一個值：

`Project` | `File` | `PropertySheet`

CPS 支援內容類型的其他值，但不會用於 Visual c + + 專案。

如果規則應該在一個以上的內容中顯示，請使用分號 (**;**) 來分隔內容值，如下所示：

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>規則格式和主要類型

規則格式相當簡單，因此本節只會說明影響規則在使用者介面中的外觀屬性。

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`屬性會定義規則在 [**屬性頁**] 對話方塊中的顯示方式。 屬性可以具有下列其中一個值：

| 屬性 | 描述 |
|------------| - |
| `generic` | 所有屬性都會顯示在單一頁面的 [類別目錄] 標題下<br/>和內容可以看到此規則 `Project` `PropertySheet` ，但無法顯示 `File` 。<br/><br/> 範例： `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | 類別目錄會顯示為子頁面。<br/>您可以在所有內容中看到此規則： `Project` 、 `PropertySheet` 和 `File` 。<br/>只有當專案中有定義為的專案時，才會在專案屬性中看到此規則 `ItemType` `Rule.DataSource` ，除非該規則名稱包含在 `ProjectTools` 專案群組中。<br/><br/>範例： `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | 頁面會顯示為 [偵錯工具] 頁面的一部分。<br/>目前忽略類別目錄。<br/>規則名稱應該符合 Debug 啟動程式 MEF 物件的 `ExportDebugger` 屬性。<br/><br/>範例： `$(VCTargetsPath)` \\ *1033* \\ *偵錯工具 \_ 本機 \_windows.xml* |
| *自 定義* | 自訂範本。 範本的名稱應符合 `ExportPropertyPageUIFactoryProvider` `PropertyPageUIFactoryProvider` MEF 物件的屬性。 請參閱 **VisualStudio ProjectSystem。 IPropertyPageUIFactoryProvider**。<br/><br/> 範例： `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

如果規則使用其中一個屬性方格型範本，它可以針對其屬性使用這些擴充點：

- [屬性值編輯器](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [動態列舉值提供者](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>擴充規則

如果您想要使用現有的規則，但需要新增或移除 (也就是隱藏) 只有一些屬性，您可以建立 [延伸模組規則](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)。

#### <a name="override-a-rule"></a>覆寫規則

您可能想要讓工具組使用大部分的專案預設規則，但只取代其中一或多個專案。 例如，假設您只想要變更 C/c + + 規則以顯示不同的編譯器參數。 您可以提供與現有規則相同名稱和顯示名稱的新規則，並在匯 `PropertyPageSchema` 入預設的 cpp 目標之後，將它包含在專案群組中。 專案中只會使用一個具有指定名稱的規則，最後一個包含在專案群組中的規則 `PropertyPageSchema` 獲勝。

#### <a name="project-items"></a>專案項目

*ProjectItemsSchema.xml* 檔 `ContentType` 會定義 `ItemType` 視為專案專案的專案和值，並定義專案 `FileExtension` 來判斷新檔案新增至哪個專案群組。

預設的 ProjectItemsSchema 檔可在 `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml* 中找到。 若要擴充，您必須建立具有新名稱的架構檔案，例如 *MyProjectItemsSchema.xml*：

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

然後，在目標檔案中新增：

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

範例： `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>偵錯工具

Visual Studio 中的 Debug service 支援 Debug 引擎的擴充性。 如需詳細資訊，請參閱下列範例：

- [支援 lldb 偵錯工具的 MIEngine、開放原始碼專案](https://github.com/Microsoft/MIEngine)

- [Visual Studio debug engine 範例](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

若要指定 debug engine 和 debug 會話的其他屬性，您必須執行 [Debug 啟動](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) 程式 MEF 元件，並新增 `debugger` 規則。 如需範例，請參閱 `$(VCTargetsPath)` \\ 1033 \\ 偵錯工具 \_ 本機 \_windows.xml 檔。

### <a name="deploy"></a>部署

。 .vcxproj 專案會針對 [部署提供者](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)使用 Visual Studio 專案系統擴充性。

### <a name="build-up-to-date-check"></a>建立最新的檢查

根據預設，組建最新的檢查需要在 `$(TlogLocation)` 組建期間于所有組建輸入和輸出的資料夾中建立 read. tlog 和 write 檔。

若要使用自訂的最新檢查：

1. 在工具組 .targets 檔案中新增功能，以停用預設的最新檢查 `NoVCDefaultBuildUpToDateCheckProvider` ： 

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. 執行您自己的 [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)。

## <a name="project-upgrade"></a>專案升級

### <a name="default-vcxproj-project-upgrader"></a>預設值： .vcxproj 專案 upgrader

.Vcxproj 專案 upgrader 變更 `PlatformToolset` 、 `ApplicationTypeRevision` 、MSBuild 工具組版本和 .net framework。 最後兩個一律會變更為 Visual Studio 版本的預設值， `PlatformToolset` 但 `ApplicationTypeRevision` 可以由特殊的 MSBuild 屬性來控制。

Upgrader 會使用這些準則來決定是否可以升級專案：

1. 針對定義和的 `ApplicationType` 專案 `ApplicationTypeRevision` ，會有一個資料夾的修訂編號高於目前的資料夾。

1. 屬性 `_UpgradePlatformToolsetFor_<safe_toolset_name>` 是針對目前的工具組所定義，而且其值不等於目前的工具組。

   在這些屬性名稱中， *\<safe_toolset_name>* 代表所有非英數位元取代為底線 () 的工具組名稱 **\_** 。

當專案可以升級時，就會參與 [ *方案重定目標*]。 如需詳細資訊，請參閱 [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2)。

如果您想要在專案使用特定工具組時，裝飾 **方案 Explorer** 中的專案名稱，請定義 `_PlatformToolsetShortNameFor_<safe_toolset_name>` 屬性。

如需 `_UpgradePlatformToolsetFor_<safe_toolset_name>` 和 `_PlatformToolsetShortNameFor_<safe_toolset_name>` 屬性定義的範例，請參閱 *.props* 檔案。 如需使用方式的範例，請參閱 `$(VCTargetPath)` \\ *Microsoft .cpp* 檔案。

### <a name="custom-project-upgrader"></a>自訂專案 upgrader

若要使用自訂專案 upgrader 物件，請執行 MEF 元件，如下所示：

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

您的程式碼可以匯入並呼叫 .vcxproj upgrader 物件：

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` 是在 *Microsoft.VisualStudio.ProjectSystem.VS.dll* 中定義，類似于 `IVsRetargetProjectAsync` 。

定義 `VCProjectUpgraderObjectName` 屬性，以告知專案系統使用您的自訂 upgrader 物件：

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>停用專案升級

若要停用專案升級，請使用 `NoUpgrade` 下列值：

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>專案快取和擴充性

為了改善在 Visual Studio 2017 中使用大型 c + + 方案時的效能，已引進 [專案](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) 快取。 它會實作為以專案資料填入的 SQLite 資料庫，然後用來載入專案，而不需要將 MSBuild 或 CPS 專案載入記憶體中。

因為從快取載入的 .vcxproj 專案沒有任何 CPS 物件，所以會匯入 `UnconfiguredProject` 或無法建立擴充功能的 MEF 元件 `ConfiguredProject` 。 為了支援擴充性，當 Visual Studio 偵測到專案使用 (或可能使用) MEF 延伸模組時，不會使用專案快取。

這些專案類型一律會完全載入，並在記憶體中擁有 CPS 物件，因此會為它們建立所有 MEF 延伸模組：

- 啟始專案

- 具有自訂專案 upgrader 的專案，也就是它們會定義 `VCProjectUpgraderObjectName` 屬性

- 不是以桌面視窗為目標的專案，也就是它們會定義 `ApplicationType` 屬性

- 共用專案專案 (. vcxitems) ，以及藉由匯入 vcxitems 專案來參考這些專案的任何專案。

如果未偵測到這些條件，則會建立專案快取。 快取包含在介面上回應查詢所需的所有 MSBuild 專案資料 `get` `VCProjectEngine` 。 這表示，擴充功能所完成的 MSBuild .props 和目標檔案層級上的所有修改，都應該只在從快取載入的專案中工作。

## <a name="shipping-your-extension"></a>交付您的延伸模組

如需如何建立 VSIX 檔案的詳細資訊，請參閱 [交付 Visual Studio 擴充](../extensibility/shipping-visual-studio-extensions.md)功能。 如需如何將檔案新增到特殊安裝位置的相關資訊，例如，若要在底下新增檔案 `$(VCTargetsPath)` ，請參閱在 [擴充功能資料夾外部安裝](../extensibility/set-install-root.md)。

## <a name="additional-resources"></a>其他資源

Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) 為專案檔提供組建引擎和可擴充的 XML 格式。 您應該熟悉基本的 [msbuild 概念](../msbuild/msbuild-concepts.md) ，以及 [MSBuild For Visual c + +](/cpp/build/reference/msbuild-visual-cpp-overview) 的運作方式，以便擴充 Visual c + + 專案系統。

Managed 擴充性架構 ([MEF](/dotnet/framework/mef/)) 提供 CPS 和 Visual c + + 專案系統所使用的延伸模組 api。 For an overview of how MEF is used by CPS, see [CPS and MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) in the [VSProjectSystem overview of MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

您可以自訂現有的組建系統，以新增組建步驟或新的檔案類型。 如需詳細資訊，請參閱 [MSBuild (Visual c + +) 總覽](/cpp/build/reference/msbuild-visual-cpp-overview) 和 [使用專案屬性](/cpp/build/working-with-project-properties)。
