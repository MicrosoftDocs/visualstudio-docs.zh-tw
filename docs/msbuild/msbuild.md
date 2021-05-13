---
title: MSBuild | Microsoft Docs
description: 瞭解 Microsoft Build Engine (MSBuild) platform 如何提供具有 XML 架構的專案檔來控制組建。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 372fc5c81b963cbb8e46cab689713e476fcfff7d
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848275"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine 是用來建立應用程式的平臺。 這個引擎也稱為 MSBuild，提供了專案檔的 XML 結構描述，以控制組建平台處理和建置軟體的方式。 Visual Studio 使用 MSBuild，但 MSBuild 並不依賴 Visual Studio。 藉由叫用專案或方案檔上的 *msbuild.exe* ，您可以在未安裝 Visual Studio 的環境中協調和建立產品。

 Visual Studio 會使用 MSBuild 載入及建置 Managed 專案。 Visual Studio 中的專案檔 (*.csproj*、*.vbproj*、*.vcxproj* 等等) 包含 MSBuild XML 程式碼，該程式碼會在您使用 IDE 建置專案時執行。 Visual Studio 專案會匯入所有必要的設定，並建置執行一般開發工作的流程，但是您可以在 Visual Studio 內或使用 XML 編輯器擴充或修改它們。

 如需 MSBuild for c + + 的相關資訊，請參閱 [msbuild (c + +) ](/cpp/build/msbuild-visual-cpp)。

 下列範例說明當您從命令列叫用 MSBuild 而非 Visual Studio IDE 時，您可能會執行組建。

- 未安裝 Visual Studio。  ([下載 MSBuild 但不 Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools)。 ) 

- 您想要使用 64 位元版的 MSBuild。 通常並不需要這個版本的 MSBuild，不過它可讓 MSBuild 存取更多記憶體。

- 您想要在多個流程中執行組建。 不過，您可以使用 IDE 在 C++ 和 C# 的專案中得到相同的結果。

- 您想要修改建置系統。 例如，您可能會想要啟用下列動作：

  - 使用編譯器處理檔案之前，先對檔案進行前置處理。

  - 將組建輸出複製到不同位置。

  - 從組建輸出建立壓縮檔。

  - 進行後續處理步驟。 例如，您可能想要對組件加上不同版本的戳記。

您可以在 Visual Studio IDE 中撰寫程式碼，但是使用 MSBuild 執行組建。 另一種方法是，您可以在開發電腦上的 IDE 中建立程式碼，但是從命令列執行 MSBuild，以建立與多個開發人員整合的程式碼。 您也可以使用 [.Net core 命令列介面 (CLI) ](/dotnet/core/tools/)（使用 MSBuild）來建立 .net core 專案。

> [!NOTE]
> 您可以使用 Azure Pipelines 來自動編譯、測試和部署您的應用程式。 您的建置系統可以在開發人員簽入程式碼 (例如，做為連續整合策略的一部分) 時或是根據排程 (例如，夜間組建驗證測試組建) 自動執行組建。 Azure Pipelines 使用 MSBuild 編譯您的程式碼。 如需詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)。

