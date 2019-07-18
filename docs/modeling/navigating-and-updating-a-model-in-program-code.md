---
title: 巡覽及更新程式碼中的模型
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15725508059dbd1c11d9abe1dfcd42d170d24b47
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814762"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>巡覽及更新程式碼中的模型

您可以撰寫程式碼來建立和刪除模型項目、 設定其屬性，以及建立和刪除項目之間的連結。 在交易內，就必須進行的所有變更。 如果項目會在圖表上檢視，圖表會 「 修正 」 自動在交易結束。

## <a name="example"></a> DSL 定義的範例
 這是本主題中的範例 DslDefinition.dsl 的主要部分：

 ![DSL 定義圖&#45;家譜模型](../modeling/media/familyt_person.png)

 此模型是此 DSL 的執行個體：

 ![都鐸王朝家譜模型](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>參考和命名空間
 若要執行本主題中的程式碼，您應該參考：

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 您的程式碼會使用此命名空間：

 `using Microsoft.VisualStudio.Modeling;`

 此外，如果您要從您的 DSL 定義所在的一個不同的專案中撰寫程式碼，您應該匯入的 Dsl 專案所建置的組件。

## <a name="navigation"></a> 瀏覽模型

### <a name="properties"></a>屬性
 您在 DSL 定義中定義的網域屬性會變成您可以存取程式碼中的屬性：

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 如果您想要設定屬性，您必須這樣內[交易](#transaction):

 `henry.Name = "Henry VIII";`

 如果在 DSL 定義中，屬性的**種類**是**Calculated**，您無法設定它。 如需詳細資訊，請參閱 <<c0> [ 計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。

### <a name="relationships"></a>關聯性
 您在 DSL 定義中定義的網域關聯性變成成對的屬性，其中每一端的關聯性類別上。 屬性的名稱會出現在 DslDefinition 圖表中，關聯性兩端角色的標籤。 Role 的多重性，根據屬性的型別會是位於關聯性另一端的類別，或是該類別的集合。

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 在關聯性的屬性會永久保持倒數。 當建立或刪除連結時，會更新這兩個項目上的角色屬性。 下列運算式 (其使用的擴充功能`System.Linq`) 一定是 true。 在此範例中的 ParentsHaveChildren 關聯性：

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**。 關聯性也由稱為模型項目*連結*，這是網域關聯性類型的執行個體。 連結一律會有一個來源項目和一個目標項目。 來源項目和目標項目可以是相同。

 您可以存取的連結和其屬性：

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 根據預設，允許一個以上的執行個體的關聯性連結模型項目的任何一對。 但在 DSL 定義中，如果`Allow Duplicates`旗標適用於關聯性，則可能會有一個以上的連結，而且您必須使用`GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 另外還有其他方法，以存取連結。 例如: 

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **隱藏的角色。** 在 DSL 定義中，如果**屬性產生**是**false**為特定的角色，則沒有屬性不會產生對應至該角色。 不過，您仍然可以存取的連結，並周遊的連結關聯性的方法：

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 最常使用的範例是<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性，它顯示在圖表的圖形所連結模型項目：

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>在項目目錄
 您可以存取使用的項目目錄存放區中的所有項目：

 `store.ElementDirectory.AllElements`

 也有方法來尋找元素，如下所示：

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="metadata"></a> 存取類別資訊
 您可以取得資訊的類別、 關聯性和 DSL 定義中的其他層面。 例如: 

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 模型項目的祖系類別如下所示：

- ModelElement-所有的項目和關聯性是 ModelElements

- ElementLink-所有關聯性都 ElementLinks

## <a name="transaction"></a> 執行交易內的變更
 每當您的程式碼變更存放區中的任何項目時，它必須在交易內進行。 這適用於所有模型項目、 關聯性、 圖形、 圖表和其屬性。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Modeling.Transaction>。

 管理交易的最方便的方法是使用`using`陳述式括住`try...catch`陳述式：

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 您可以讓任意數目的一筆交易內的變更。 您可以開啟新的交易內使用中交易。

 若要進行永久變更，您應該`Commit`交易之前處置它。 如果發生例外狀況不會攔截在交易內，所做的變更之前的狀態將會重設的存放區。

## <a name="elements"></a> 建立模型項目
 此範例會將項目加入至現有的模型：

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 此範例會說明這些重點有關建立項目：

- 建立新的項目存放區的特定資料分割中。 模型項目和關聯性，但不形狀，這通常是預設資料分割。

- 可讓內嵌關聯性的目標。 在此範例的 DslDefinition，每個人都必須是內嵌關聯性 FamilyTreeHasPeople 的目標。 若要達到此目的，我們可以設定 Person 物件，FamilyTreeModel 角色屬性，或是將人員新增至 FamilyTreeModel 物件的使用者角色屬性。

- 設定新的項目，特別是為其屬性的屬性`IsName`是 DslDefinition 中，則為 true。 這個旗標標記是用來識別在其擁有者的唯一元素的屬性。 在此情況下，[名稱] 屬性會有該旗標。

- 此 DSL 的 DSL 定義必須載入到存放區。 如果您正在撰寫擴充功能，例如功能表命令，這通常會是已經為 true。 在其他情況下，您可以明確地將模型載入存放區，或使用<xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>載入它。 如需詳細資訊，請參閱[如何：從程式碼中的檔案中開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)。

  當您建立的項目，如此一來時，圖形會自動建立 （如果 DSL 圖表）。 它會出現在 自動指派的位置，而預設圖形、 色彩和其他功能。 如果您想要控制相關聯的圖形顯示的位置和方式，請參閱 <<c0> [ 建立項目和其圖形](#merge)。

## <a name="links"></a> 建立連結關聯性
 有兩個範例 DSL 定義中定義的關聯性。 每個關聯性會定義*角色屬性*每一端的關聯性類別上。

 有三種方式，您可以在其中建立關聯性的執行個體。 每一種方法有相同的效果：

- 設定來源角色扮演者的屬性。 例如: 

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- 設定目標角色扮演者的屬性。 例如: 

  - `edward.familyTreeModel = familyTree;`

       此角色的多重性是 「 `1..1`，因此我們將值指派。

  - `henry.Children.Add(edward);`

       此角色的多重性是 「 `0..*`，因此我們將新增至集合。

- 明確建構關聯性執行的個體。 例如: 

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  最後一個方法是很有用，如果您想要設定關聯性本身的屬性。

  當您建立的項目，如此一來時，在圖表上的連接器會自動建立，但它有 「 預設 」 圖形、 色彩和其他功能。 若要控制相關聯的連接器的建立方式，請參閱[建立項目和其圖形](#merge)。

## <a name="deleteelements"></a> 刪除項目

刪除項目，藉由呼叫`Delete()`:

`henry.Delete();`

此外，也會刪除這項作業：

- 關聯性的連結項目。 例如，`edward.Parents`就不再包含`henry`。

- 在角色的項目`PropagatesDelete`旗標為 true。 比方說，將刪除的圖形顯示的項目。

根據預設，每個內嵌關聯性具有`PropagatesDelete`在目標角色，則為 true。 正在刪除`henry`不會刪除`familyTree`，但`familyTree.Delete()`會刪除所有`Persons`。

根據預設，`PropagatesDelete`不適用於參考關聯性的角色。

您可能會導致刪除規則，當您刪除物件時，請略過特定的傳用。 這非常有用，如果您會取代另一個項目。 您提供為其刪除不應散佈的一或多個角色的 GUID。 從關聯性類別，可以取得 GUID:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(這個特定範例中會有任何作用中，，因為`PropagatesDelete`已`false`的角色`ParentsHaveChildren`關聯性。)

在某些情況下，禁止刪除鎖定，項目或項目，會刪除傳播的存在。 您可以使用`element.CanDelete()`來檢查是否可以刪除的項目。

## <a name="deletelinks"></a> 刪除關聯性連結
 您可以藉由移除角色屬性中的項目來刪除關聯性連結：

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 您也可以明確地刪除連結：

 `edwardHenryLink.Delete();`

 所有這三種方法有相同的效果。 您只需要使用其中一個。

 如果角色具有多重性 0..1 或 1..1，您就可以將它設定為`null`，或為另一個值：

 `edward.FamilyTreeModel = null;` 或：

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="reorder"></a> 重新排序的連結關聯性
 特定的關聯性來源或目標為特定的模型項目連結有特定的順序。 它們會出現在已加入的順序。 例如，此陳述式一定會產生相同的順序中的子系：

 `foreach (Person child in henry.Children) ...`

 您可以變更連結順序：

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a> 鎖定
 您的變更可能會無法以鎖定。 個別項目、 資料分割，和存放區，可以設定鎖定。 如果任何這些層級鎖定來防止您想要的變更類型的當您在嘗試可能會擲回例外狀況。 您可以探索是否鎖定使用設定的項目。GetLocks()，這是定義命名空間中的延伸模組方法<xref:Microsoft.VisualStudio.Modeling.Immutability>。

 如需詳細資訊，請參閱 <<c0> [ 定義鎖定原則來建立唯讀區段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)。

## <a name="copy"></a> 複製和貼上
 您可以將複製的項目或項目來群組<xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 項目會儲存為序列化的項目群組。

 您可將從 IDataObject 項目合併的模型：

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` 可以接受任一`PresentationElement`或`ModelElement`。 如果您提供`PresentationElement`，您也可以做為第三個參數的目標圖表上指定的位置。

## <a name="diagrams"></a> 巡覽及更新圖表
 在 DSL 中，網域模型項目，這表示的概念，例如人或歌曲，為分開的圖形項目，表示您在圖表上所看到的內容。 網域模型項目會儲存重要屬性和關聯性的概念。 圖形項目會儲存大小、 位置和物件的檢視，請在圖表上的色彩和其元件部分的配置。

### <a name="presentation-elements"></a>簡報項目
 ![基本圖案和項目類型的類別圖表](../modeling/media/dslshapesandelements.png)

 在 DSL 定義中，您指定每個項目會建立衍生自其中一個下列的標準類別的類別。

|元素的類型|基底類別|
|-|-|
|網域類別|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|網域關聯性|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|圖形|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|接點|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|圖表|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 在圖表上的項目通常表示模型項目。 通常 （但不是一定），<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>代表網域類別執行個體，並有<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>代表網域關聯性執行個體。 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性連結至模型項目所代表的節點或連結的圖形。

 每一個節點或連結的圖形都屬於一個圖表。 二進位連結圖形會連接兩個節點的圖形。

 圖形可以有兩個集合中的子圖形。 中的圖形`NestedChildShapes`組會侷限於其父系的週框方塊。 中的圖形`RelativeChildShapes`清單可以出現外部或部分的父-例如 「 標籤 」 或 「 連接埠範圍之外。 圖表沒有任何`RelativeChildShapes`並沒有`Parent`。

### <a name="views"></a> 圖案和項目之間瀏覽
 相關網域模型項目和圖形元素<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性。

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 相同的關聯性的連結關聯性圖表上的連接器：

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 此關聯性也會連結至圖表之模型的根目錄：

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 若要取得圖形所代表的模型項目，請使用：

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>巡覽圖表
 一般而言不建議您將圖形和圖表上的連接器之間瀏覽。 最好是以瀏覽在模型中，只有在需要作用於圖表的外觀時，才移動圖形與連接器之間的關聯性。 這些方法會連結至每一端的圖形連接器：

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 許多圖形都是複合應用程式;它們會組成父圖形和一個或多個層級的子系。 相對於另一個圖形的圖形可以說是其*子系*。 當父圖形移時，隨之移動子系。

 *相對的子系*可以出現父圖形的週框方塊外。 *巢狀*系嚴格地出現在父代的界限內。

 若要取得最上層的一組圖形在圖表上，請使用：

 `Diagram.NestedChildShapes`

 圖案和接點的上階類別包括：

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="shapeProperties"></a> 圖案和接點的屬性
 在大部分情況下，不需要對圖形進行明確的變更。 當您變更模型項目時，「 修正 」 規則會更新圖案和接點。 如需詳細資訊，請參閱 <<c0> [ 回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。

 不過，最好的模型項目無關的內容中的圖形中進行一些明確的變更。 例如，您可以變更這些屬性：

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -決定圖形的寬度與高度。

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -相對於父圖形或圖表的位置

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -一組畫筆和筆刷用於繪製圖形或連接器

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -使圖案的不可見

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -使圖形出現之後 `Hide()`

### <a name="merge"></a> 建立項目和其圖形

當您建立一個項目，並將它連結到的內嵌關聯性樹狀結構時，圖形會自動建立並與它相關聯。 做法是在交易結束執行的 「 修復 」 規則。 不過，圖形會出現在 自動指派的位置，而且其形狀、 色彩和其他功能都有預設值。 若要控制圖形的建立方式，您可以使用合併函式。 您必須先加入您想要新增到 ElementGroup，項的目，然後合併到圖表的群組。

這個方法：

- 如果您已指派為元素名稱的屬性，請設定名稱。

- 觀察到任何項目合併指示詞，您在 DSL 定義中指定。

當使用者按兩下圖表，此範例會建立圖形的滑鼠位置。 在 DSL 定義中，此範例中，`FillColor`屬性`ExampleShape`已公開。

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}
```

 如果您提供多個圖形，設定它們使用的相對位置`AbsoluteBounds`。

 您也可以設定色彩和公開的其他屬性使用此方法的連接器。

### <a name="use-transactions"></a>使用交易
 圖形、 連接器和圖表是的子類型<xref:Microsoft.VisualStudio.Modeling.ModelElement>選和即時存放區中。 您因此必須只在交易內，它們進行變更。 如需詳細資訊，請參閱[如何：使用異動更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。

## <a name="docdata"></a> 文件檢視和文件資料
 ![標準圖表類型的類別圖表](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>儲存資料分割
 當載入模型時，隨附的圖表會載入一次。 一般而言，模型載入至 Store.DefaultPartition，而圖表內容載入至另一個磁碟分割。 通常，每個分割區的內容會載入，並儲存到個別的檔案。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [特定領域語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)
- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)
- [如何：使用異動來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)
- [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
