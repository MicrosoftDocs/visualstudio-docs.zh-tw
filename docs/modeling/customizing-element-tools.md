---
title: 自訂項目工具
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: cf990ea206a299c72ec55150bf2e4935b80fb473
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-element-tools"></a>自訂項目工具
在一些 DSL 定義，您一組項目代表單一的概念。 例如，如果您建立的模型，其中一個元件都有一組固定的通訊埠，您一定想要在其父元件的同時間建立的連接埠。 因此，您必須自訂項目建立工具，讓它會建立一組項目，而不是其中一個。 若要達成此目的，您可以自訂如何初始化項目建立工具。

 您也可以覆寫工具拖曳到圖表或項目時，會發生什麼事。

## <a name="customizing-the-content-of-an-element-tool"></a>自訂項目工具的內容
 每個項目工具儲存的執行個體<xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>(EGP)，其中包含一或多個模型項目和連結的序列化的版本。 根據預設，項目工具的 EGP 會包含一個類別，以您指定工具的執行個體。 您可以覆寫來變更此*YourLanguage*`ToolboxHelper.CreateElementToolPrototype`。 DSL 在載入時，會呼叫這個方法。

 方法的參數是您在 DSL 定義中指定的類別識別碼。 您感興趣的類別呼叫方法時，您可以將額外的項目加入 EGP。

 EGP 必須包含內嵌的附屬項目從一個主要的項目連結。 它也可以包含參考的連結。

 下列範例會建立 main 項目和兩個內嵌的項目。 主要類別稱為電阻，而且具有名為終端機的元素的兩個內嵌關聯性。 內嵌的角色內容會命名為 Terminal1 和 Terminal2，且兩者都有的多重性為 1..1。

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>另請參閱

- [自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)