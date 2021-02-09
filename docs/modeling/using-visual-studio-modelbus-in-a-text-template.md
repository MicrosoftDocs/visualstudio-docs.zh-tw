---
title: 在文字模板中使用 ModelBus
description: 如果您要撰寫可讀取包含 Visual Studio ModelBus 參考之模型的文字模板，請瞭解如何解析參考以存取目標模型。
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f65ece27122949fec006d73858c8c89483441f1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924369"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>使用文字範本中的 Visual Studio ModelBus

如果您撰寫可讀取包含 Visual Studio ModelBus 參考之模型的文字模板，您可能會想要解析參考以存取目標模型。 在這種情況下，您必須 (Dsl) ，調整文字模板和參考的特定網域語言：

- 作為參考目標的 DSL 必須具有設定為可從文字模板存取的 ModelBus 介面卡。 如果您也從其他程式碼存取 DSL，除了標準的 ModelBus 介面卡之外，還需要重新設定的介面卡。

     介面卡管理員必須繼承自 [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) ，且必須有屬性 `[HostSpecific(HostName)]` 。

- 範本必須繼承自 [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))。

> [!NOTE]
> 如果您想要讀取不包含 ModelBus 參考的 DSL 模型，您可以使用 DSL 專案中產生的指示詞處理器。 如需詳細資訊，請參閱 [從文字模板存取模型](../modeling/accessing-models-from-text-templates.md)。

如需文字模板的詳細資訊，請參閱 [使用 T4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>建立可從文字模板存取的模型匯流排介面卡

若要解析文字模板中的 ModelBus 參考，目標 DSL 必須有相容的介面卡。 文字模板會在 Visual Studio 檔編輯器的不同 AppDomain 中執行，因此該介面卡必須載入模型，而不是透過 DTE 來存取它。

1. 如果目標 DSL 方案沒有 **ModelBusAdapter** 專案，請使用 Modelbus 擴充功能 wizard 建立一個專案：

    1. 如果您尚未這麼做，請下載並安裝 Visual Studio ModelBus 延伸模組。 如需詳細資訊，請參閱 [視覺化和模型 SDK](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)。

    2. 開啟 DSL 定義檔。 以滑鼠右鍵按一下設計介面，然後按一下 [ **啟用 Modelbus**]。

    3. 在對話方塊中，選取 [ **我要將這個 DSL 公開給 ModelBus**]。 如果您想要讓此 DSL 公開其模型並取用其他 Dsl 的參考，您可以選取兩個選項。

    4. 按一下 [確定]  。 新專案 "ModelBusAdapter" 會隨即加入至 DSL 方案。

    5. 按一下 [ **轉換所有範本**]。

    6. 重建方案。

2. 如果您想要從文字模板和其他程式碼（例如命令）存取 DSL，請複製 **ModelBusAdapter** 專案：

    1. 在 Windows 檔案總管中，複製並貼上包含 **ModelBusAdapter** 的資料夾。

    2. 重新命名專案檔 (例如，將專案檔案重新命名為 **T4ModelBusAdapter .csproj**) 。

    3. 在 **方案總管** 中，以滑鼠右鍵按一下方案節點，指向 [ **新增**]，然後按一下 [ **現有專案**]。 找出新的介面卡專案 **T4ModelBusAdapter。**

    4. 在新專案的每個檔案中 `*.tt` ，變更命名空間。

    5. 在 **方案總管** 中，以滑鼠右鍵按一下新專案，然後按一下 [ **屬性**]。 在 [屬性編輯器] 中，變更所產生元件的名稱和預設命名空間。

    6. 在 DslPackage 專案中，加入新介面卡專案的參考，使其參考這兩張介面卡。

    7. 在 [DslPackage\source.extension.tt] 中，加入參考新介面卡專案的行。

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **轉換所有範本** 並重建解決方案。 不應發生任何組建錯誤。

3. 在新的介面卡專案中，加入下列元件的參考：

    - VisualStudio. TextTemplating 11。0
    - VisualStudio. TextTemplating. 11。0

4. 在 AdapterManager.tt 中：

    - 變更 AdapterManagerBase 的宣告，使其繼承自 [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))。

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - 在檔案結尾附近，將 HostSpecific 屬性取代為 AdapterManager 類別之前。 移除下行：

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         插入下列程式程式碼：

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         這個屬性會篩選 modelbus 取用者搜尋介面卡時可用的介面卡集合。

5. **轉換所有範本** 並重建解決方案。 不應發生任何組建錯誤。

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>撰寫可解析 ModelBus 參考的文字模板

