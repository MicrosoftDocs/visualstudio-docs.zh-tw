---
title: 視覺化C++專案擴充性
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10869ad290b0b8df614d25d792d0b3ed1e88eb17
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825560"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual StudioC++專案系統擴充性和工具組整合

視覺效果C++專案系統會用於.vcxproj 檔案。 它根據[Visual Studio 通用專案系統 (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) ，並提供其他C++特定的擴充性點，新的工具集，整合更容易建置架構，以及平台為目標。

## <a name="c-msbuild-targets-structure"></a>C++MSBuild 目標結構

所有的.vcxproj 檔案匯入這些檔案：

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

這些檔案會定義小本身。 相反地，它們匯入其他檔案，根據這些屬性值：

- `$(ApplicationType)`

   例如：Windows 市集、 Android、 Linux

- `$(ApplicationTypeRevision)`

   這必須是有效的版本字串，表單 major.minor[.build[.revision]]。

   例如：1.0, 10.0.0.0

- `$(Platform)`

   組建架構中，名為 「 平台 」，由於歷史原因。

   例如：Win32，x86、 x64、 ARM

- `$(PlatformToolset)`

   範例： v140、 v141、 v141_xp、 llvm

這些屬性值會指定下的資料夾名稱`$(VCTargetsPath)`根資料夾：

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*應用程式類型*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*平台*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*平台*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

`$(VCTargetsPath)` \\*平台*\\會使用資料夾時`$(ApplicationType)`是空的 Windows 桌面專案。

### <a name="add-a-new-platform-toolset"></a>加入新的平台工具組

若要新增新的工具組，例如，"MyToolset 」 針對現有的 Win32 平台，建立*MyToolset*下方的資料夾`$(VCTargetsPath)` *\\平台\\Win32\\PlatformToolsets\\* ，然後建立*Toolset.props*並*Toolset.targets*檔案。

在每個資料夾名稱*PlatformToolsets*會出現在**專案屬性**為 可用的對話方塊**平台工具組**針對指定的平台，如下所示：

![在 [專案屬性頁] 對話方塊中的平台工具組屬性](media/vc-project-extensibility-platform-toolset-property.png "平台工具組屬性，在專案屬性頁對話方塊")

建立類似*MyToolset*資料夾並*Toolset.props*並*Toolset.targets*每個現有的平台資料夾中的檔案服務支援此工具組。

### <a name="add-a-new-platform"></a>加入新的平台

若要新增新的平台，例如，"MyPlatform，「 建立*MyPlatform*下方的資料夾`$(VCTargetsPath)` *\\平台\\* ，並建立*Platform.default.props*， *Platform.props*，以及*Platform.targets*檔案。 也會建立`$(VCTargetsPath)` *\\平台\\* <strong><em>MyPlatform</em></strong> *\\PlatformToolsets\\* 資料夾，並在其中建立至少一個工具組。

下的所有資料夾名稱*平台*每個資料夾`$(ApplicationType)`並`$(ApplicationTypeRevision)`會出現在 IDE 中為可用的**平台**專案的選項。

![新的平台選擇，在 [新增專案平台] 對話方塊](media/vc-project-extensibility-new-project-platform.png "在 [新增專案平台] 對話方塊的新增平台選擇")

### <a name="add-a-new-application-type"></a>加入新的應用程式類型

若要新增新的應用程式類型，建立*MyApplicationType*下方的資料夾`$(VCTargetsPath)` *\\應用程式類型\\* ，並建立*Defaults.props*檔案。 至少一個修訂需要應用程式類型，因此也會建立`$(VCTargetsPath)` *\\應用程式類型\\MyApplicationType\\1.0*資料夾，並建立*Defaults.props*檔案。 您也應該建立`$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\平台*資料夾，並在其中建立至少一個平台。

`$(ApplicationType)` 和`$(ApplicationTypeRevision)`屬性看不到使用者介面中。 這些專案範本中所定義，並建立專案之後，無法變更。

## <a name="the-vcxproj-import-tree"></a>.Vcxproj 匯入樹狀目錄

簡化的樹狀目錄中，匯入 microsoft C++ props 和目標檔案看起來像：

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*預設*\\\*。*屬性* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*應用程式類型*\\`$(ApplicationType)`\\*Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*應用程式類型*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*應用程式類型*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*平台*\\ `$(Platform)` \\ *Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*預設*\\\*。*屬性*

Windows 桌面專案未定義`$(ApplicationType)`，因此它們只匯入

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*預設*\\\*。*屬性* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platforms*\\`$(Platform)`\\*Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*預設*\\\*。*屬性*

我們將使用`$(_PlatformFolder)`屬性來保留`$(Platform)`平台資料夾位置。 這個屬性

> `$(VCTargetsPath)`\\*平台*\\`$(Platform)`

Windows 傳統型應用程式，以及

> `$(VCTargetsPath)`\\*應用程式類型*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*平台*\\`$(Platform)`

至於其他項目。

Props 檔案匯入順序如下：

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*.*props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*。*屬性*

目標檔案匯入順序如下：

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*。*目標* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*。*目標*

如果您需要定義一些預設屬性，您的工具組，您可以將檔案新增到適當的 ImportBefore 和 ImportAfter 資料夾。

## <a name="author-toolsetprops-and-toolsettargets-files"></a>作者 Toolset.props 和 Toolset.targets 檔案

*Toolset.props*並*Toolset.targets*檔案就可以全權掌控使用此工具組時，在建置期間會發生什麼事。 它們也可以控制可用的偵錯工具 IDE 使用者介面，例如內容中的一些**屬性頁** 對話方塊中和一些其他專案的行為層面。

雖然工具組可以覆寫整個建置程序，通常您只想要修改或加入一些建置步驟，或使用不同的建置工具，為現有的建置程序的一部分的工具組。 若要達成此目標，有一些常見可以匯入您的工具組的 props 和目標檔案。 根據您想要您工具組，這些檔案可能會使用為匯入，或是做為範例：

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

  此檔案會定義原生組建程序的主要部分，並也會匯入：

  - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

  - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

  - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   設定工具組，使用 Microsoft 編譯器，並以 Windows 為目標的預設值。

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   這個檔案會決定 Windows SDK 的位置，並定義一些重要的屬性，用於以 Windows 為目標的應用程式。

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>整合工具組特定目標的預設值C++建置程序

預設值C++中所定義的建置程序*Microsoft.CppCommon.targets*。 那里的目標不要呼叫任何特定的建置工具;它們會指定主要建置步驟、 順序和相依性。

C++組建有三個主要的步驟，由下列目標：

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

因為每個組建步驟可能會獨立執行，所以在一個步驟中執行的目標不能依賴的項目群組和不同步驟的過程中執行的目標中所定義的屬性。 這項分割可讓特定組建的效能最佳化。 雖然它不使用預設值，我們還是鼓勵您採用這種區隔。

每個步驟內執行的目標所控制的這些屬性：

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

每個步驟也會有之前和之後的屬性。

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

請參閱*Microsoft.CppBuild.targets*檔案之目標的每個步驟中包含的範例：

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

如果您查看目標，例如`_ClCompile`，您會看到它們不會進行任何直接由本身，但改為相依於其他目標，包括`ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` 與特定工具的目標定義中的空目標為其他組建*Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

因為`ClCompile`目標是空的就會覆寫的工具組，除非不實際組建執行任何動作。 工具組的目標可以覆寫`ClCompile`目標，也就是它們可以包含另一個`ClCompile`之後匯入定義*Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

儘管其名稱，建立 Visual Studio 實作跨平台支援之前，`ClCompile`目標不必呼叫 CL.exe。 它也可以使用適當的 MSBuild 工作，呼叫 Clang、 gcc 或其他編譯器。

`ClCompile`目標不應該有任何相依性，除了`SelectClCompile`目標所需的單一檔案的編譯命令，以在 IDE 中工作。

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>若要使用工具組目標的 MSBuild 工作

若要叫用實際的建置工具，目標必須呼叫 MSBuild 工作。 沒有基本[Exec 工作](../msbuild/exec-task.md)，可讓您指定要執行的命令列。 不過，建置工具通常會有許多選項，輸入。 並輸出到追蹤的累加建置，因此合理更多可以有特殊的工作。 比方說，`CL`工作 MSBuild 屬性轉譯為 CL.exe 交換器、 將其寫入至回應檔案，以及呼叫 CL.exe。 它也會追蹤所有的輸入和輸出檔案的後續累加組建。 如需詳細資訊，請參閱 <<c0> [ 累加組建 」 和 「 最新檢查](#incremental-builds-and-up-to-date-checks)。

Microsoft.Cpp.Common.Tasks.dll 會實作下列工作：

- `BSCMake`

- `CL`

- `ClangCompile` （clang gcc 參數）

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` （例如 Exec 但有輸入和輸出追蹤）

- `SetEnv`

- `GetOutOfDateItems`

如果您有一項工具，以執行相同的動作，做為現有的工具，和 （如同 clang-cl 和 CL） 具有類似的命令列參數，您可以使用相同的工作兩者都是。

如果您需要建立新的工作，建置工具，您可以選擇下列選項：

1. 如果您很少使用這項工作，或者幾秒鐘的時間不重要的組建，您可以使用 MSBuild 'inline' 工作：

   - Xaml 工作 （自訂建置規則）

     如需 Xaml 工作宣告的範例，請參閱`$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*，以及它的用法，請參閱`$(VCTargetsPath)` \\*BuildCustomizations*\\*masm.targets*。

   - [程式碼工作](../msbuild/msbuild-inline-tasks.md)

1. 如果您想要更佳的工作效能，或只是需要更複雜的功能，使用一般的 MSBuild[工作撰寫](../msbuild/task-writing.md)程序。

   如果並非所有的輸入和輸出的工具 工具命令列上為中列出`CL`， `MIDL`，和`RC`情況下，以及如果您想自動輸入和輸出檔案追蹤和.tlog 檔案建立時，會將您的工作源自`Microsoft.Build.CPPTasks.TrackedVCToolTask`類別。 目前，雖然沒有基底的文件[ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)類別中，沒有任何範例或文件的詳細資料`TrackedVCToolTask`類別。 這會特別感興趣的是，如果您的語音要求上新增[developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html)。

## <a name="incremental-builds-and-up-to-date-checks"></a>累加建置和更新狀態檢查

目標會使用預設的 MSBuild 累加建置`Inputs`和`Outputs`屬性。 如果您指定它們，MSBuild 就會呼叫目標只能在任何輸入有較新的時間戳記，於所有輸出。 原始程式檔通常包含或匯入其他檔案，並建置工具產生不同的工具選項而定的輸出，因為它很難指定所有可能的輸入和輸出中的 MSBuild 目標。

若要管理這個問題，請C++建置使用不同的技術來支援累加建置。 大部分的目標不指定輸入和輸出，並如此一來，一律會在建置期間執行。 呼叫目標的工作撰寫所有的相關資訊輸入，並輸出到*tlog*副檔名的.tlog 檔案。 用來檢查項目已變更且需要重建的更新版本組建的.tlog 檔案，以及為何保持最新狀態。 .tlog 檔案也是預設的組建保持最新狀態檢查在 IDE 中的唯一來源。

若要判斷所有輸入和輸出，原生工具工作會使用 tracker.exe 並[FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) MSBuild 所提供的類別。

Microsoft.Build.CPPTasks.Common.dll 定義`TrackedVCToolTask`公用抽象的基底類別。 原生工具工作大部分都衍生自這個類別。

從 Visual Studio 2017 更新 15.8 開始，您可以使用`GetOutOfDateItems`Microsoft.Cpp.Common.Tasks.dll 来產生已知的輸入和輸出的自訂目標的.tlog 檔案中實作的工作。
或者，您可以藉由建立它們`WriteLinesToFile`工作。 請參閱`_WriteMasmTlogs`中的目標`$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*做為範例。

## <a name="tlog-files"></a>.tlog 檔案。

有三種類型的.tlog 檔案：*讀取*，*撰寫*，並*命令列*。 累加建置和 IDE 中最新的檢查，則會使用讀取和寫入的.tlog 檔案。 命令列的.tlog 檔案。 只適用於累加建置。

MSBuild 會提供這些協助程式類別，來讀取和寫入.tlog 檔案：

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata)類別可以用來存取這兩個讀取和寫入.tlog 檔案，以及識別輸入比輸出，或如果輸出已遺失的更新。 它會在最新的檢查。

