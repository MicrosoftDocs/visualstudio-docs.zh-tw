---
title: "如何︰ 使用 Visual Studio 擴充功能的規則為基礎的 UI 的內容 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
ms.author: "gregvanl"
caps.handback.revision: 7
---
# 如何︰ 使用 Visual Studio 擴充功能的規則為基礎的 UI 的內容
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 可讓載入 Vspackage 時，某些已知 <xref:Microsoft.VisualStudio.Shell.UIContext>s 會啟動。 不過，這些 UI 內容不是非常精細精細，離開延伸模組作者沒有其他選擇，但選擇可用的 UI 內容啟動點之前，他們其實想要載入 VSPackage。 如需已知 UI 的內容，請參閱 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>。  
  
 載入封裝可能會造成效能影響，比在需要更快載入它們不是最佳做法。 Visual Studio 2015 導入以規則為基礎 UI 的內容，一種機制，讓延伸模組作者可以定義在其下就會啟用 UI 內容和相關聯的 VSPackages 載入的精確條件的概念。  
  
## 以規則為基礎的 UI 的內容  
 「 規則 」，其中包含新的 UI 內容 \(GUID\) 並參考一個或多個 「 詞彙 」 的布林運算式結合邏輯"and"、"，"not"作業。 「 詞彙 」 會在執行階段以動態方式評估，每當任何其條款變更也會重新評估運算式。 當運算式評估為 true 時，就會啟用相關聯的 UI 內容。 否則，UI 是取消啟動。  
  
 可以使用規則為基礎的 UI 內容中有許多種︰  
  
1.  指定命令和工具視窗的可見性條件約束。 您可以隱藏命令\/工具 windows，直到符合 UI 內容規則。  
  
2.  以自動載入條件約束︰ 符合規則時，才會自動載入封裝  
  
3.  延遲的工作︰ 載入指定的間隔時間經過，並仍然符合規則之前的延遲時間。  
  
 此機制可供任何 Visual Studio 擴充功能。  
  
## 建立規則為基礎的 UI 的內容  
 假設您有稱為 TestPackage，它提供了功能表命令，就僅適用於 「.config"副檔名的檔案副檔名。 之前 VS2015，最好的選擇是要載入 TestPackage 時 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI 內容已啟動。 這不是有效的因為載入的方案可能甚至沒有.config 檔案。 讓我們，請參閱如何以規則為基礎的 UI 內容可以用來啟用在 UI 的內容時，才具有.config 副檔名的檔案已選取，並載入 TestPackage 時就會啟用該 UI 的內容。  
  