一般來說，您會從「來源」 DSL 讀取和產生檔案的範本開始。 此範本會使用來源 DSL 專案中所產生的指示詞，以 [從文字模板存取模型](../modeling/accessing-models-from-text-templates.md)中所述的方式來讀取來源模型檔案。 不過，來源 DSL 包含「目標」 DSL 的 ModelBus 參考。 因此，您想要啟用範本程式碼來解析參考並存取目標 DSL。 因此，您必須遵循下列步驟來調整範本：

- 將範本的基類變更為 [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))。

- 包含 `hostspecific="true"` 在範本指示詞中。

- 將元件參考新增至目標 DSL 和其介面卡，並啟用 ModelBus。

- 您不需要產生做為目標 DSL 一部分的指示詞。

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
    // (Let's assume they're all in the same model file):
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

 當這個文字模板執行時，指示詞會 `SourceDsl` 載入檔案 `Sample.source` 。 從開始，範本可以存取該模型的元素 `this.ModelRoot` 。 程式碼可以使用該 DSL 的網域類別和屬性。

 此外，範本可以解析 ModelBus 參考。 當參考指向目標模型時，元件指示詞會讓程式碼使用該模型 DSL 的網域類別和屬性。

- 如果您未使用 DSL 專案所產生的指示詞，您也應該包含下列專案。

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- 用 `this.ModelBus` 來取得 ModelBus 的存取權。

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>逐步解說：測試使用 ModelBus 的文字模板
 在這個逐步解說中，您會遵循下列步驟：

1. 建立兩個 Dsl。 一個 DSL （取用 *者*）有一個 `ModelBusReference` 屬性，可以參考另一個 dsl，也就是 *提供者*。

2. 在提供者中建立兩個 ModelBus 介面卡：一個用於文字模板存取，另一個用於一般程式碼。

3. 在單一實驗專案中建立 Dsl 的實例模型。

4. 在一個模型中設定定義域屬性，以指向另一個模型。

5. 撰寫按兩下以開啟所指向之模型的按兩下處理常式。

6. 撰寫可以載入第一個模型的文字模板，遵循另一個模型的參考，然後讀取其他模型。

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>建立可供 ModelBus 存取的 DSL

1. 建立新的 DSL 解決方案。 在此範例中，請選取 [工作流程] 方案範本。 將 [語言名稱] 設定為 `MBProvider` ，並將副檔名設定為 [提供]。

2. 在 DSL 定義圖中，以滑鼠右鍵按一下圖表的空白部分，而不靠近頂端，然後按一下 [ **啟用 Modelbus**]。

   如果您看不到 [ **啟用 Modelbus**]，請下載並安裝 VMSDK Modelbus 擴充功能。

3. 在 [ **啟用 Modelbus** ] 對話方塊中，選取 [將 **此 DSL 公開給 Modelbus**]，然後按一下 **[確定]**。

    新的專案 `ModelBusAdapter` 會加入至方案。

您現在有可透過 ModelBus 存取文字模板的 DSL。 您可以在命令、事件處理常式或規則的程式碼中解析它的參考，這些都是在模型檔案編輯器的 AppDomain 中運作。 不過，文字模板會在不同的 AppDomain 中執行，而且在編輯時無法存取模型。 如果您想要從文字模板存取此 DSL 的 ModelBus 參考，則必須有個別的 ModelBusAdapter。

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>建立為文字模板設定的 ModelBus 介面卡

1. 在檔案總管中，複製並貼上包含 *ModelBusAdapter* 的資料夾。

    將資料夾命名為 **T4ModelBusAdapter**。

    重新命名專案檔 *T4ModelBusAdapter .csproj*。

2. 在方案總管中，將 T4ModelBusAdapter 新增至 MBProvider 方案。 以滑鼠右鍵按一下方案節點，指向 [ **加入**]，然後按一下 [ **現有專案**]。

3. 以滑鼠右鍵按一下 [T4ModelBusAdapter] 專案節點，然後按一下 [屬性]。 在 [專案屬性] 視窗中，將 [ **元件名稱** ] 和 [ **預設命名空間** ] 變更為 `Company.MBProvider.T4ModelBusAdapters` 。

4. 在 T4ModelBusAdapter 的每個 * 檔中，將 "T4" 插入命名空間的最後一個部分，如此一行就會如下所示。

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. 在 `DslPackage` 專案中，加入的專案參考 `T4ModelBusAdapter` 。

6. 在 DslPackage\source.extension.tt 中，于底下加入下列程式程式碼 `<Content>` 。

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. 在 `T4ModelBusAdapter` 專案中，將參考加入至： **VisualStudio. TextTemplating** 。

8. 開啟 T4ModelBusAdapter\AdapterManager.tt：

   1. 將 AdapterManagerBase 的基類變更為 [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))。 檔案的這個部分現在類似于下列內容。

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

   2. 在檔案結尾附近，于類別 AdapterManager 前面插入下列其他屬性。

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