命令列的.tlog 檔案包含在組建中使用命令列的相關資訊。 它們只會用於累加建置，而不是最新的檢查，所以內部的格式取決於它們所產生的 MSBuild 工作。

### <a name="read-tlog-format"></a>閱讀.tlog 格式

*讀取*.tlog 檔案。 (\*.read。\*。tlog) 包含原始程式檔和其相依性的相關資訊。

插入號 ( **^** ) 開頭的一條線表示一個或多個來源。 共用相同的相依性的來源以分隔號分隔 ( **\|** )。

在來源中，每個的那一行之後，會列出相依性檔案。 所有的檔案名稱都是完整路徑。

例如，假設您專案的來源位於*f:\\測試\\ConsoleApplication1\\ConsoleApplication1*。 如果原始程式檔*Class1.cpp*，有這些包含，

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

然後*CL.read.1.tlog*檔案包含後面接著其兩個相依性的原始程式檔：

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

要寫入的檔案名稱以大寫，不必要，但它可讓您輕鬆的一些工具。

### <a name="write-tlog-format"></a>撰寫.tlog 格式

*撰寫*.tlog (\*.write。\*。tlog) 檔案會在來源和輸出連線。

插入號 ( **^** ) 開頭的一條線表示一個或多個來源。 多個來源以分隔號分隔 ( **\|** )。

