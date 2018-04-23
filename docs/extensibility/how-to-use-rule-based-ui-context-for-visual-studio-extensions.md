---
title: 如何： 使用 Visual Studio 擴充功能以規則為基礎的 UI 內容 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8597c413c899b54e61e848649c3c524cbdb20724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>如何： 使用 Visual Studio 擴充功能以規則為基礎的 UI 內容
Visual Studio 可讓載入 Vspackage 時，某些已知<xref:Microsoft.VisualStudio.Shell.UIContext>s 會啟動。 不過，這些 UI 內容不是非常精細的更細緻，離開延伸模組作者沒有其他選擇，但挑選可用的 UI 內容點之前啟動他們真的想載入 VSPackage。 如需已知 UI 內容，請參閱<xref:Microsoft.VisualStudio.Shell.KnownUIContexts>。  
  
 載入封裝可能會影響效能，比在需要更快載入它們並非最佳的作法。 Visual Studio 2015 導入以規則為基礎 UI 內容中，一種機制，可讓延伸模組作者定義的精確條件，程式就會啟動 UI 內容和相關聯的 Vspackage 載入的概念。  
  
## <a name="rule-based-ui-context"></a>以規則為基礎的 UI 內容  
 「 規則 」 包含新的 UI 內容 (GUID) 和參考一個或多個 「 詞彙 」 的布林運算式結合邏輯"and"、"，"not"作業。 「 詞彙 」 會在執行階段以動態方式評估，每當任何其詞彙變更，會重新評估運算式。 當運算式評估為 true 時，就會啟動關聯的 UI 內容。 否則，UI 內容是取消啟動。  
  
 以規則為基礎的 UI 內容可用於各種不同的方式：  
  
1.  指定命令及工具視窗的可見性條件的約束。 您可以隱藏命令/工具 windows，直到符合 UI 內容規則。  
  
2.  為自動載入條件約束： 只在符合規則時，才自動載入的封裝  
  
3.  延遲的工作： 延遲載入，直到經過指定時間間隔，且仍然符合規則。  
  
 任何 Visual Studio 擴充功能可能使用的機制。  
  
## <a name="create-a-rule-based-ui-context"></a>建立規則為基礎的 UI 內容  
 假設您有稱為 TestPackage，後者只適用於".config"副檔名的檔案功能表命令會提供擴充功能。 VS2015 之前, 的最佳選項已載入 TestPackage 時<xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>UI 內容已啟用。 這不是有效的因為載入的方案可能甚至包含.config 檔案。 讓我們如何以規則為基礎的 UI 內容可以用來啟用 UI 內容時，才具有.config 副檔名的檔案選取時，且該 UI 內容啟動時載入 TestPackage。  
  
1.  定義新 UIContext GUID，加入 VSPackage 類別<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>。  
  
     例如，假設新 UIContext"UIContextGuid"是要加入。 建立的 GUID (您可以建立的 GUID，依序按一下 工具-> 建立 guid) 是 「 8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"。 然後您加入下列封裝類別內：  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     屬性，加入下列: （這些屬性的詳細資料稍後會加以解說）  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     這些中繼資料定義新的 UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) 和運算式參考到單一詞彙，「 DotConfig"。 「 DotConfig 」 一詞會評估為 true，每當目前的選取範圍，在使用中的階層中具有名稱符合規則運算式模式 」\\.config$"（結尾是".config"）。 （預設） 值定義規則適用於偵錯的選擇性名稱。  
  
     若要在建置階段之後產生 pkgdef 加入屬性的值。  
  
2.  在 TestPackage 命令的 VSCT 檔案中，加入適當的命令中的"DynamicVisibility 」 旗標：  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  在 VSCT 可視性區段中，將繫結至新 UIContext GUID #1 中定義適當的命令：  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  在 [符號] 區段中，加入 UIContext 的定義：  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     現在，*.config 檔案的內容功能表命令會顯示在 [方案總管] 中選取的項目是".config"檔案，而且已選取其中一個這些命令之前，將不會載入封裝時，才。  
  
 接下來，讓我們確認只有在我們預期當它載入封裝中使用偵錯工具。 若要偵錯 TestPackage:  
  
1.  在設定的中斷點<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
2.  建置 TestPackage 並開始偵錯。  
  
3.  建立專案或開啟其中一個。  
  
4.  選取副檔名為.config 以外的任何檔案。應該不會叫用中斷點。  
  
5.  選取的 App.Config 檔案。  
  
 TestPackage 載入，並在中斷點停止。  
  
