---
title: 自訂屬性視窗
description: 瞭解如何在 Visual Studio 中自訂特定領域語言 (DSL) 的 [屬性] 視窗的外觀和行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f7d4ac76b8b10fde0c193e3eda73cec611c1441
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362870"
---
# <a name="customize-the-properties-window"></a>自訂屬性視窗

您可以在 Visual Studio 中，自訂特定領域語言中的 [屬性] 視窗的外觀和行為 (DSL) 。 在 DSL 定義中，您可以定義每個網域類別的網域屬性。 依預設，當您在圖表上或在 [模型瀏覽器] 中選取類別的實例時，每個定義域屬性都會列在 [屬性] 視窗中。 這可讓您查看和編輯定義域屬性的值，即使您未將它們對應至圖表上的圖形欄位也一樣。

## <a name="names-descriptions-and-categories"></a>名稱、描述和類別

**名稱和顯示名稱**。 在定義域屬性的定義中，屬性的顯示名稱是在執行時間于 [屬性] 視窗中顯示的名稱。 相較之下，當您撰寫程式碼來更新屬性時，會使用此名稱。 名稱必須是正確的 CLR 英數位元名稱，但顯示名稱可以包含空格。

當您在 DSL 定義中設定屬性的名稱時，其顯示名稱會自動設定為名稱的複本。 如果您撰寫像是 "FuelGauge" 的 Pascal 大小寫名稱，則顯示名稱會自動包含空格：「燃料量測計」。 不過，您可以明確地將顯示名稱設定為另一個值。

**描述**。 定義域屬性的描述會出現在兩個位置：

- 當使用者選取屬性時，在 [屬性] 視窗的底部。 您可以使用它向使用者說明屬性代表的內容。

- 在產生的程式碼中。 如果您使用檔功能來解壓縮 API 檔，它會顯示為 API 中這個屬性的描述。

**類別**。 類別是屬性視窗中的標題。

## <a name="expose-style-features"></a>公開樣式功能

圖形元素的部分動態功能可以表示或 *公開* 為定義域屬性。 以這種方式公開的功能，可由使用者更新，並可讓程式碼更容易更新。

以滑鼠右鍵按一下 DSL 定義中的圖形類別，指向 [ **加入**]，然後選擇功能。

在圖形上，您可以公開 **FillColor**、 **OutlineColor**、 **TextColor**、 **OutlineDashStyle**、 **OutlineThickness** 和 **FillGradientMode** 屬性。 在連接器上，您可以公開 **色彩** `,` **TextColor**、 **DashStyle** 和 **粗細** 屬性。 在圖表中，您可以公開 **FillColor** 和 **TextColor** 屬性。

## <a name="forwarding-display-properties-of-related-elements"></a>轉送：顯示相關元素的屬性

當 DSL 的使用者選取模型中的元素時，該專案的屬性會顯示在 [屬性] 視窗中。 不過，您也可以顯示指定之相關專案的屬性。 如果您已定義一組可一起運作的元素，這就很有用。 例如，您可以定義主要專案和選擇性的外掛程式元素。 如果主要元素對應至圖形，另一個則不是，則查看其所有屬性，就像是在一個元素上一樣。

這項效果是命名 *屬性轉送*，在幾種情況下會自動發生。 在其他情況下，您可以藉由定義網欄位型別描述元來達到屬性轉送。

### <a name="default-property-forwarding-cases"></a>預設屬性轉送案例

當使用者選取圖形或連接器，或在 [Explorer] 中選取專案時，屬性視窗中會顯示下列屬性：

- 在模型專案的網域類別上定義的網域屬性，包括在基類中定義的屬性。 例外狀況是您已設定 **為可流覽** 的網域屬性 `False` 。

- 透過具有多重性 0 ..1 的關聯性連結的元素名稱。 這提供了一個方便的方法來查看選擇性連結的元素，即使您尚未為關聯性定義連接器對應也是一樣。

- 以元素為目標之內嵌關聯性的網域屬性。 因為內嵌關聯性通常不會明確顯示，所以這可讓使用者查看其屬性。

- 在選取的圖形或連接器上定義的定義域屬性。

### <a name="add-property-forwarding"></a>新增屬性轉送