在來源中，每個的那一行之後，應該會列出從來源建置的輸出檔案。 所有的檔案名稱必須是完整路徑。

例如，對於簡單的 ConsoleApplication 專案都有一個額外來源檔案*Class1.cpp*，則*link.write.1.tlog*檔案可能包含：

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>設計階段組建

在 IDE 中，.vcxproj 專案會使用一組的 MSBuild 目標，以從專案取得其他資訊，以及重新產生輸出檔案。 這些目標的一些只適用於設計階段組建，但其中大部分用於定期執行組建和設計階段組建。

如需設計階段組建的一般資訊，請參閱的 CPS 文件[設計階段建置](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)。 這份文件才對視覺效果部分適用C++專案。

`CompileDesignTime`和`Compile`設計階段中所述的目標建置從未執行.vcxproj 專案的文件。 視覺化C++.vcxproj 專案使用不同的設計階段目標來取得 IntelliSense 資訊。

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense 資訊的設計階段目標

.Vcxproj 專案中使用的設計階段目標中所定義`$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*。

`GetClCommandLines`目標如何收集適用於 IntelliSense 的編譯器選項：

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – 設計階段只建置的目標，所需的設計階段初始化。 除此之外，這些目標停用的某些一般組建功能來改善效能。

- `ComputeCompileInputsTargets` -修改編譯器選項和項目中的目標集。 在設計階段與一般組建中，執行這些目標。

目標呼叫`CLCommandLine`工作以建立要用於 IntelliSense 的命令列。 同樣地，儘管其名稱，它可以處理不僅 CL 選項，但 Clang 和 gcc 選項。 編譯器參數的型別由控制`ClangMode`屬性。

目前，在命令列所產生的`CLCommandLine`工作一律會使用 CL 參數 （即使在 Clang 模式） 因為它們更容易剖析 IntelliSense 引擎。

如果您要新增的目標執行之前編譯時，是否定期或設計階段，請確定它不會中斷設計階段組建，或影響效能。 若要測試您的目標的最簡單方式是開啟開發人員命令提示字元並執行此命令：

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

此命令會產生詳細的組建記錄檔中， *msbuild.log*，結尾具有摘要的目標和工作的效能。

請務必使用`Condition ="'$(DesignTimeBuild)' != 'true'"`才有意義的定期執行組建，而不適用於設計階段組建的所有作業中。

### <a name="design-time-targets-that-generate-sources"></a>產生來源的設計階段目標

*桌面的原生專案的預設會停用這項功能，和目前不支援快取的專案上*。

如果`GeneratorTarget`中繼資料都定義為專案項目，則會執行目標會自動同時載入專案時，來源檔案變更時。

::: moniker range="vs-2017"

比方說，若要自動產生.cpp 或.h 檔案從.xaml 檔案`$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\ *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets*檔案會定義這些實體：

