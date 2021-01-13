---
title: 在機器碼中調試執行緒的秘訣 |Microsoft Docs
description: 如果您要在 Visual Studio 中進行多執行緒應用程式的偵錯工具，請參閱在機器碼中偵測執行緒的秘訣清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9249e1527a7dd2ae720ab575b1d443c10b85376e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150050"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>在機器碼中偵錯執行緒的秘訣
在機器碼中對執行緒執行偵錯時，有下列幾個訣竅：

- 您可以在 [監看式] 視窗或 [快速監看式] 對話方塊中鍵入 `@TIB`，以檢視執行緒資訊區塊的內容。

- 您可以在 [監看式] 視窗或 [快速監看式] 對話方塊中輸入 `@Err`，以檢視目前執行緒的最後錯誤碼。

- C 執行階段程式庫 (CRT) 功能可能有助於執行多執行緒應用程式偵錯。 如需詳細資訊，請參閱 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)。

## <a name="see-also"></a>另請參閱
- [Debug 多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)