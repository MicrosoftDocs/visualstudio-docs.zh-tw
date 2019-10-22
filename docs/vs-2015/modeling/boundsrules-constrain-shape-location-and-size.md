---
title: BoundsRules 會限制圖形位置和大小 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672720"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules 限制圖案位置和大小
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*界限規則*是定義圖形大小和位置限制的類別。 它提供一個方法，可在使用者拖曳圖形或形狀的角落或邊時重複呼叫。

 下列範例會將矩形圖形限制為固定大小的長條（水準或垂直）。 當使用者拖曳角落或側邊時，大綱會在兩個允許的高度和寬度設定之間翻轉。

 界限規則是衍生自 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> 的類別。 系統會在圖形中建立規則的實例：

```
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

 請注意，如果您想要的話，可以限制位置和大小。

## <a name="see-also"></a>請參閱
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>[回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
