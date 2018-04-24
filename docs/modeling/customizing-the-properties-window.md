---
title: 自訂屬性視窗
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 50753da026f091d541bffd664f0aa964b4cba3f0
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-the-properties-window"></a>自訂屬性視窗
您可以在您的特定領域語言 (DSL) 自訂的外觀和行為的 [屬性] 視窗，在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在 DSL 定義中，您網域屬性類別上定義每個網域。 根據預設，當您選取類別，在圖表或模型總管 中的執行個體的每個網域屬性列在 屬性 視窗中。 這可讓您查看和編輯網域屬性值，即使您尚未對應這些圖形在圖表上的欄位。

## <a name="names-descriptions-and-categories"></a>名稱、 描述和類別
 **名稱和顯示名稱**。 在定義中的網域屬性，屬性的顯示名稱會是顯示在 [屬性] 視窗中的執行階段的名稱。 相反地，當您撰寫程式碼來更新屬性時，會使用的名稱。 名稱必須是正確的 CLR 英數字元名稱，但是顯示名稱可以包含空格。

 DSL 定義中設定屬性的名稱，其顯示名稱會自動設定複本的名稱。 如果您撰寫一個 Pascal cased 的名稱，例如"FuelGauge 」 時，顯示名稱會自動包含空格:"油量"。 不過，您可以與另一個值明確設定顯示名稱。

 **描述**。 網域屬性的描述會出現在兩個地方：

-   當使用者選取的屬性中的 [屬性] 視窗底端。 您可以使用它來向使用者解釋屬性所代表的意義。

-   在產生的程式碼中。 如果您使用的文件功能來擷取應用程式開發介面文件時，它會做為應用程式開發介面中的此屬性的描述。

 **分類**. 類別是在 [屬性] 視窗的標題。

## <a name="exposing-style-features"></a>公開樣式功能
 某些圖形元素的動態功能可以表示或*公開*做為網域屬性。 使用者可以更新已在這種方式公開的功能，可以更輕鬆地更新程式碼。

 DSL 定義中的圖形類別上按一下滑鼠右鍵，指向**新增公開**，然後選擇一項功能。

 您可以在圖形上公開**FillColor**， **OutlineColor**， **TextColor**， **OutlineDashStyle**， **OutlineThickness**和**FillGradientMode**屬性。 您可以在連接器上公開**色彩**`,`**TextColor**， **DashStyle**，和**粗細**屬性。 您可以在圖表上公開**FillColor**和**TextColor**屬性。

## <a name="forwarding-displaying-properties-of-related-elements"></a>轉送： 顯示相關的項目屬性
 當 DSL 的使用者在模型中，選取項目時，該元素的屬性會顯示在 [屬性] 視窗中。 不過，您也可以顯示指定的相關項目的屬性。 這非常有用，如果您已經定義一組項目一起運作。 例如，您可以定義主要項目和選擇性的外掛程式項目。 如果主要的項目會對應至圖形，而另一個無效，會很有用，若要查看其所有屬性，如同上一個項目。

 名為這種效果*屬性轉送*，而且它在數個情況下自動發生。 在其他情況下，可讓您藉由定義網域類型描述元轉送的屬性。

### <a name="default-property-forwarding-cases"></a>預設屬性轉寄狀況
 當使用者選取圖形或連接器或項目，在 [總管] 中時，下列屬性會顯示在 [屬性] 視窗中：

-   在模型項目，包括基底類別中定義的目的領域類別定義的網域屬性。 例外狀況是您已設定的網域屬性**是可瀏覽**至`False`。

-   透過多重性為 「 0..1 的關聯性連結的項目名稱。 這可提供便利的方法選擇性地查看連結項目，即使您還沒有定義關聯性的接點對應。

-   內嵌關聯性項目為目標的網域屬性。 內嵌關聯性通常不會顯示明確，因為這會讓使用者可以查看其屬性。

-   選取的圖形或連接器定義的定義域屬性。

