---
title: 使用 UML API 導覽關聯性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: a4d11d45-b8c0-40f9-a597-363f07659610
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c0067e213fdff2bde09c290d9fcaa9b4f52b9ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668537"
---
# <a name="navigate-relationships-with-the-uml-api"></a>使用 UML API 巡覽關聯性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

模型會包含由不同類型的關聯性連結在一起的項目。 此主題將說明如何巡覽程式碼中的模型。

## <a name="traversing-relationships"></a>周遊關聯性

### <a name="any-relationship"></a>任何關聯性
 使用 `GetRelatedElements<T>()` 尋找所有與指定項目連接的項目。 將 `T` 設為 `IRelationship` 以周遊所有類型的關聯性，或是使用更明確的類型 (例如 `IAssociation`) 僅周遊該類型。

```
IElement anElement;
// Select all elements related to anElement.
Context.CurrentDiagram.SelectShapes (
   anElement.GetRelatedElements<IRelationship>()
    .SelectMany(e=>e.Shapes()).ToArray());

```

 使用 `GetRelatedLinks<T>()` 尋找所有與項目連接的關聯性。

```
// Process all relationships connected to an element.
foreach (IRelationship relationship in
   anElement.GetRelatedLinks<IRelationship>())
{
  Debug.Assert(relationship.SourceElement == anElement
      || relationship.TargetElement == anElement);
}

```

### <a name="association"></a>關聯
 關聯是兩個屬性之間的關聯性，這兩個屬性各屬於一個分類器。

```
IClassifier classifier; // class, interface, component, actor, ...
// Get all the associations sourced from this classifier
foreach (IProperty p in classifier.GetOutgoingAssociationEnds())
{
  // p represents the end further end of an association.
  IType oppositeElement = p.Type;
    // The type to which this association connects classifier

  IProperty oppositeProperty = p.Opposite;
    // The nearer end of the association.
  Debug.Assert(oppositeProperty.Type == classifier);
  IAssociation association = p.Association;
  Debug.Assert(association.MemberEnds.Contains(p)
     && association.MemberEnds.Contains(oppositeProperty));
}
```

### <a name="generalization-and-realization"></a>一般化和實現
 存取一般化的另一端：

```
foreach (IClassifier supertype in classifier.Generals) {…}
foreach (IClassifier subtype in classifier.GetSpecifics()) {…}
Access the relationship itself:
foreach (IGeneralization gen in classifier.Generalizations)
{ Debug.Assert(classifier == gen.Specific); }
```

```

/// InterfaceRealization:
IEnumerable<IInterface> GetRealizedInterfaces
    (this IBehavioredClassifier classifier);
IEnumerable<IBehavioredClassifier> GetRealizingClassifiers
    (this IInterface interface);

```

### <a name="dependency"></a>相依性

```
/// Returns the elements depending on this element
IEnumerable<INamedElement> GetDependencyClients(this INamedElement element);
/// Returns the elements this element depends on
IEnumerable<INamedElement> INamedElement GetDependencySuppliers(this INamedElement element);

```

### <a name="activity-edge"></a>活動邊緣

```
/// Returns the nodes targeted by edges outgoing from this one
IEnumerable<IActivityNode> GetActivityEdgeTargets(this IActivityNode node);
/// Returns the nodes sourcing edges incoming to this one
IEnumerable<IActivityNode> GetActivityEdgeSources(this IActivityNode node);

```

### <a name="connector-assembly-and-delegation"></a>連接器 (組件和委派)

```
/// Returns the elements connected via assembly
/// or delegation to this one
IEnumerable<IConnectableElement> GetConnectedElements(this IConnectableElement element);

```

### <a name="messages-and-lifelines"></a>訊息和生命線

```
IEnumerable<IMessage> GetAllOutgoingMessages(this ILifeline  lifeline);
// both from lifeline and execution occurrences
IEnumerable<IMessage> GetAllIncomingMessages(this ILifeline  lifeline);
ILifeline GetSourceLifeline(this IMessage message);
    // may return null for found messages
ILifeline GetTargetLifeline(this IMessage message);
    // may return null for lost messages

```

### <a name="package-import"></a>封裝匯入

```
IEnumerable<IPackage>GetImportedPackages(this INamespace namespace);
IEnumerable<INamespace> GetImportingNamespaces(this IPackage package);

```

### <a name="use-case-extend-and-include"></a>使用案例擴充並包含

```
IEnumerable<IUseCase>GetExtendedCases(this IUseCase usecase);
IEnumerable<IUseCase>GetExtendingCases(this IUseCase usecase);
IEnumerable<IUseCase>GetIncludedCases(this IUseCase usecase);
IEnumerable<IUseCase>GetIncludingCases(this IUseCase usecase);
```

## <a name="enumerating-relationships"></a>列舉關聯性
 傳回多個值的 UML 模型的所有屬性都符合 IEnumerable < > 介面。 這表示您可以使用[Linq 查詢運算式](http://go.microsoft.com/fwlink/?LinkId=168834)，以及在**System. Linq**命名空間中定義的擴充方法。

 例如:

```
from shape in     Context.CurrentDiagram.GetSelectedShapes<IClassifier>()
where shape.Color == System.Drawing.Color.Red
select shape.Element

```

## <a name="see-also"></a>請參閱
 [擴充 uml 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)[導覽 uml 模型](../modeling/navigate-the-uml-model.md)
