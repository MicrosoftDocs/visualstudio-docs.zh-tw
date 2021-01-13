---
title: 點擊中斷點時對話方塊 |Microsoft Docs
description: 當叫用中斷點時使用，以指定中斷的動作。 您可以指定要列印的訊息，並在之後繼續執行。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a528709769f599219a7b3df2b8157b0ee3a605b1
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149309"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>叫用中斷點時對話方塊
您可以使用此對話方塊來自訂叫用中斷點時所發生的動作。

## <a name="uielement-list"></a>UIElement 清單
 **列印訊息** 使用 DebuggerDisplay 語法來列印訊息。 如需詳細資訊，請參閱 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)。

 此文字方塊也支援特殊關鍵字 (例如 $ADDRESS) ，可以單獨使用，或在 DebuggerDisplay 運算式的大括弧內使用。 可用的關鍵字會列在對話方塊中。

 **繼續執行** 只有在選取 [ **列印訊息** ] 時，才會啟用這個控制項。 選取此控制項時，您可以使用中斷點做為追蹤程式執行的追蹤點，而不是在達到位置時中斷。

## <a name="see-also"></a>另請參閱
- [使用中斷點](../debugger/using-breakpoints.md)
- [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)