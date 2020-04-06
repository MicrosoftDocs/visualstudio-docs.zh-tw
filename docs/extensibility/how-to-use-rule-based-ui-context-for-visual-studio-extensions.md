---
title: 操作方式:將基於規則的 UI 上下文用於可視化工作室擴展 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710587"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>操作方式:將基於規則的 UI 上下文用於視覺化工作室擴展

當啟動某些已知<xref:Microsoft.VisualStudio.Shell.UIContext>元件時,Visual Studio 允許載入 VS 包。 但是,這些 UI 上下文不是細粒度的,這使得擴展作者別無選擇,只能選擇一個可用的 UI 上下文,該上下文在真正希望 VSPackage 載入的點之前啟動。 有關已知 UI 上下文的清單,請<xref:Microsoft.VisualStudio.Shell.KnownUIContexts>參閱 。

載入包可能會對性能產生影響,並且載入它們的時間不是最佳做法。 Visual Studio 2015 引入了基於規則的 UI 上下文的概念,該機制允許擴展作者定義啟動 UI 上下文並載入關聯的 VS 包的確切條件。

## <a name="rule-based-ui-context"></a>基於規則的 UI 內容

"規則"由新的 UI 上下文 (GUID) 和布爾運算式組成,這些運算式引用一個或多個"術語",並結合邏輯"和","或","不"操作。 "術語"在運行時動態計算,每當表達式的任何術語發生更改時,都會重新評估表達式。 當表達式計算為 true 時,關聯的 UI 上下文將啟動。 否則,UI 上下文將取消啟動。

基於規則的 UI 功能可透過多種方式使用:

1. 指定命令和工具視窗的可見性約束。 您可以隱藏命令/工具視窗,直到滿足 UI 上下文規則。

2. 作為自動載入約束:僅在滿足規則時自動載入包。

3. 作為延遲任務:延遲載入,直到指定間隔過去,並且仍滿足規則。

   任何視覺工作室擴展都可以使用該機制。

## <a name="create-a-rule-based-ui-context"></a>建立基於規則的 UI 中文
 假設您有一個名為 TestPackage 的副檔名,它提供了一個功能表命令,該命令僅適用於具有 *.config*擴展名的檔。 在 VS2015 之前,最佳選項是在<xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>啟動 UI 上下文時載入測試套件。 以這種方式載入 TestPackage 效率不高,因為載入的解決方案可能甚至不包含 *.config*檔。 這些步驟演示如何僅在選擇*具有 .config*副檔名的檔時才使用基於規則的 UI 上下文來啟動 UI 上下文,並在啟動該 UI 上下文時載入 TestPackage。

1. 定義新的 UIContext GUID 並加入 VSPackage<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute><xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>類別與 。

    例如,假設要添加新的 UIContext"UIContextGuid"。 創建的 GUID(您可以通過單擊 **"工具** > **創建 GUID"創建 GUID)** 是「8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B」。。 然後,在包類中添加以下聲明:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    對於屬性,添加以下值:(稍後將介紹這些屬性的詳細資訊)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    這些元數據定義了新的 UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) 和一個引用單個術語「DotConfig」的運算式。 當活動層次結構中的目前選擇具有與正規表示式模式「.config$」(\\以 .config 結尾)的名稱匹配時,「DotConfig」*.config*項將計算為 true。 (預設)值為可用於調試的規則定義可選名稱。

    屬性的值將添加到生成期間生成的 pkgdef 中。

2. 在測試套件指令的 VSCT 檔中,將「動態可見性」標誌新增到相應的命令:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. 在 VSCT 的可見性部份中,將適當的指令與#1 中定義的新 UIContext GUID 進行連線:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. 在「符號」部分中,添加 UIContext 定義:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    現在,*\*僅當*解決方案資源管理器中的選定項為 *.config*檔且在選擇其中一個命令之前不會載入包時,.config 檔的上下文菜單命令才會可見。

   接下來,使用調試器確認包僅在預期載入時載入。 要除錯測試套件:

5. 在<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法中設置斷點。

6. 生成測試包並開始調試。

7. 創建專案或打開專案。

8. 選擇副*檔名以外的任何*檔。不應命中斷點。

9. 選擇*App.Config*檔。

   測試包在斷點載入和停止。

## <a name="add-more-rules-for-ui-context"></a>為 UI 內文新增更多規則
 由於 UI 上下文規則是布林運算式,因此可以為 UI 上下文添加更多受限制的規則。 例如,在上面的 UI 上下文中,可以指定規則僅在載入具有專案的解決方案時才適用。 這樣,如果將 *.config*檔案作為獨立檔而不是作為專案的一部分打開,則命令不會顯示。

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 現在表達式引用三個術語。 前兩個術語「單一專案」和「多專案」是指其他知名 UI 上下文(由其 GUID)。 第三個術語「DotConfig」是本文前面定義的基於規則的 UI 上下文。