::: moniker-end

::: moniker range=">=vs-2019"

比方說，若要自動產生.cpp 或.h 檔案從.xaml 檔案`$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\ *WindowsXaml*\\*v16.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets*檔案會定義這些實體：

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

若要使用`Task.HostObject`若要取得的原始程式檔未儲存的內容，目標和工作應該註冊為[MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) pkgdef 中指定的專案：

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>視覺化C++專案在 Visual Studio IDE 中的擴充性

視覺效果C++專案系統以基礎[VS 專案系統](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)，並使用其擴充性點。 不過，特定視覺效果專案階層架構實作是C++而不根據 CPS，所以階層架構的擴充性會限制為專案項目。

### <a name="project-property-pages"></a>專案屬性頁

一般設計資訊，請參閱[VC + + 專案的 Framework 多目標](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/)。

簡單地說，屬性頁 所示**專案屬性** 對話方塊的C++專案所定義*規則*檔案。 規則檔案指定要顯示在 [屬性] 頁面上，以及如何在它們應儲存在專案和檔案屬性的集。 規則檔案是使用 Xaml 格式的.xml 檔案。 用來序列化它們的型別所述[Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes)。 如需有關使用的專案中的規則檔案，請參閱[屬性頁面 XML 規則檔案](/cpp/build/reference/property-page-xml-files)。

規則檔案必須新增至`PropertyPageSchema`項目群組：

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` 中繼資料限制規則可見性，這也會受到規則類型，而且可以有下列值之一：

