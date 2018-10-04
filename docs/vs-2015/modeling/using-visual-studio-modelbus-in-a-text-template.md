---
title: 使用文字範本中的 Visual Studio ModelBus |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3c6c3d9e35f14a03f8130982c562ba812ac11d6b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499481"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>使用文字範本中的 Visual Studio ModelBus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[文字範本中使用 Visual Studio ModelBus](https://docs.microsoft.com/visualstudio/modeling/using-visual-studio-modelbus-in-a-text-template)。  
  
如果您撰寫文字範本，以讀取模型，其中包含[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ModelBus 參考，您可能想要解決存取目標模型的參考。 在此情況下，您必須調整文字範本和參考的特定領域語言 (Dsl):  
  
-   是一個參考目標 DSL 必須具有已設定為從文字範本存取的 ModelBus 配接器。 您也會從其他程式碼存取 DSL，重新設定配接器需要除了標準的 ModelBus 配接器。  
  
     配接器管理員必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>必須有屬性和`[HostSpecific(HostName)]`。  
  
-   範本必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。  
  
> [!NOTE]
>  如果您想要讀取不包含 ModelBus 參考的 DSL 模型，您可以使用會在您的 DSL 專案中產生指示詞處理器。 如需詳細資訊，請參閱 <<c0> [ 文字範本存取模型](../modeling/accessing-models-from-text-templates.md)。  
  
 如需文字範本的詳細資訊，請參閱[使用 T4 文字範本在設計階段的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>建立從文字範本存取模型匯流排配接器  
 若要解決 ModelBus 參考文字範本中的，目標 DSL 必須具有相容的配接器。 從不同的 AppDomain 中執行的文字範本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]文件編輯器，且因此配接器載入而不是存取 DTE 透過模型。  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>若要建立適用於文字範本的 ModelBus 配接器  
  
1.  如果目標 DSL 方案並沒有**ModelBusAdapter**專案中，建立一個使用 Modelbus 擴充功能精靈:  
  
    1.  下載並安裝[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ModelBus 擴充功能，如果您還沒有這麼。 如需詳細資訊，請參閱 < [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
    2.  開啟 DSL 定義檔。 以滑鼠右鍵按一下設計介面，然後按一下**啟用 Modelbus**。  
  
    3.  在對話方塊中，選取**我想要這個 DSL 公開給 ModelBus**。 如果您想要這個 DSL 公開給其模型並使用其他 Dsl 的參考，您可以選取這兩個選項。  
  
    4.  按一下 [確定 **Deploying Office Solutions**]。 新專案 "ModelBusAdapter" 會隨即加入至 DSL 方案。  
  
    5.  按一下 **轉換所有範本**。  
  
    6.  重建方案。  
  
2.  如果您想要存取 DSL，從文字範本和其他程式碼，例如命令，從重複**ModelBusAdapter**專案：  
  
    1.  在 Windows 檔案總管中，複製並貼上包含的資料夾**ModelBusAdapter.csproj**。  
  
    2.  重新命名專案檔 (例如，若要**T4ModelBusAdapter.csproj**)。  
  
    3.  在**方案總管**，以滑鼠右鍵按一下方案節點，指向**新增**，然後按一下 **現有專案**。 找不到新的配接器專案中， **T4ModelBusAdapter.csproj**。  
  
    4.  在每個`*.tt`檔案的新專案中，變更命名空間。  
  
    5.  以滑鼠右鍵按一下方案總管] 中新的專案，然後按一下 [屬性。 在屬性編輯器 中，變更產生的組件和預設命名空間的名稱。  
  
    6.  在 DslPackage 專案中，加入新的配接器專案的參考，使其具有兩種配接器的參考。  
  
    7.  在 DslPackage\source.extension.tt，新增一行，以參考新的配接器專案。  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **轉換所有範本**並重建方案。 應該會不發生任何建置錯誤。  
  
3.  在新的配接器專案中，加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  在 AdapterManager.tt:  
  
    -   變更 AdapterManagerBase 的宣告，使它繼承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   檔案結尾附近取代 HostSpecific 屬性之前的 AdapterManager 類別。 移除下面這一行：  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         插入下面這一行：  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         這個屬性來篩選配接器會搜尋 modelbus 取用者時可用的配接器集。  
  
5.  **轉換所有範本**並重建方案。 應該會不發生任何建置錯誤。  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>撰寫文字範本可以解析 ModelBus 參考  
 一般而言，您會開始讀取，並產生從 「 來源 」 DSL 檔案的範本。 此範本會使用在來源 DSL 專案中讀取來源模型檔中所述的方式產生指示詞[文字範本存取模型](../modeling/accessing-models-from-text-templates.md)。 不過，來源 DSL 包含 「 目標 」 DSL 的 ModelBus 參考。 您因此想要讓範本程式碼，來解析的參考，以及存取目標 DSL。 您因此必須遵循下列步驟來配合範本：  
  
-   變更範本的基底類別<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。  
  
-   包含`hostspecific="true"`範本指示詞中。  
  
-   目標 DSL 和其介面卡，以及啟用 ModelBus，請新增組件參考。  
  
-   您不需要產生目標 DSL 的一部分的指示詞。  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let’s assume they’re all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 執行這個文字範本時，`SourceDsl`指示詞會載入該檔案`Sample.source`。 範本可以存取該模型，從開始的項目`this.ModelRoot`。 程式碼可以使用的網域類別和屬性的 DSL。  
  
 此外，範本可以解析 ModelBus 參考。 參考指向之目標模型時，其中的組件指示詞會讓程式碼使用的網域類別和屬性，該模型的 DSL。  
  
-   如果您不要使用所產生的 DSL 專案的指示詞，您也應該包含下列。  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   使用`this.ModelBus`取得存取權的 ModelBus。  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>逐步解說： 測試使用 ModelBus 的文字範本  
 在本逐步解說中，您可以遵循下列步驟：  
  
1.  建構兩個 Dsl。 同一個 DSL 中，*消費者*，已`ModelBusReference`DSL，可以參考的屬性*提供者*。  
  
2.  提供者中建立兩個的 ModelBus 配接器： 一個用於另一個則用於一般程式碼的文字範本存取。  
  
3.  在單一實驗性專案中建立 Dsl 執行個體的模型。  
  
4.  設定為指向另一個模型的模型中的網域屬性。  
  
5.  撰寫開啟模型所指向的按兩下處理常式。  
  
6.  撰寫文字範本，可以載入的第一個模型，請遵循參考到其他模型，並讀取其他模型。  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>建構 DSL 的 ModelBus 可存取  
  
1.  建立新的 DSL 方案。 針對此範例中，選取工作流程 方案範本。 若要設定的語言名稱`MBProvider`和 「.provide"副檔名。  
  
2.  在 DSL 定義圖表中，以滑鼠右鍵按一下最上方，不是圖表的空白部分，並再按**啟用 Modelbus**。  
  
    -   如果您看不見**啟用 Modelbus**，您必須下載並安裝 VMSDK ModelBus 擴充功能。 VMSDK 網站上找到它： [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
3.  在 **啟用 Modelbus**對話方塊中，選取**這個 DSL 公開給 ModelBus**，然後按一下 **確定**。  
  
     新的專案， `ModelBusAdapter`，加入至方案。  
  
 您現在已可存取的 ModelBus 透過文字範本的 DSL。 在程式碼中的命令、 事件處理常式或全部都運作的模型檔案編輯器的 AppDomain 中的規則，就可以解決它的參考。 不過，文字範本在不同的 AppDomain 中執行，而當正在進行編輯時，無法存取模型。 如果您想要存取此 DSL 的 ModelBus 參考從文字範本，您必須擁有個別的 ModelBusAdapter。  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>若要建立文字範本已設定的 ModelBus 配接器  
  
1.  在 Windows 檔案總管中，複製並貼上包含 ModelBusAdapter.csproj 的資料夾。  
  
     將資料夾命名為 T4ModelBusAdapter。  
  
     重新命名專案檔 T4ModelBusAdapter.csproj。  
  
2.  在方案總管 中，新增 T4ModelBusAdapter MBProvider 解決方案。 以滑鼠右鍵按一下方案節點，指向**新增**，然後按一下**現有專案**。  
  
3.  以滑鼠右鍵按一下 T4ModelBusAdapter 專案節點，然後按一下 屬性。 在 [專案屬性] 視窗中，變更**組件名稱**並**預設命名空間**到`Company.MBProvider.T4ModelBusAdapters`。  
  
4.  每 *.tt 檔案中 T4ModelBusAdapter 的說明，「 T4"插入命名空間的最後一個部分，使該行如下所示。  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  在 `DslPackage`專案中，加入的專案參考`T4ModelBusAdapter`。  
  
6.  在 DslPackage\source.extension.tt，加入下列這行程式`<Content>`。  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  在 `T4ModelBusAdapter`專案中，加入的參考： **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  開啟 T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  將 AdapterManagerBase 的基底類別變更為 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。 此組件的檔案現在會如下所示。  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  檔案結尾附近插入下列額外的屬性，類別 AdapterManager 的前面。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         結果如下所示。  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. 按一下 [**轉換所有範本**中的方案總管] 標題列。  
  
10. 重建方案。 按一下 F5。  
  
11. 確認 DSL 運作按下 F5。 在實驗性的專案中，開啟`Sample.provider`。 關閉 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體。  
  
 在文字範本，也在一般程式碼，現在可以解決此 DSL 的 ModelBus 參考。  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>建構 DSL 的 ModelBus 參考網域屬性  
  
1.  使用 [最小語言] 方案範本建立新的 DSL。 命名 MBConsumer 的語言，並設定 「.consume"副檔名。  
  
2.  在 DSL 專案中加入 MBProvider DSL 的組件的參考。 以滑鼠右鍵按一下`MBConsumer\Dsl\References`，然後按一下 **加入參考**。 在 **瀏覽**索引標籤上，找出 `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     這可讓您建立使用其他 DSL 的程式碼。 如果您想要建立數個 Dsl 的參考，也請對它們進行新增。  
  
3.  在 DSL 定義圖表中，以滑鼠右鍵按一下圖表，並再按**啟用 ModelBus**。 在對話方塊中，選取**啟用這個 DSL 以使用 ModelBus**。  
  
4.  在類別中`ExampleElement`，將新的網域屬性`MBR`，並在 [屬性] 視窗中，將其類型設`ModelBusReference`。  
  
5.  以滑鼠右鍵按一下圖表上的網域屬性，然後按一下**編輯 ModelBusReference 特定屬性**。 在對話方塊中，選取**模型項目**。  
  
     下列設定檔案對話方塊篩選器。  
  
     `Provider File|*.provide`  
  
     之後的子字串"&#124;"為檔案選取對話方塊的篩選條件。 您可以將它設定為允許的任何檔案使用 *。\*  
  
     在 **模型項目型別**清單中，輸入提供者 (例如 Company.MBProvider.Task) DSL 中的一或多個網域類別的名稱。 它們可以是抽象類別。 如果您將清單保留空白，使用者可以設定任何項目參考。  
  
6.  關閉對話方塊並**轉換所有範本**。  
  
 您已建立可包含另一個 DSL 中的項目參考的 DSL。  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>在方案中建立另一個檔案的 ModelBus 參考  
  
1.  在 MBConsumer 解決方案中，按 CTRL + F5。 實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]以開啟**MBConsumer\Debugging**專案。  
  
2.  新增一份要 Sample.provide **MBConsumer\Debugging**專案。 這是必要的因為 ModelBus 參考必須參考相同的方案中的檔案。  
  
    1.  以滑鼠右鍵按一下 偵錯專案，指向**新增**，然後按一下**現有項目**。  
  
    2.  在 [**加入項目**] 對話方塊中，將篩選器設**的所有檔案 (\*。\*)**.  
  
    3.  瀏覽至`MBProvider\Debugging\Sample.provide`，然後按一下 **新增**。  
  
3.  開啟 `Sample.consume`。  
  
4.  一個 「 範例 」 圖形，然後在 [屬性] 視窗中，按一下 **[...]** MBR 屬性中。 在對話方塊中，按一下**瀏覽**，然後選取`Sample.provide`。 在項目] 視窗中，展開 [工作類型，然後選取其中一個項目。  
  
5.  儲存檔案。  
  
     (請勿尚未關閉的實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。)  
  
 您已建立包含另一個模型中項目的 ModelBus 參考的模型。  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>解析文字範本中的 ModelBus 參考  
  
1.  在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，開啟範例文字範本檔案。 設定其內容如下所示。  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     請注意以下要點：  
  
    1.  `hostSpecific`並`inherits`屬性的`template`必須設定指示詞。  
  
    2.  取用者模型指示詞處理器所產生的 DSL 中透過一般方式存取。  
  
    3.  組件 」 和 「 匯入的指示詞必須能夠存取 ModelBus 與 DSL 的提供者的類型。  
  
    4.  如果您知道許多 Mbr 會連結到同一個模型，它是呼叫 CreateAdapter 只能一次。  
  
2.  儲存範本。 請確認產生的文字檔案如下所示。  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>解決在軌跡處理常式中的 ModelBus 參考  
  
1.  關閉實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，如果它正在執行。  
  
2.  加入檔案，名為 MBConsumer\Dsl\Custom.cs 並將其內容如下。  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  按下 CTRL+F5。  
  
4.  在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，開啟`Debugging\Sample.consume`。  
  
5.  按兩下一個圖形。  
  
     如果您已將 MBR 該項目上，開啟 參考的模型，並選取參考的項目。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)



