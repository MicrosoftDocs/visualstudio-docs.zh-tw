---
title: MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2387526860b7d6da136a72cf83727f6714e2e52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633066"
---
# <a name="msbuild"></a>MSBuild

微軟構建引擎是構建應用程式的平臺。 這個引擎也稱為 MSBuild，提供了專案檔的 XML 結構描述，以控制組建平台處理和建置軟體的方式。 視覺化工作室使用 MSBuild，但 MSBuild 不依賴于視覺化工作室。 通過在專案或解決方案檔中調用*msbuild.exe，* 可以在未安裝 Visual Studio 的環境中協調和生成產品。

 Visual Studio 會使用 MSBuild 載入及建置 Managed 專案。 Visual Studio 中的專案檔 (*.csproj*、*.vbproj*、*.vcxproj* 等等) 包含 MSBuild XML 程式碼，該程式碼會在您使用 IDE 建置專案時執行。 Visual Studio 專案會匯入所有必要的設定，並建置執行一般開發工作的流程，但是您可以在 Visual Studio 內或使用 XML 編輯器擴充或修改它們。

 有關 C++的 MSBuild 的資訊，請參閱[MSBuild （C++）](/cpp/build/msbuild-visual-cpp)。

 以下示例說明了何時可以通過從命令列而不是 Visual Studio IDE 調用 MSBuild 來運行生成。

- 未安裝 Visual Studio。 （[下載MSBuild沒有視覺工作室](https://visualstudio.microsoft.com/downloads/?q=build+tools)。

- 您想要使用 64 位元版的 MSBuild。 通常並不需要這個版本的 MSBuild，不過它可讓 MSBuild 存取更多記憶體。

- 您想要在多個流程中執行組建。 不過，您可以使用 IDE 在 C++ 和 C# 的專案中得到相同的結果。

- 您想要修改建置系統。 例如，您可能會想要啟用下列動作：

  - 使用編譯器處理檔案之前，先對檔案進行前置處理。

  - 將組建輸出複製到不同位置。

  - 從組建輸出建立壓縮檔。

  - 進行後續處理步驟。 例如，您可能想要對組件加上不同版本的戳記。

您可以在 Visual Studio IDE 中撰寫程式碼，但是使用 MSBuild 執行組建。 作為另一種選擇，您可以在開發電腦上在 IDE 中生成代碼，但從命令列運行 MSBuild 以生成由多個開發人員集成的代碼。 您還可以使用[.NET Core 命令列介面 （CLI） （CLI）](/dotnet/core/tools/)來構建 .NET Core 專案。

> [!NOTE]
> 可以使用 Azure 管道自動編譯、測試和部署應用程式。 您的建置系統可以在開發人員簽入程式碼 (例如，做為連續整合策略的一部分) 時或是根據排程 (例如，夜間組建驗證測試組建) 自動執行組建。 Azure 管道使用 MSBuild 編譯代碼。 如需詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)。

