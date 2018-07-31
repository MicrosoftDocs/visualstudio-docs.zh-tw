---
title: MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd6736242e6fa130fdbb356261cae8e63f3c952f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154784"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] 是用於建置應用程式的平台。 這個引擎也稱為 MSBuild，提供了專案檔的 XML 結構描述，以控制組建平台處理和建置軟體的方式。 Visual Studio 會使用 MSBuild，但 MSBuild 並不倚賴 Visual Studio。 藉由在專案或方案檔上叫用 *msbuild.exe*，就可以在未安裝 Visual Studio 的環境中組織及建置產品。  
  
 Visual Studio 會使用 MSBuild 載入及建置 Managed 專案。 Visual Studio 中的專案檔 (*.csproj*、*.vbproj*、*.vcxproj* 等等) 包含 MSBuild XML 程式碼，該程式碼會在您使用 IDE 建置專案時執行。 Visual Studio 專案會匯入所有必要的設定，並建置執行一般開發工作的流程，但是您可以在 Visual Studio 內或使用 XML 編輯器擴充或修改它們。  
  
 如需 C++ 適用之 MSBuild 的相關資訊，請參閱 [MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp)。  
  
 下列範例將說明何時可能會使用 MSBuild 命令列執行組建，而不是使用 Visual Studio IDE。  
  
-   未安裝 Visual Studio。  
  
-   您想要使用 64 位元版的 MSBuild。 通常並不需要這個版本的 MSBuild，不過它可讓 MSBuild 存取更多記憶體。  
  
-   您想要在多個流程中執行組建。 不過，您可以使用 IDE 在 C++ 和 C# 的專案中得到相同的結果。  
  
-   您想要修改建置系統。 例如，您可能會想要啟用下列動作：  
  
    -   使用編譯器處理檔案之前，先對檔案進行前置處理。  
  
    -   將組建輸出複製到不同位置。  
  
    -   從組建輸出建立壓縮檔。  
  
    -   進行後續處理步驟。 例如，您可能想要對組件加上不同版本的戳記。  

您可以在 Visual Studio IDE 中撰寫程式碼，但是使用 MSBuild 執行組建。 另一種替代方式是，您可以在開發電腦的 IDE 中建置程式碼，但是使用 MSBuild 命令列建置整合自多位開發人員的程式碼。  
  
> [!NOTE]
>  您可以使用 Team Foundation Build 自動編譯、測試和部署您的應用程式。 您的建置系統可以在開發人員簽入程式碼 (例如，做為連續整合策略的一部分) 時或是根據排程 (例如，夜間組建驗證測試組建) 自動執行組建。 Team Foundation Build 會使用 MSBuild 編譯您的程式碼。 如需詳細資訊，請參閱[建置及發行](/vsts/build-release/index)。  
  
 本主題提供 MSBuild 的概觀。 如需入門教學課程，請參閱[逐步解說︰使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。  

##  <a name="use-msbuild-at-a-command-prompt"></a>在命令提示字元中使用 MSBuild  
 若要在命令提示字元執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]，請使用適當的命令列選項，將專案檔傳遞給 *MSBuild.exe*。 命令列選項能讓您設定屬性、執行特定目標，以及設定可控制建置流程的其他選項。 例如，您可以使用下列命令列語法，在 `Configuration` 屬性設為 `Debug` 的情況下建置 *MyProj.proj* 檔案。  
  
```cmd  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 如需有關 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 命令列選項的詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)。  
  
> [!IMPORTANT]
>  下載專案之前，請判斷程式碼的可信度。  
  
##  <a name="project-file"></a>專案檔  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 使用直接且可擴充的 XML 專案檔格式。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔格式讓開發人員可以描述將要建置的項目，以及如何針對不同的作業系統和組態來建置這些項目。 此外，專案檔格式還能讓開發人員撰寫可重複使用的建置規則供個別檔案使用，讓這些組建在產品內的不同專案中仍有一致的表現。  
  
 下列章節將說明 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔格式的一些基本項目。 如需如何建立基本專案檔的教學課程，請參閱[逐步解說：從頭開始建立 MSBuild 專案檔](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)。  
  
###  <a name="BKMK_Properties"></a> 屬性  
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
  
 如需屬性的詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。  
  
###  <a name="BKMK_Items"></a> 項目  
 項目是建置系統的輸入內容，通常代表檔案。 項目會依據使用者定義的項目名稱分組為各個項目類型。 這些項目類型可以做為工作的參數，工作會使用個別項目來執行建置流程的步驟。  
  
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
  
###  <a name="BKMK_Tasks"></a> 工作  
 工作是 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案用來執行建置作業之可執行程式碼的單元。 例如，工作可能是編譯輸入檔，或是執行外部工具。 工作可以重複使用，而且可以由不同專案中的不同開發人員共用。  
  
 工作的執行邏輯是以 Managed 程式碼撰寫，並使用 [UsingTask](../msbuild/usingtask-element-msbuild.md) 項目對應到 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]。 若想撰寫自己的工作，您可以撰寫一個實作 <xref:Microsoft.Build.Framework.ITask> 介面的 Managed 類型。 如需有關如何撰寫工作的詳細資訊，請參閱[工作撰寫](../msbuild/task-writing.md)。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 包含您可以依據自己的需求修改的一般工作。  範例包括用於複製檔案的 [Copy](../msbuild/copy-task.md)、用於建立目錄的 [MakeDir](../msbuild/makedir-task.md)，以及用於編譯 Visual C# 原始程式碼檔的 [Csc](../msbuild/csc-task.md)。 如需可用工作的清單和用法資訊，請參閱[工作參考](../msbuild/msbuild-task-reference.md)。  
  
 在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔中執行工作的方式就是建立一個具有工作名稱的項目，做為 [Target](../msbuild/target-element-msbuild.md) 項目的子系。 工作通常會接受參數，而這些參數會當做項目的屬性傳遞。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 屬性和項目都可當做參數使用。 例如，下列程式碼會呼叫 [MakeDir](../msbuild/makedir-task.md) 工作，並將前面範例中宣告的 `BuildDir` 屬性值傳遞給此工作。  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 如需工作的詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。  
  
###  <a name="BKMK_Targets"></a> 目標  
 目標 (Target) 會將工作以特殊順序組成群組，並公開 (Expose) 專案檔的區段做為建置處理序的進入點 (Entry Point)。 目標通常會分組為許多邏輯區段，以提高可讀性和進行擴充。 將建置步驟分成多個目標之後，您就可以從其他目標呼叫一段建置流程，而不需要在每個目標內複製那一段程式碼。 例如，如果建置流程的許多個進入點都必須建置參考，您可以建立一個建置參考的目標，再於每個需要建置參考的進入點執行此目標。  
  
 在專案檔中，目標是使用 [Target](../msbuild/target-element-msbuild.md) 項目宣告的。 例如，下列程式碼會建立名為 `Compile` 的目標，接著呼叫 [Csc](../msbuild/csc-task.md) 工作，而此工作具有在前面範例中宣告的項目清單。  
  
```xml  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 在進階案例中，目標可用於描述彼此之間的關係並執行相依性分析，如果目標是最新版，即可略過建置流程的整個區段。 如需目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。  
  
