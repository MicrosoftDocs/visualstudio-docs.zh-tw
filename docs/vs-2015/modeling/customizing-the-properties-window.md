---
title: 自訂屬性視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c346cc488966448cc1b77b624c80fe602555840
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088791"
---
# <a name="customizing-the-properties-window"></a>自訂屬性視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在您的特定領域語言 (DSL) 中自訂的外觀和行為的 [屬性] 視窗，在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 在 DSL 定義中，您可以定義網域內容上每個網域類別。 根據預設，當您選取的類別，在圖表上或在 [模型總管] 中，執行個體時每個網域屬性列在 [屬性] 視窗中。 這可讓您查看和編輯屬性的值網域，即使您尚未對應它們在圖表上的形狀欄位。  
  
## <a name="names-descriptions-and-categories"></a>名稱、 描述和類別  
 **名稱和顯示名稱**。 在網域屬性的定義中，屬性的顯示名稱會出現在 [屬性] 視窗中的執行階段的名稱。 相反地，當您撰寫程式碼來更新屬性時，會使用的名稱。 名稱必須是正確的 CLR 英數字元名稱，但顯示名稱可以包含空格。  
  
 當您在 DSL 定義中設定的屬性名稱時，其顯示名稱會自動設定複本的名稱。 如果您撰寫 pascal 命名法大小寫的名稱，例如"FuelGauge 」 時，顯示名稱會自動包含空格：「 油表 」。 不過，您可以為另一個值明確設定顯示名稱。  
  
 **描述**。 網域屬性的描述會出現在兩個地方：  
  
- 當使用者選取的屬性中的 [屬性] 視窗的底部。 您可以使用它來向使用者解釋屬性所代表的意義。  
  
- 在產生的程式碼。 如果您使用的文件功能來擷取 API 文件時，它會顯示為 API 中的這個屬性的描述。  
  
  **分類**. 類別是中 [屬性] 視窗的標題。  
  
## <a name="exposing-style-features"></a>公開的樣式功能  
 可以表示的某些圖形化元素動態功能或*公開*為網域屬性。 使用者可以更新已在這種方式公開的功能，可以更輕鬆地更新程式碼。  
  
 以滑鼠右鍵按一下 DSL 定義中的圖形類別，指向**加入已公開**，然後選擇一項功能。  
  
 您可以在圖形上公開**FillColor**， **OutlineColor**， **TextColor**， **OutlineDashStyle**， **OutlineThickness**並**FillGradientMode**屬性。 您可以在連接器上公開**色彩**`,`**TextColor**，**考慮到 DashStyle**，並**粗細**屬性。 您可以在圖表上，公開**FillColor**並**TextColor**屬性。  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>轉送：顯示相關項目的屬性  
 當您的 DSL 使用者模型中，選取項目時，該項目的屬性會顯示在 [屬性] 視窗中。 不過，您也可以顯示指定的相關項目的屬性。 這非常有用，如果您已經定義一組項目，然後搭配運作。 例如，您可以定義主要的項目和選擇性的外掛程式項目。 如果主要的項目對應至某個圖形，另一個不是很有用，若要查看其所有屬性，如同它們是上一個項目。  
  
 這種效果名為*屬性轉送*，它會自動在有些情況下。 您可以在其他情況下，達到轉送藉由定義網域類型描述元的屬性。  
  
### <a name="default-property-forwarding-cases"></a>預設屬性轉送案例  
 當使用者選取的圖形或連接器或項目，[總管] 中時，下列屬性會顯示在 [屬性] 視窗中：  
  
- 定義域屬性所定義的模型項目，包括基底類別中定義的網域類別上。 例外狀況是您已設定定義域屬性**Is Browsable**至`False`。  
  
- 透過具有多重性 0..1 關聯性連結的項目名稱。 這可提供方便的方法，選擇性地查看連結項目，即使您還沒有定義關聯性的接點對應。  
  
- 網域屬性的元素為目標的內嵌關聯性。 內嵌關聯性通常不會顯示明確，因為這可讓使用者查看其屬性。  
  
- 選取的圖形或連接器定義的網域屬性。  
  