本文提供 MSBuild 的總覽。 如需入門教學課程，請參閱[逐步解說︰使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。

## <a name="use-msbuild-at-a-command-prompt"></a>在命令提示字元中使用 MSBuild

 若要在命令提示字元中執行 MSBuild，請將專案檔傳遞至 *MSBuild.exe*，以及適當的命令列選項。 命令列選項能讓您設定屬性、執行特定目標，以及設定可控制建置流程的其他選項。 例如，您可以使用下列命令列語法，在 `Configuration` 屬性設為 `Debug` 的情況下建置 *MyProj.proj* 檔案。

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 如需 MSBuild 命令列選項的詳細資訊，請參閱 [命令列參考](../msbuild/msbuild-command-line-reference.md)。

> [!IMPORTANT]
> 下載專案之前，請判斷程式碼的可信度。

## <a name="project-file"></a>專案檔

 MSBuild 使用以 XML 為基礎的專案檔格式，它既簡單又可擴充。 MSBuild 專案檔案格式可讓開發人員描述要建立的專案，以及如何針對不同的作業系統和設定建立這些專案。 此外，專案檔格式還能讓開發人員撰寫可重複使用的建置規則供個別檔案使用，讓這些組建在產品內的不同專案中仍有一致的表現。

 下列各節說明 MSBuild 專案檔格式的一些基本元素。 如需如何建立基本專案檔的教學課程，請參閱 [逐步解說：從頭開始建立 MSBuild 專案](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)檔。

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

 您可以使用語法 $ () ，在整個專案檔中參考屬性 \<PropertyName> 。 例如，您可以使用 `$(BuildDir)` 和 `$(Configuration)` 參考上述範例中的屬性。

 如需屬性的詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

### <a name="items"></a><a name="BKMK_Items"></a> 專案

 項目是建置系統的輸入內容，通常代表檔案。 根據使用者定義的專案名稱，將專案分組為專案類型。 這些項目類型可以做為工作的參數，工作會使用個別項目來執行建置流程的步驟。

 在專案檔中宣告項目 (Item) 的方式就是建立一個具有項目 (Item) 類型名稱的項目 (Element)，做為 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目 (Element) 的子系。 例如，下列程式碼會建立名為 `Compile` 的項目 (Item) 類型，其中包含兩個檔案。

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 您可以使用語法 @ () ，在整個專案檔中參考專案類型 \<ItemType> 。 例如，範例中的項目類型應該是藉由使用 `@(Compile)` 參考的。

 在 MSBuild 中，項目 (Element) 和屬性 (Attribute) 名稱區分大小寫。 不過，屬性 (Property)、項目 (Item) 和中繼資料名稱則不區分大小寫。 下列範例會建立項目類型 `Compile`、`comPile` 或任何其他大小寫變化，並且為項目類型提供 "one.cs;two.cs" 值。

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 在進階的建置案例中，可以使用萬用字元宣告項目，而項目中可包含額外中繼資料。 如需項目的詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

### <a name="tasks"></a><a name="BKMK_Tasks"></a> 工作

 工作是 MSBuild 專案用來執行組建作業的可執行程式碼單位。 例如，工作可能是編譯輸入檔，或是執行外部工具。 工作可以重複使用，而且可以由不同專案中的不同開發人員共用。

 工作的執行邏輯是以 managed 程式碼撰寫，並使用 [UsingTask](../msbuild/usingtask-element-msbuild.md) 元素對應至 MSBuild。 若想撰寫自己的工作，您可以撰寫一個實作 <xref:Microsoft.Build.Framework.ITask> 介面的 Managed 類型。 如需如何撰寫工作的詳細資訊，請參閱工作 [撰寫](../msbuild/task-writing.md)。

 MSBuild 包含您可以修改的一般工作，以符合您的需求。 範例包括用於複製檔案的 [Copy](../msbuild/copy-task.md)、用於建立目錄的 [MakeDir](../msbuild/makedir-task.md)，以及用於編譯 Visual C# 原始程式碼檔的 [Csc](../msbuild/csc-task.md)。 如需可用工作的清單以及使用資訊，請參閱工作 [參考](../msbuild/msbuild-task-reference.md)。

 在 MSBuild 專案檔中執行工作的方式，是建立一個具有工作名稱的專案做為 [目標](../msbuild/target-element-msbuild.md) 元素的子系。 工作通常會接受參數，而這些參數會當做項目的屬性傳遞。 MSBuild 屬性和專案都可以當做參數使用。 例如，下列程式碼會呼叫 [MakeDir](../msbuild/makedir-task.md) 工作，並將前面範例中宣告的 `BuildDir` 屬性值傳遞給此工作。

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 如需工作的詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。

### <a name="targets"></a><a name="BKMK_Targets"></a> 目標

 目標 (Target) 會將工作以特殊順序組成群組，並公開 (Expose) 專案檔的區段做為建置處理序的進入點 (Entry Point)。 目標通常會分組為許多邏輯區段，以提高可讀性和進行擴充。 將建置步驟分成多個目標之後，您就可以從其他目標呼叫一段建置流程，而不需要在每個目標內複製那一段程式碼。 例如，如果建置流程的許多個進入點都必須建置參考，您可以建立一個建置參考的目標，再於每個需要建置參考的進入點執行此目標。

 在專案檔中，目標是使用 [Target](../msbuild/target-element-msbuild.md) 項目宣告的。 例如，下列程式碼會建立名為 `Compile` 的目標，接著呼叫 [Csc](../msbuild/csc-task.md) 工作，而此工作具有在前面範例中宣告的項目清單。

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 在進階案例中，目標可用於描述彼此之間的關係並執行相依性分析，如果目標是最新版，即可略過建置流程的整個區段。 如需目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。

## <a name="build-logs"></a>組建記錄

 您可以將建置錯誤、警告和訊息記錄至主控台或另一個輸出裝置。 如需詳細資訊，請參閱[在 MSBuild 中](../msbuild/logging-in-msbuild.md)[取得組建記錄](../msbuild/obtaining-build-logs-with-msbuild.md)和記錄。

## <a name="use-msbuild-in-visual-studio"></a>在 Visual Studio 中使用 MSBuild

 Visual Studio 使用 MSBuild 專案檔案格式來儲存有關 managed 專案的組建資訊。 使用 Visual Studio 介面加入或變更的專案設定會反映在中 *。 \** 為每個專案產生的 proj 檔。 Visual Studio 使用託管的 MSBuild 實例來建立 managed 專案。 這表示可以在 Visual Studio 或命令提示字元內內建 managed 專案 (即使 Visual Studio 未安裝) ，而且結果會相同。

 如需如何在 Visual Studio 中使用 MSBuild 的教學課程，請參閱[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> 多目標

 藉由使用 Visual Studio，您可以將應用程式編譯為在數個 .NET Framework 版本的任一個上執行。 例如，您可以將應用程式編譯為在32位平臺上的 .NET Framework 2.0 上執行，而且您可以將相同的應用程式編譯為在64平臺上的 .NET Framework 4.5 上執行。 編譯為一個以上 Framework 版本的能力稱為「多目標」(Multitargeting)。

 以下為多目標的一些優點：

- 您可以開發以舊版 .NET Framework 為目標的應用程式，例如版本2.0、3.0 和3.5。

- 您可以將 .NET Framework 以外的 framework 作為目標，例如 Silverlight。

- 您可以將「Framework 設定檔」當做目標，這是預先定義的目標 Framework 子集。

- 如果發行 .NET Framework 目前版本的 service pack，您可以將其設為目標。

- 多目標可保證應用程式只使用目標 Framework 和平台中提供的功能。

如需詳細資訊，請參閱[多目標](../msbuild/msbuild-multitargeting-overview.md)。

## <a name="see-also"></a>另請參閱

| 標題 | 描述 |
| - | - |
| [逐步解說：從頭開始建立 MSBuild 專案檔](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | 顯示如何僅使用文字編輯器來累加建立基本專案檔。 |
| [逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md) | 介紹 MSBuild 的建置區塊，以及顯示如何在不關閉 Visual Studio IDE 的情況下，撰寫和管理 MSBuild 專案及進行偵錯。 |
| [MSBuild 概念](../msbuild/msbuild-concepts.md) | 呈現 MSBuild 的四個建置組塊：屬性、項目、目標和工作。 |
| [項目](../msbuild/msbuild-items.md) | 描述 MSBuild 檔案格式背後的一般概念，以及這些元件如何彼此配合。 |
| [MSBuild 屬性](../msbuild/msbuild-properties.md) | 介紹屬性和屬性集合。 屬性是成對的索引鍵/值組，可以用來設定組建 (Build)。 |
| [目標](../msbuild/msbuild-targets.md) | 解釋如何以特定順序將各項工作集合在一起成為群組，並能夠在命令列上呼叫建置流程的區段。 |
| [工作](../msbuild/msbuild-tasks.md) | 顯示如何建立可由 MSBuild 用來執行不可部分完成之組建作業的可執行程式碼單位。 |
| [條件](../msbuild/msbuild-conditions.md) | 討論如何在 MSBuild 項目中使用 `Condition` 屬性。 |
| [進階概念](../msbuild/msbuild-advanced-concepts.md) | 呈現批次處理、執行轉換、多目標、以及其他進階技巧。 |
| [MSBuild 中的記錄](../msbuild/logging-in-msbuild.md) | 描述如何記錄建置事件、訊息和錯誤。 |
| [MSBuild 如何建置專案](build-process-overview.md) | 描述 MSBuild 內使用的內部組建進程 |
| [其他資源](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | 列出社群和支援資源，以提供 MSBuild 的詳細資訊。 |

## <a name="reference"></a>參考

- [MSBuild 參考](../msbuild/msbuild-reference.md)\
 包含參考資訊的主題連結。

- [詞彙](msbuild-glossary.md)\
 定義通用 MSBuild 詞彙。
