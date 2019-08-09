---
title: 導覽及更新程式碼中的圖層模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb0c600830c114ca24f9cdc0619fd84c6e18d232
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871816"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>巡覽及更新程式碼中的圖層模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述圖層模型中的項目和關聯性，而您可以使用程式碼巡覽和更新它們。 如需從使用者的觀點來看分層圖的詳細資訊, 請[參閱分層圖:參考](../modeling/layer-diagrams-reference.md) 和[分層圖:方針](../modeling/layer-diagrams-guidelines.md)。

 本主題所述的 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` 模型是較為一般 <xref:Microsoft.VisualStudio.GraphModel> 模型的正面。 如果您要撰寫[功能表命令或手勢擴充](../modeling/add-commands-and-gestures-to-layer-diagrams.md)功能, 請使用`Layer`模型。 如果您是撰寫[圖層驗證擴充](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)功能, 則使用`GraphModel`會比較容易。

## <a name="transactions"></a>異動
 當您更新模型時，請考慮將變更納入 `ILinkedUndoTransaction` 中。 這會將您的變更群組為一個交易。 如果任何變更失敗，則會復原整個異動。 如果使用者復原某項變更，則也會一併復原所有變更。

 如需詳細資訊, 請參閱[使用交易連結 UML 模型更新](../modeling/link-uml-model-updates-by-using-transactions.md)。

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>內含項目
 ![ILayer 和 ILayerModel 都可以包含 ilayer。](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 圖層 ([ILayer](/previous-versions/ff644251(v=vs.140))) 和圖層模型 ([ILayerModel](/previous-versions/ff643069(v=vs.140))) 可以包含批註和圖層。

 圖層 (`ILayer`) 可以包含在圖層模型 (`ILayerModel`) 中，也可以巢狀於另一個 `ILayer` 內。

 若要建立註解或圖層，請在適當的容器上使用建立方法。

## <a name="dependency-links"></a>相依性連結
 相依性連結是以物件代表。 而且可以使用任一方向進行巡覽：

 ![ILayerDependencyLink 會連接兩個 ilayer。](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 若要建立相依性連結，請呼叫 `source.CreateDependencyLink(target)`。

## <a name="comments"></a>註解
 註解可以包含在圖層或圖層模型內，也可以連結至任何圖層項目：

 ![批註可以附加至任何圖層元素。](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 註解可以連結至任何數目的項目 (包含零個項目)。

 若要取得連結至圖層項目的註解，請使用：

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> `Comments` 的 `ILayer` 屬性會取得包含在 `ILayer` 內的註解。 但不會取得與它連結的註解。

 在適當的容器上叫用 `CreateComment()`，以建立註解。

 在註解上使用 `CreateLink()`，以建立連結。

## <a name="layer-elements"></a>圖層項目
 可以包含在模型中的所有類型的項目都是圖層項目：

 ![分層圖內容為 ILayerElements。](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>屬性
 每個 `ILayerElement` 都有名稱為 `Properties` 的字串字典。 您可以使用此字典，將任意資訊連結至任何圖層項目。

## <a name="artifact-references"></a>成品參考
 成品參考 ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))) 代表圖層和專案專案 (例如檔案、類別或資料夾) 之間的連結。 當他們建立圖層，或從 [方案總管]、[類別檢視] 或 [物件瀏覽器] 拖曳項目到分層圖藉此加入時，使用者即可建立成品。 您可以將任意數目的成品參考連結至圖層。

 [圖層總管] 中的每個資料列都會顯示成品參考。 如需詳細資訊, 請參閱[從您的程式碼建立分層圖](../modeling/create-layer-diagrams-from-your-code.md)。

 專注於成品參考的主體類型和方法如下：

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))。 Categories 屬性指出參考哪一種類型的成品 (如類別、可執行檔或組件)。 Categories 決定 Identifier 如何識別目標成品。

 [ArtifactReferenceExtensions。 CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140))會從<xref:EnvDTE.Project>或<xref:EnvDTE.ProjectItem>建立成品參考。 這是一個非同步作業。 因此，您通常會提供在建立完成時呼叫的回呼。

 「圖層成品參考」不應該與使用案例圖中的「成品」混淆。

## <a name="shapes-and-diagrams"></a>圖案和圖表
 有兩個物件用來表示圖層模型中的每個`ILayerElement`元素: 和[IShape](/previous-versions/ee806673(v=vs.140))。 `IShape` 代表圖案在圖表上的位置和大小。 在圖層模型中，每個 `ILayerElement` 都有一個 `IShape`，而圖層圖表上的每個 `IShape` 都有一個 `ILayerElement`。 `IShape` 也用於 UML 模型。 因此，不是每個 `IShape` 都有圖層項目。

 以相同的方式, `ILayerModel`會在一個[IDiagram](/previous-versions/ee789658(v=vs.140))上顯示。

 在自訂命令或手勢處理常式的程式碼中，您可以透過 `DiagramContext` 匯入，取得目前圖表以及目前圖案選取範圍：

```
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

 ![每個 ILayerElement 都是由 IShape 表示。](../modeling/media/layerapi-shapes.png)

 [IShape](/previous-versions/ee806673(v=vs.140))和[IDiagram](/previous-versions/ee789658(v=vs.140))也會用來顯示 UML 模型。 如需詳細資訊, 請參閱[在圖表上顯示 UML 模型](../modeling/display-a-uml-model-on-diagrams.md)。

## <a name="see-also"></a>另請參閱

- [將命令和軌跡新增至分層圖](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [在分層圖中新增自訂架構驗證](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [將自訂屬性新增至分層圖](../modeling/add-custom-properties-to-layer-diagrams.md)
- [圖層圖表：參考](../modeling/layer-diagrams-reference.md)
- [圖層圖表：方針](../modeling/layer-diagrams-guidelines.md)
- [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)