### <a name="adding-property-forwarding"></a>加入屬性轉送
 若要轉遞屬性，您會定義網域類型描述元。 如果您有兩個網域類別之間的網域關聯性，您可以使用網域型別描述項，在第二個網域類別中的網域屬性值的第一個類別中設定定義域屬性。 例如，如果您有之間的關聯性**書籍**網域類別和**作者**網域類別，您可以使用網域型別描述項進行**名稱**屬性活頁簿的**作者**使用者選取活頁簿時，會出現在 [屬性] 視窗。

> [!NOTE]
>  屬性的轉送會影響使用者編輯模型屬性 視窗。 它並未定義接收類別上的網域屬性。 如果您想要存取轉送的網域屬性 DSL 定義的其他組件，或在程式碼中，您必須存取轉送的項目。

 下列程序假設您已建立 DSL。 前幾個步驟摘要說明必要條件。

##### <a name="to-forward-a-property-from-another-element"></a>從另一個項目轉送屬性

1.  建立[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]方案，其中包含至少兩個類別，在此範例會呼叫**書籍**和**作者**。 應該是其中一個類型之間的關聯性**書籍**和**作者**。

     來源 role 的多重性 (位於角色**書籍**側邊) 應為 0..1 或 1..1，因此每個**書籍**有一個**作者**。

2.  在**DSL 總管**，以滑鼠右鍵按一下**書籍**網域類別，然後按一下**新增新 DomainTypeDescriptor**。

     名為的節點**路徑的自訂屬性描述項**之下**自訂類型描述元**節點。

3.  以滑鼠右鍵按一下**自訂類型描述元**節點，然後再按一下**加入新的 PropertyPath**。

     新的屬性路徑會出現在**路徑的自訂屬性描述項**節點。

4.  選取新的屬性路徑，然後在**屬性**視窗中，將**屬性路徑**至適當的模型項目的路徑。

     您可以在這個屬性的右邊的向下箭頭，即可編輯樹狀檢視中的路徑。 如需網域路徑的詳細資訊，請參閱[網域路徑語法](../modeling/domain-path-syntax.md)。 當您已經編輯它時，路徑看起來應該像**BookReferencesAuthor.Author/ ！作者**。

5.  設定**屬性**至**名稱**網域屬性的**作者**。

6.  設定**顯示名稱**至**撰寫名稱**。

7.  轉換所有範本、 建置及執行 DSL。

8.  在模型圖中，建立書中，作者，並將其連結使用參考關聯性。 選取的書籍項目，並在 [屬性] 視窗應該會看到作者名稱以及活頁簿內容。 變更連結的作者，名稱，或將活頁簿連結至不同的作者，然後觀察書籍的作者名稱已變更。

## <a name="custom-property-editors"></a>自訂屬性編輯器
 [屬性] 視窗會提供適當的編輯經驗，針對每個網域屬性的型別預設值。 比方說，列舉型別，使用者會看到下拉式清單中，然後針對數值屬性，使用者可以輸入數字。 這只適用於內建型別。 如果您指定外部型別時，使用者將能夠看到屬性的值，但無法進行編輯。

 不過，您可以指定下列的編輯器和型別：

1.  使用與標準類型的另一個編輯器。 例如，您可以指定檔案路徑編輯器 為字串屬性。

2.  網域屬性，而且它的編輯器外部類型。

3.  在.NET 編輯器，例如檔案路徑編輯器中，或者您可以建立您自己的自訂屬性編輯器。

     外部型別與型別，例如具有預設編輯器的字串之間的轉換。

 在 DSL*外部型別*不是其中一個簡單類型 （例如布林值或 Int32） 或字串的所有類型。

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>若要定義具有外部類型的網域屬性

1.  在**方案總管 中**，將參考加入組件 (DLL) 中包含外部型別， **Dsl**專案。

     組件可以是.NET 組件或您所提供的組件。

2.  加入類型以**網域類型**清單，除非您已完成操作。

    1.  開啟 DslDefinition.dsl，然後在**DSL 總管**，根節點，以滑鼠右鍵按一下，然後按一下**加入新的外部類型**。

         新的項目之下**網域類型**節點。

        > [!WARNING]
        >  功能表項目不是 DSL 根節點上，**網域類型**節點。

    2.  在 [屬性] 視窗中設定的名稱和新類型的命名空間。