`Project` | `File` | `PropertySheet`

CPS 會支援其他值的內容型別，但不會用在視覺效果C++專案。

如果規則應該顯示在一個以上的內容，請使用分號 ( **;** ) 來分隔內容值，如下所示：

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>規則格式和主要的型別

規則格式很簡單，，因此本節只說明會影響規則的使用者介面中的外觀的屬性。

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`屬性可讓您定義規則中的顯示方式**屬性頁**對話方塊。 屬性可以有下列值之一：

| 屬性 | 描述 |
|------------| - |
| `generic` | 在類別目錄標題下的單一頁面上會顯示所有的屬性<br/>規則可以是顯示`Project`並`PropertySheet`內容，但不是`File`。<br/><br/> 範例：`$(VCTargetsPath)`\\*1033*\\*general.xml* |
| `tool` | 類別會顯示為子頁面。<br/>規則可以是顯示在所有的內容： `Project`，`PropertySheet`和`File`。<br/>規則內容中會顯示專案的專案已使用的項目時，才`ItemType`中定義`Rule.DataSource`，除非規則名稱會包含在`ProjectTools`項目群組。<br/><br/>範例：`$(VCTargetsPath)`\\*1033*\\*clang.xml* |
| `debugger` | 頁面會顯示為 [偵錯] 頁面的一部分。<br/>類別目前會被忽略。<br/>規則名稱應該符合偵錯啟動器 MEF 物件的`ExportDebugger`屬性。<br/><br/>範例：`$(VCTargetsPath)`\\*1033*\\*debugger\_local\_windows.xml* |
| *custom* | 自訂範本。 範本的名稱應該符合`ExportPropertyPageUIFactoryProvider`屬性的`PropertyPageUIFactoryProvider`MEF 物件。 請參閱**Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**。<br/><br/> 範例：`$(VCTargetsPath)`\\*1033*\\*userMacros.xml* |

如果此規則會使用其中一個屬性方格為基礎的範本，它可以使用這些擴充點的屬性：

- [屬性值編輯器](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [動態 enum 值提供者](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>擴充的規則

如果您想要使用現有的規則，但需要新增或移除 （也就，隱藏） 只要幾個屬性，您可以建立[延伸模組規則](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)。

#### <a name="override-a-rule"></a>覆寫規則

或許您想要您的工具組使用大部分的專案預設規則，但取代其中一個或幾個。 例如，假設您只想要變更 C /C++規則，以顯示不同的編譯器參數。 您可以提供新的規則具有相同名稱和顯示名稱與現有的規則，並將它併入`PropertyPageSchema`之後匯入的預設 cpp 目標項目群組。 只有一個具有指定名稱的規則會在專案中，和最後一個納入`PropertyPageSchema`項目群組 wins。

#### <a name="project-items"></a>專案項目

*ProjectItemsSchema.xml*檔案會定義`ContentType`並`ItemType`值的項目會被視為專案項目，並定義`FileExtension`來判斷新的檔案新增至哪一個項目群組的項目。

預設 ProjectItemsSchema 檔案位於`$(VCTargetsPath)` \\ *1033年*\\*ProjectItemsSchema.xml*。 若要擴充它，您必須建立結構描述檔案與新的名稱，例如*MyProjectItemsSchema.xml*:

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

然後在目標檔案中，新增：

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

範例：`$(VCTargetsPath)`\\*BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>偵錯工具

Visual Studio 中的偵錯服務支援的偵錯引擎的擴充性。 如需詳細資訊，請參閱這些範例：

- [MIEngine，支援 lldb 偵錯的開放原始碼專案](https://github.com/Microsoft/MIEngine)

- [Visual Studio 偵錯引擎的範例](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

若要指定偵錯工作階段的偵錯引擎以及其他屬性，您必須實作[偵錯啟動器](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md)MEF 元件，並新增`debugger`規則。 如需範例，請參閱`$(VCTargetsPath)` \\1033年\\偵錯工具\_本機\_windows.xml 檔案。

### <a name="deploy"></a>部署

.vcxproj 專案使用 Visual Studio 專案系統的擴充性[部署提供者](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)。

### <a name="build-up-to-date-check"></a>建置最新的檢查

根據預設，組建的最新檢查要求讀取的.tlog 」 和 「 寫入.tlog 檔案。 若要在建立`$(TlogLocation)`所有組建的輸入和輸出的建置期間的資料夾。

若要使用自訂的最新檢查：

1. 加入停用預設的最新檢查`NoVCDefaultBuildUpToDateCheckProvider`中的功能*Toolset.targets*檔案：

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. 實作您自己[IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)。

## <a name="project-upgrade"></a>專案升級

### <a name="default-vcxproj-project-upgrader"></a>預設.vcxproj 專案升級程式

預設.vcxproj 專案升級程式變更`PlatformToolset`， `ApplicationTypeRevision`，MSBuild 工具組版本和.Net framework。 這兩個永遠都會變更為 Visual Studio 版本預設值，但`PlatformToolset`和`ApplicationTypeRevision`可以控制特殊的 MSBuild 屬性。

升級程式會使用這些準則來決定與否，是否可以升級專案：

1. 定義的專案`ApplicationType`和`ApplicationTypeRevision`，沒有更高版本的修訂編號，與目前的資料夾。

1. 屬性`_UpgradePlatformToolsetFor_<safe_toolset_name>`定義目前的工具組，且其值不等於目前的工具組。

   在這些屬性名稱 中，  *\<safe_toolset_name >* 由底線取代所有的非英數字元與代表的工具組的名稱 ( **\_** )。

當可以升級專案時，它所參與*重定方案目標*。 如需詳細資訊，請參閱 < [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2)。

如果您想要裝飾中的專案名稱**方案總管**時的專案使用特定的工具組，定義`_PlatformToolsetShortNameFor_<safe_toolset_name>`屬性。

如需的範例`_UpgradePlatformToolsetFor_<safe_toolset_name>`並`_PlatformToolsetShortNameFor_<safe_toolset_name>`屬性的定義，請參閱*Microsoft.Cpp.Default.props*檔案。 如需使用方式的範例，請參閱 < `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets*檔案。

