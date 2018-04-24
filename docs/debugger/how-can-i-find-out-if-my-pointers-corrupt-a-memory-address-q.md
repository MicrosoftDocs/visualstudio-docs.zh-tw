---
title: 如何發覺我的指標是否損毀記憶體位址？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8965ec268e5d236b9a33e5c3e8acfa35e51dcdb3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>如何發覺我的指標是否損毀記憶體位址？
## <a name="problem-description"></a>問題說明  
 我認為我的其中一個指標可能損毀在 0x00408000 位址的記憶體。 我該如何確定那裡的狀況？  
  
## <a name="solution"></a>方案  
  
#### <a name="check-for-heap-corruption"></a>檢查堆積損毀  
  
-   大部分的記憶體損毀實際上是由於堆積損毀所造成。 請嘗試使用全域旗標公用程式 (gflags.exe) 或 pageheap.exe。 請參閱[ http://support.microsoft.com/default.aspx?scid=kb; en-us-我們; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470)。  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>若要找出記憶體位址遭修改的位置  
  
1.  在 0x00408000 設定資料中斷點。 請參閱[設定資料變更中斷點 （原生 c + + 只）](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only)。  
  
2.  當您叫用中斷點時，使用**記憶體**0x00408000 開始的視窗來檢視記憶體內容。 如需詳細資訊，請參閱[記憶體 Windows](../debugger/memory-windows.md)。  
  
## <a name="see-also"></a>另請參閱  
 [機器碼偵錯 Faq](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)