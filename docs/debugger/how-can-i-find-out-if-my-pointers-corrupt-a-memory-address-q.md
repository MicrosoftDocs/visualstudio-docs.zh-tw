---
title: 找出是否有我的指標損毀記憶體位址 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43b7c94cfc989564a150825b653cdd32d8b85f97
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697958"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>如何發覺我的指標是否損毀記憶體位址？
## <a name="problem-description"></a>問題說明
 我認為我的其中一個指標可能損毀在 0x00408000 位址的記憶體。 我該如何確定那裡的狀況？

## <a name="solution"></a>方案

#### <a name="check-for-heap-corruption"></a>檢查堆積損毀

-   大部分的記憶體損毀實際上是由於堆積損毀所造成。 請嘗試使用全域旗標公用程式 (gflags.exe) 或 pageheap.exe。 請參閱[ http://support.microsoft.com/default.aspx?scid=kb; en-us-我們; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470)。

#### <a name="to-find-where-the-memory-address-is-modified"></a>若要找出記憶體位址遭修改的位置

1.  在 0x00408000 設定資料中斷點。 請參閱[設定資料變更中斷點 (僅限原生 C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only)。

2.  當您遇到中斷點時，使用 [記憶體] 視窗來檢視從 0x00408000 開始的記憶體內容。 如需詳細資訊，請參閱 <<c0> [ 記憶體 Windows](../debugger/memory-windows.md)。

## <a name="see-also"></a>請參閱
- [偵錯機器碼常見問題集](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)