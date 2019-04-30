---
title: 控制色彩、線條樣式和其他圖形屬性
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1783ecf3b30207838d93fdb9cda93e3ed7e232c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422923"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>控制色彩、線條樣式和其他圖形屬性

某些圖形屬性，例如色彩可以 ' 公開 '。 亦即，屬性可以連結至圖形的網域屬性。 人直接控制的狀態。

## <a name="exposing-a-property"></a>公開屬性
 某些圖形屬性，例如色彩可以連結至網域屬性的值。

 在 DSL 定義中，選取 圖形、 連接線或圖表類別。 其以滑鼠右鍵按一下功能表上，選擇**加入已公開**，然後選擇您要填滿色彩等的屬性。

 圖形現在具有程式碼中，或以使用者身分，您可以設定的網域屬性。

## <a name="dynamically-updating-an-exposed-property"></a>動態更新一個公開的屬性
 通常您會想要公開的屬性相依於另一個屬性。 例如，您可以小於零的圖形以特定的網域屬性時變成紅色。 若要讓此相依性，建立[規則](../modeling/rules-propagate-changes-within-the-model.md)。 例如: 

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