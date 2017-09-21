---
title: "自訂屬性視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 屬性視窗"
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# 自訂屬性視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以自訂外觀和行為的屬性\] 視窗中您定義域專屬語言 \(DSL\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  在您的 DSL 定義，請在網域中的每個類別定義網域內容。  預設情況下，當您選取的類別，在圖表上或在 \[模型總管\] 中，執行個體網域中的每個屬性會列在 \[屬性\] 視窗中。  這可讓您查看及編輯屬性值的網域，即使您未對應它們在圖表上的圖形欄位。  
  
## 名稱、 描述及類別  
 **名稱\] 和 \[顯示名稱**。  在您定義網域屬性中，顯示屬性的名稱會是在執行階段，在 \[屬性\] 視窗中顯示的名稱。  相反地，當您撰寫程式碼，以更新屬性時，會使用的名稱。  名稱必須是正確的 CLR 英數字元名稱，但顯示名稱可以包含空格。  
  
 當您設定的屬性名稱在 DSL 定義時，其顯示名稱會自動設定複本的名稱。  如果您撰寫 pascal 命名法 cased 的名稱，例如"FuelGauge"，顯示名稱將自動包含一個空格："油料表"。  不過，您可以為其他值明確設定顯示名稱。  
  
 **描述**：  網域屬性的描述會出現在兩個地方：  
  
-   在 \[當使用者選取的屬性中的 \[屬性\] 視窗的底端。  您可以使用它來解釋使用者屬性所代表的意義。  
  
-   在 \[產生的程式碼。  如果您可以使用的文件 」 功能來擷取 API 的說明文件，則會為在 API 中的這個屬性的描述。  
  
 **分類**：  類別是在 \[屬性\] 視窗的標題。  
  
## 可以明顯的樣式特色  
 部份圖形元素的動態功能可以用來表示或*公開*為網域屬性。  可以由使用者更新遭受以這種方式的功能，可以更輕鬆地更新的程式碼。  
  
 DSL 定義中的圖形類別上按一下滑鼠右鍵，指到**加入公開**，然後選擇一項功能。  
  
 您可以在圖形上公開 **FillColor**，  **OutlineColor**，  **TextColor**，  **OutlineDashStyle**，  **OutlineThickness** 和 **FillGradientMode** 屬性。  您可以在連接器上公開**色彩**`,`**TextColor**，  **DashStyle**，以及**粗細**屬性。  您可以在圖表上公開 **FillColor** 和 **TextColor** 屬性。  
  
## 轉寄： 顯示相關項目的屬性  
 當您的 DSL 使用者選取模型中的項目時，該元素的屬性會顯示在 \[屬性\] 視窗中。  不過，您也可以顯示指定的相關項目的屬性。  這是很有用，如果您已經定義一組元件一起運作。  例如，您可以定義主要的項目，並選擇性的外掛程式元素。  如果主要的項目會對應到圖案，另一個不是很有用，如同它們是上一個項目，查看它們的屬性。  
  
 這種效果至名為*屬性轉寄*，而在許多情況下會自動發生。  在其他情況下，您可以得到轉寄藉由定義網域型別描述項的屬性。  
  
### 預設屬性轉送案例  
 當使用者選取圖形或 \[連接器\] 或 \[項目，在 \[檔案總管\] 中時，下列屬性會顯示在 \[屬性\] 視窗中：  
  
-   在模型項目，包括基底類別中定義的目的網域類別定義的網域屬性。  例外狀況是您已設定的網域內容**是可瀏覽**到`False`。  
  
-   透過擁有..1 的重數的關聯性連結的項目名稱。  這提供了便利的方法，或者不想看到的連結項目，即使您還沒有定義連接器的對應關係。  
  
-   網域關係屬性的內嵌項目為目標。  內嵌的關聯性通常沒有明確地顯示，因為這會讓使用者看到它們的屬性。  
  
-   在選取的圖形或連接器定義的網域內容。  
  
### 加入屬性轉送  
 轉送給屬性，您可以定義網域型別描述項。  如果您有兩個網域類別之間的網域關聯性時，您可以使用網域型別描述項，在網域中設定屬性值的第二個網域類別中的網域屬性的第一個類別。  比方說，如果您有活頁簿的網域類別和作者網域類別之間的關係，則您可以使用網域型別描述項，讓使用者選取活頁簿時，會出現在 \[屬性\] 視窗中的活頁簿的作者的 Name 屬性。  
  
> [!NOTE]
>  當使用者正在編輯模型屬性轉送會影響只有 \[屬性\] 視窗。  它不會接收類別定義網域屬性。  如果您想要存取 DSL 定義的其他組件或程式碼中的 \[轉接的網域\] 屬性，您必須存取轉寄項目。  
  
 下列程序假設您已建立 DSL。  前幾個步驟中，合併彙算必要條件。  
  
##### 若要從另一個項目轉接屬性  
  
1.  建立[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]方案包含兩個以上的類別，以在這個範例中稱為活頁簿和作者。  應該要有與活頁簿作者不論是哪一類型的關聯性。  
  
     來源角色 \(在活頁簿旁邊角色\) 的重數應該..1 或 1..1，所以每一本書會有一位作者。  
  
2.  在 **DSL 總管**，以滑鼠右鍵按一下活頁簿網域類別，然後按一下 **加入新的 DomainTypeDescriptor**。  
  
     節點，名為**路徑的自訂屬性描述項** 會出現在 **自訂型別描述項**節點。  
  
3.  以滑鼠右鍵按一下**自訂型別描述項** 節點，然後再按一下 **加入新的 PropertyPath**。  
  
     新的屬性路徑就會出現在**路徑的自訂屬性描述項**節點。  
  
4.  選取新的屬性路徑，並在**屬性** \] 視窗中，設定 **屬性路徑**到適當的模型項目的路徑。  
  
     您可以向下箭號，這個屬性的右邊，即可編輯樹狀檢視中的路徑。  如需有關網域路徑的詳細資訊，請參閱[網域路徑語法](../modeling/domain-path-syntax.md)。  當您已經編輯它時，路徑應該看起來像 **BookReferencesAuthor.Author\/\!作者**。  
  
5.  設定**屬性**到**Name**網域屬性的作者。  
  
6.  設定**的顯示名稱**作者名稱。  
  
7.  轉換所有的範本、 建置和執行 DSL。  
  
8.  在模型圖中，建立一本書，一位作者，並將其連結使用的參考關聯性。  選取活頁簿的項目，並在 \[屬性\] 視窗應該會看到作者名稱除了活頁簿的內容。  變更連結的作者的名稱或連結的活頁簿為不同的作者，並觀察書籍的作者名稱已變更。  
  
## 自訂屬性編輯器  
 \[屬性\] 視窗會提供適當的預設值，編輯經驗的每個網域內容類型。  比方說，列舉型別的使用者會看到下拉式清單中，並針對數字的屬性，使用者可以輸入數字。  這只適用於內建的型別。  如果您指定外部的型別時，使用者可以看到該屬性的值，但不得編輯它。  
  
 不過，您可以指定下列的編輯器和型別：  
  
1.  與標準的型別搭配使用時的另一個編輯器。  例如，您可以指定為字串屬性的檔案路徑編輯器。  
  
2.  \[網域\] 屬性中，而且它編輯外部型別。  
  
3.  答：。NET 的編輯器，例如檔案路徑編輯器\] 中，或者您可以建立自己的自訂屬性編輯器。  
  
     外部的型別和字串，其中有一個預設的編輯器類型之間轉換。  
  
 在 DSL， *外部型別*是不是其中一個簡單的型別 \(例如，布林值或為 Int32\) 或字串的任何型別。  
  
#### 若要定義網域屬性有外部的型別  
  
1.  在**方案總管\] 中**，將參考加入至組件 \(DLL\) 中包含外部類型而定， **Dsl**專案。  
  
     將組件。NET 組件或您所提供的組件。  
  
2.  加入至型別**網域類型**列出，除非您已經完成操作。  
  
    1.  開啟 DslDefinition.dsl，並在 **DSL 總管**，以滑鼠右鍵按一下根節點，然後按一下 \[ **加入新的外部類型**。  
  
         新的項目會出現在**網域類型**節點。  
  
        > [!WARNING]
        >  功能表項目不是在 DSL 根節點上， **網域類型**節點。  
  
    2.  在 \[屬性\] 視窗中，設定名稱和新型別的命名空間。  
  
3.  將屬性新增到網域的網域類別以平常的方式。  
  
     在 \[屬性\] 視窗中，選取 \[從下拉式清單中的 \[外部的型別**型別**欄位。  
  
 在這個階段，使用者可以檢視的屬性值，但無法加以編輯。  顯示的值取自`ToString()`函式。  您可以撰寫程式碼，設定屬性的值，例如 「 指令 」 或 「 規則。  
  
### 設定屬性編輯器  
 將 CLR 屬性加入至網域\] 屬性中，格式如下：  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 您可以在屬性上設定屬性，藉由使用**自訂屬性** \[屬性\] 視窗中的項目。  
  
 哪種`AnEditor`必須衍生自第二個參數中指定的型別。  第二個參數應該<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.ComponentEditor>。  如需詳細資訊，請參閱 <xref:System.ComponentModel.EditorAttribute>。  
  
 您可以指定您自己的編輯器或所提供的編輯器[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，例如<xref:System.Windows.Forms.Design.FileNameEditor>或<xref:System.Drawing.Design.ImageEditor>。  例如，使用下列程序，具有讓使用者輸入檔案名稱的屬性。  
  
##### 若要定義 \[檔案名稱的網域內容  
  
1.  將屬性新增到網域的網域類別在您的 DSL 定義。  
  
2.  選取新的屬性。  在**自訂屬性**欄位中的 \[屬性\] 視窗中，輸入下列的屬性。  若要輸入這個屬性，請按一下省略符號 **\[...\]** ，然後分別輸入 \[屬性名稱和參數：  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  將網域屬性的型別保留其預設值為**字串**。  
  
4.  若要測試編輯器\] 中，請確認使用者可以開啟檔案名稱編輯器來編輯您網域的屬性。  
  
    1.  按下 CTRL \+ F5。  在偵錯方案中，開啟 \[測試檔案。  建立網域類別的項目，並加以選取。  
  
    2.  在 \[屬性\] 視窗中，選取 \[網域\] 屬性。  \[值\] 欄位會顯示省略符號 **\[...\]**.  
  
    3.  按一下省略符號。  \[檔案\] 對話方塊隨即出現。  選取檔案並關閉對話方塊。  檔案路徑已經網域屬性的值。  
  
### 定義您自己的屬性編輯器  
 您可以定義您自己的編輯器。  若要如此，讓使用者編輯已定義的型別，或以特殊方式編輯標準的型別。  例如，您可能會允許使用者輸入字串，表示公式。  
  
 您所撰寫的從衍生的類別定義編輯器<xref:System.Drawing.Design.UITypeEditor>。  您的類別必須覆寫：  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>以與使用者互動，並更新屬性值。  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>以指定您的編輯器是否將會開啟對話方塊，或提供下拉式功能表。  
  
 您也可以提供屬性的值將顯示在屬性方格中的圖形化表示。  若要這樣做，請覆寫`GetPaintValueSupported`，以及`PaintValue`。  如需詳細資訊，請參閱 <xref:System.Drawing.Design.UITypeEditor>。  
  
> [!NOTE]
>  加入程式碼中的個別程式碼檔案**Dsl**專案。  
  
 例如：  
  
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
  
 若要使用這個編輯器，設定**自訂屬性**的網域屬性以：  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 如需詳細資訊，請參閱 <xref:System.Drawing.Design.UITypeEditor>。  
  
## 提供值的下拉式清單  
 您可以提供一份使用者可從中選擇的值。  
  
> [!NOTE]
>  這項技術提供一份可以在執行階段變更的值。  如果您想要提供不會變更的清單，請考慮改為定義域屬性的型別中使用列舉型別。  
  
 若要定義的標準值清單，您加入至網域屬性都採用下列格式的 CLR 屬性：  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 定義從 <xref:System.ComponentModel.TypeConverter> 衍生的類別  加入程式碼置於個別檔案，在**Dsl**專案。  例如：  
  
```c#  
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
  
## 請參閱  
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)