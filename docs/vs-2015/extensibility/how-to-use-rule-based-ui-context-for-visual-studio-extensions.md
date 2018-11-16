---
title: 如何： 使用 Visual Studio 擴充功能的規則為基礎的 UI 內容 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: 1c7f1bf5aa80316e0b663f247ce905060f6029fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784321"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>如何： 使用 Visual Studio 擴充功能的規則為基礎的 UI 內容
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 可讓載入 Vspackage 時有特定已知<xref:Microsoft.VisualStudio.Shell.UIContext>s 會啟動。 不過，這些 UI 內容不是非常細微精密，不離開延伸模組作者任何選擇，但選擇可用的 UI 內容，就會啟動點之前，他們其實想要載入 VSPackage。 如需已知的 UI 內容，請參閱<xref:Microsoft.VisualStudio.Shell.KnownUIContexts>。  
  
 載入封裝可能會造成效能影響，比在需要更快載入它們並非最佳的作法。 Visual Studio 2015 導入規則型 UI 內容，一種機制，讓延伸模組作者可以定義在其下啟動 UI 內容，以及相關聯的 Vspackage 載入的精確條件的概念。  
  
## <a name="rule-based-ui-context"></a>以規則為基礎的 UI 內容  
 「 規則 」 包含新的 UI 內容 (GUID) 和參考一或多個 「 條款 」 的布林運算式結合邏輯"and"、"，"not"作業。 「 條款 」 會在執行階段以動態方式評估，每當任何其條款的變更，會重新評估運算式。 當運算式評估為 true 時，就會啟動相關聯的 UI 內容。 否則，UI 內容會取消已啟動。  
  
 以規則為基礎的 UI 內容可以使用各種不同的方式：  
  
1. 指定命令和工具視窗的可見性條件的約束。 直到符合 UI 內容規則時，您可以隱藏的命令/工具視窗。  
  
2. 為自動載入條件約束： 只在符合規則時，自動載入封裝  
  
3. 延遲的工作： 延遲載入，直到經過指定的間隔，且仍然符合規則。  
  
   此機制可供任何 Visual Studio 擴充功能。  
  
## <a name="create-a-rule-based-ui-context"></a>建立規則為基礎的 UI 內容  
 假設您有稱為 TestPackage，可提供後者只適用於具有".config"副檔名的檔案功能表命令擴充功能。 VS2015 之前, 的最佳選項是載入 TestPackage 時<xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>UI 內容已啟動。 這不是有效的因為載入的方案甚至可能不包含.config 檔案。 告訴我們，請參閱如何以規則為基礎的 UI 內容可用來啟用的 UI 內容時，才具有.config 副檔名的檔案已選取，然後啟動該 UI 內容時，載入 TestPackage。  
  
1. 定義新的 ui 內容 GUID，並加入 VSPackage 類別<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>。  
  
    例如，假設新的 ui 內容 「 UIContextGuid"是要加入。 建立 GUID (您可以建立 GUID，依序按一下 工具-> 建立 guid) 是 「 8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"。 然後，請將下列套件類別：  
  
   ```csharp  
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
   ```  
  
    針對屬性，新增下列: （這些屬性的詳細資料將於稍後說明）  
  
   ```csharp  
   [ProvideAutoLoad(TestPackage.UIContextGuid)]      
   [ProvideUIContextRule(TestPackage.UIContextGuid,  
       name: "Test auto load",   
       expression: "DotConfig",  
       termNames: new[] { "DotConfig" },  
       termValues: new[] { "HierSingleSelectionName:.config$" })]  
   ```  
  
    這些中繼資料定義新的 ui 內容 GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) 和運算式參考的 「 DotConfig"的詞彙。 「 DotConfig 」 一詞會評估為 true，每當目前的選取範圍，在使用中的階層架構中有符合規則運算式模式的名稱"\\.config$ 」 （結尾為".config"）。 （預設值） 值定義的規則適用於偵錯的選擇性名稱。  
  
    屬性的值會新增至 pkgdef 建置期間之後產生。  
  
