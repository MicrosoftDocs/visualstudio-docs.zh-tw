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
ms.openlocfilehash: b53896e2c16980352d0ce223295c4e2dab08b9e1
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870521"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>巡覽及更新程式碼中的模型

您可以撰寫程式碼來建立和刪除模型專案、設定其屬性, 以及建立和刪除元素之間的連結。 所有的變更都必須在交易內進行。 如果在圖表上查看元素, 則圖表會在交易結束時自動「固定」。

## <a name="example"></a>範例 DSL 定義
 這是本主題中範例的 Dsldefinition.dsl 檔的主要部分:

 ![DSL 定義圖表&#45;系列樹狀結構模型](../modeling/media/familyt_person.png)

 此模型是此 DSL 的實例:

 ![都鐸王朝家譜模型](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>參考和命名空間
 若要執行本主題中的程式碼, 您應該參考:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 您的程式碼會使用此命名空間:

 `using Microsoft.VisualStudio.Modeling;`

 此外, 如果您要從定義 DSL 的不同專案中撰寫程式碼, 則應該匯入 Dsl 專案所建立的元件。

## <a name="navigation"></a>導覽模型

### <a name="properties"></a>屬性
 您在 DSL 定義中定義的網域屬性會變成您可以在程式碼中存取的屬性:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 如果您想要設定屬性, 您必須在[交易](#transaction)內執行此動作:

 `henry.Name = "Henry VIII";`

 如果在 DSL 定義中, 會**計算**屬性的**種類**, 您就無法加以設定。 如需詳細資訊，請參閱 <<c0> [ 計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。

### <a name="relationships"></a>關聯性
 您在 DSL 定義中定義的網域關聯性會變成成對的屬性, 在關聯性的每一端的類別上各一個。 屬性的名稱會出現在 Dsldefinition.dsl 檔圖中, 作為關聯性各端角色的標籤。 視角色的重數而定, 屬性的類型為關聯性另一端的類別, 或該類別的集合。

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 關聯性之相反端的屬性一律是交互的。 建立或刪除連結時, 會更新兩個元素上的角色屬性。 下列運算式 (使用的延伸`System.Linq`模組) 對於範例中的 ParentsHaveChildren 關聯性一律為 true:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**。 關聯性也會以稱為「*連結*」的模型專案表示, 這是網域關聯性類型的實例。 連結一律會有一個 source 元素和一個 target 元素。 來源專案和目標元素可以相同。

 您可以存取連結和其屬性:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 根據預設, 不能有一個以上的關聯性實例可以連結任何對模型專案。 但是, 如果在 DSL 定義中, `Allow Duplicates`關聯性的旗標為 true, 則可能會有一個以上的連結, 而且您必須`GetLinks`使用:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 還有其他方法可存取連結。 例如：

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **隱藏的角色。** 如果在 DSL 定義中, 針對特定角色**產生的屬性**為**false** , 則不會產生對應至該角色的任何屬性。 不過, 您仍然可以使用關聯性的方法, 存取連結並流覽連結:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 最常使用的範例是<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性, 可將模型專案連結至在圖表上顯示的圖形:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>元素目錄
 您可以使用元素目錄來存取存放區中的所有元素:

 `store.ElementDirectory.AllElements`

 還有一些尋找專案的方法, 如下所示:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="metadata"></a>存取類別資訊
 您可以取得有關 DSL 定義的類別、關聯性和其他方面的資訊。 例如：

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 模型元素的上階類別如下所示:

- ModelElement-所有元素和關聯性都是 ModelElements

- ElementLink-所有關聯性都是 ElementLinks

## <a name="transaction"></a>在交易內執行變更
 每當程式碼變更存放區中的任何專案時, 都必須在交易內執行此動作。 這適用于所有模型元素、關聯性、圖形、圖表和其屬性。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Modeling.Transaction>。

 管理交易最方便的方法是使用`using`語句括住`try...catch`的語句:

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

 您可以在單一交易內進行任意數目的變更。 您可以在使用中交易內開啟新交易。

 若要讓變更成為永久的, `Commit`您應該在交易處置之前進行。 如果發生未在交易內攔截到的例外狀況, 存放區將會重設為其在變更之前的狀態。

## <a name="elements"></a>建立模型元素
 這個範例會將元素加入至現有的模型:

```csharp
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

 這個範例說明建立元素的這些基本重點:

- 在存放區的特定資料分割中建立新的元素。 對於模型專案和關聯性, 但不是圖形, 這通常是預設的資料分割。

- 使其成為內嵌關聯性的目標。 在此範例的 Dsldefinition.dsl 檔中, 每個人都必須是內嵌關聯性 FamilyTreeHasPeople 的目標。 若要達到此目的, 我們可以設定 Person 物件的 FamilyTreeModel role 屬性, 或將 Person 新增至 FamilyTreeModel 物件的人員角色屬性。

- 設定新元素的屬性, 特別是在 dsldefinition.dsl 檔中為 true `IsName`的屬性。 這個旗標會標示用來在其擁有者內唯一識別元素的屬性。 在此情況下, Name 屬性會有該旗標。

- 此 DSL 的 DSL 定義必須已經載入到存放區中。 如果您要撰寫擴充功能 (例如功能表命令), 這通常會是 true。 在其他情況下, 您可以將模型明確載入至存放區, 或使用[ModelBus](/previous-versions/ee904639(v=vs.140))來載入它。 如需詳細資訊，請參閱[如何：在程式碼](../modeling/how-to-open-a-model-from-file-in-program-code.md)中從檔案開啟模型。

  當您以這種方式建立元素時, 會自動建立圖形 (如果 DSL 有圖表)。 它會出現在自動指派的位置, 並具有預設圖形、色彩和其他功能。 如果您想要控制相關聯圖形的顯示位置和方式, 請參閱[建立元素和其圖形](#merge)。

## <a name="links"></a>建立關聯性連結
 範例 DSL 定義中定義了兩個關聯性。 每個關聯性都會在關聯性的每一端定義類別的*role 屬性*。

 有三種方式可建立關聯性的實例。 這三種方法的每一個都有相同的效果:

- 設定來源角色扮演者的屬性。 例如：

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- 設定目標角色扮演者的屬性。 例如：

  - `edward.familyTreeModel = familyTree;`

       此角色的多重性為, `1..1`因此我們會指派值。

  - `henry.Children.Add(edward);`

       此角色的多重性為, `0..*`因此我們會將新增至集合。

- 明確地建立關聯性的實例。 例如：

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  如果您想要設定關聯性本身的屬性, 最後一個方法會很有用。

  當您以這種方式建立專案時, 圖表上的連接器會自動建立, 但它具有預設圖形、色彩和其他功能。 若要控制相關聯連接器的建立方式, 請參閱[建立元素和其圖形](#merge)。

## <a name="deleteelements"></a>刪除元素

藉由呼叫`Delete()`來刪除元素:

`henry.Delete();`

這種操作也會一併刪除:

- 元素的關聯性連結。 例如, `edward.Parents`將不再包含`henry`。

- 位於角色的元素, 其`PropagatesDelete`旗標為 true。 例如, 顯示元素的圖形將會被刪除。

根據預設, 每個內嵌關聯`PropagatesDelete`性在目標角色上都為 true。 刪除`henry`並不會`familyTree`刪除`familyTree.Delete()` ,`Persons`但會刪除所有。

根據預設, `PropagatesDelete`參考關聯性的角色不會是 true。

當您刪除物件時, 可能會導致刪除規則省略特定的傳播。 如果您要將某個元素替換成另一個專案, 這會很有用。 您會提供一或多個不應傳播刪除之角色的 GUID。 您可以從關聯性類別取得 GUID:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(這個特定範例不會有任何作用, `PropagatesDelete`因為`false` `ParentsHaveChildren`適用于關聯性的角色)。

在某些情況下, 在專案上或會透過傳播刪除的專案上, 會導致刪除遭到封鎖。 您可以使用`element.CanDelete()`來檢查是否可以刪除元素。

## <a name="deletelinks"></a>刪除關聯性連結
 您可以從 [角色] 屬性移除元素, 以刪除關聯性連結:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 您也可以明確地刪除連結:

 `edwardHenryLink.Delete();`

 這三種方法都有相同的效果。 您只需要使用其中一個。

 如果角色具有 0 ..1 或 1 ..1 多重性, 您可以將它設定為`null`或另一個值:

 `edward.FamilyTreeModel = null;`或

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="reorder"></a>重新排序關聯性的連結
 以特定模型專案為來源或目標之特定關聯性的連結具有特定的序列。 它們會依新增的順序出現。 例如, 這個語句一律會以相同的順序產生子系:

 `foreach (Person child in henry.Children) ...`

 您可以變更連結的順序:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a>鎖定
 鎖定可能會防止您的變更。 您可以在個別專案、資料分割和存放區上設定鎖定。 如果其中有任何層級的鎖定防止您想要進行的變更類型, 則在您嘗試時可能會擲回例外狀況。 您可以使用元素來探索鎖定是否已設定。GetLocks (), 這是在命名空間<xref:Microsoft.VisualStudio.Modeling.Immutability>中定義的擴充方法。

 如需詳細資訊, 請參閱[定義鎖定原則以建立唯讀區段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)。

## <a name="copy"></a>複製並貼上
 您可以將元素或專案群組複製到<xref:System.Windows.Forms.IDataObject>:

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 元素會儲存為序列化元素群組。

 您可以將 IDataObject 中的元素合併到模型中:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()`可以接受`PresentationElement` `ModelElement`或。 如果您提供`PresentationElement`, 您也可以指定靶心圖表表上的位置做為第三個參數。

## <a name="diagrams"></a>導覽和更新圖表
 在 DSL 中, 代表概念 (例如人員或歌曲) 的領域模型專案與 shape 元素分開, 這代表您在圖表上看到的內容。 領域模型元素會儲存概念的重要屬性和關聯性。 Shape 元素會在圖表上儲存物件檢視的大小、位置和色彩, 以及其元件部分的版面配置。

### <a name="presentation-elements"></a>簡報元素
 ![基本圖案和項目類型的類別圖表](../modeling/media/dslshapesandelements.png)

 在 DSL 定義中, 您指定的每個元素都會建立衍生自下列其中一個標準類別的類別。

|元素種類|基底類別|
|-|-|
|網域類別|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|網域關聯性|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|圖形|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|接點|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|圖表|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 圖表上的元素通常代表模型專案。 通常 (但不一定), <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>代表網域類別實例, 而則<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>代表網域關聯性實例。 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性會將「節點」或「連結」圖形連結至它所代表的模型元素。

 每個「節點」或「連結」圖形都屬於一個圖表。 「二元連結」圖形連接兩個「節點」圖形。

 圖形在兩個集合中可以有子圖形。 `NestedChildShapes`集合中的圖形僅限於其父系的周框方塊。 `RelativeChildShapes`清單中的圖形可能會出現在父代外或部分外部 (例如標籤或埠)。 圖表`RelativeChildShapes`沒有和否`Parent`。

### <a name="views"></a>在圖形與元素之間流覽
 領域模型專案和圖形元素都與<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性相關。

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 相同的關聯性會將關聯性連結至圖表上的連接器:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 此關聯性也會將模型的根連結至圖表:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 若要取得圖形所代表的模型專案, 請使用:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>在圖表周圍流覽
 一般而言, 不建議在圖表上的圖形和連接器之間流覽。 最好的方式是導覽模型中的關聯性, 只有在需要處理圖表的外觀時, 才會在圖形和連接器之間移動。 這些方法會將連接器連結到各端的圖形:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 許多圖形都是複合的;它們是由父圖形以及一或多個子系層所組成。 相對於另一個圖形定位的圖形稱為其子系。 當父圖形移動時, 子系會隨之移動。

 *相對子*系可出現在父圖形的周框方塊外。 *嵌套*的子系嚴格地出現在父系的界限內。

 若要取得圖表上的最上層圖形集, 請使用:

 `Diagram.NestedChildShapes`

 圖形和連接器的上階類別為:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="shapeProperties"></a>圖形和連接器的屬性
 在大部分的情況下, 不需要對圖形進行明確的變更。 當您變更模型元素時, 「修正」規則會更新圖形和連接器。 如需詳細資訊, 請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

 不過, 在與模型專案無關的屬性中, 對圖形進行一些明確的變更是很有用的。 例如, 您可以變更下列屬性:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-決定圖形的高度和寬度。

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-相對於父圖形或圖表的位置

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-用來繪製圖形或接點的畫筆和筆刷集合

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-讓圖形變得不可見

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-讓圖形顯示在`Hide()`

### <a name="merge"></a>建立元素和其圖形

當您建立專案並將它連結到內嵌關聯性的樹狀結構時, 會自動建立圖形並與其相關聯。 這是由在交易結束時執行的「修復」規則所完成。 不過, 此圖形會出現在自動指派的位置, 而其圖形、色彩和其他功能會有預設值。 若要控制圖形的建立方式, 您可以使用 merge 函數。 您必須先將想要新增的專案新增至 ElementGroup, 然後將該群組合並到圖表中。

這個方法:

- 如果您已將屬性指派為專案名稱, 則設定名稱。

- 觀察您在 DSL 定義中指定的任何元素合併指示詞。

這個範例會在使用者按兩下圖表時, 于滑鼠位置建立一個圖形。 在這個範例的 DSL 定義中, `FillColor`的`ExampleShape`屬性已公開。

```csharp
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

 如果您提供一個以上的`AbsoluteBounds`圖形, 請使用來設定其相對位置。

 您也可以使用這個方法來設定連接器的色彩和其他公開屬性。

### <a name="use-transactions"></a>使用交易
 圖形、連接器和圖表是存放區<xref:Microsoft.VisualStudio.Modeling.ModelElement>中的子類型和即時。 因此, 您必須只在交易內對它們進行變更。 如需詳細資訊，請參閱[如何：使用交易來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。

## <a name="docdata"></a>檔視圖和檔資料
 ![標準圖表類型的類別圖表](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>儲存資料分割
 載入模型時, 會同時載入隨附的圖表。 通常會將模型載入 DefaultPartition, 並將圖表內容載入至另一個分割區。 通常會載入每個分割區的內容, 並將其儲存至個別的檔案。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [特定領域語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)
- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)
- [如何：使用異動來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)
- [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
