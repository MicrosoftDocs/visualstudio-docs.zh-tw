---
title: 控制色彩、線條樣式和其他圖形屬性
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eee36ad0361f40f23c29c5672b155fc5e5405dbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546675"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>控制色彩、線條樣式和其他圖形屬性

某些圖形屬性（例如色彩）可以「公開」。 也就是說，這些屬性可以連結到圖形的網域屬性。 您必須直接控制其他人。

## <a name="exposing-a-property"></a>公開屬性
 某些圖形屬性（例如 color）可以連結至網域屬性的值。

 在 DSL 定義中，選取 [圖形]、[連接器] 或 [圖表] 類別。 在其右鍵功能表上，選擇 [ **加入公開**]，然後選擇您想要的屬性，例如 [填滿色彩]。

 圖形現在具有可在程式碼或使用者中設定的網域屬性。

## <a name="dynamically-updating-an-exposed-property"></a>動態更新公開的屬性
 通常您會想要讓公開的屬性相依于其他屬性。 例如，您可能想要在特定網域屬性小於零時，讓圖形變成紅色。 若要建立這項相依性，請建立 [規則](../modeling/rules-propagate-changes-within-the-model.md)。 例如：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```