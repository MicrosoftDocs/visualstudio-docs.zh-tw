---
title: 逐步執行應用程式時保持焦點 |Microsoft Docs
description: 當您在偵測視窗啟用問題時，請使用遠端偵錯程式讓您的程式無法遺失焦點。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 561e5d4dc009642ee7773cd60d004ef8a64261d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386926"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>逐步執行應用程式時，如何保持焦點？
## <a name="description"></a>描述
 我的程式有視窗啟動的問題。 要重現問題時，以偵錯工具逐步執行程式會帶來干擾，因為程式會一直失焦。 有什麼方法可以避免這個問題嗎？

## <a name="solution"></a>解決方法
 如果您有第二台電腦，使用遠端偵錯。 當您在本機上執行偵錯工具時，您可以在遠端電腦上操作程式。 如需詳細資訊，請參閱 [如何：選取遠端電腦](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100))。

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [附加到正在執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)