若要轉送屬性，您必須定義網欄位型別描述元。 如果您在兩個網域類別之間有網域關聯性，您可以使用網欄位型別描述元，將第一個類別中的網域屬性設定為第二個網域類別中的網域屬性值。 例如，如果您在 **書籍** 網域類別和 **作者** 網域類別之間有關聯性，則可以使用定義欄位型別描述項，讓書籍 **作者** 的 **名稱** 屬性在使用者選取書籍時出現在屬性視窗中。

> [!NOTE]
> 屬性轉送只會影響使用者編輯模型時的屬性視窗。 它不會在接收的類別上定義網域屬性。 如果您想要在 DSL 定義的其他部分或在程式碼中存取轉送的網域屬性，您必須存取轉送元素。

下列程式假設您已建立 DSL。 前幾個步驟匯總了必要條件。

#### <a name="forward-a-property-from-another-element"></a>從另一個元素轉寄屬性

1. 建立 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 包含至少兩個類別的方案，在此範例中稱為 **Book** 和 **Author**。 **書籍** 與 **作者** 之間應該有兩種類型的關聯性。

    「來源」角色的多重性 (**書** 中的角色) 應為 0 ..1 或 1 ..1，如此一來，每 **本書** 都有一 **位作者**。

2. 在 [ **DSL Explorer**] 中，以滑鼠右鍵按一下 [ **Book** 網域] 類別，然後按一下 [ **加入新的 {0} domaintypedescriptor**]。

    自 **定義類型描述** 項節點下會出現名為 [**自訂屬性描述項的路徑**] 的節點。

3. 以滑鼠右鍵按一下 [ **自訂類型描述** 項] 節點，然後按一下 [ **加入新的 PropertyPath**]。

    新的屬性路徑會出現在 [ **自訂屬性描述項** ] 節點的 [路徑] 下。

4. 選取新的屬性路徑，並在 [ **屬性** ] 視窗中，將 [ **路徑** ] 設定為適當模型元素的路徑。

    您可以按一下此屬性右邊的向下箭號，以編輯樹狀檢視中的路徑。 如需網域路徑的詳細資訊，請參閱 [網域路徑語法](../modeling/domain-path-syntax.md)。 當您編輯它時，路徑應該類似 **BookReferencesAuthor。 Author/！作者**。

5. 將 **屬性** 設為 **Author** 的 **Name** 網域屬性。

6. 將 [ **顯示名稱** ] 設定為 [ **作者名稱**]。

7. 轉換所有範本、建立並執行 DSL。

