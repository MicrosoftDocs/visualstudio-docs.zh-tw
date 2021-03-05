---
title: 找出我的指標是否損毀記憶體位址 |Microsoft 檔
description: 若要判斷指標是否會損毀記憶體，您可以尋找堆積損毀，而且可以設定資料中斷點，以找出值的修改方式。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d95e38c6393d6576f2867aad5d1224940f33cebc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155196"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>如何發覺我的指標是否損毀記憶體位址？
## <a name="problem-description"></a>問題說明
 我認為我的其中一個指標可能損毀在 0x00408000 位址的記憶體。 我該如何確定那裡的狀況？

## <a name="solution"></a>解決方法

#### <a name="check-for-heap-corruption"></a>檢查堆積損毀

- 大部分的記憶體損毀實際上是由於堆積損毀所造成。 請嘗試使用全域旗標公用程式 (gflags.exe) 或 pageheap.exe。 請參閱 [/windows-hardware/drivers/debugger/gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap)。

#### <a name="to-find-where-the-memory-address-is-modified"></a>若要找出記憶體位址遭修改的位置

1. 在 0x00408000 設定資料中斷點。 請參閱[設定資料變更中斷點 (僅限原生 C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)。

2. 當您遇到中斷點時，使用 [記憶體] 視窗來檢視從 0x00408000 開始的記憶體內容。 如需詳細資訊，請參閱 [記憶體視窗](../debugger/memory-windows.md)。

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)