2. VSCT 檔案中 TestPackage 的命令，加入適當的命令中的"DynamicVisibility 」 旗標：  
  
   ```xml  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
3. 在 VSCT 可視性 區段中，將繫結適當的命令，以新的 ui 內容 #1 中所定義的 GUID:  
  
   ```xml  
   <VisibilityConstraints>   
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
   </VisibilityConstraints>  
   ```  
  
4. 在 [符號] 區段中，新增 ui 內容的定義：  
  
   ```xml  
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
   ```  
  
    現在，*.config 檔案的內容功能表命令將會顯示在 [方案總管] 中選取的項目是".config"檔案，直到已選取其中一個這些命令，將不會載入封裝時，才。  
  
   接下來，讓我們使用來確認只有在我們預期當它載入封裝的 偵錯工具。 若要偵錯 TestPackage:  
  
5. 在設定的中斷點<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
6. 建置 TestPackage 並開始偵錯。  
  
7. 建立專案或開啟其中一個。  
  
8. 選取副檔名為.config 以外的任何檔案。應該不會叫用中斷點。  
  
9. 選取的 App.Config 檔案。  
  
   TestPackage 載入，並在中斷點停止。  
  
## <a name="adding-more-rules-for-ui-context"></a>新增更多的規則的 UI 內容  
 由於 UI 內容規則都是布林運算式，您可以新增更多限制的規則 UI 內容。 例如，在上述的 UI 內容中，您可以指定只在載入內含專案的方案時才套用規則。 如此一來，命令不會顯示是否您開啟".config"檔案以獨立檔案，而非專案的一部分。  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 現在運算式會參考三個詞彙。 前兩個詞彙，「 SingleProject"和"MultipleProjects 」，請參閱其他已知的 UI 內容 （由其 Guid 中)。 第三個詞彙，「 DotConfig 」 是以規則為基礎的 UI 內容，而此一我們稍早定義。  
  
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
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID 是指 UI 內容。 每當 UI 內容因作用中和，則為 false，則一詞將會是 true。|  
|HierSingleSelectionName:\<模式 >|一詞的作用中的階層架構中的選擇是單一項目和選取的項目名稱符合 「 模式 」 所指定的.Net 規則運算式時，將會是 true。|  
|UserSettingsStoreQuery:\<查詢 >|「 查詢 」 到使用者設定存放區必須評估為非零值表示的完整路徑。 查詢分割成"collection"和"propertyName 」，在最後的斜線。|  
|ConfigSettingsStoreQuery:\<查詢 >|「 查詢 」 到組態設定存放區必須評估為非零值表示的完整路徑。 查詢分割成"collection"和"propertyName 」，在最後的斜線。|  
|ActiveProjectFlavor:\<projectTypeGuid >|詞彙將會是 true，每當目前選取的專案特定 （彙總） 和類別，比對指定的專案類型 GUID。|  
|ActiveEditorContentType:\<contentType >|選取的文件時指定的內容類型文字編輯器，將會是 true 一詞。|  
|ActiveProjectCapability:\<運算式 >|作用中的專案功能符合提供的運算式時，則為 true 的詞彙。 運算式可以是 VB 類似&#124;CSharp|  
|SolutionHasProjectCapability:\<運算式 >|當方案中有任何比對運算式的載入的專案時，與上述類似，但是一詞是如此。|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|解決方案具備特色 （彙總） 的專案，並比對指定的專案類型 GUID 類別時，將會是 true 一詞。|


  
## <a name="compatibility-with-cross-version-extension"></a>副檔名為跨版本相容性  
 規則型的 UI 內容是在 Visual Studio 2015 的新功能，並不會移轉至較早版本。 這會建立為目標的 Visual Studio 會自動載入在 Visual Studio 2013 及更早版本，但可受益於以規則為基礎的 UI 內容以避免被自動載入 Visual Studio 2015 中的多個版本的延伸模組/套件有問題。  
  
 為了支援這類套件，AutoLoadPackages 在登錄中的項目現在可以提供其 [值] 欄位來表示在 Visual Studio 2015 及更新版本，應該略過此項目中的旗標。 這可以加上旗標選項，來完成<xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>。 現在可以將加入 Vspackage **SkipWhenUIContextRulesActive**選項設定為其<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性來指出應該忽略的項目，在 Visual Studio 2015 和更新版本。  
  
## <a name="extensible-ui-context-rules"></a>可延伸的 UI 內容規則  
 某些情況下，封裝無法使用靜態的 UI 內容規則。 例如，假設您有支援擴充性，使得命令狀態根據匯入的 MEF 提供者所支援的編輯器類型的封裝。 如果沒有延伸模組支援目前的編輯類型，此命令會啟用。 在此情況下封裝本身無法使用靜態的 UI 內容規則，因為條款會根據哪一個 MEF 擴充功能可變更。  
  
 若要支援這類套件，以規則為基礎的 UI 內容支援硬式編碼運算式"*"表示所有下列條款會與加入或者。 這是用來定義主要封裝的已知的規則型 UI 內容，並將繫結至這個內容其命令狀態。 之後針對主要封裝任何 MEF 擴充功能也可以新增其條款，它支援而不會影響其他條款或主要運算式編輯器。  
  
 建構函式<xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>文件會示範可延伸的 UI 內容規則的語法。

