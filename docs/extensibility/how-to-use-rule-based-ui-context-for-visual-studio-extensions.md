---
title: 作法：使用 Visual Studio 擴充功能的規則為基礎的 UI 內容 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: c3075ca5092dd1b8a69aa4b34c0e507505cf7123
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67309684"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>作法：使用 Visual Studio 擴充功能的規則為基礎的 UI 內容

Visual Studio 可讓載入 Vspackage 時有特定已知<xref:Microsoft.VisualStudio.Shell.UIContext>s 會啟動。 不過，這些 UI 內容不正常精細，延伸模組作者，讓任何選擇，但選擇可用的 UI 內容，就會啟動點之前，他們其實想要載入 VSPackage。 如需已知的 UI 內容，請參閱<xref:Microsoft.VisualStudio.Shell.KnownUIContexts>。

載入封裝可能會造成效能影響，並比所需更快載入它們並非最佳的作法。 Visual Studio 2015 導入規則型 UI 內容，一種機制，可定義精確的條件下啟動 UI 內容，以及相關聯的 Vspackage 會載入延伸模組作者的概念。

## <a name="rule-based-ui-context"></a>以規則為基礎的 UI 內容

「 規則 」 包含新的 UI 內容 (GUID) 和參考一或多個 「 條款 」 的布林運算式結合邏輯"and"、"，"not"作業。 「 條款 」 會在執行階段以動態方式評估，每當任何其條款的變更，並會重新評估運算式。 當運算式評估為 true 時，就會啟動相關聯的 UI 內容。 否則，UI 內容會取消已啟動。

以規則為基礎的 UI 內容可以使用各種不同的方式：

1. 指定命令和工具視窗的可見性條件的約束。 直到符合 UI 內容規則時，您可以隱藏的命令/工具視窗。

2. 為自動載入條件約束： 只在符合規則時，自動載入封裝。

3. 做為延遲的工作： 延遲載入，直到經過指定的間隔，且仍然符合規則。

   此機制可供任何 Visual Studio 擴充功能。

## <a name="create-a-rule-based-ui-context"></a>建立規則為基礎的 UI 內容
 假設您有稱為 TestPackage 延伸模組，提供功能表命令，僅適用於檔案與 *.config*延伸模組。 VS2015 之前, 的最佳選項是載入 TestPackage 時<xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>UI 內容已啟動。 以這種方式載入 TestPackage 並非有效，因為載入的方案甚至不能包含 *.config*檔案。 這些步驟顯示如何以規則為基礎的 UI 內容可用來啟用的 UI 內容的檔案時才 *.config*延伸模組，並選取該 UI 內容啟動時載入 TestPackage。

1. 定義新的 ui 內容 GUID，並加入 VSPackage 類別<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>。

    例如，假設新的 ui 內容 「 UIContextGuid"是要加入。 建立 GUID (您可以按一下來建立 GUID**工具** > **建立 GUID**) 是 「 8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"。 然後，您會新增下列宣告套件類別：

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    針對屬性，加入下列值：（這些屬性的詳細資料將於稍後說明）

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    這些中繼資料定義新的 ui 內容 GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) 和運算式參考的 「 DotConfig"的詞彙。 「 DotConfig 」 一詞會評估為 true，每當目前的選取範圍，在使用中的階層架構中有符合規則運算式模式的名稱 「\\.config$ 」 (結尾 *.config*)。 （預設值） 值定義的規則適用於偵錯的選擇性名稱。

    屬性的值會新增至 pkgdef 建置期間之後產生。

2. VSCT 檔案中 TestPackage 的命令，加入適當的命令中的"DynamicVisibility 」 旗標：

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. 在 VSCT 可視性 區段中，將繫結適當的命令，以新的 ui 內容 #1 中所定義的 GUID:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. 在 [符號] 區段中，新增 ui 內容的定義：

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    現在，內容功能表命令 *\*.config*檔案將會顯示在 [方案總管] 中選取的項目時才 *.config*檔案和套件將不會載入之前的其中之一選取命令。

   接下來，使用偵錯工具來確認只有當您預期載入封裝。 若要偵錯 TestPackage:

5. 在設定的中斷點<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。

6. 建置 TestPackage 並開始偵錯。

7. 建立專案或開啟其中一個。

8. 選取任何副檔名的檔案以外 *.config*。應該不會叫用中斷點。

9. 選取  *App.Config*檔案。

   TestPackage 載入，並在中斷點停止。

## <a name="add-more-rules-for-ui-context"></a>新增更多規則的 UI 內容
 由於 UI 內容規則都是布林運算式，您可以新增更多限制的規則 UI 內容。 例如，在上述的 UI 內容中，您可以指定只在載入內含專案的方案時才套用規則。 如此一來，命令不會顯示是否您開啟 *.config*檔案以獨立檔案，而非專案的一部分。

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 現在運算式會參考三個詞彙。 前兩個詞彙，「 SingleProject"和"MultipleProjects 」，請參閱其他已知的 UI 內容 （由其 Guid 中)。 第三個詞彙中，"DotConfig 」 是以規則為基礎的 UI 內容，而此一稍早在本文中所定義。

