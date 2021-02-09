---
title: 在 Visual Studio 外部執行應用程式時，偵測存取違規
titleSuffix: ''
description: 使用即時偵錯工具來偵測在 Visual Studio 環境之外發生的存取違規。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dd4709807b176806d8a7ca56de4adda8cdfe13ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904328"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>在偵錯工具外執行我的程式時，如何偵錯存取違規？

## <a name="problem-description"></a>問題說明
 我的程式在 Visual Studio 環境裡執行正常，但是當我以 Windows 作業系統獨立執行它時，它會產生存取違規。 我該如何偵錯這個問題？

## <a name="solution"></a>解決方案
 設定 [ 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)選項並獨立執行您的程式，直到發生存取違規為止。 然後，在 [存取違規] 對話方塊中，您可以按一下 [取消] 來啟動偵錯工具。

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)