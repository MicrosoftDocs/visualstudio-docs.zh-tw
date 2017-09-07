---
title: "巡覽和更新的模型中的程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 26
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 40f3a1d56019a8bcab4a11ffaf3aa7d37b02d262
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="navigating-and-updating-a-model-in-program-code"></a>巡覽及更新程式碼中的模型
您可以撰寫程式碼，以建立和刪除模型項目、 設定其屬性，以及建立和刪除項目之間的連結。 在交易內，就必須進行的所有變更。 如果項目會在圖表檢視，圖表將會 「 」 自動修正交易的結尾。  
  
## <a name="in-this-topic"></a>本主題內容  
 [DSL 定義範例](#example)  
  
 [瀏覽模型](#navigation)  
  
 [存取類別資訊](#metadata)  
  
 [執行交易內的變更](#transaction)  
  
 [建立模型項目](#elements)  
  
 [建立關聯性連結](#links)  
  
 [刪除項目](#deleteelements)  
  
 [刪除關聯性的連結](#deletelinks)  
  
 [重新排列關聯性的連結](#reorder)  
  
 [鎖定](#locks)  
  
 [複製和貼上](#copy)  
  
 [巡覽和更新圖表](#diagrams)  
  
 [圖案和項目之間巡覽](#views)  
  
 [圖形和連接器的內容](#shapeProperties)  
  
 [DocView 和 DocData](#docdata)  
  
##  <a name="example"></a>DSL 定義範例  
 這是本主題中的範例如 DslDefinition.dsl 的主要部分：  
  
 ![DSL 定義圖表 &#45;王朝家譜模型](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 此模型是此 DSL 的執行個體：  
  
 ![都鐸王朝家譜模型](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>參考和命名空間  
 若要執行本主題中的程式碼，您應該參考：  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 您的程式碼會使用此命名空間：  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 此外，如果您要從 DSL 定義所在的一個不同的專案中撰寫程式碼，您應該匯入 Dsl 專案所建置的組件。  
  
##  <a name="navigation"></a>瀏覽模型  
  
### <a name="properties"></a>屬性  
 DSL 定義中定義的網域屬性會變成屬性，您可以在程式碼中存取：  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 如果您想要設定屬性，您必須這樣內[交易](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 DSL 定義中，屬性的 if**種類**是**計算**，您無法設定它。 如需詳細資訊，請參閱[計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。  
  
### <a name="relationships"></a>關聯性  
 DSL 定義中定義的網域關聯性變成成對的其中一個關聯性的每一端類別上的屬性。 屬性的名稱會出現在 DslDefinition 圖表中，為在每個關聯性端的角色上的標籤。 Role 的多重性，根據屬性的型別是位於關聯性另一端的類別，或是該類別的集合。  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 在關聯性的相反兩端屬性永遠是對等。 當建立或刪除連結時，會更新這兩個項目上的角色屬性。 下列運算式 (其中使用的副檔名`System.Linq`) 一定是 true。 ParentsHaveChildren 中的關聯性的範例：  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**。 關聯性也由稱為將模型項目*連結*，這是網域關聯性類型的執行個體。 連結永遠都有一個來源項目和一個目標項目。 來源項目和目標項目可以是相同。  
  
 您可以存取的連結和其屬性：  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 根據預設，允許一個以上的執行個體關聯性的連結模型項目的任何配對。 DSL 定義中，但`Allow Duplicates`旗標為 true 的關聯性，則可能會有一個以上的連結，而且您必須使用`GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 另外還有其他方法來存取連結。 例如:   
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **隱藏的角色。** DSL 定義中**產生屬性**是**false**為特定的角色，則沒有屬性不會產生對應至該角色。 不過，您仍可以存取連結及周遊的連結關聯性的方法：  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 最常使用的範例是<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性，將模型項目會連結到圖表顯示的圖形：  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>項目目錄  
 您可以存取使用的項目目錄存放區中的所有項目：  
  
 `store.ElementDirectory.AllElements`  
  
 另外還有的方法來尋找項目，如下所示：  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="metadata"></a>存取類別資訊  
 您可以從中取得資訊的類別、 關聯性和 DSL 定義的其他層面。 例如:   
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 模型項目上階類別如下所示：  
  
-   ModelElement-所有項目和關聯性是 ModelElements  
  
-   ElementLink-所有關聯性都 ElementLinks  
  
##  <a name="transaction"></a>執行交易內的變更  
 每當您的程式碼變更存放區中的任何項目時，它必須在交易內執行。 這適用於所有模型項目、 關聯性、 圖形、 圖表和其屬性。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Modeling.Transaction>。  
  
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
  
 您可以將任意數目的一筆交易內的變更。 您可以開啟使用中交易內的新交易。  
  
 若要進行永久變更，您應該`Commit`交易之前加以處置。 如果未攔截到在交易內發生的例外狀況，存放區將會重設為所做的變更之前的狀態。  
  
##  <a name="elements"></a>建立模型項目  
 這個範例會將元素加入至現有的模型：  
  
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
  
 這個範例會說明這些重點有關建立一個項目：  
  
-   存放區的特定資料分割中建立新的項目。 模型項目和關聯性，但不圖形，這通常是預設資料分割。  
  
-   進行內嵌的關聯性的目標。 在此範例的 DslDefinition，每個人必須是內嵌 FamilyTreeHasPeople 關聯性的目標。 若要達成此目的，我們可以設定 FamilyTreeModel 角色物件的屬性人員，或將人員加入至 FamilyTreeModel 物件的使用者角色屬性。  
  
-   設定新的項目，特別是其屬性的屬性`IsName`DslDefinition 中成立。 這個旗標標記可以用來識別唯一中其擁有者的項目屬性。 在此情況下，Name 屬性具有該旗標。  
  
-   DSL 定義的這個 DSL 必須載入到存放區。 如果您在撰寫如功能表命令擴充功能，這通常會是已為 true。 在其他情況下，您可以明確地將模型載入到存放區，或使用<xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>載入它。 如需詳細資訊，請參閱[How to： 從程式碼中的檔案中開啟模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)。  
  
 當您建立項目，如此一來時，圖形會自動建立 （如果 DSL 圖表）。 它會顯示在自動指派的位置，與預設圖形、 色彩和其他功能。 如果您想要控制相關聯的圖形出現的位置和方式，請參閱[建立項目和其圖形](#merge)。  
  
##  <a name="links"></a>建立關聯性連結  
 有兩個範例 DSL 定義中定義的關聯性。 每個關聯性定義*角色屬性*每一端的關聯性類別上。  
  
 有三種方式，您可以在其中建立關聯性的執行個體。 每種方法具有相同的效果：  
  
-   設定來源角色扮演者的屬性。 例如:   
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   設定目標角色扮演者的屬性。 例如:   
  
    -   `edward.familyTreeModel = familyTree;`  
  
         此角色的重數是`1..1`，因此我們會將指派值。  
  
    -   `henry.Children.Add(edward);`  
  
         此角色的重數是`0..*`，因此我們加入至集合。  
  
-   明確建構關聯性執行的個體。 例如:   
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 最後的方法是如果您想要設定屬性本身的關聯性很有用。  
  
 當您以這種方式建立項目時，自動建立在圖表上的連接器，但它有預設圖形、 色彩和其他功能。 若要控制相關聯的連接器的建立方式，請參閱[建立項目和其圖形](#merge)。  
  
##  <a name="deleteelements"></a>刪除項目  
 刪除的項目，藉由呼叫`Delete()`:  
  
 `henry.Delete();`  
  
 也會刪除這項作業：  
  
-   關聯性的連結項目。 例如，`edward.Parents`就不再包含`henry`。  
  
-   位於其角色的項目`PropagatesDelete`旗標為 true。 例如，將刪除顯示的項目圖形。  
  
 根據預設，每個內嵌的關聯性具有`PropagatesDelete`目標的角色，則為 true。 刪除`henry`不會刪除`familyTree`，但`familyTree.Delete()`會刪除所有`Persons`。 如需詳細資訊，請參閱[自訂刪除行為](../modeling/customizing-deletion-behavior.md)。  
  
 根據預設，`PropagatesDelete`不適用的參考關聯性的角色。  
  
 您可能會導致刪除規則，若要刪除的物件時，略過特定的傳播。 這非常有用，如果您會取代另一個項目。 您提供一或多個角色的刪除動作應該不會傳播的 GUID。 從 關聯性類別可取得 GUID:  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (此特定範例會有任何作用，因為`PropagatesDelete`是`false`的角色`ParentsHaveChildren`關聯性。)  
  
 在某些情況下，因鎖定項目上，或是會刪除傳播的項目上存在而無法刪除。 您可以使用`element.CanDelete()`來檢查是否可以刪除項目。  
  
##  <a name="deletelinks"></a>刪除關聯性的連結  
 您可以藉由從角色屬性中移除項目刪除關聯性的連結：  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 您也可以明確地刪除連結：  
  
 `edwardHenryLink.Delete();`  
  
 所有這三種方法有相同的效果。 您只需要使用其中一個。  
  
 如果角色有 0..1 或 1..1 的多重性，您就可以將它設定為`null`，或為另一個值：  
  
 `edward.FamilyTreeModel = null;`或：  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="reorder"></a>重新排序的關聯性的連結  
 取得資料來源或在特定模型項目為目標的特定關聯性的連結，會有特定的順序。 它們會出現在已加入的順序。 例如，此陳述式一定會產生相同的順序中的子系：  
  
 `foreach (Person child in henry.Children) ...`  
  
 您可以變更連結的順序：  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="locks"></a>鎖定  
 鎖定可能會阻止您的變更。 個別項目、 資料分割，以及在存放區，可以設定鎖定。 如果任何這些層級鎖定來防止您想要的變更種類，當您嘗試它時可能會擲回例外狀況。 您可以探索是否鎖定使用設定的項目。GetLocks()，這是定義在命名空間的擴充方法<xref:Microsoft.VisualStudio.Modeling.Immutability>。  
  
 如需詳細資訊，請參閱[鎖定原則，以建立唯讀區段定義](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)。  
  
##  <a name="copy"></a>複製和貼上  
 您可以複製項目或群組的項目<xref:System.Windows.Forms.IDataObject>:  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 項目會儲存為序列化的項目群組。  
  
 您可以將項目從 IDataObject 合併至模型：  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`可以接受`PresentationElement`或`ModelElement`。 如果您提供`PresentationElement`，您也可以做為第三個參數的目標圖表上指定的位置。  
  
##  <a name="diagrams"></a>巡覽和更新圖表  
 DSL，在網域模型項目，它代表的概念，例如人或歌曲，則是分開的圖形元素，代表圖表上看到的內容項目。 網域模型項目儲存的重要屬性和關聯性的概念。 圖形元素儲存大小、 位置和色彩在圖表上的物件的檢視以及其元件部分的配置。  
  
### <a name="presentation-elements"></a>簡報項目  
 ![基底的圖案和項目類型的類別圖表](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 在 DSL 定義中，您指定每個項目會建立衍生自下列標準類別的其中一個類別。  
  
|一種項目|基底類別|  
|---------------------|----------------|  
|領域類別|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|網域關聯性|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|圖形|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|接點|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|圖表|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 在圖表上的項目通常代表模型項目。 通常 （但並非一定），<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>代表網域類別的執行個體，和<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>代表網域關聯性執行個體。 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性連結至模型項目所代表的節點或連結的圖形。  
  
 每個節點或連結 」 圖形都屬於一個圖表。 二進位連結 」 圖形會連接兩個節點圖案。  
  
 圖形可以有兩個集合中的子圖形。 中的圖形`NestedChildShapes`組僅限於其父系的週框方塊。 中的圖形`RelativeChildShapes`清單會顯示外部或部分的父-例如標籤或連接埠範圍之外。 圖表沒有任何`RelativeChildShapes`，而且沒有`Parent`。  
  
###  <a name="views"></a>圖案和項目之間巡覽  
 網域模型項目和圖形元素以相關<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>關聯性。  
  
```csharp  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 相同的關聯性會連結到圖表上的連接器的關聯性：  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 此關聯性也會連結到圖表中，模型根：  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 若要取得圖形所代表的模型項目，請使用：  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>巡覽圖表  
 一般情況下不建議巡覽圖形和圖表上的連接器。 最好是瀏覽在模型中，只在必要時用於圖表的外觀，圖形和連接器之間移動的關聯性。 這些方法會連結至每一端的圖形連接器：  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 許多圖形都是複合型態。它們所組成的父圖案和一或多個層級的子系。 據說相對於另一個圖形的形狀是其*子系*。 父圖形移動時，子系隨著一起移動。  
  
 *相對的子系*可以出現在父圖形的週框方塊之外。 *巢狀*系嚴格出現在父系範圍內。  
  
 若要取得最上層的一組圖形在圖表上，請使用：  
  
 `Diagram.NestedChildShapes`  
  
 圖形及連接器的上階類別有：  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="shapeProperties"></a>圖形和連接器的內容  
 在大部分情況下，不需要對圖形進行明確的變更。 當您變更模型項目時，「 修復 」 規則更新圖形和連接器。 如需詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
 不過，很有用明確變更屬性的模型項目中的圖形。 例如，您可以變更這些屬性：  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-決定圖形的寬度與高度。  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-相對於父圖形或圖表的位置  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-畫筆和筆刷用來繪製圖形或連接器的集合  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>為使圖形不可見  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>為使圖形可見之後`Hide()`  
  
###  <a name="merge"></a>建立項目和其圖形  
 當您建立一個項目，並將它連結到的內嵌關聯性樹狀結構時，圖形會自動建立並與它相關聯。 做法是在交易結束執行的 「 修復 」 規則。 不過，圖形會在自動指派的位置，且其形狀、 色彩和其他功能，則會有預設值。 若要控制圖形的建立方式，您可以使用 merge 函式。 您必須先加入您想要加入至 ElementGroup，項的目，然後再合併到圖表的群組。  
  
 這個方法：  
  
-   如果，設定的名稱，您已指派為元素名稱的屬性。  
  
-   會遵守任何項目合併指示詞 DSL 定義中所指定。  
  
 當使用者按兩下圖表，此範例會建立圖形滑鼠位置。 在此範例中，DSL 定義`FillColor`屬性`ExampleShape`已公開。  
  
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
  
 如果您提供多個圖形，設定其使用的相對位置`AbsoluteBounds`。  
  
 您也可以設定色彩，以及使用此方法的連接器的其他公開的屬性。  
  
### <a name="use-transactions"></a>使用交易  
 圖形、 連接器和圖表會的子類型<xref:Microsoft.VisualStudio.Modeling.ModelElement>和即時存放區中。 因此，您必須進行這些變更只在交易內。 如需詳細資訊，請參閱[How to： 使用異動來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
##  <a name="docdata"></a>文件檢視和文件資料  
 ![標準圖表類型的類別圖表](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>儲存資料分割  
 當載入模型時，同時載入隨附的圖表。 一般而言，模型載入 Store.DefaultPartition，而且圖表內容載入至另一個磁碟分割。 通常，每個資料分割的內容會載入，並儲存至個別檔案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [中的網域特定定義域語言的驗證](../modeling/validation-in-a-domain-specific-language.md)   
 [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)   
 [如何： 使用異動來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)

