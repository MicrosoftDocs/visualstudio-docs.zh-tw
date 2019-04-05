---
title: BoundsRules 限制圖案位置和大小 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09be82be084767bfb2d300a1877e95456a957b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942557"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules 限制圖案位置和大小
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A*繫結規則，* 是一個類別來定義的大小和形狀的位置上的限制。 它提供時的使用者正在拖曳圖形或角落或四周的圖形會重複呼叫的方法。  
  
 下列範例會限制為固定大小的水平或垂直列 「 矩形 」 圖形。 當使用者拖曳的角落或四周時外, 框會在兩個允許的設定的高度與寬度之間翻轉。  
  
 範圍規則的類別衍生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>。 在圖形中建立規則的執行個體：  
  
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
  
 請注意，位置和大小可以限制是否您想要的。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
