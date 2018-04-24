---
title: 建立 Windows Form 架構之網域指定的語言
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2e031a87093a765c7ca79f929b6fe5666c322aad
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>建立 Windows Form 架構之網域指定的語言
您可以使用 Windows Form 顯示的特定領域語言 (DSL) 模型，而不是使用 DSL 圖表狀態。 本主題會引導您繫結至 DSL 的 Windows Form 中，使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Visualization and Modeling SDK。

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2") DSL 執行個體，顯示 Windows 表單 UI 和 [模型總管] 中。

## <a name="creating-a-windows-forms-dsl"></a>建立 Windows Form DSL
 **最少的 WinForm 設計師**DSL 範本所建立的最小的 DSL，您可以修改以符合您自己的需求。

#### <a name="to-create-a-minimal-winforms-dsl"></a>若要建立最小的 WinForms DSL

1.  建立從 DSL**最少的 WinForm 設計師**範本。

     在本逐步解說中，會假設下列名稱：

    |||
    |-|-|
    |方案和 DSL 的名稱|FarmApp|
    |命名空間|Company.FarmApp|

2.  初始範本所提供的範例實驗：

    1.  轉換所有範本。

    2.  建置及執行範例 (**CTRL + F5**)。

    3.  在 Visual Studio 的實驗執行個體，開啟`Sample`偵錯的專案中的檔案。

         請注意，它會顯示 Windows Form 控制項中。

         您也可以查看顯示在 [總管] 中的模型項目。

         加入一些項目，在表單或 [總管] 中的，請注意，它們會出現在其他顯示器。

 主要執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，請注意下列有關 DSL 方案的重點：

-   `DslDefinition.dsl` 不包含任何圖表項目。 這是因為您不會使用 DSL 圖表來檢視此 DSL 的執行個體模型。 相反地，您會將 Windows Form 繫結至模型，並在表單上的項目會顯示模型。

-   除了`Dsl`和`DslPackage`專案的方案包含名為的第三個專案`UI.` **UI**專案包含 Windows Form 控制項的定義。 `DslPackage` 取決於`UI`，和`UI`取決於`Dsl`。

-   在`DslPackage`專案，`UI\DocView.cs`包含顯示 Windows Form 控制項中所定義的程式碼`UI`專案。

-   `UI`專案包含表單控制項繫結至 DSL 的工作範例。 不過，它將無法運作 DSL 定義變更之後。 `UI`專案包含：

    -   Windows Form 類別的`ModelViewControl`。

    -   名為`DataBinding.cs`，其中包含的其他部分定義`ModelViewControl`。 若要查看其內容，在**方案總管 中**，開啟檔案的捷徑功能表並選擇**檢視程式碼**。

### <a name="about-the-ui-project"></a>關於 UI 專案
 當您更新 DSL 定義檔案，以定義您自己的 DSL 時，您必須更新中的控制項`UI`專案，以顯示 DSL。 不同於`Dsl`和`DslPackage`專案、 範例`UI`專案不從產生`DslDefinitionl.dsl`。 您可以將產生的程式碼，如果您想，雖然所未涵蓋在本逐步解說.tt 檔案。

## <a name="updating-the-dsl-definition"></a>DSL 定義的更新
 DSL 定義用於這個逐步解說下列。

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")

#### <a name="to-update-the-dsl-definition"></a>若要更新 DSL 定義

1.  DSL 設計工具中開啟 DslDefinition.dsl。

2.  刪除**ExampleElement**

3.  重新命名**ExampleModel**網域類別`Farm`。

     提供額外的網域屬性，名為`Size`型別的**Int32**，和`IsOrganic`型別的**布林**。

    > [!NOTE]
    >  如果您刪除根網域類別，然後再建立新的根目錄，您必須重設編輯器根類別屬性。 在**DSL 總管**，選取**編輯器**。 然後在 [屬性] 視窗中，將**根類別**至`Farm`。

4.  使用**名為網域類別**工具來建立下列網域類別：

    -   `Field` -為提供此其他網域屬性名為`Size`。

    -   `Animal` -在 [屬性] 視窗中，設定**繼承修飾詞**至**抽象**。

5.  使用**網域類別**工具來建立下列類別：

    -   `Sheep`

    -   `Goat`

6.  使用**繼承**工具進行`Goat`和`Sheep`繼承自`Animal`。

7.  使用**內嵌**內嵌工具`Field`和`Animal`下`Farm`。

8.  您可能想要清理的圖表。 若要減少重複的項目數目，使用**這裡顯示的樹狀子目錄**分葉項目的捷徑功能表上的命令。

9. **轉換所有範本** 的 方案總管 工具列中。

10. 建置**Dsl**專案。

    > [!NOTE]
    >  在這個階段，不會無誤建置其他專案。 不過，我們想要建置 Dsl 專案，讓它的組件可用於資料來源精靈。

## <a name="updating-the-ui-project"></a>更新 UI 專案
 現在您可以建立新的使用者控制項將會顯示儲存 DSL 模型中的資訊。 連接至模型的使用者控制項的最簡單方式是透過資料繫結。 資料繫結介面卡類型名為**ModelingBindingSource**專為 Dsl 連接至非 VMSDK 介面。

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>若要定義 DSL 模型做為資料來源

1.  在**資料**功能表上，選擇**顯示資料來源**。

     **資料來源**視窗隨即開啟。

     選擇**加入新資料來源**。 **資料來源組態精靈**隨即開啟。

2.  選擇**物件**，**下一步**。

     展開**Dsl**， **Company.FarmApp**，然後選取**伺服陣列**，這是您的模型的根類別。 選擇 [完成]。

     在 方案總管**UI**專案現在會包含**Properties\DataSources\Farm.datasource**

     屬性和關聯性的模型類別會出現在 [資料來源] 視窗。

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")

