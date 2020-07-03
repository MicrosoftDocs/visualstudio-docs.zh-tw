---
title: 如何：針對 Visual Studio 延伸模組使用以規則為基礎的 UI 內容 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 1457b8178a48ac867ee8407df9501dee56afd45b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905575"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>如何：針對 Visual Studio 延伸模組使用以規則為基礎的 UI 內容

Visual Studio 允許在某些知名的啟用時載入 Vspackage <xref:Microsoft.VisualStudio.Shell.UIContext> 。 不過，這些 UI 內容並不精細，這會使延伸模組作者不會選擇，而是會挑選在真正希望 VSPackage 載入的那一點之前啟動的可用 UI 內容。 如需已知 UI 內容的清單，請參閱 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> 。

載入封裝可能會對效能造成影響，而且比所需更快載入套件不是最佳作法。 Visual Studio 2015 引進了以規則為基礎的 UI 內容概念，這是一種機制，可讓延伸模組作者定義啟動 UI 內容和載入相關 Vspackage 的精確條件。

## <a name="rule-based-ui-context"></a>以規則為基礎的 UI 內容

「規則」是由新的 UI 內容（GUID）和布林運算式所組成，其參考一或多個「詞彙」與邏輯 "and"、"or"、"not" 作業結合。 「詞彙」會在執行時間以動態方式進行評估，而且每當其任何字詞變更時，就會重新評估運算式。 當運算式評估為 true 時，會啟用相關聯的 UI 內容。 否則，UI 內容就會取消啟用。

以規則為基礎的 UI 內容可透過各種方式來使用：

1. 指定命令和工具視窗的可見度條件約束。 您可以隱藏 [命令/工具] 視窗，直到符合 UI 內容規則為止。

2. 做為自動載入條件約束：只有在符合規則時，才會自動載入封裝。

3. 做為延遲的工作：延遲載入直到指定的間隔過後，而且仍然符合規則。

   任何 Visual Studio 的延伸模組都可以使用此機制。

## <a name="create-a-rule-based-ui-context"></a>建立以規則為基礎的 UI 內容
 假設您有一個稱為 TestPackage 的延伸模組，它所提供的功能表命令只適用于副檔名為 *.config*的檔案。 在 VS2015 之前，最佳選項是在 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> 啟用 UI 內容時載入 TestPackage。 以這種方式載入 TestPackage 並不有效率，因為載入的方案可能甚至不會包含 *.config*檔案。 這些步驟顯示如何使用以規則為基礎的 UI 內容，僅在已選取副檔名為 *.config*的檔案時才啟動 ui 內容，以及在啟用該 ui 內容時載入 TestPackage。

1. 定義新的 UICoNtext GUID，並將新增至 VSPackage 類別 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> 。

    例如，假設要加入新的 UICoNtext "UICoNtextGuid"。 建立的 guid （您可以按一下 [**工具**] [建立 guid] 來建立 guid  >  ** **）為 "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"。 然後在您的 package 類別內新增下列宣告：

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    針對屬性，新增下列值：（這些屬性的詳細資料將于稍後說明）

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    這些中繼資料會定義新的 UICoNtext GUID （8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B），以及參考單一詞彙 "DotConfig" 的運算式。 每當作用中階層中的目前選取範圍的名稱符合正則運算式模式 " \\ .config $" （結尾為 *.config*）時，"DotConfig" 詞彙就會評估為 true。 （預設值）值會定義適用于進行偵錯工具之規則的選擇性名稱。

    屬性的值會加入至之後在組建期間產生的 .pkgdef。

2. 在 TestPackage 命令的 .VSCT 檔案中，將 "DynamicVisibility" 旗標新增至適當的命令：

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. 在 .VSCT 的可視性區段中，將適當的命令與 #1 中定義的新 UICoNtext GUID 結合：

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. 在 [符號] 區段中，新增 UICoNtext 的定義：

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    現在，只有在 [solution explorer] 中選取的專案是 *.config*檔案，且在選取其中一個命令之前，才會顯示* \* .config*檔案的內容功能表命令。

   接下來，使用偵錯工具來確認封裝只有在您預期的時候才會載入。 若要進行 TestPackage 的調試：

5. 在方法中設定中斷點 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 。

6. 建立 TestPackage 並開始進行調試。

7. 建立專案或開啟一個。

8. 選取副檔名不是 *.config*的任何檔案。不應叫用中斷點。

9. 選取 [ *App.Config* ] 檔案。

   TestPackage 會在中斷點載入並停止。

## <a name="add-more-rules-for-ui-context"></a>新增更多 UI 內容的規則
 由於 UI 內容規則是布林運算式，因此您可以為 UI 內容新增更受限制的規則。 例如，在上述 UI 內容中，您可以指定只有在載入具有專案的方案時，才會套用規則。 如此一來，如果您以獨立檔案的形式開啟 *.config*檔案，而不是做為專案的一部分，則不會顯示命令。

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 現在，運算式會參考三個詞彙。 前兩個詞彙 "SingleProject" 和 "MultipleProjects"，指的是其他已知的 UI 內容（依其 Guid）。 第三個詞彙 "DotConfig" 是本文稍早所定義的以規則為基礎的 UI 內容。