9. 在方案總管的標題列中，按一下 [ **轉換所有範本** ]。

10. 按 **F5**。

11. 確認 DSL 可正常運作。 在實驗專案中，開啟 `Sample.provider` 。 關閉 Visual Studio 的實驗執行個體。

    此 DSL 的 ModelBus 參考現在可以在文字模板中解析，也可以在一般程式碼中解析。

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>使用 ModelBus 參考領域屬性來建立 DSL

1. 使用最基本的語言解決方案範本來建立新的 DSL。 將語言命名為 MBConsumer，並將副檔名設定為 ". 使用"。

2. 在 DSL 專案中，新增 MBProvider DSL 元件的參考。 以滑鼠右鍵按一下  `MBConsumer\Dsl\References` ，然後按一下 [ **加入參考**]。 在 [ **流覽** ] 索引標籤中，找出 `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    這可讓您建立使用其他 DSL 的程式碼。 如果您想要建立多個 Dsl 的參考，也請新增它們。

3. 在 DSL 定義圖中，以滑鼠右鍵按一下圖表，然後按一下 [ **啟用 ModelBus**]。 在對話方塊中，選取 [ **啟用此 DSL] 以使用 ModelBus**。

4. 在類別中 `ExampleElement` ，加入新的網域屬性 `MBR` ，然後在屬性視窗中，將其類型設定為 `ModelBusReference` 。

5. 以滑鼠右鍵按一下圖表上的 [網域] 屬性，然後按一下 [ **編輯 ModelBusReference 特定屬性**]。 在對話方塊中，選取 **模型元素**。

    將 [檔案] 對話方塊篩選器設定為下列程式。

    `Provider File|*.provide`

    "&#124;" 後面的子字串是 [檔案選取專案] 對話方塊的篩選。 您可以使用 * 將它設定為允許任何檔案。\*

    在 [ **模型專案類型** ] 清單中，輸入提供者 DSL (中一個或多個網域類別的名稱，例如 MBProvider) 。 它們可以是抽象類別。 如果您將清單保留空白，使用者可以設定任何專案的參考。

6. 關閉對話方塊並 **轉換所有範本**。

   您已建立可包含另一個 DSL 中元素之參考的 DSL。

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>在方案中建立另一個檔案的 ModelBus 參考

1. 在 MBConsumer 方案中，按 CTRL + F5。 Visual Studio 的實驗實例會在 **MBConsumer\Debugging** 專案中開啟。

2. 將範例的複本加入至 **MBConsumer\Debugging** 專案。 這是必要的，因為 ModelBus 參考必須參考相同方案中的檔案。

   1. 以滑鼠右鍵按一下 [調試] 專案，指向 [ **加入**]，然後按一下 [ **現有專案**]。

   2. 在 [ **加入專案** ] 對話方塊中，將 [篩選] 設定為 [所有檔案] **(\* \*)**。

   3. 流覽至 `MBProvider\Debugging\Sample.provide` ，然後按一下 [ **新增**]。

3. 開啟 `Sample.consume`。

4. 按一下 [一個範例] 圖形，然後在 [屬性視窗中，按一下 [MBR] 屬性中的 **[...]** 。 在對話方塊中，按一下 **[流覽]** 並選取 `Sample.provide` 。 在 [專案] 視窗中，展開 [類型] 工作，然後選取其中一個元素。

5. 儲存檔案。  (尚未關閉 Visual Studio 的實驗性實例。 ) 

   您已建立一個模型，其中包含另一個模型中某個元素的 ModelBus 參考。

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>解析文字模板中的 ModelBus 參考

1. 在 Visual Studio 的實驗實例中，開啟範例文字模板檔案。 設定其內容，如下所示。

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

    - 必須設定指示詞的 `hostSpecific` 和 `inherits` 屬性 `template` 。

    - 取用者模型會透過在該 DSL 中產生的指示詞處理器，以平常的方式存取。

    - 元件和匯入指示詞必須能夠存取 ModelBus 和提供者 DSL 的類型。

    - 如果您知道有許多 Mbr 連結到相同的模型，最好只呼叫 CreateAdapter 一次。

2. 儲存範本。 確認產生的文字檔如下所示。

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>解析軌跡處理常式中的 ModelBus 參考

1. 如果正在執行，請關閉 Visual Studio 的實驗實例。

2. 新增名為 *MBConsumer\Dsl\Custom.cs* 的檔案，並將其內容設定為下列內容：

    ```csharp
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

3. 按下 **Ctrl** + **F5**。

4. 在 Visual Studio 的實驗實例中，開啟 `Debugging\Sample.consume` 。

5. 按兩下一個圖形。

    如果您已在該元素上設定 MBR，則會開啟參考的模型，並選取參考的元素。

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
