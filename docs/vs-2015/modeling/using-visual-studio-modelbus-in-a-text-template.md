---
title: 在文字模板中使用 ModelBus |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3815ed93156a70a547a892a281f8907419503a3d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845405"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>使用文字範本中的 Visual Studio ModelBus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您撰寫的文字模板會讀取包含 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus 參考的模型，您可能會想要解析參考以存取目標模型。 在此情況下，您必須調整文字模板和參考的特定領域語言（Dsl）：

- 做為參考目標的 DSL 必須擁有已設定為從文字模板存取的 ModelBus 介面卡。 如果您也從其他程式碼存取 DSL，則除了標準 ModelBus 介面卡以外，還需要重新配置的介面卡。

     介面卡管理員必須繼承自[VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) ，而且必須將屬性 `[HostSpecific(HostName)]`。

- 範本必須繼承自[ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))。

> [!NOTE]
> 如果您想要讀取不包含 ModelBus 參考的 DSL 模型，您可以使用在 DSL 專案中產生的指示詞處理器。 如需詳細資訊，請參閱[從文字模板存取模型](../modeling/accessing-models-from-text-templates.md)。

 如需文字模板的詳細資訊，請參閱[使用 T4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>建立可從文字模板存取的模型匯流排介面卡
 若要解析文字模板中的 ModelBus 參考，目標 DSL 必須有相容的介面卡。 文字模板會在與 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 檔編輯器不同的 AppDomain 中執行，因此，介面卡必須載入模型，而不是透過 DTE 來存取。

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>建立與文字模板相容的 ModelBus 介面卡

1. 如果目標 DSL 解決方案沒有**ModelBusAdapter**專案，請使用 Modelbus 延伸模組 wizard 建立一個：

    1. 下載並安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus 擴充功能（如果您尚未這麼做）。 如需詳細資訊，請參閱[視覺效果和模型化 SDK](https://www.visualstudio.com/)。

    2. 開啟 DSL 定義檔。 以滑鼠右鍵按一下設計介面，然後按一下 [**啟用 Modelbus**]。

    3. 在對話方塊中，選取 [**我想要將此 DSL 公開給 ModelBus**]。 如果您想要讓此 DSL 公開其模型，並使用其他 Dsl 的參考，您可以同時選取這兩個選項。

    4. 按一下 [ **確定**]。 新專案 "ModelBusAdapter" 會隨即加入至 DSL 方案。

    5. 按一下 [**轉換所有範本**]。

    6. 重建方案。

2. 如果您想要從文字模板和其他程式碼（例如命令）存取 DSL，請複製**ModelBusAdapter**專案：

    1. 在 Windows Explorer 中，複製並貼上包含**ModelBusAdapter**的資料夾。

    2. 將專案檔重新命名（例如， **T4ModelBusAdapter .csproj**）。

    3. 在**方案總管**中，以滑鼠右鍵按一下方案節點，指向 [**加入**]，然後按一下 [**現有專案**]。 找出新的介面卡專案**T4ModelBusAdapter**。

    4. 在新專案的每個 `*.tt` 檔案中，變更命名空間。

    5. 以滑鼠右鍵按一下方案總管中的新專案，然後按一下 [屬性]。 在 [屬性編輯器] 中，變更所產生元件和預設命名空間的名稱。

    6. 在 DslPackage 專案中，新增新介面卡專案的參考，使其具有這兩個介面卡的參考。

    7. 在 DslPackage\source.extension.tt 中，新增參考新介面卡專案的程式程式碼。

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **轉換所有範本**並重建方案。 不應該發生任何組建錯誤。

3. 在新介面卡專案中，新增下列元件的參考：

    - VisualStudio. TextTemplating. 11。0

         VisualStudio. TextTemplating. 建立11。0

4. 在 AdapterManager.tt 中：

    - 變更 AdapterManagerBase 的宣告，使其繼承自[VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))。

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - 在檔案結尾附近，將 HostSpecific 屬性取代為 AdapterManager 類別之前。 移除下列程式程式碼：

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         插入下列程式程式碼：

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         此屬性會篩選 modelbus 取用者搜尋介面卡時可用的介面卡集合。

5. **轉換所有範本**並重建方案。 不應該發生任何組建錯誤。

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>撰寫可以解析 ModelBus 參考的文字模板
 一般來說，您一開始會從「來源」 DSL 讀取並產生檔案的範本。 此範本會使用來源 DSL 專案中產生的指示詞，以[從文字模板存取模型](../modeling/accessing-models-from-text-templates.md)中所述的方式來讀取來源模型檔案。 不過，來源 DSL 包含對「目標」 DSL 的 ModelBus 參考。 因此，您會想要啟用範本程式碼來解析參考並存取目標 DSL。 因此，您必須遵循下列步驟來調整範本：

- 將範本的基類變更為[ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))。

