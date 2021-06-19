---
title: 建立 Windows Forms 架構的特定領域語言
description: 提供有關如何使用 Windows Forms 來顯示特定領域語言模型狀態的資訊。
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9a77a22b7ed888b28f12154974d735213952899c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389536"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>建立以 Windows Forms 為基礎的 Domain-Specific 語言

您可以使用 Windows Forms 來顯示特定領域語言 (DSL) 模型的狀態，而不是使用 DSL 圖表。 本主題將逐步引導您使用 Visual Studio 視覺效果和模型 SDK，將 Windows Form 系結至 DSL。

下圖顯示的是 DSL 實例的 Windows Form UI 和 model explorer：

![Visual Studio 中的 DSL 實例](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>建立 Windows Forms DSL

**最基本的 WinForm 設計** 工具 dsl 範本會建立最基本的 dsl，您可加以修改以符合您自己的需求。

1. 從 **最基本的 WinForm 設計** 工具範本建立 DSL。

    在這個逐步解說中，會假設下列名稱：

    - 解決方案和 DSL 名稱： `FarmApp`
    - 命名空間：`Company.FarmApp`

2. 試驗範本提供的初始範例：

   1. 轉換所有範本。

   2. 建立並執行範例 (**Ctrl** + **F5**) 。

   3. 在 Visual Studio 的實驗實例中，開啟 `Sample` 偵錯工具專案中的檔案。

        請注意，它會顯示在 Windows Forms 控制項中。

        您也可以看到在 [Explorer] 中顯示的模型元素。

        在表單或 Explorer 中加入一些元素，並注意它們出現在另一個顯示中。

   在 Visual Studio 的主要實例中，請注意下列 DSL 解決方案的相關幾點：

- `DslDefinition.dsl` 未包含任何圖表元素。 這是因為您不會使用 DSL 圖表來查看此 DSL 的實例模型。 相反地，您會將 Windows Form 系結至模型，而且表單上的元素將會顯示模型。

- 除了 `Dsl` 和 `DslPackage` 專案之外，方案還包含名為 UI 專案的第三個專案， `UI.` 其中包含 Windows Forms 控制項的定義。 `DslPackage` 相依于 `UI` 和 `UI` `Dsl` 。

- 在 `DslPackage` 專案中 `UI\DocView.cs` 包含程式碼，該程式碼會顯示專案中所定義的 Windows Forms 控制項 `UI` 。

- `UI`專案包含系結至 DSL 之表單控制項的工作範例。 但是，當您變更 DSL 定義時，它將無法運作。 `UI`專案包含：

  - 名為的 Windows Forms 類別 `ModelViewControl` 。

  - 名為 `DataBinding.cs` 的檔案，其中包含的其他部分定義 `ModelViewControl` 。 若要查看其內容，請在 **方案總管** 中開啟檔案的快捷方式功能表，然後選擇 [ **View Code**]。

### <a name="about-the-ui-project"></a>關於 UI 專案

當您更新 DSL 定義檔來定義您自己的 DSL 時，必須更新專案中的控制項， `UI` 以顯示您的 dsl。 不同于 `Dsl` 和 `DslPackage` 專案， `UI` 不會從產生範例專案 `DslDefinitionl.dsl` 。 您可以視需要新增 tt 檔來產生程式碼，雖然本逐步解說並未涵蓋此程式碼。

## <a name="update-the-dsl-definition"></a>更新 DSL 定義

下圖是本逐步解說中使用的 DSL 定義。

![DSL 定義](../modeling/media/dsl-wpf-1.png)

1. 在 DSL 設計工具中開啟 Dsldefinition.dsl 檔。

2. 刪除 **ExampleElement**

3. 將 **examplemodel.store.customer** 網域類別重新命名為 `Farm` 。

     提供其他名稱為 `Size` **Int32** 和 `IsOrganic` 類型為 **Boolean** 的網域屬性。

    > [!NOTE]
    > 如果您刪除根域類別，然後建立新的根目錄，就必須重設編輯器的根類別屬性。 在 [ **DSL Explorer**] 中，選取 [ **編輯器**]。 然後，在屬性視窗中，將 **根類別** 設定為 `Farm` 。

4. 使用 **命名網域類別** 工具來建立下列網域類別：

    - `Field` -為這個額外的網域屬性命名 `Size` 。

    - `Animal` -在屬性視窗中，將 **繼承修飾** 詞設定為 **Abstract**。

5. 使用 **網域類別** 工具來建立下列類別：

    - `Sheep`

    - `Goat`

6. 使用 **繼承** 工具進行 `Goat` 和 `Sheep` 繼承自 `Animal` 。

7. 使用內嵌 **工具來** 內嵌 `Field` 和 `Animal` 下 `Farm` 。

8. 您可能會想要整理圖表。 若要減少重複元素的數目，請使用分葉元素的快捷方式功能表上的 [將 **子樹帶入這裡** ] 命令。

9. 轉換方案總管的工具列中的 **所有範本**。

10. 建立 **Dsl** 專案。

    > [!NOTE]
    > 在這個階段中，其他專案將不會有任何錯誤而建立。 但是，我們想要建立 Dsl 專案，讓它的元件可供資料來源 Wizard 使用。

## <a name="update-the-ui-project"></a>更新 UI 專案

現在您可以建立新的使用者控制項，以顯示 DSL 模型中所儲存的資訊。 將使用者控制項連接至模型最簡單的方式是透過資料系結。 名為 **ModelingBindingSource** 的資料系結配接器類型是特別設計來將 dsl 連接到非 VMSDK 介面。

### <a name="define-your-dsl-model-as-a-data-source"></a>將 DSL 模型定義為數據源

1. 在 [ **資料** ] 功能表上，選擇 [ **顯示資料來源**]。

     [資料來源] 視窗隨即開啟。

     選擇 [ **加入新資料來源**]。 [ **資料來源設定]** 設定會開啟。

2. 選擇[物件 **]、[下一步]**。

     展開 **Dsl**、 **FarmApp**，然後選取 [ **伺服器** 陣列]，這是您模型的根類別。 選擇 [完成]。

     在方案總管中， **UI** 專案現在包含 **Properties\DataSources\Farm.datasource**

     模型類別的屬性和關聯性會出現在 [資料來源] 視窗中。

     ![資料來源視窗](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>將您的模型連接至表單

1. 在 **UI** 專案中，刪除所有現有的 .cs 檔案。

2. 將名為的新 **使用者控制項** 檔加入 `FarmControl` 至 **UI** 專案。

3. 在 [ **資料來源** ] 視窗的 [ **伺服器** 陣列] 下拉式功能表上，選擇 [ **詳細** 資料]。

    保留其他屬性的預設設定。

4. 在設計檢視中開啟 FarmControl。

    將 [ **伺服器** 陣列] 從 [資料來源] 視窗拖曳至 FarmControl。

    隨即出現一組控制項，每個屬性各有一個控制項。 關聯性屬性不會產生控制項。

5. 刪除 **farmBindingNavigator**。 這也會在設計工具中自動產生 `FarmControl` ，但不適用於此應用程式。

6. 使用 [工具箱] 建立兩個 **DataGridView** 實例，並將它們命名為 `AnimalGridView` 和 `FieldGridView` 。

   > [!NOTE]
   > 另一個步驟是將動物和 Fields 專案從 [資料來源] 視窗拖曳到控制項上。 此動作會自動建立格線視圖與資料來源之間的資料格和系結。 不過，此系結無法針對 Dsl 正常運作。 因此，最好是手動建立資料格和系結。

7. 如果 [工具箱] 未包含 **ModelingBindingSource** 工具，請新增它。 在 [ **資料** ] 索引標籤的快捷方式功能表上，選擇 [ **選擇專案**]。 在 [**選擇工具箱專案**] 對話方塊中，從 [ **.NET Framework** ] 索引標籤選取 [ **ModelingBindingSource** ]。

8. 使用 [工具箱] 建立 **ModelingBindingSource** 的兩個實例，並將它們命名為 `AnimalBinding` 和 `FieldBinding` 。

9. 將每個 **ModelingBindingSource** 的 **DataSource** 屬性設定為 **farmBindingSource**。

     將 **DataMember** 屬性設定為 **動物** 或 **欄位**。

10. 將的 **DataSource** 屬性 `AnimalGridView` `AnimalBinding` （和）設定  `FieldGridView` 為 `FieldBinding` 。

11. 調整伺服器陣列控制項的版面配置。

    **ModelingBindingSource** 是執行數個 dsl 專屬功能的介面卡：

- 它會在 VMSDK 存放區交易中包裝更新。

   例如，當使用者從資料檢視方格中刪除資料列時，一般系結會產生交易例外狀況。

- 它可確保當使用者選取資料列時，屬性視窗會顯示對應模型專案的屬性，而不是資料格資料列。

  ![DSL 系結的架構](../modeling/media/dslwpf4.png)
  
  資料來源和視圖之間的連結架構。

### <a name="complete-the-bindings-to-the-dsl"></a>完成 DSL 的系結

1. 在 **UI** 專案中的不同程式碼檔案中新增下列程式碼：

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2. 在 **DslPackage** 專案中編輯 **DslPackage\DocView.tt** ，以更新下列變數定義：

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>測試 DSL

DSL 解決方案現在可以建立並執行，不過您稍後可能會想要新增進一步的改進。

1. 建置並執行解決方案。

2. 在 Visual Studio 的實驗實例中，開啟 **範例** 檔案。

3. 在 [ **FarmApp Explorer**] 中，開啟 **伺服器** 陣列根節點的快捷方式功能表，然後選擇 [ **加入新的 Goat**]。

     `Goat1` 出現在 **動物** 視圖中。

    > [!WARNING]
    > 您必須使用 **伺服器** 陣列節點上的快捷方式功能表，而不是 **動物** 節點。

4. 選取 **伺服器** 陣列根節點，並查看其屬性。

     在表單檢視中，變更伺服器陣列的 **名稱** 或 **大小** 。

     當您離開表單中的每個欄位時，屬性視窗中的對應屬性會變更。

## <a name="enhance-the-dsl"></a>增強 DSL

### <a name="make-the-properties-update-immediately"></a>立即更新屬性

1. 在 FarmControl 的設計檢視中，選取簡單的欄位，例如 [名稱]、[大小] 或 [IsOrganic]。

2. 在屬性視窗中 **，展開 []，然後** 開啟 **(Advanced)**。

     在 [ **格式化和先進** 系結] 對話方塊的 [ **資料來源更新模式**] 下，選擇 [ **OnPropertyChanged**]。

3. 建置並執行解決方案。

     確認當您變更欄位的內容時，伺服器陣列模型的對應屬性會立即變更。

### <a name="provide-add-buttons"></a>提供新增按鈕

1. 在 FarmControl 的設計檢視中，使用 [工具箱] 在表單上建立按鈕。

    編輯按鈕的名稱和文字，例如 `New Sheep` ：。

2. 開啟按鈕 (的程式碼，例如按兩下它) 。

    進行編輯，如下所示：

   ```csharp
   private void NewSheepButton_Click(object sender, EventArgs e)
   {
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
     {
       elementOperations.MergeElementGroup(farm,
         new ElementGroup(new Sheep(farm.Partition)));
       t.Commit();
     }
   }

   // The following code is shared with other add buttons:
   private ElementOperations operationsCache = null;
   private ElementOperations elementOperations
   {
     get
     {
       if (operationsCache == null)
       {
         operationsCache = new ElementOperations(farm.Store, farm.Partition);
       }
       return operationsCache;
     }
   }
   private Farm farm
   {
     get { return this.farmBindingSource.DataSource as Farm; }
   }
   ```

    您也必須插入下列指示詞：

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. 為 Goats 和欄位新增類似的按鈕。

4. 建置並執行解決方案。

5. 確認 [新增] 按鈕會新增專案。 新的專案應該會出現在 FarmApp Explorer 和適當的資料方格視圖中。

    您應該能夠在資料方格視圖中編輯元素的名稱。 您也可以從該處刪除它。

   ![範例資料方格視圖](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>關於新增專案的程式碼

針對新的元素按鈕，下列替代程式碼稍微簡單一些。

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}
```

不過，此程式碼不會設定新專案的預設名稱。 它不會執行您可能已在 DSL 的專案 **合併** 指示詞中定義的任何自訂合併，且不會執行任何可能已定義的自訂合併程式碼。

因此，建議您使用 <xref:Microsoft.VisualStudio.Modeling.ElementOperations> 來建立新元素。 如需詳細資訊，請參閱 [自訂元素建立和移動](../modeling/customizing-element-creation-and-movement.md)。

## <a name="see-also"></a>另請參閱

- [如何定義 Domain-Specific 語言](../modeling/how-to-define-a-domain-specific-language.md)
- [撰寫程式碼以自訂 Domain-Specific 語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
