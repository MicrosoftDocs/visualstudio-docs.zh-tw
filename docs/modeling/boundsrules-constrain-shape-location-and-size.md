---
title: "BoundsRules 限制圖形的位置和大小 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7600f71cc7203b48a6a20da98f59846a0b62bc13
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules 限制圖案位置和大小
A*範圍規則*是類別，定義限制的大小和圖形的位置。 它提供時的使用者正在拖曳圖形或角落或四周的圖形會重複呼叫的方法。  
  
 下列範例限制矩形是固定的大小，水平或垂直列。 當使用者拖曳的角落或四周時，大綱翻轉之間允許的兩個設定的高度和寬度。  
  
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
  
 請注意，位置和大小可以限制是否您想要。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)