- 在範本指示詞中包含 `hostspecific="true"`。

- 將元件參考新增至目標 DSL 及其介面卡，並啟用 ModelBus。

- 您不需要在目標 DSL 中產生的指示詞。

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

 執行此文字模板時，`SourceDsl` 指示詞會將檔案載入 `Sample.source`。 從 `this.ModelRoot`開始，此範本可以存取該模型的元素。 程式碼可以使用該 DSL 的網域類別和屬性。

 此外，此範本也可以解析 ModelBus 參考。 當參考指向目標模型時，元件指示詞可讓程式碼使用該模型 DSL 的網域類別和屬性。

- 如果您未使用 DSL 專案所產生的指示詞，則也應該包含下列各項。

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- 使用 `this.ModelBus` 來取得 ModelBus 的存取權。

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>逐步解說：測試使用 ModelBus 的文字模板
 在此逐步解說中，您會遵循下列步驟：

1. 建立兩個 Dsl。 一個 DSL （取用*者*）有一個 `ModelBusReference` 屬性，可以參考另一個 Dsl （*提供者*）。

2. 在提供者中建立兩個 ModelBus 介面卡：一個供文字模板存取，另一個用於一般程式碼。

3. 在單一實驗專案中建立 Dsl 的實例模型。

4. 在一個模型中設定網域屬性，以指向另一個模型。

5. 撰寫可開啟所指向之模型的按兩下處理常式。

6. 撰寫可載入第一個模型的文字模板、遵循另一個模型的參考，然後讀取其他模型。

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>建立可供 ModelBus 存取的 DSL

1. 建立新的 DSL 解決方案。 在此範例中，請選取 [工作流程] 方案範本。 將語言名稱設定為 `MBProvider`，並將副檔名設為 ". 提供"。

2. 在 DSL 定義圖中，以滑鼠右鍵按一下圖表的空白部分，而不在頂端附近，然後按一下 [**啟用 Modelbus**]。

   - 如果您看不到 [**啟用 Modelbus**]，則必須下載並安裝 VMSDK Modelbus 擴充功能。 請在 VMSDK 網站上找到它：[視覺效果和模型化 SDK](https://www.visualstudio.com/)。

3. 在 [**啟用 Modelbus** ] 對話方塊中，選取 [將**此 DSL 公開給 Modelbus**]，然後按一下 **[確定]** 。

    新的專案（`ModelBusAdapter`）會加入至方案。

   您現在有一個可透過 ModelBus 的文字模板存取的 DSL。 您可以在命令、事件處理常式或規則的程式碼中解析它的參考，這些都是在模型檔案編輯器的 AppDomain 中運作。 不過，文字模板會在不同的 AppDomain 中執行，而且在編輯時無法存取模型。 如果您想要從文字模板存取此 DSL 的 ModelBus 參考，您必須有個別的 ModelBusAdapter。

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>建立為文字模板設定的 ModelBus 介面卡

1. 在 Windows Explorer 中，複製並貼上包含 ModelBusAdapter 的資料夾。

    將資料夾命名為 T4ModelBusAdapter。

    將專案檔 T4ModelBusAdapter 重新命名。

2. 在方案總管中，將 T4ModelBusAdapter 新增至 MBProvider 方案。 以滑鼠右鍵按一下方案節點，指向 [**加入**]，然後按一下 [**現有專案**]。

3. 以滑鼠右鍵按一下 T4ModelBusAdapter 專案節點，然後按一下 [屬性]。 在 [專案屬性] 視窗中，將 [**元件名稱**] 和 [**預設命名空間**] 變更為 `Company.MBProvider.T4ModelBusAdapters`。

4. 在 T4ModelBusAdapter 中的每個 * tt 檔案中，將 "T4" 插入命名空間的最後一個部分，讓這一行看起來像下面這樣。

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. 在 `DslPackage` 專案中，將專案參考新增至 `T4ModelBusAdapter`。

6. 在 DslPackage\source.extension.tt 中，將下面這一行新增到 `<Content>`底下。

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. 在 `T4ModelBusAdapter` 專案中，加入的參考： **VisualStudio. TextTemplating. 11.0**

8. 開啟 T4ModelBusAdapter\AdapterManager.tt：

   1. 將 AdapterManagerBase 的基類變更為[VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))。 檔案的這個部分現在與下列內容類別似。

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

   2. 在檔案結尾附近，于 [類別 AdapterManager] 前面插入下列其他屬性。

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

