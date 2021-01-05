---
title: '調試 F # |Microsoft Docs'
description: 檢查與 Visual Studio 中的其他 managed 語言進行偵錯工具的偵錯工具之間的差異清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2dcacff924386cc279708c34d2232e50aa92c55
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728417"
---
# <a name="debugging-f"></a>偵錯 F\#
除了下列幾點差異，偵錯 F# 的方式與偵錯任何 Managed 語言非常類似：

- [自動變數] 視窗不會顯示 F# 變數。

- F# 不支援 [編輯後繼續]。 在偵錯工作階段期間編輯 F# 程式碼是可行的作法，但應該避免。 因為偵錯工作階段期間不會套用程式碼變更，所以在偵錯期間編輯 F# 程式碼會導致原始程式碼與正在偵錯的程式碼變成不相符。

- 偵錯工具無法辨識 F# 運算式。 若要於 F# 偵錯期間，在偵錯工具視窗或對話方塊中輸入運算式，您必須將運算式轉譯成 C# 語法。 當您將 F# 運算式轉譯成 C# 時，請切記 C# 使用 == 做為相等運算子，而 F# 則使用單一的 =。

## <a name="see-also"></a>請參閱
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
