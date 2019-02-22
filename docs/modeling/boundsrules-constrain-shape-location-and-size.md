---
title: BoundsRules 限制圖案位置和大小
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3028f5b023f40c721d5a81f7b33242463f2425cd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910827"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules 限制圖案位置和大小

A*繫結規則，* 是一個類別來定義的大小和形狀的位置上的限制。 它提供時的使用者正在拖曳圖形或角落或四周的圖形會重複呼叫的方法。

下列範例會限制為固定大小的水平或垂直列 「 矩形 」 圖形。 當使用者拖曳的角落或四周時外, 框會在兩個允許的設定的高度與寬度之間翻轉。

範圍規則的類別衍生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>。 在圖形中建立規則的執行個體：

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

請注意，位置和大小可以限制是否您想要的。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [回應及散佈變更](../modeling/responding-to-and-propagating-changes.md)