## <a name="delayed-activation"></a>延遲的啟用
 規則可以有選擇性的 「 延遲 」。 以毫秒為單位指定延遲時間。 如果有的話，啟用或停用規則的 UI 內容，該時間間隔延遲的作業，會導致延遲。 若是規則變更之前的延遲間隔，則會發生任何事。 這項機制可用來 「 交錯 」 初始化步驟-特別是單次初始化，而不需要依賴的計時器，或註冊閒置的通知。

 例如，您可以指定您的測試負載規則有 100 毫秒的延遲：

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>詞彙類型

以下是詞彙的支援的各種類型:

|詞彙|描述|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID 是指 UI 內容。 每當 UI 內容因作用中和，則為 false，則一詞將會是 true。|
|HierSingleSelectionName:\<模式 >|一詞的作用中的階層架構中的選擇是單一項目和選取的項目名稱符合 「 模式 」 所指定的.Net 規則運算式時，將會是 true。|
|UserSettingsStoreQuery:\<query>|「 查詢 」 到使用者設定存放區，必須評估為非零值表示的完整路徑。 查詢分割成"collection"和"propertyName 」，在最後的斜線。|
|ConfigSettingsStoreQuery:\<query>|「 查詢 」 到組態設定存放區，必須評估為非零值表示的完整路徑。 查詢分割成"collection"和"propertyName 」，在最後的斜線。|
|ActiveProjectFlavor:\<projectTypeGuid>|詞彙將會是 true，每當目前選取的專案特定 （彙總） 和類別，比對指定的專案類型 GUID。|
|ActiveEditorContentType:\<contentType>|選取的文件時指定的內容類型文字編輯器，將會是 true 一詞。|
|ActiveProjectCapability:\<Expression>|作用中的專案功能符合提供的運算式時，則為 true 的詞彙。 運算式可以是 VB 類似&#124;CSharp。|
|SolutionHasProjectCapability:\<Expression>|當方案中有任何比對運算式的載入的專案時，與上述類似，但是一詞是如此。|
|SolutionHasProjectFlavor:\<projectTypeGuid>|解決方案具備特色 （彙總） 的專案，並比對指定的專案類型 GUID 類別時，將會是 true 一詞。|
|ProjectAddedItem:\<pattern>| 比對 「 模式 」 的檔案新增至開啟 soluion 中的專案時，一詞是如此。|
|ActiveProjectOutputType:\<outputType>|詞彙是，則為 true 時輸出類型使用中的專案會確實比對。  OutputType 可能是整數或<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE>型別。|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|現用專案有指定的組建屬性和屬性值符合所提供的 regex 篩選條件時，一詞是如此。 請參閱[MSBuild 專案檔中的保存資料](internals/persisting-data-in-the-msbuild-project-file.md)更多有關建置屬性。|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|解決方案已載入的專案，以指定的組建屬性和屬性值符合所提供的 regex 篩選條件時，一詞是如此。|

## <a name="compatibility-with-cross-version-extension"></a>副檔名為跨版本相容性

以規則為基礎的 UI 內容是在 Visual Studio 2015 的新功能，並不會移轉至較早版本。 不移轉到較早的版本建立為目標的 Visual Studio 的多個版本的延伸模組/套件有問題。 這些版本會自動載入在 Visual Studio 2013 及更早版本，但可受益於將 UI 內容規則為基礎來防止正在自動載入 Visual Studio 2015 中。

為了支援這類套件，AutoLoadPackages 在登錄中的項目現在可以提供其 [值] 欄位來表示在 Visual Studio 2015 及更新版本，應該略過此項目中的旗標。 這可以加上旗標選項，來完成<xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>。 現在可以將加入 Vspackage **SkipWhenUIContextRulesActive**選項設定為其<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性來指出應該忽略的項目，在 Visual Studio 2015 和更新版本。
## <a name="extensible-ui-context-rules"></a>可延伸的 UI 內容規則

某些情況下，封裝無法使用靜態的 UI 內容規則。 例如，假設您有支援擴充性，使得命令狀態根據匯入的 MEF 提供者所支援的編輯器類型的封裝。 如果沒有延伸模組支援目前的編輯類型，此命令會啟用。 在此情況下，封裝本身無法使用靜態的 UI 內容規則，因為條款會根據哪一個 MEF 擴充功能可變更。

若要支援這類套件，以規則為基礎的 UI 內容支援硬式編碼運算式"*"表示所有下列條款會與加入或者。 這可讓主要的封裝，以定義已知的規則式 UI 內容，並將此內容中其命令狀態。 之後針對主要封裝任何 MEF 擴充功能也可以新增其條款，它支援而不會影響其他條款或主要運算式編輯器。

建構函式<xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>文件會示範可延伸的 UI 內容規則的語法。