### <a name="custom-project-upgrader"></a>自訂專案升級程式

若要使用自訂的專案升級程式物件，實作 MEF 元件，如下所示：

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

您的程式碼可以匯入，並呼叫預設.vcxproj upgrader 物件：

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` 定義於*Microsoft.VisualStudio.ProjectSystem.VS.dll* ，類似於`IVsRetargetProjectAsync`。

定義`VCProjectUpgraderObjectName`告訴專案系統，以使用您的自訂升級程式物件的屬性：

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>停用專案升級

若要停用專案升級，請使用`NoUpgrade`值：

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>專案快取和擴充性

若要改善效能，使用 大型時C++在 Visual Studio 2017 中，解決方案[專案快取](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/)導入。 它會實作為 SQLite 資料庫填入專案資料，以及用來載入專案而不需要載入記憶體中的 MSBuild 或 CPS 專案。

因為沒有 CPS 物件從快取載入的.vcxproj 專案存在，擴充功能的 MEF 元件，匯入`UnconfiguredProject`或`ConfiguredProject`無法建立。 若要支援擴充性，Visual Studio 會偵測是否專案會使用 （或可能會使用） MEF 擴充功能時，不使用專案快取。

這些專案類型都完全載入，並在記憶體中，有 CPS 物件，因此所有的 MEF 擴充功能會為他們建立：

- 啟始專案

- 也就是有自訂的專案升級程式的專案，它們定義`VCProjectUpgraderObjectName`屬性

- 也就是沒有目標桌面 Windows 專案中，它們定義`ApplicationType`屬性

- 在這兩者的.vcxitems 專案匯入該參考共用項目專案 (.vcxitems) 和任何專案。

如果偵測到這些條件時，會建立專案的快取。 快取包含所需回答 MSBuild 專案中的所有資料`get`查詢上`VCProjectEngine`介面。 這表示在 MSBuild 屬性的所有修改，並由延伸模組的目標檔案層級應該就會從快取載入的專案中的方式運作。

## <a name="shipping-your-extension"></a>傳送您的延伸模組

如需如何建立 VSIX 檔案資訊，請參閱[傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。 如需如何將檔案新增至特殊的安裝位置，例如，新增下的檔案`$(VCTargetsPath)`，請參閱 <<c2> [ 安裝擴充功能資料夾之外](../extensibility/set-install-root.md)。

## <a name="additional-resources"></a>其他資源

Microsoft 建置系統 ([MSBuild](../msbuild/msbuild.md)) 提供的專案檔建置引擎和可延伸的 XML 格式。 您應該先熟悉與 basic [MSBuild 概念](../msbuild/msbuild-concepts.md)與如何[視覺效果的 MSBuild C++ ](/cpp/build/reference/msbuild-visual-cpp-overview)為了擴充視覺效果的運作方式C++專案系統。

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) 提供延伸模組 CPS 和視覺效果所使用的 ApiC++專案系統。 CPS 如何使用 MEF 的概觀，請參閱[CPS 和 MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef)中[VSProjectSystem MEF 概觀](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md)。

您可以自訂現有的建置系統，以新增建置步驟或新的檔案類型。 如需詳細資訊，請參閱 < [MSBuild (Visual C++) 概觀](/cpp/build/reference/msbuild-visual-cpp-overview)並[使用專案屬性](/cpp/build/working-with-project-properties)。
