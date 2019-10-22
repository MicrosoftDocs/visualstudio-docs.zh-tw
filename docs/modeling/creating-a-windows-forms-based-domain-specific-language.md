---
title: 建立 Windows Form 架構之網域指定的語言
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc9d043f64204c50be06952ecc39be75e15087cf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654112"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>建立以 Windows Forms 為基礎的網域特定語言

您可以使用 Windows Forms 來顯示特定領域語言（DSL）模型的狀態，而不是使用 DSL 圖表。 本主題將逐步引導您使用 Visual Studio 的視覺效果和模型化 SDK，將 Windows Form 系結至 DSL。

下圖顯示適用于 DSL 實例的 Windows Form UI 和模型瀏覽器：

![Visual Studio 中的 DSL 實例](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>建立 Windows Forms DSL

**最小的 WinForm 設計**工具 dsl 範本會建立最小的 dsl，讓您可以修改以符合您自己的需求。

1. 從**最小的 WinForm 設計**工具範本建立 DSL。

    在此逐步解說中，假設採用下列名稱：

   | | |
   |-|-|
   | 解決方案和 DSL 名稱 | FarmApp |
   | 命名空間 | FarmApp |

2. 試驗範本提供的初始範例：

   1. 轉換所有範本。

   2. 建立並執行範例（**Ctrl** +**F5**）。

   3. 在 Visual Studio 的實驗實例中，開啟調試專案中的 `Sample` 檔案。

        請注意，它會顯示在 Windows Forms 控制項中。

        您也可以查看在 Explorer 中顯示之模型的元素。

        在表單或瀏覽器中新增一些專案，並注意它們會出現在另一個顯示中。

   在 Visual Studio 的主要實例中，請注意下列關於 DSL 解決方案的要點：

- `DslDefinition.dsl` 不包含任何圖表元素。 這是因為您不會使用 DSL 圖表來查看此 DSL 的實例模型。 相反地，您會將 Windows Form 系結至模型，而表單上的元素會顯示模型。

- 除了 `Dsl` 和 `DslPackage` 專案以外，方案包含第三個名為 `UI.`**UI**專案的專案，其中包含 Windows Forms 控制項的定義。 `DslPackage` 取決於 `UI`，`UI` 取決於 `Dsl`。

- 在 `DslPackage` 專案中，`UI\DocView.cs` 包含的程式碼會顯示 `UI` 專案中定義的 Windows Forms 控制項。

- @No__t_0 專案包含系結至 DSL 之表單控制項的工作範例。 不過，當您變更 DSL 定義時，它不會有作用。 @No__t_0 專案包含：

  - 名為 `ModelViewControl` 的 Windows Forms 類別。

  - 名為 `DataBinding.cs` 的檔案，其中包含 `ModelViewControl` 的其他部分定義。 若要查看其內容，請在**方案總管**中，開啟檔案的快捷方式功能表，然後選擇 [ **View Code**]。

### <a name="about-the-ui-project"></a>關於 UI 專案

當您更新 DSL 定義檔以定義您自己的 DSL 時，您必須更新 `UI` 專案中的控制項，以顯示您的 DSL。 不同于 `Dsl` 和 `DslPackage` 專案，不會從 `DslDefinitionl.dsl` 產生範例 `UI` 專案。 如有需要，您可以新增 tt 檔案來產生程式碼，雖然本逐步解說並未涵蓋這項功能。

## <a name="update-the-dsl-definition"></a>更新 DSL 定義

在本逐步解說中，會使用下列 DSL 定義。

![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png)

1. 在 DSL 設計工具中開啟 Dsldefinition.dsl 檔。

2. 刪除**ExampleElement**

3. 將**examplemodel.store.customer**網域類別重新命名為 `Farm`。

     提供名為 `Size` 類型為**Int32**的其他網域屬性，以及**布林**類型的 `IsOrganic`。

    > [!NOTE]
    > 如果您刪除根域類別，然後建立新的根，就必須重設編輯器的根類別屬性。 在 [ **DSL Explorer**] 中，選取 [**編輯器**]。 然後在屬性視窗中，將 [**根類別**] 設定為 [`Farm`]。

4. 使用**命名網域類別**工具來建立下列網域類別：

    - `Field`-提供另一個名為 `Size` 的網域屬性。

    - `Animal`-在屬性視窗中，將**繼承修飾**詞設定為**Abstract**。

5. 使用**網域類別**工具來建立下列類別：

    - `Sheep`

    - `Goat`

6. 使用 [**繼承**] 工具可進行 `Goat`，`Sheep` 繼承自 `Animal`。

7. 使用內嵌**工具，在 `Farm`** 底下嵌入 `Field` 和 `Animal`。

8. 您可能想要整理圖表。 若要減少重複元素的數目，請使用分葉元素的快捷方式功能表上的 [將**子樹帶入此處**] 命令。

9. 轉換方案總管工具列中的**所有範本**。

10. 建立**Dsl**專案。

    > [!NOTE]
    > 在這個階段，其他專案將不會建立任何錯誤。 不過，我們想要建立 Dsl 專案，讓資料來源 Wizard 能夠使用其元件。

## <a name="update-the-ui-project"></a>更新 UI 專案

現在您可以建立新的使用者控制項，它會顯示儲存在 DSL 模型中的資訊。 將使用者控制項連接到模型的最簡單方式是透過資料系結。 名為**ModelingBindingSource**的資料系結介面卡類型特別設計用來連接 dsl 與非 VMSDK 介面。

### <a name="define-your-dsl-model-as-a-data-source"></a>將 DSL 模型定義為數據源

1. 在 [**資料**] 功能表上，選擇 [**顯示資料來源**]。

     [資料來源] 視窗隨即開啟。

     選擇 [**加入新的資料來源**]。 [資料來源組態精靈] 隨即開啟。

2. 選擇[物件 **]，[下一步]** 。

     展開 [ **Dsl**]、[ **FarmApp**] 和 [選取**伺服器**陣列]，這是您模型的根類別。 選擇 [完成]。

     在方案總管中， **UI**專案現在包含**Properties\DataSources\Farm.datasource**

     模型類別的屬性和關聯性會出現在 [資料來源] 視窗中。

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>將您的模型連接至表單

1. 在**UI**專案中，刪除所有現有的 .cs 檔案。

2. 將名為 `FarmControl` 的新**使用者控制項**檔案加入至**UI**專案。

3. 在 [**資料來源**] 視窗的 [**伺服器**陣列] 下拉式功能表上，選擇 [**詳細資料**]。

    保留其他屬性的預設設定。

4. 在設計檢視中開啟 FarmControl.cs。

    將 [**伺服器**陣列] 從 [資料來源] 視窗拖曳至 [FarmControl]。

    此時會出現一組控制項，每個屬性各有一個。 關聯性屬性不會產生控制項。

5. 刪除**farmBindingNavigator**。 這也會在 `FarmControl` 設計工具中自動產生，但對此應用程式而言並不實用。

6. 使用 [工具箱] 建立兩個**DataGridView**實例，並將它們命名為 `AnimalGridView` 和 `FieldGridView`。

   > [!NOTE]
   > 另一個步驟是將 [動物] 和 [欄位] 專案從 [資料來源] 視窗拖曳到控制項上。 此動作會自動建立方格視圖和資料來源之間的資料格和系結。 不過，此系結在 Dsl 中無法正常運作。 因此，最好是手動建立資料格和系結。

7. 如果 [工具箱] 不包含**ModelingBindingSource**工具，請將它加入。 在 [**資料**] 索引標籤的快捷方式功能表上，選擇 **[選擇專案**]。 在 [**選擇工具箱專案**] 對話方塊中，從 [ **.NET Framework** ] 索引標籤中選取 [ **ModelingBindingSource** ]。

8. 使用 [工具箱] 建立兩個**ModelingBindingSource**實例，並將它們命名為 `AnimalBinding` 和 `FieldBinding`。

9. 將每個**ModelingBindingSource**的**DataSource**屬性設定為**farmBindingSource**。

     將 [ **DataMember** ] 屬性設定為 [**動物**] 或 [**欄位**]。

10. 將 `AnimalGridView` 的**資料來源**屬性設定為 `AnimalBinding`，`FieldGridView` 為 `FieldBinding`。

11. 調整伺服器陣列控制項的配置，以配合您的感受。

    **ModelingBindingSource**是一種介面卡，可執行 dsl 特有的數個功能：

- 它會包裝 VMSDK 存放區交易中的更新。

   例如，當使用者從資料檢視方格中刪除資料列時，一般系結會導致交易例外狀況。

- 它可確保當使用者選取資料列時，屬性視窗會顯示對應之模型專案的屬性，而不是資料格資料列。

  ![DslWpf4 資料來源和 views 之間連結的 ](../modeling/media/dslwpf4.png) 架構。

### <a name="complete-the-bindings-to-the-dsl"></a>完成 DSL 的系結

1. 在**UI**專案的不同程式碼檔案中新增下列程式碼：

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

2. 在**DslPackage**專案中，編輯**DslPackage\DocView.tt**以更新下列變數定義：

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>測試 DSL

DSL 解決方案現在可以建立和執行，但您可能會想要稍後再新增進一步的改良功能。

1. 建置並執行方案。

2. 在 Visual Studio 的實驗實例中，開啟**範例**檔案。

3. 在**FarmApp Explorer**中，開啟**伺服器**陣列根節點上的快捷方式功能表，然後選擇 [**加入新 Goat**]。

     `Goat1` 會出現在 [**動物**] 視圖中。

    > [!WARNING]
    > 您必須使用 [**伺服器**陣列] 節點上的快捷方式功能表，而不是 [**動物**] 節點。

4. 選取 [**伺服器**陣列] 根節點，並查看其屬性。

     在表單檢視中，變更伺服器陣列的**名稱**或**大小**。

     當您從表單中的每個欄位離開時，對應的屬性會在屬性視窗中變更。

## <a name="enhance-the-dsl"></a>增強 DSL

### <a name="make-the-properties-update-immediately"></a>立即更新屬性

1. 在 FarmControl.cs 的設計檢視中，選取簡單欄位，例如 [名稱]、[大小] 或 [IsOrganic]。

2. 在屬性視窗中 **，展開 [** 系結] 並開啟 **[（Advanced）** ]。

     在 [**格式化和高級**系結] 對話方塊的 [**資料來源更新模式**] 下，選擇 [ **OnPropertyChanged**]。

3. 建置並執行方案。

     確認當您變更欄位的內容時，伺服器陣列模型的對應屬性會立即變更。

### <a name="provide-add-buttons"></a>提供 [新增] 按鈕

1. 在 FarmControl.cs 的設計檢視中，使用 [工具箱] 在表單上建立按鈕。

    編輯按鈕的名稱和文字，例如，`New Sheep`。

2. 開啟按鈕後方的程式碼（例如，按兩下它）。

    編輯它，如下所示：

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

4. 建置並執行方案。

5. 確認 [新增] 按鈕會加入專案。 新專案應該會出現在 FarmApp Explorer 和適當的資料方格視圖中。

    您應該能夠在資料方格視圖中編輯元素的名稱。 您也可以從該處刪除它。

   ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>關於要加入元素的程式碼

針對新的元素按鈕，下列替代程式碼稍微簡單一點。

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

不過，此程式碼不會設定新專案的預設名稱。 它不會執行您可能已在 DSL 的專案**合併**指示詞中定義的任何自訂合併，而且也不會執行任何可能已定義的自訂合併程式碼。

因此，建議您使用 <xref:Microsoft.VisualStudio.Modeling.ElementOperations> 來建立新的元素。 如需詳細資訊，請參閱[自訂元素的建立和移動](../modeling/customizing-element-creation-and-movement.md)。

## <a name="see-also"></a>請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