##  <a name="build-logs"></a>組建記錄檔  
 您可以將建置錯誤、警告和訊息記錄至主控台或另一個輸出裝置。 如需詳細資訊，請參閱[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)和 [MSBuild 中的記錄](../msbuild/logging-in-msbuild.md)。  
  
## <a name="use-msbuild-in-visual-studio"></a>在 Visual Studio 中使用 MSBuild  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔格式儲存 Managed 專案的建置資訊。 使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 介面加入或變更的專案設定，會反映在針對每個專案產生的 *.\*proj* 檔案中。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的裝載執行個體 (Hosted Instance) 來建置 Managed 專案。 這表示 Managed 專案可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中或是於命令提示字元 (即使未安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]) 建置，其結果完全相同。  
  
 如需如何在 Visual Studio 中使用 MSBuild 的教學課程，請參閱[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)。  
  
##  <a name="BKMK_Multitargeting"></a> 多目標  
 您可以使用 Visual Studio，將應用程式編譯為在數個 .NET Framework 版本中的任何一版上執行。 例如，您可以將應用程式編譯為在 32 位元平台的 .NET Framework 2.0 上執行，也可以將同一個應用程式編譯為在 64 位元平台的 .NET Framework 4.5 上執行。 編譯為一個以上 Framework 版本的能力稱為「多目標」(Multitargeting)。  
  
 以下為多目標的一些優點：  
  
-   您可以開發以較舊版 .NET Framework (例如 2.0、3.0 和 3.5 版) 為目標的應用程式。  
  
-   您可以將 .NET Framework 以外的 Framework 做為目標，例如 Silverlight。  
  
-   您可以將「Framework 設定檔」當做目標，這是預先定義的目標 Framework 子集。  
  
-   如果 .NET Framework 目前版本的 Service Pack 已發行，您可以將它當做目標。  
  
-   多目標可保證應用程式只使用目標 Framework 和平台中提供的功能。  

如需詳細資訊，請參閱[多目標](../msbuild/msbuild-multitargeting-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：從頭開始建立 MSBuild 專案檔案](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|顯示如何僅使用文字編輯器來累加建立基本專案檔。|  
|[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)|介紹 MSBuild 的建置區塊，以及顯示如何在不關閉 Visual Studio IDE 的情況下，撰寫和管理 MSBuild 專案及進行偵錯。|  
|[MSBuild 概念](../msbuild/msbuild-concepts.md)|呈現 MSBuild 的四個建置組塊：屬性、項目、目標和工作。|  
|[項目](../msbuild/msbuild-items.md)|描述 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 檔案格式的一般概念，以及項目如何彼此搭配。|  
|[MSBuild 屬性](../msbuild/msbuild-properties.md)|介紹屬性和屬性集合。 屬性是成對的索引鍵/值組，可以用來設定組建 (Build)。|  
|[目標](../msbuild/msbuild-targets.md)|解釋如何以特定順序將各項工作集合在一起成為群組，並能夠在命令列上呼叫建置流程的區段。|  
|[工作](../msbuild/msbuild-tasks.md)|顯示如何建立 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可用來執行原子建置作業的可執行程式碼單元。|  
|[條件](../msbuild/msbuild-conditions.md)|討論如何在 MSBuild 項目中使用 `Condition` 屬性。|  
|[進階概念](../msbuild/msbuild-advanced-concepts.md)|呈現批次處理、執行轉換、多目標、以及其他進階技巧。|  
|[MSBuild 中的記錄](../msbuild/logging-in-msbuild.md)|描述如何記錄建置事件、訊息和錯誤。|  
|[其他資源](../msbuild/additional-msbuild-resources.md)|列出社群和支援資源，以提供 MSBuild 的詳細資訊。|  
  
## <a name="reference"></a>參考資料  
 [MSBuild 參考](../msbuild/msbuild-reference.md)  
 包含參考資訊的主題連結。  
  
 [字彙表](msbuild-glossary.md)定義通用的 MSBuild 字詞。
