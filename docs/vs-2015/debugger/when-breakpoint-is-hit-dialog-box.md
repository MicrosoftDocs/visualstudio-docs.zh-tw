---
title: 點擊中斷點時對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149414"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>叫用中斷點時對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用此對話方塊來自訂叫用中斷點時所發生的動作。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **列印訊息**  
 使用 DebuggerDisplay 語法來列印訊息。 如需詳細資訊，請參閱 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)。  
  
 此文字方塊也支援特殊關鍵字 (例如 $ADDRESS) ，可以單獨使用，或在 DebuggerDisplay 運算式的大括弧內使用。 可用的關鍵字會列在對話方塊中。  
  
 **繼續執行**  
 只有在選取 [ **列印訊息** ] 時，才會啟用這個控制項。 選取此控制項時，您可以使用中斷點做為追蹤程式執行的追蹤點，而不是在達到位置時中斷。  
  
## <a name="see-also"></a>另請參閱  
 [使用中斷點](../debugger/using-breakpoints.md)   
 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)