## <a name="delayed-activation"></a>延遲啟動
 規則可以具有可選的" 延遲以毫秒為單位指定。 如果存在,則延遲會導致規則的 UI 上下文的啟動或停用延遲到該時間間隔。 如果規則在延遲間隔之前更改回來,則沒有任何反應。 此機制可用於"錯開"初始化步驟 - 尤其是一次性初始化,而無需依賴計時器或註冊空閒通知。

 例如,您可以指定測試負載規則具有 100 毫秒的延遲:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>字語類型

以下是支援的各種術語型態:

|詞彙|描述|
|-|-|
|[nnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnnnnnnnnnnnnnnnnnn]|GUID 引用 UI 上下文。 每當 UI 上下文處於活動狀態且 false 否則,該術語將為 true。|
|Hier 單選\<名稱 :圖案>|每當活動層次結構中的選擇是單個項且所選項的名稱與"pattern"給出的 .net 正則運算式匹配時,術語將為 true。|
|使用者設定儲存查詢:\<查詢>|"查詢"表示進入使用者設置存儲的完整路徑,該路徑必須計算為非零值。 查詢在最後一個斜杠上拆分為"集合"和"屬性名稱"。|
|設定設定儲存查詢:\<查詢>|"查詢"表示進入配置設置存儲的完整路徑,該路徑必須計算為非零值。 查詢在最後一個斜杠上拆分為"集合"和"屬性名稱"。|
|活動專案口味:\<專案類型>|每當當前選定的專案具有調味料(聚合),並且具有與給定專案類型 GUID 匹配的味道時,該術語將為 true。|
|作用編輯器內容類型:\<內容類型>|當所選文件是具有給定內容類型的文字編輯器時,術語將為 true。 注意:重新命名選取文件時,在關閉並重新打開檔之前,此術語不會刷新。|
|活動專案功能:\<運算式>|當活動專案功能與提供的表達式匹配時,該術語為 true。 表達式可以是類似於 VB &#124; CSharp。|
|解決方案具有專案能力:\<運算式>|與上面類似,但當解決方案具有與表達式匹配的任何載入專案時,術語為 true。|
|解決方案HasProjectFlavor:\<專案類型>|每當解決方案具有具有調味料(聚合)且具有與給定專案類型 GUID 匹配的風味時,該術語將是正確的。|
|專案新增專案:\<模式>| 當將匹配"模式"的檔添加到打開的 soluion 中的專案中時,該術語為 true。|
|作用項目輸出型態\<: 輸出類型>|當活動項目的輸出類型完全匹配時,術語為 true。  輸出類型可以是整數或<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE>類型。|
|作用項目建構屬性\<: 建構財產\<>= 正則>|當活動專案具有指定的生成屬性和屬性值與提供的 regex 篩選器匹配時,該術語為 true。 有關產生屬性的更多詳細資訊,請參閱[MSBuild 專案檔中的持久資料](internals/persisting-data-in-the-msbuild-project-file.md)。|
|解決方案HasProjectBuild屬性:\<建構財產>\<= 正則>|當解決方案具有與提供的 regex 篩選器匹配的載入專案且具有指定的生成屬性和屬性值匹配時,該術語為 true。|

## <a name="compatibility-with-cross-version-extension"></a>與跨版本延伸相容

基於規則的 UI 上下文是 Visual Studio 2015 中的新功能,不會移植到早期版本。 不移植到早期版本會造成針對 Visual Studio 多個版本的擴展/包的問題。 這些版本必須在 Visual Studio 2013 和更早版本中自動載入,但可以從基於規則的 UI 上下文中獲益,以防止在 Visual Studio 2015 中自動載入。

為了支援此類包,註冊表中的 AutoLoadPackages 條目現在可以在其值欄位中提供一個標誌,以指示應在 Visual Studio 2015 及以上中跳過該條目。 這可以透過新增旗標選項來<xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>實作 。 VSPackages 現在可以將**SkipWhenUIContextRulesActive**選項<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>添加到其屬性中,以指示應在 Visual Studio 2015 及以上內容中忽略該條目。
## <a name="extensible-ui-context-rules"></a>可擴充的 UI 功能規則

有時,包不能使用靜態 UI 上下文規則。 例如,假設您有一個包支援可擴充性,以便命令狀態基於導入的 MEF 提供程式支援的編輯器類型。 如果有支援當前編輯類型的擴展,則啟用該命令。 在這種情況下,包本身不能使用靜態 UI 上下文規則,因為術語會根據可用的 MEF 擴展而變化。

為了支援此類包,基於規則的 UI 上下文支援硬編碼表達式"*",該表達式指示其下的所有術語都將與 OR 聯接。 這允許主包定義一個已知的基於規則的 UI 上下文,並將其命令狀態綁定到此上下文。 之後,針對主包的任何 MEF 擴展都可以為其支援的編輯器添加其術語,而不會影響其他術語或主運算式。

建構函式<xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>文件顯示可擴展 UI 上下文規則的語法。