### <a name="adding-property-forwarding"></a>新增屬性轉送  
 若要轉送屬性，您可以定義網域類型描述元。 如果您有兩個網域類別之間的網域關聯性，您可以使用網域型別描述項來設定第二個網域類別中的網域屬性值的第一個類別中的網域屬性。 例如，如果您有之間的關聯性**活頁簿**網域類別與**作者**網域類別，您可以使用網域型別描述項來進行**名稱**屬性本書**作者**出現在 [屬性] 視窗中，當使用者選取的書籍。  
  
> [!NOTE]
>  當使用者編輯模型時，轉送屬性會影響僅 [屬性] 視窗。 它不會接收的類別上定義的網域屬性。 如果您想要存取轉送的網域屬性，在 DSL 定義中的其他部分，或在程式碼中，您必須存取轉送項目。  
  
 下列程序假設您已建立 DSL。 前幾個步驟摘要說明的必要條件。  
  
##### <a name="to-forward-a-property-from-another-element"></a>若要從另一個項目將屬性  
  
1. 建立[!INCLUDE[dsl](../includes/dsl-md.md)]方案，其中包含至少兩個類別，以在此範例中稱為**活頁簿**並**作者**。 應該有的其中一種之間的關聯性**活頁簿**並**作者**。  
  
     來源 role 的多重性 (職務**活頁簿**側邊) 應該是 0..1 或 1..1，因此，每個**活頁簿**有**作者**。  
  
2. 在  **DSL 總管**，以滑鼠右鍵按一下**活頁簿**網域類別，然後按一下 **加入新 {0} DomainTypeDescriptor**。  
  
     名為的節點**路徑的自訂屬性描述元**下方將會出現**自訂類型描述元**節點。  
  
3. 以滑鼠右鍵按一下**自訂類型描述元**節點，然後再按一下**新增新的 PropertyPath**。  
  
     新的屬性路徑之下**路徑的自訂屬性描述元**節點。  
  
4. 選取新的屬性路徑，然後在**屬性**視窗中，將**屬性的路徑**至適當的模型項目的路徑。  
  
     按一下此屬性右邊的向下箭號，您可以編輯樹狀檢視中的路徑。 如需網域路徑的詳細資訊，請參閱 <<c0> [ 網域路徑語法](../modeling/domain-path-syntax.md)。 當您完成編輯它時，路徑看起來應該像**BookReferencesAuthor.Author/ ！作者**。  
  
5. 設定**屬性**要**名稱**網域屬性**作者**。  
  
6. 設定**顯示名稱**要**撰寫名稱**。  
  
7. 轉換所有範本、 建置和執行 DSL。  
  
8. 在模型圖中，建立一本書，作者，並將它們連結使用的參考關聯性。 選取的書籍項目，並在 [屬性] 視窗應該會看到作者名稱以及活頁簿內容。 變更連結的作者、 名稱或將活頁簿連結至不同的作者，並觀察一書的作者名稱已變更。  
  
## <a name="custom-property-editors"></a>自訂屬性編輯器  
 [屬性] 視窗會提供適當的預設編輯體驗每個網域屬性的型別。 例如，列舉型別，使用者會看到下拉式清單中，然後針對數值的屬性，使用者可以輸入數字。 這只適用於內建類型。 如果您指定外部類型時，使用者將能夠看到屬性的值，但無法編輯它。  
  
 不過，您可以指定下列的編輯器和型別：  
  
1. 使用與標準類型的另一個編輯器。 例如，您可以指定為字串屬性的檔案路徑編輯器。  
  
2. 網域屬性和它的編輯器外部類型。  
  
3. .NET 編輯器，例如檔案路徑編輯器中，或者您可以建立您自己的自訂屬性編輯器。  
  
    外部類型和類型，例如都有一個預設編輯器的字串之間轉換。  
  
   在 DSL 中，*外部類型*是不是其中一個簡單的型別 （例如布林值或 Int32） 或字串的任何類型。  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>若要定義具有外部類型的網域屬性  
  
1. 在 **方案總管**，將參考加入組件 (DLL) 中包含外部型別， **Dsl**專案。  
  
    .NET 組件或您所提供的組件，可以使用組件。  
  
