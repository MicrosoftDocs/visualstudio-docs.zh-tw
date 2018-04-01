---
title: 中斷點時叫用的對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c03e68315c8c0818d6b9cf6a102adde4ea4f8a10
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>叫用中斷點時對話方塊
使用此對話方塊中，您可以自訂中斷點叫用時所發生的動作。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **列印訊息**  
 列印訊息，使用 DebuggerDisplay 語法。 如需詳細資訊，請參閱[使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)。  
  
 此文字方塊也支援 （例如 $ADDRESS) 可以單獨使用或使用 DebuggerDisplay 運算式的括號內的特殊關鍵字。 在對話方塊中，會列出可用的關鍵字。  
  
 **繼續執行**  
 啟用此控制項時，才**列印訊息**已選取。 選取這個控制項，您可以使用中斷點當做追蹤點追蹤程式執行，而不是重大時叫用的位置。  
  
## <a name="see-also"></a>請參閱  
 [使用中斷點](../debugger/using-breakpoints.md)   
 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)