1.  定義新的 UIContext GUID，並加入 VSPackage 類別 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>。  
  
     例如，假設新 UIContext"UIContextGuid"是要加入。 建立的 GUID \(您可以建立 GUID，依序按一下 \[工具\]\-\> \[建立 guid\) 是 「 8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B 」。 然後，請將下列套件類別內︰  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     針對屬性，加入下列: （這些屬性的詳細資料將會稍後說明）  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     這些中繼資料定義新的 UIContext GUID \(8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B\) 和運算式參考的 「 DotConfig 」 的詞彙。 「 DotConfig 」 一詞評估為 true，只要在使用中的階層架構中目前選取範圍有符合規則運算式模式"\\.config$"（".config"結尾） 的名稱。 （預設） 值定義規則適用於偵錯的選擇性名稱。  
  
     屬性的值會加入至 pkgdef 在建置階段之後產生。  
  
2.  在 TestPackage 命令 VSCT 檔案中，加入適當的命令中的 「 DynamicVisibility 」 旗標︰  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  在 VSCT 可視性區段中，將繫結適當的命令，以新 UIContext \#1 中所定義的 GUID:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  在 \[符號\] 區段中，加入 UIContext 的定義︰  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     現在，\*.config 檔案的內容功能表命令會顯示在 \[方案總管\] 中選取的項目，是一個 「.config 」 檔案中選取其中一個這些命令之前，將不會載入封裝時，才。  
  
 接下來，我們要使用偵錯工具來確認只有在我們預期當它載入封裝。 若要偵錯 TestPackage:  
  
1.  在設定中斷點 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
2.  建置 TestPackage 並開始偵錯。  
  
3.  建立專案或開啟其中一個。  
  
4.  選取副檔名為.config 以外的任何檔案。 應該不會叫用中斷點。  
  
5.  選取的 App.Config 檔案。  
  
 TestPackage 載入，並在中斷點停止。  
  
## 新增更多的規則適用於 UI 的內容  
 由於 UI 內容規則是布林運算式，您可以針對 UI 的內容加入限制更嚴格的規則。 例如，在上述的 UI 內容中，您可以指定只有在載入專案的方案時才套用規則。 如此一來，命令不會顯示是否您開啟 「.config"檔案以獨立檔案，而非專案的一部分。  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 現在運算式參考了三個詞彙。 前兩個詞彙，「 SingleProject 」 和 「 MultipleProjects 」，請參閱其他已知的 UI 內容 （藉由其 Guid\)。 第三個詞彙，「 DotConfig 」 是以規則為基礎的 UI 內容，而此一我們稍早定義。  
  
## 延遲的啟用  
 規則可以有選擇性的 「 延遲 」。 延遲是以毫秒為單位指定。 如果有的話，啟用或停用規則的 UI 內容延遲該時間間隔的會導致延遲。 如果規則變更回之前的延遲間隔，則會發生任何事。 這項機制可以用來 「 錯開 」 初始化步驟\-尤其是單次初始化，而不需依賴計時器或註冊閒置通知。  
  
 例如，您可以指定您的測試負載規則有 100 毫秒的延遲︰  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## 詞彙類型  
 以下是詞彙的所支援的各種類型:  
  
|||  
|-|-|  
|{nnnnnnnn\-nnnn\-nnnn\-nnnn\-nnnnnnnnnnnn nnnn\-nnnn\-如下}|GUID 是指在 UI 的內容。 每當 UI 內容處於使用中則為 false，則一詞將是 true。|  
|HierSingleSelectionName: \< 模式 \>|每當使用中的階層中的選擇是單一項目和選取的項目名稱符合.Net 規則運算式提供 「 模式 」 一詞將是 true。|  
|UserSettingsStoreQuery: \< 查詢 \>|「 查詢 」 到使用者設定存放區必須評估為非零值表示的完整路徑。 查詢會分割為 「 集合 」 和 「 propertyName 」，在最後一個斜線。|  
|ConfigSettingsStoreQuery: \< 查詢 \>|「 查詢 」 到組態設定存放區必須評估為非零值表示的完整路徑。 查詢會分割為 「 集合 」 和 「 propertyName 」，在最後一個斜線。|  
|ActiveProjectFlavor: \< projectTypeGuid \>|每當目前選取的專案特定詞彙將會是 true （彙總） 且具有類別比對指定的專案類型的 GUID。|  
|ActiveEditorContentType: \< contentType \>|選取的文件時指定的內容類型的文字編輯器，將會是 true 一詞。|  
|ActiveProjectCapability: \< 運算式 \>|作用中專案功能符合提供的運算式時，條件為 true。 運算式可以是像是 VB &#124;CSharp|  
|SolutionHasProjectCapability: \< 運算式 \>|方案中有運算式比對任何載入的專案時，與上述類似，但是一詞是如此。|  
  
## 副檔名跨版本相容性  
 根據的 UI 內容是在 Visual Studio 2015 的新功能並不會移植到較早版本的規則。 這會建立為目標的 Visual Studio 會自動載入，在 Visual Studio 2013 及之前版本，但可以受益於以規則為基礎的 UI 內容以避免被自動載入 Visual Studio 2015 中的多個版本的延伸模組\/套件有問題。  
  
 為了支援此類封裝，AutoLoadPackages 在登錄中的項目現在可以提供其值欄位，以指出在 Visual Studio 2015 及以上版本，應該略過項目中的旗標。 可以新增的旗標選項來做到這 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>。 現在可以新增 VSPackages **SkipWhenUIContextRulesActive** 選項及其 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 屬性來指出應該忽略的項目，在 Visual Studio 2015 及以上版本。  
  
## 可延伸的 UI 內容規則  
 有時候，封裝無法使用 UI 內容的靜態規則。 例如，假設您有支援擴充性，使得命令狀態根據匯入的 MEF 提供者所支援的編輯器類型的封裝。 此命令會在支援目前的編輯類型擴充功能是否啟用。 在這種情況下封裝本身無法使用靜態 UI 內容規則，因為條款將會變更哪些 MEF 根據延伸模組都會提供。  
  
 為了支援此類封裝，以規則為基礎的 UI 內容支援硬式編碼運算式"\*"，指出所有條款將會使用已加入或者。 這可定義主要封裝已知的規則基礎 UI 的內容，並將繫結命令狀態給此內容。 之後針對主要封裝任何 MEF 延伸模組可以新增的編輯器不會影響其他條款或主要運算式支援條款。  
  
 建構函式 <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> 文件所示的語法可延伸的 UI 內容規則。