2. 將類型新增至**網域類型**清單，除非您已經完成此動作。  
  
   1. 開啟 DslDefinition.dsl，然後在**DSL Explorer**，以滑鼠右鍵按一下根節點，然後按一下 **加入新的外部類型**。  
  
        新的項目之下**網域類型**節點。  
  
       > [!WARNING]
       >  功能表項目不是 DSL 的根節點上**網域類型**節點。  
  
   2. 在 [屬性] 視窗中設定的名稱和新類型的命名空間。  
  
3. 將加入網域類別的網域屬性，以一般方式。  
  
    在 屬性 視窗中，從下拉式清單中選取 外部類型**型別**欄位。  
  
   在這個階段，使用者可以檢視屬性的值，但他們無法編輯它。 顯示的值取自`ToString()`函式。 您可以撰寫程式碼中的命令或規則，例如設定屬性的值。  
  
### <a name="setting-a-property-editor"></a>設定屬性編輯器  
 CLR 將屬性新增至網域屬性，以下列形式：  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 您也可以使用在屬性上設定屬性**自訂屬性**屬性 視窗中的項目。  
  
 型別`AnEditor`必須衍生自第二個參數中指定的類型。 第二個參數應為<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.ComponentEditor>。 如需詳細資訊，請參閱<xref:System.ComponentModel.EditorAttribute>。  
  
 您可以指定您自己的編輯器或在提供的編輯器[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，這類<xref:System.Windows.Forms.Design.FileNameEditor>或<xref:System.Drawing.Design.ImageEditor>。 例如，使用下列程序具有使用者可以在其中輸入檔案名稱的屬性。  
  
##### <a name="to-define-a-file-name-domain-property"></a>若要定義檔案名稱的網域屬性  
  
1. 網域屬性加入您的 DSL 定義中的網域類別。  
  
2. 選取新的屬性。 在 **自訂屬性**欄位在 屬性 視窗中，輸入下列屬性。 若要輸入此屬性，按一下省略符號 **[...]** 然後分別輸入 屬性名稱和參數：  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3. 保留預設值的網域屬性的型別**字串**。  
  
4. 若要測試編輯器，請確認使用者可以開啟的檔案名稱值編輯器來編輯您的網域屬性。  
  
    1. 按下 ctrl+f5 或 F5。 在偵錯方案中，開啟 測試檔案。 建立網域類別的項目，並加以選取。  
  
    2. 在 [屬性] 視窗中，選取網域屬性。 [值] 欄位會顯示省略符號 **[...]**.  
  
    3. 按一下省略符號。 [檔案] 對話方塊隨即出現。 選取檔案，然後關閉對話方塊。 檔案路徑現在是網域屬性的值。  
  
### <a name="defining-your-own-property-editor"></a>定義您自己的屬性編輯器  
 您可以定義自己的編輯器。 您會執行這項操作，讓使用者編輯類型，您已定義，或以特殊方式編輯標準的類型。 例如，您可以允許使用者輸入公式表示的字串。  
  
 您所撰寫的類別是衍生自定義編輯器<xref:System.Drawing.Design.UITypeEditor>。 您的類別必須覆寫：  
  
- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>與使用者互動，並更新屬性值。  
  
- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>指定您的編輯器會開啟一個對話方塊，或提供下拉式選單。  
  
  您也可以提供屬性的值，將會顯示在屬性方格中的圖形表示。 若要這樣做，請覆寫`GetPaintValueSupported`，和`PaintValue`。  如需詳細資訊，請參閱<xref:System.Drawing.Design.UITypeEditor>。  
  
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
  
 若要使用此編輯器，將**自訂屬性**的網域屬性：  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 如需詳細資訊，請參閱<xref:System.Drawing.Design.UITypeEditor>。  
  
## <a name="providing-a-drop-down-list-of-values"></a>提供值的下拉式清單  
 您可以提供一份使用者可從中選擇的值。  
  
> [!NOTE]
>  這項技術會提供一份可能會在執行階段變更的值。 如果您想要提供不會變更的清單，請考慮改為使用列舉的類型做為您的網域屬性的類型。  
  
 若要定義的標準值清單，您將新增至您的網域屬性具有下列格式的 CLR 屬性：  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 定義衍生自 <xref:System.ComponentModel.TypeConverter> 的類別。 中的個別檔案中加入程式碼**Dsl**專案。 例如：  
  
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
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
