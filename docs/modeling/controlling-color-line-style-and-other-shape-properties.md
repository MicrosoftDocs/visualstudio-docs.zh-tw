---
title: 控制色彩、線條樣式和其他圖形屬性
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bcc7e3a80650edff411506b9e651885b3852383
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654165"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>控制色彩、線條樣式和其他圖形屬性

某些圖形屬性（例如色彩）可以是「公開」。 也就是說，屬性可以連結至圖形的網域屬性。 有些則必須直接控制。

## <a name="exposing-a-property"></a>公開屬性
 某些圖形屬性（例如色彩）可以連結至網域屬性的值。

 在 DSL 定義中，選取圖形、連接器或圖表類別。 在其右鍵功能表上，選擇 [**新增**] [公開]，然後選擇您想要的屬性，例如 [填滿色彩]。

 圖形現在具有可在 [程式碼] 或 [使用者] 中設定的網域屬性。

## <a name="dynamically-updating-an-exposed-property"></a>動態更新公開的屬性
 您通常會想要讓公開的屬性相依于另一個屬性。 例如，您可能想要在特定網域屬性小於零時，讓圖形變成紅色。 若要進行這項相依性，請建立[規則](../modeling/rules-propagate-changes-within-the-model.md)。 例如：

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