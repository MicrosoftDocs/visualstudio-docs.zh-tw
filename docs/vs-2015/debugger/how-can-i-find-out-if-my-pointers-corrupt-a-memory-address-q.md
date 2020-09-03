---
title: 如何發覺我的指標是否損毀記憶體位址？ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d4f23b885b2e72e53d288946df18e038d9d956d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476773"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>如何發覺我的指標是否損毀記憶體位址？
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

問題說明  
 我認為我的其中一個指標可能損毀在 0x00408000 位址的記憶體。 我該如何確定那裡的狀況？  
  
## <a name="solution"></a>解決方法  
  
#### <a name="check-for-heap-corruption"></a>檢查堆積損毀  
  
- 大部分的記憶體損毀實際上是由於堆積損毀所造成。 請嘗試使用全域旗標公用程式 (gflags.exe) 或 pageheap.exe。 請參閱 [GFlags 和 PageHeap](/windows-hardware/drivers/debugger/gflags-and-pageheap) ，以及 [如何使用 PageHeap 公用程式來偵測 Microsoft Visual C++ 專案中的記憶體錯誤](https://support.microsoft.com/help/264471/how-to-use-the-pageheap-utility-to-detect-memory-errors-in-a-microsoft)。
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>若要找出記憶體位址遭修改的位置  
  
1. 在 0x00408000 設定資料中斷點。 請參閱[設定資料變更中斷點 (僅限原生 C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only)。  
  
2. 當您遇到中斷點時，使用 [記憶體]**** 視窗來檢視從 0x00408000 開始的記憶體內容。 如需詳細資訊，請參閱 [記憶體視窗](../debugger/memory-windows.md)。  
  
## <a name="see-also"></a>另請參閱  
 [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)