8. 在模型圖中，建立書籍、作者，並使用參考關聯性連結。 選取 [book] 元素，然後在 [屬性視窗除了書籍的屬性之外，您還應該看到作者名稱。 變更連結的作者名稱，或將書籍連結至不同的作者，然後觀察本書的作者名稱會變更。

## <a name="custom-property-editors"></a>自訂屬性編輯器

[屬性] 視窗會針對每個定義域屬性的類型提供適當的預設編輯體驗。 例如，針對列舉型別，使用者會看到一個下拉式清單，而針對數值屬性，使用者可以輸入數位。 這僅適用于內建類型。 如果您指定外部類型，使用者將能夠看到屬性的值，但無法編輯它。

不過，您可以指定下列編輯器和類型：

1. 使用於標準類型的另一個編輯器。 例如，您可以指定字串屬性的檔案路徑編輯器。

2. 網域屬性的外部類型和其編輯器。

3. .NET 編輯器（例如檔案路徑編輯器）或您可以建立自己的自訂屬性編輯器。

   外部類型與具有預設編輯器的類型（例如字串）之間的轉換。

   在 DSL 中， *外部類型* 是指不是其中一種簡單類型 (例如布林值或 Int32) 或字串的任何類型。

### <a name="define-a-domain-property-that-has-an-external-type"></a>定義具有外部類型的網域屬性

1. 在 **方案總管** 中，將參考加入至 **Dsl** 專案中包含外部類型的元件 (DLL) 。

    元件可以是 .NET 元件，也可以是您所提供的元件。

2. 除非您已經這麼做，否則請將類型新增至 [ **網欄位型別** ] 清單。

   1. 開啟 Dsldefinition.dsl 檔，然後在 [ **Dsl Explorer**] 中，以滑鼠右鍵按一下根節點，然後按一下 [ **加入新的外部類型**]。

        新的專案會出現在 [ **網欄位型別** ] 節點底下。

       > [!WARNING]
       > 功能表項目位於 DSL 根節點，而非 [ **網欄位型別** ] 節點上。

   2. 在屬性視窗中設定新型別的名稱和命名空間。

3. 以一般方式將網域屬性加入至網域類別。

    在 [屬性視窗中，從 [ **類型** ] 欄位的下拉式清單中選取 [外部類型]。

   在這個階段，使用者可以查看屬性的值，但無法加以編輯。 顯示的值是從函數取得 `ToString()` 。 您可以撰寫程式碼來設定屬性的值，例如在命令或規則中。

### <a name="set-a-property-editor"></a>設定屬性編輯器

將 CLR 屬性加入至網域屬性，其格式如下：

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

您可以使用屬性視窗中的 **自訂屬性** 專案，在屬性上設定屬性。

的型別 `AnEditor` 必須衍生自第二個參數中指定的型別。 第二個參數應該是 <xref:System.Drawing.Design.UITypeEditor> 或 <xref:System.ComponentModel.ComponentEditor> 。 如需詳細資訊，請參閱<xref:System.ComponentModel.EditorAttribute>。

您可以指定自己的編輯器或 .NET 編輯器，例如 <xref:System.Windows.Forms.Design.FileNameEditor> 或 <xref:System.Drawing.Design.ImageEditor> 。 例如，您可以使用下列程式取得屬性，讓使用者可以在其中輸入檔案名。

#### <a name="define-a-file-name-domain-property"></a>定義檔案名網域屬性

1. 將網域屬性加入至 DSL 定義中的網域類別。

2. 選取新的屬性。 在 [屬性視窗的 [ **自訂屬性** ] 欄位中，輸入下列屬性。 若要輸入此屬性，請按一下省略號 **[...]** ，然後分別輸入屬性名稱和參數：

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. 將 [網域] 屬性的類型保留為 [ **字串**] 的預設設定。

4. 若要測試編輯器，請確認使用者可以開啟 [檔案名編輯器] 以編輯您的網域屬性。

    1. 按 CTRL + F5 或 F5。 在調試方案中，開啟測試檔案。 建立網域類別的元素，然後選取它。

    2. 在 [屬性視窗中，選取 [網域] 屬性。 [值] 欄位會顯示省略號 **[...]**。

    3. 按一下省略號。 [檔案] 對話方塊隨即出現。 選取檔案，然後關閉對話方塊。 檔案路徑現在是 [網域] 屬性的值。

### <a name="define-your-own-property-editor"></a>定義您自己的屬性編輯器

您可以定義自己的編輯器。 您可以這樣做，讓使用者可以編輯您所定義的型別，或以特殊方式編輯標準型別。 例如，您可以允許使用者輸入代表公式的字串。

您可以藉由撰寫衍生自的類別來定義編輯器 <xref:System.Drawing.Design.UITypeEditor> 。 您的類別必須覆寫：

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>：與使用者互動，並更新屬性值。

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>，指定您的編輯器將開啟對話方塊或提供下拉式功能表。

您也可以提供將在屬性方格中顯示之屬性值的圖形表示。 若要這樣做，請覆寫 `GetPaintValueSupported` 、和 `PaintValue` 。  如需詳細資訊，請參閱<xref:System.Drawing.Design.UITypeEditor>。

> [!NOTE]
> 將程式碼新增至 **Dsl** 專案中的不同程式碼檔案。

例如：

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

若要使用這個編輯器，請將網域屬性的 **自訂屬性** 設定為：

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

如需詳細資訊，請參閱<xref:System.Drawing.Design.UITypeEditor>。

## <a name="provide-a-drop-down-list-of-values"></a>提供值的下拉式清單

您可以提供值清單供使用者選擇。

> [!NOTE]
> 這項技術提供可在執行時間變更的值清單。 如果您想要提供不會變更的清單，請考慮改為使用列舉型別作為網域屬性的型別。

若要定義標準值的清單，請將具有下列格式的 CLR 屬性加入至網域屬性：

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

定義衍生自 <xref:System.ComponentModel.TypeConverter> 的類別。 將程式碼新增至 **Dsl** 專案中的個別檔案。 例如：

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
