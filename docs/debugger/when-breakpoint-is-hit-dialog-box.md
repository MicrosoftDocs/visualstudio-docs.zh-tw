---
title: 中斷點時叫用的對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53f27b400c96f6b4336339e8d1beeec0dd87277c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944744"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>叫用中斷點時對話方塊
使用此對話方塊中，您可以自訂在觸及中斷點時，就會發生的動作。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **列印訊息**  
 列印訊息，使用 DebuggerDisplay 語法。 如需詳細資訊，請參閱 <<c0> [ 使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)。  
  
 在此文字方塊也支援 （例如 $ADDRESS) 可單獨或 DebuggerDisplay 運算式的括號內的特殊關鍵字。 可用的關鍵字會列在對話方塊中。  
  
 **繼續執行**  
 啟用此控制項時，才**列印訊息**已選取。 選取此控制項，您可以使用中斷點與追蹤點來追蹤程式執行，而不是重大時叫用位置。  
  
## <a name="see-also"></a>請參閱  
 [使用中斷點](../debugger/using-breakpoints.md)   
 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)