## <a name="adding-more-rules-for-ui-context"></a>UI 內容加入更多的規則  
 由於 UI 內容規則都是布林運算式，您可以針對 UI 的內容加入限制更嚴格的規則。 例如，在上述的 UI 內容中，您可以指定只在載入內含專案的方案時才套用規則。 如此一來，命令不會顯示是否您開啟".config"檔以獨立檔案，而不是做為專案的一部分。  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 現在運算式參考了三個詞彙。 前兩個詞彙，「 SingleProject"和"MultipleProjects 」，請參閱其他已知 UI 內容中 （由其 Guid)。 第三個詞彙，「 DotConfig 」 是以規則為基礎 UI 內容我們稍早定義。  
  
## <a name="delayed-activation"></a>延遲的啟用  
 規則可以有選擇性的 「 延遲 」。 延遲是以毫秒為單位指定。 如果有的話，啟用或停用規則的 UI 內容，該時間間隔延遲的作業，會導致延遲。 如果規則變更回之前的延遲間隔，然後會發生任何事。 這項機制可以用來 「 錯開"初始化步驟-特別一次初始化，而不需依賴計時器，或註冊閒置通知。  
  
 例如，您可以指定您將測試載入規則有 100 毫秒的延遲：  
  
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
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID 是指 UI 內容。 每當 UI 內容因作用中和 false，將會成立的詞彙。|  
|HierSingleSelectionName:\<模式 >|每當使用中的階層中的選擇是單一項目和選取的項目名稱符合.Net 規則運算式 」 模式 」 所指定詞彙將會成立。|  
|UserSettingsStoreQuery:\<查詢 >|「 查詢 」 代表完整路徑到使用者設定存放區必須評估為非零值。 查詢分割成"collection"和"propertyName"，在最後一個斜線。|  
|ConfigSettingsStoreQuery:\<查詢 >|「 查詢 」 代表完整路徑到組態設定存放區必須評估為非零值。 查詢分割成"collection"和"propertyName"，在最後一個斜線。|  
|ActiveProjectFlavor:\<projectTypeGuid >|每當目前選取的專案具備一詞是否會為 true （彙總） 和的類別，比對指定的專案類型的 GUID。|  
|ActiveEditorContentType:\<contentType >|文字編輯器，具有給定的內容類型選取的文件時，將會成立一詞。|  
|ActiveProjectCapability:\<運算式 >|使用中的專案功能符合提供的運算式時，該詞彙就為 true。 運算式可以是類似 VB &#124; CSharp|  
|SolutionHasProjectCapability:\<運算式 >|與上述類似，但是詞彙也是方案中有任何運算式比對的載入的專案。|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|每當有具備 （彙總） 的專案和的類別，比對指定的專案類型 GUID 的解決方案，將會成立一詞。|


  
## <a name="compatibility-with-cross-version-extension"></a>副檔名為跨版本相容性  
 根據的 UI 內容是在 Visual Studio 2015 的新功能並不會匯出至較早版本的規則。 這會建立為目標的 Visual Studio 會自動載入在 Visual Studio 2013 及更早版本，但可受益於以規則為基礎 UI 內容，以防止被自動載入 Visual Studio 2015 中的多個版本的延伸模組/封裝有問題。  
  
 為了支援這類封裝，AutoLoadPackages 登錄中的項目現在可以提供其值欄位，以表示 Visual Studio 2015 和更新版本，應該略過的項目中的旗標。 作法是加上旗標選項<xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>。 現在可以將加入 Vspackage **SkipWhenUIContextRulesActive**選項設定為其<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性來指出應該忽略項目，在 Visual Studio 2015 及更新版本。  
  
## <a name="extensible-ui-context-rules"></a>可延伸的 UI 內容規則  
 某些情況下，封裝無法使用 UI 內容的靜態規則。 例如，假設您有支援擴充性，使得命令狀態根據匯入的 MEF 提供者所支援的編輯器類型的封裝。 支援目前的編輯類型擴充功能是否已啟用命令。 在這種情況下封裝本身無法使用靜態 UI 內容規則，因為條款也可能會變更哪些 MEF 根據延伸模組都會提供。  
  
 為了支援這類封裝，以規則為基礎的 UI 內容支援硬式編碼運算式"*"，表示所有以下的條款將會使用已加入或者。 這允許在已知的規則基礎 UI 內容來定義主要封裝，並繫結到此內容其命令狀態。 之後針對主要封裝任何 MEF 擴充功能可以加入它支援而不會影響其他條款或主要運算式編輯器的條款。  
  
 建構函式<xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>文件會顯示可延伸的 UI 內容規則的語法。