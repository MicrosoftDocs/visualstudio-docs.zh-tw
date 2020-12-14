---
title: 在對前景應用程式進行偵錯工具時使用偵錯工具視窗 |Microsoft Docs
Description: 如果您要對必須停留在前景的程式進行偵錯工具，請使用遠端偵錯程式來避免將它放在背景中。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f39f7dfbd463c48675f4b8c98612dfab3f33de3c
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398736"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>偵錯前景程式時，如何使用偵錯工具視窗？
## <a name="problem-description"></a>問題說明
 我試著偵錯螢幕圖片問題。 若要觀察這個問題，我必須將我的程式保持在前景，這表示我無法存取偵錯視窗。 我該怎麼處理？

## <a name="solution"></a>解決方案
 如果您有第二台電腦，您可以使用遠端偵錯。 有了兩台電腦設定，當您在主機上操作偵錯工具時，您可以查看遠端電腦上的螢幕圖片。 如需遠端偵錯程式的詳細資訊，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)