## <a name="delayed-activation"></a>延遲啟用
 規則可以有選擇性的「延遲」。 延遲時間以毫秒為單位來指定。 如果存在，延遲會導致規則的 UI 內容啟用或停用，並延遲該時間間隔。 如果規則在延遲間隔之前變更，則不會發生任何事。 這項機制可以用來「錯開」初始化步驟，特別是單次初始化，而不依賴計時器或註冊閒置通知。

 例如，您可以指定測試負載規則的延遲為100毫秒：

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

以下是支援的各種類型詞彙：

|詞彙|描述|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID 會參考 UI 內容。 每當 UI 內容為作用中時，此詞彙將為 true，否則為 false。|
|HierSingleSelectionName:\<pattern>|只要作用中階層中的選取範圍是單一專案，而且所選取專案的名稱符合「模式」所指定的 .Net 正則運算式時，這個詞彙就會是 true。|
|UserSettingsStoreQuery:\<query>|"query" 代表使用者設定存放區中的完整路徑，必須評估為非零值。 查詢會分割成最後一個斜線的 "collection" 和 "propertyName"。|
|ConfigSettingsStoreQuery:\<query>|「查詢」代表 config 設定存放區中的完整路徑，必須評估為非零值。 查詢會分割成最後一個斜線的 "collection" 和 "propertyName"。|
|ActiveProjectFlavor:\<projectTypeGuid>|只要目前選取的專案是 flavored （匯總），而且具有符合指定專案類型 GUID 的類別，這個詞彙就會是 true。|
|ActiveEditorContentType:\<contentType>|當選取的檔是具有指定之內容類型的文字編輯器時，此詞彙將會是 true。 注意：重新命名選取的檔時，在關閉並重新開啟檔案之前，不會重新整理此字詞。|
|ActiveProjectCapability:\<Expression>|當作用中的專案功能符合提供的運算式時，此詞彙為 true。 運算式可能類似 VB &#124; CSharp。|
|SolutionHasProjectCapability:\<Expression>|與上述類似，但當方案具有符合運算式的任何已載入專案時，此詞彙為 true。|
|SolutionHasProjectFlavor:\<projectTypeGuid>|每當方案具有 flavored （匯總）的專案，且其類別符合指定的專案類型 GUID 時，這個詞彙就會是 true。|
|ProjectAddedItem:\<pattern>| 當符合「模式」的檔案加入至 soluion 中已開啟的專案時，此詞彙為 true。|
|ActiveProjectOutputType:\<outputType>|當作用中專案的輸出類型完全相符時，此詞彙為 true。  OutputType 可以是整數或 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> 類型。|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|當作用中專案的指定組建屬性和屬性值符合所提供的 RegEx 篩選準則時，此詞彙為 true。 如需組建屬性的詳細資訊，請參閱[在 MSBuild 專案檔中保存資料](internals/persisting-data-in-the-msbuild-project-file.md)。|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|當方案的載入專案具有指定的組建屬性，且屬性值符合所提供的 RegEx 篩選準則時，此詞彙為 true。|

## <a name="compatibility-with-cross-version-extension"></a>與跨版本擴充功能的相容性

以規則為基礎的 UI 內容是 Visual Studio 2015 中的新功能，而且不會移植到舊版。 未移植到舊版，會導致以多個 Visual Studio 版本為目標的擴充功能/套件發生問題。 這些版本必須在 Visual Studio 2013 和更早的版本中自動載入，但可受益于以規則為基礎的 UI 內容，以避免在 Visual Studio 2015 中自動載入。

為了支援這類封裝，登錄中的 AutoLoadPackages 專案現在可以在其 [值] 欄位中提供旗標，以指出應該在 Visual Studio 2015 和更新版本中略過該專案。 這可以藉由將旗標選項新增至來完成 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> 。 Vspackage 現在可以將**SkipWhenUICoNtextRulesActive**選項新增至其 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 屬性，以指出應該在 Visual Studio 2015 和更新版本中忽略此專案。
## <a name="extensible-ui-context-rules"></a>可擴充的 UI 內容規則

有時候，封裝無法使用靜態 UI 內容規則。 例如，假設您的封裝支援擴充性，因此命令狀態是以匯入的 MEF 提供者所支援的編輯器類型為基礎。 如果有支援目前編輯類型的擴充功能，則會啟用命令。 在這種情況下，封裝本身無法使用靜態 UI 內容規則，因為這些詞彙會根據可用的 MEF 延伸模組而變更。

為了支援這類封裝，以規則為基礎的 UI 內容支援硬式編碼運算式 "*"，指出其底下的所有詞彙將會與或聯結。 這可讓主要套件定義已知的以規則為基礎的 UI 內容，並將其命令狀態與此內容結合。 之後，任何以主要封裝為目標的 MEF 延伸模組，都可以為其支援的編輯器新增其詞彙，而不會影響其他詞彙或主要運算式。

此 <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> 程式集檔會顯示可擴充 UI 內容規則的語法。