本文概述了 MSBuild。 如需入門教學課程，請參閱[逐步解說︰使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。

## <a name="use-msbuild-at-a-command-prompt"></a>在命令提示字元中使用 MSBuild

 要在命令提示符下運行 MSBuild，將專案檔案傳遞給*MSBuild.exe，* 以及相應的命令列選項。 命令列選項能讓您設定屬性、執行特定目標，以及設定可控制建置流程的其他選項。 例如，您可以使用下列命令列語法，在 `Configuration` 屬性設為 `Debug` 的情況下建置 *MyProj.proj* 檔案。

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 有關 MSBuild 命令列選項的詳細資訊，請參閱[命令列引用](../msbuild/msbuild-command-line-reference.md)。

> [!IMPORTANT]
> 下載專案之前，請判斷程式碼的可信度。

## <a name="project-file"></a>專案檔

 MSBuild 使用基於 XML 的專案檔案格式，該格式簡單明瞭且可擴展。 MSBuild 專案檔案格式允許開發人員描述要生成的項，以及如何為不同的作業系統和配置構建這些專案。 此外，專案檔格式還能讓開發人員撰寫可重複使用的建置規則供個別檔案使用，讓這些組建在產品內的不同專案中仍有一致的表現。

 以下各節介紹 MSBuild 專案檔案格式的一些基本元素。 有關如何創建基本專案檔案的教程，請參閱[演練：從頭開始創建 MSBuild 專案檔案](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)。

### <a name="properties"></a><a name="BKMK_Properties"></a> 屬性

 屬性表示成對的索引鍵/值組，可以用來設定組建。 宣告屬性的方式是建立具有屬性名稱的項目，做為 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 項目的子項目。 例如，下列程式碼會建立名為 `BuildDir` 並具有 `Build` 值的屬性。

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 您可以在項目中放入 `Condition` 屬性 (Attribute)，藉此定義條件式屬性 (Property)。 除非條件判斷值為 `true`，否則會忽略條件式項目的內容。 下列範例會定義 `Configuration` 項目 (如果尚未定義的話)。

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 使用語法 $(\<PropertyName>)，就可以在整個專案檔中參考屬性。 例如，您可以使用 `$(BuildDir)` 和 `$(Configuration)` 參考上述範例中的屬性。

 有關屬性的詳細資訊，請參閱[MSBuild 屬性](../msbuild/msbuild-properties.md)。

### <a name="items"></a><a name="BKMK_Items"></a>專案

 項目是建置系統的輸入內容，通常代表檔案。 根據使用者定義的項名稱將項分組到項類型中。 這些項目類型可以做為工作的參數，工作會使用個別項目來執行建置流程的步驟。

 在專案檔中宣告項目 (Item) 的方式就是建立一個具有項目 (Item) 類型名稱的項目 (Element)，做為 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目 (Element) 的子系。 例如，下列程式碼會建立名為 `Compile` 的項目 (Item) 類型，其中包含兩個檔案。

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 使用語法 @(\<ItemType>)，就可以在整個專案檔中參考項目類型。 例如，範例中的項目類型應該是藉由使用 `@(Compile)` 參考的。

 在 MSBuild 中，項目 (Element) 和屬性 (Attribute) 名稱區分大小寫。 不過，屬性 (Property)、項目 (Item) 和中繼資料名稱則不區分大小寫。 下列範例會建立項目類型 `Compile`、`comPile` 或任何其他大小寫變化，並且為項目類型提供 "one.cs;two.cs" 值。

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 在進階的建置案例中，可以使用萬用字元宣告項目，而項目中可包含額外中繼資料。 如需項目的詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

### <a name="tasks"></a><a name="BKMK_Tasks"></a>任務

 任務是 MSBuild 專案用於執行生成操作的可執行代碼單元。 例如，工作可能是編譯輸入檔，或是執行外部工具。 工作可以重複使用，而且可以由不同專案中的不同開發人員共用。

 任務的執行邏輯是用託管代碼編寫的，並使用[UsingTask](../msbuild/usingtask-element-msbuild.md)元素映射到 MSBuild。 若想撰寫自己的工作，您可以撰寫一個實作 <xref:Microsoft.Build.Framework.ITask> 介面的 Managed 類型。 有關如何編寫任務的詳細資訊，請參閱[任務編寫](../msbuild/task-writing.md)。

 MSBuild 包括可修改以滿足您要求的常見任務。 範例包括用於複製檔案的 [Copy](../msbuild/copy-task.md)、用於建立目錄的 [MakeDir](../msbuild/makedir-task.md)，以及用於編譯 Visual C# 原始程式碼檔的 [Csc](../msbuild/csc-task.md)。 有關可用任務的清單以及使用方式資訊，請參閱[任務引用](../msbuild/msbuild-task-reference.md)。

 通過在 MSBuild 專案檔案中創建具有任務名稱作為[目標](../msbuild/target-element-msbuild.md)元素子項目的元素來執行任務。 工作通常會接受參數，而這些參數會當做項目的屬性傳遞。 MSBuild 屬性和項都可以用作參數。 例如，下列程式碼會呼叫 [MakeDir](../msbuild/makedir-task.md) 工作，並將前面範例中宣告的 `BuildDir` 屬性值傳遞給此工作。

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 如需工作的詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。

### <a name="targets"></a><a name="BKMK_Targets"></a>目標

 目標 (Target) 會將工作以特殊順序組成群組，並公開 (Expose) 專案檔的區段做為建置處理序的進入點 (Entry Point)。 目標通常會分組為許多邏輯區段，以提高可讀性和進行擴充。 將建置步驟分成多個目標之後，您就可以從其他目標呼叫一段建置流程，而不需要在每個目標內複製那一段程式碼。 例如，如果建置流程的許多個進入點都必須建置參考，您可以建立一個建置參考的目標，再於每個需要建置參考的進入點執行此目標。

 在專案檔中，目標是使用 [Target](../msbuild/target-element-msbuild.md) 項目宣告的。 例如，下列程式碼會建立名為 `Compile` 的目標，接著呼叫 [Csc](../msbuild/csc-task.md) 工作，而此工作具有在前面範例中宣告的項目清單。

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 在進階案例中，目標可用於描述彼此之間的關係並執行相依性分析，如果目標是最新版，即可略過建置流程的整個區段。 如需目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。

## <a name="build-logs"></a>組建記錄

 您可以將建置錯誤、警告和訊息記錄至主控台或另一個輸出裝置。 有關詳細資訊，請參閱[在 MSBuild 中](../msbuild/logging-in-msbuild.md)[獲取生成日誌](../msbuild/obtaining-build-logs-with-msbuild.md)和日誌記錄。

## <a name="use-msbuild-in-visual-studio"></a>在 Visual Studio 中使用 MSBuild

 Visual Studio 使用 MSBuild 專案檔案格式來存儲有關託管專案的生成資訊。 使用 Visual Studio 介面添加或更改的專案設置將反映在 中 *。\** 為每個專案生成的 proj 檔。 Visual Studio 使用 MSBuild 的託管實例來構建託管專案。 這意味著託管專案可以在 Visual Studio 或命令提示符下生成（即使未安裝 Visual Studio），結果將相同。

 如需如何在 Visual Studio 中使用 MSBuild 的教學課程，請參閱[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a>多目標

 通過使用 Visual Studio，可以編譯應用程式以在 .NET Framework 的多個版本中的任何一個上運行。 例如，可以編譯應用程式以在 .NET 框架 2.0 上 32 位平臺上運行，也可以編譯相同的應用程式在 .NET 框架 4.5 上 64 位平臺上運行。 編譯為一個以上 Framework 版本的能力稱為「多目標」(Multitargeting)。

 以下為多目標的一些優點：

- 您可以開發針對早期版本的 .NET Framework 的應用程式，例如版本 2.0、3.0 和 3.5。

- 您可以針對 .NET 框架以外的框架，例如，銀光。

- 您可以將「Framework 設定檔」** 當做目標，這是預先定義的目標 Framework 子集。

- 如果發佈當前版本的 .NET Framework 的服務包，則可以將其定位。

- 多目標可保證應用程式只使用目標 Framework 和平台中提供的功能。

如需詳細資訊，請參閱[多目標](../msbuild/msbuild-multitargeting-overview.md)。

## <a name="see-also"></a>另請參閱

| Title | 描述 |
| - | - |
| [演練：從頭開始創建 MSBuild 專案檔案](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | 顯示如何僅使用文字編輯器來累加建立基本專案檔。 |
| [逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md) | 介紹 MSBuild 的建置區塊，以及顯示如何在不關閉 Visual Studio IDE 的情況下，撰寫和管理 MSBuild 專案及進行偵錯。 |
| [MSBuild 概念](../msbuild/msbuild-concepts.md) | 呈現 MSBuild 的四個建置組塊：屬性、項目、目標和工作。 |
| [項目](../msbuild/msbuild-items.md) | 描述 MSBuild 檔案格式背後的一般概念，以及這些部分如何組合在一起。 |
| [MSBuild 屬性](../msbuild/msbuild-properties.md) | 介紹屬性和屬性集合。 屬性是成對的索引鍵/值組，可以用來設定組建 (Build)。 |
| [目標](../msbuild/msbuild-targets.md) | 解釋如何以特定順序將各項工作集合在一起成為群組，並能夠在命令列上呼叫建置流程的區段。 |
| [工作](../msbuild/msbuild-tasks.md) | 演示如何創建可執行代碼單元，MSBuild 可用於執行原子生成操作。 |
| [條件](../msbuild/msbuild-conditions.md) | 討論如何在 MSBuild 項目中使用 `Condition` 屬性。 |
| [進階概念](../msbuild/msbuild-advanced-concepts.md) | 呈現批次處理、執行轉換、多目標、以及其他進階技巧。 |
| [MSBuild 中的記錄](../msbuild/logging-in-msbuild.md) | 描述如何記錄建置事件、訊息和錯誤。 |
| [其他資源](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | 列出社群和支援資源，以提供 MSBuild 的詳細資訊。 |

## <a name="reference"></a>參考

- [MSBuild 參考](../msbuild/msbuild-reference.md)\
 包含參考資訊的主題連結。

- [詞彙](msbuild-glossary.md)\
 定義通用 MSBuild 詞彙。