9. 按一下方案總管標題列中的 [**轉換所有範本**]。

10. 重建方案。 按一下 F5。

11. 按 F5 確認 DSL 是否正常運作。 在實驗專案中，開啟 [`Sample.provider`]。 關閉 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體。

    此 DSL 的 ModelBus 參考現在可在文字模板中解析，也可以在一般程式碼中解決。

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>使用 ModelBus 參考網域屬性來建立 DSL

1. 使用 [最小語言解決方案] 範本來建立新的 DSL。 將語言命名為 MBConsumer，並將副檔名設定為「使用」。

2. 在 DSL 專案中，新增 MBProvider DSL 元件的參考。 以滑鼠右鍵按一下 `MBConsumer\Dsl\References`，然後按一下 [**加入參考**]。 在 [**流覽**] 索引標籤中，找出 `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    這可讓您建立使用其他 DSL 的程式碼。 如果您想要建立數個 Dsl 的參考，請同時新增它們。

3. 在 DSL 定義圖中，以滑鼠右鍵按一下圖表，然後按一下 [**啟用 ModelBus**]。 在對話方塊中，選取 [**啟用此 DSL 以使用 ModelBus**]。

4. 在類別 `ExampleElement`中，加入新的網域屬性 `MBR`，然後在屬性視窗中，將其類型設定為 [`ModelBusReference`]。

5. 以滑鼠右鍵按一下圖表上的網域屬性，然後按一下 [**編輯 ModelBusReference 特定屬性**]。 在對話方塊中，選取**模型元素**。

    將檔案對話方塊篩選器設定如下。

    `Provider File|*.provide`

    "&#124;" 後面的子字串是 [檔案選取] 對話方塊的篩選準則。 您可以使用 * 將它設定為允許任何檔案。\*

    在 [**模型專案類型**] 清單中，輸入提供者 DSL 中一個或多個網域類別的名稱（例如，MBProvider. Task）。 它們可以是抽象類別。 如果您將清單保留空白，使用者可以設定任何元素的參考。

6. 關閉對話方塊並**轉換所有範本**。

   您已建立可包含另一個 DSL 中專案之參考的 DSL。

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>在方案中建立另一個檔案的 ModelBus 參考

1. 在 MBConsumer 方案中，按下 CTRL + F5。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗實例會在**MBConsumer\Debugging**專案中開啟。

2. 新增範例的複本。提供給**MBConsumer\Debugging**專案。 這是必要的，因為 ModelBus 參考必須參考同一個方案中的檔案。

   1. 以滑鼠右鍵按一下 [調試] 專案，指向 [**加入**]，然後按一下 [**現有專案**]。

   2. 在 [**新增專案**] 對話方塊中，將篩選準則設定為 [所有檔案] **（\*.\*）** 。

   3. 流覽至 `MBProvider\Debugging\Sample.provide`，然後按一下 [**新增**]。

3. 開啟 `Sample.consume`。

4. 按一下一個範例圖形，然後在 屬性視窗中，按一下 **[...]** ，然後在 [MBR] 屬性中。 在對話方塊中，按一下 **[流覽]** 並選取 [`Sample.provide`]。 在 [專案] 視窗中，展開 [類型] 工作，然後選取其中一個元素。

5. 儲存檔案。

    （尚未關閉 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例。）

   您已建立一個模型，其中包含另一個模型中專案的 ModelBus 參考。

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>解析文字模板中的 ModelBus 參考

1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例中，開啟範例文字模板檔案。 設定其內容，如下所示。

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

    1. 必須設定 `template` 指示詞的 `hostSpecific` 和 `inherits` 屬性。

    2. 取用者模型會透過在該 DSL 中產生的指示詞處理器，以一般方式存取。

    3. 元件和匯入指示詞必須能夠存取 ModelBus 和提供者 DSL 的類型。

    4. 如果您知道許多 Mbr 都連結到相同的模型，最好只呼叫 CreateAdapter 一次。

2. 儲存範本。 請確認產生的文字檔與下列類似。

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>解析手勢處理常式中的 ModelBus 參考

1. 如果正在執行，請關閉 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例。

2. 新增名為 MBConsumer\Dsl\Custom.cs 的檔案，並將其內容設定如下。

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

3. 按下 CTRL+F5 鍵。

4. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例中，開啟 `Debugging\Sample.consume`。

5. 按兩下一個圖形。

     如果您已在該元素上設定 MBR，則會開啟參考的模型，並選取所參考的元素。

## <a name="see-also"></a>請參閱
 [使用 Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)程式[代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)來整合模型