#### <a name="to-connect-your-model-to-a-form"></a>您的模型連接至表單

1.  在**UI**專案中，刪除所有現有的.cs 檔案。

2.  加入新**使用者控制項**檔名為`FarmControl`至**UI**專案。

3.  在**資料來源**視窗中，功能表中的下拉式清單上**伺服陣列**，選擇**詳細資料**。

     保留預設設定其他屬性。

4.  在 [設計] 檢視中開啟 FarmControl.cs。

     拖曳**伺服陣列**從資料來源視窗拖曳至 FarmControl。

     一組控制項隨即出現，其中每一個屬性。 關聯性屬性不會產生控制項。

5.  刪除**farmBindingNavigator**。 這也會自動產生`FarmControl`設計工具中，但它並不適合此應用程式。

6.  使用 [工具箱] 中，建立兩個執行個體**DataGridView**，並將它們命名`AnimalGridView`和`FieldGridView`。

    > [!NOTE]
    >  替代的步驟是動物和欄位的項目從資料來源視窗拖曳至控制項。 這個動作會自動建立資料格和格線檢視與資料來源之間的繫結。 不過，此繫結無法正常運作的 Dsl。 因此最好是在建立資料格和繫結以手動方式。

7.  如果 [工具箱] 未包含**ModelingBindingSource**工具，請將它加入。 在捷徑功能表上**資料**索引標籤上，選擇**選擇項目**。 在**選擇工具箱項目**對話方塊中，選取**ModelingBindingSource**從 **.NET Framework 索引標籤**。

8.  使用 [工具箱] 中，建立兩個執行個體**ModelingBindingSource**，並將它們命名`AnimalBinding`和`FieldBinding`。

9. 設定**DataSource**每個屬性**ModelingBindingSource**至**farmBindingSource**。

     設定**DataMember**屬性**動物**或**欄位**。

10. 設定**DataSource**屬性`AnimalGridView`至`AnimalBinding`，和`FieldGridView`至`FieldBinding`。

11. 調整您的喜好的伺服陣列控制項的版面配置。

 **ModelingBindingSource**是配接器，用於執行特定的 Dsl 幾個函式：

-   它所包裝 VMSDK 存放區交易中更新。

     例如，當使用者刪除一個資料列的資料檢視方格中，規則的繫結將會導致交易例外狀況。

-   它可確保，當使用者選取一個資料列時，[屬性] 視窗會顯示對應的模型項目，而不是資料方格資料列的屬性。

 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")結構描述資料來源和檢視之間的連結。

#### <a name="to-complete-the-bindings-to-the-dsl"></a>若要完成程式的繫結 DSL

1.  在不同的程式碼檔案中加入下列程式碼**UI**專案：

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

2.  在**DslPackage**專案中，編輯**DslPackage\DocView.tt**更新變數的定義如下：

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>測試 DSL
 DSL 方案現在可以建置並執行，但是您可能想要新增其他增強功能更新版本。

#### <a name="to-test-the-dsl"></a>若要測試 DSL

1.  建置並執行方案。

2.  在 Visual Studio 的實驗執行個體，開啟**範例**檔案。

3.  在**FarmApp 總管**，開啟捷徑功能表上**伺服陣列**根節點，然後選擇 **新增新 Goat**。

     `Goat1` 會出現在**動物**檢視。

    > [!WARNING]
    >  您必須使用捷徑功能表上**伺服陣列** 節點，不**動物**節點。

4.  選取**伺服陣列**根節點並檢視其屬性。

     在 [表單] 檢視中，變更**名稱**或**大小**伺服器陣列。

     當您離開在表單中，對應的屬性變更，在 [屬性] 視窗中的每個欄位。

## <a name="enhancing-the-dsl"></a>加強 DSL

#### <a name="to-make-the-properties-update-immediately"></a>若要進行立即更新的屬性

1.  在 FarmControl.cs [設計] 檢視中，選取簡單的欄位，例如名稱、 大小或 IsOrganic。

2.  在 [屬性] 視窗中，依序展開**DataBindings**並開啟**（進階）**。

     在**格式化與進階繫結**對話方塊下方**資料來源更新模式**，選擇**OnPropertyChanged**。

3.  建置並執行方案。

     請確認當您變更欄位，伺服器陣列的模型變更立即的對應屬性的內容。

#### <a name="to-provide-add-buttons"></a>提供加入按鈕

1.  在 FarmControl.cs [設計] 檢視中，使用 [工具箱] 表單上建立按鈕。

     編輯名稱和按鈕的文字，例如以`New Sheep`。

2.  [] 按鈕後的程式碼 （例如按兩下以開啟它）。

     編輯，如下所示：

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

3.  將類似的按鈕加入山羊和欄位。

4.  建置並執行方案。

5.  請確認 [新增] 按鈕將項目。 在這兩個 FarmApp 總管和適當的資料格檢視中，應該會出現新的項目。

     您應該能夠編輯的資料格檢視中的項目名稱。 您也可以從那裡刪除它。

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")

### <a name="about-the-code-to-add-an-element"></a>關於程式碼中新增項目
 新的項目按鈕，如下列替代程式碼則稍微簡單一些。

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

 不過，這段程式碼不會設定新項目的預設名稱。 不會執行任何可能在中定義的自訂的合併**項目合併指示詞**的 DSL，而且它不會執行任何自訂合併程式碼可能已經定義的。

 因此我們建議您改用<xref:Microsoft.VisualStudio.Modeling.ElementOperations>建立新的項目。 如需詳細資訊，請參閱[自訂項目建立及移動](../modeling/customizing-element-creation-and-movement.md)。

## <a name="see-also"></a>另請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)