3.  將網域屬性加入網域類別，以一般方式。

     在 [屬性] 視窗中，請從下拉式清單中選取外部型別**類型**欄位。

 在這個階段，使用者可以檢視屬性的值，但無法加以編輯。 顯示的值取自`ToString()`函式。 您可以撰寫程式碼中的命令或規則，例如設定屬性的值。

### <a name="setting-a-property-editor"></a>設定屬性編輯器
 將 CLR 屬性加入至網域屬性，請以下列形式：

```
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]

```

 您也可以使用屬性上設定屬性**自訂屬性**[屬性] 視窗中的項目。

 型別`AnEditor`必須衍生自第二個參數中指定的類型。 第二個參數應該是<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.ComponentEditor>。 如需詳細資訊，請參閱<xref:System.ComponentModel.EditorAttribute>。

 您可以指定您自己的編輯器或在提供的編輯器[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，例如<xref:System.Windows.Forms.Design.FileNameEditor>或<xref:System.Drawing.Design.ImageEditor>。 例如，使用下列程序能夠讓使用者輸入檔案名稱的屬性。

##### <a name="to-define-a-file-name-domain-property"></a>若要定義檔案名稱的網域屬性

1.  DSL 定義中的網域類別中加入的網域屬性。

2.  選取新的屬性。 在**自訂屬性**欄位在 [屬性] 視窗中，輸入下列屬性。 若要輸入此屬性，按一下省略符號 **[…]** ，然後輸入屬性名稱和參數分別：

    ```
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3.  網域屬性的型別保留其預設值為**字串**。

4.  若要測試編輯器，請確認使用者可以開啟的檔案名稱值編輯器來編輯您的網域屬性。

    1.  按 CTRL + F5。 在偵錯方案中，開啟測試檔案。 建立網域類別的項目，並加以選取。

    2.  在 [屬性] 視窗中，選取的網域屬性。 [值] 欄位會顯示省略符號 **[…]**.

    3.  按一下省略符號。 檔案對話方塊隨即出現。 選取檔案並關閉對話方塊。 檔案路徑現在是網域屬性的值。

### <a name="defining-your-own-property-editor"></a>定義您自己的屬性編輯器
 您可以定義您自己的編輯器。 這樣可允許使用者編輯您定義的型別，或以特殊方式編輯標準的類型。 例如，您可能會允許使用者輸入字串，表示公式。

 撰寫衍生自的類別定義編輯器<xref:System.Drawing.Design.UITypeEditor>。 您的類別必須覆寫：

-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>與使用者互動，並更新屬性值。

-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>指定您的編輯器會開啟一個對話方塊，或提供下拉式選單。

 您也可以提供屬性的值，將會顯示在屬性方格中的圖形表示法。 若要這樣做，請覆寫`GetPaintValueSupported`，和`PaintValue`。  如需詳細資訊，請參閱<xref:System.Drawing.Design.UITypeEditor>。

> [!NOTE]
>  在不同的程式碼檔案中加入程式碼**Dsl**專案。

 例如: 

```
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

 若要使用此編輯器，設定**自訂屬性**要的網域屬性：

```
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]

```

 如需詳細資訊，請參閱<xref:System.Drawing.Design.UITypeEditor>。

## <a name="providing-a-drop-down-list-of-values"></a>提供值的下拉式清單
 您可以提供使用者從選擇的值清單。

> [!NOTE]
>  這項技術會提供一份可以在執行階段變更的值。 如果您想要提供不會變更的清單，請考慮改為使用列舉的類型做為網域屬性的類型。

 若要定義的標準值清單，您將加入至定義域屬性具有下列格式的 CLR 屬性：

```
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]

```

 定義衍生自 <xref:System.ComponentModel.TypeConverter> 的類別。 加入程式碼中的個別檔案中**Dsl**專案。 例如: 

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