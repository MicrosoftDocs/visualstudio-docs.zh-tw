---
title: "不支援 IA64 處理序的混合模式偵錯。 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9965f83feed7d12ac48aefdd248aebfc9a524473
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>不支援 IA64 處理序的混合模式偵錯。
Visual Studio 不支援對 IA64 處理序中的 Managed 程式碼和機器碼進行混合模式偵錯。 這表示在偵錯時，您無法從 Managed 程式碼逐步執行到機器碼，或從機器碼逐步執行到 Managed 程式碼。  
  
### <a name="workarounds"></a>替代解決辦法  
  
-   在不同的偵錯工作階段中分別偵錯 Managed 程式碼和機器碼。  
  
     -或-  
  
     將混合程式碼當做 32 位元處理序來偵錯，如下列程序所述。  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>若要將平台變更為 32 位元 (Visual Basic 或 C#)  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下您的專案，然後按一下 [**屬性**快顯功能表中。  
  
2.  在 屬性頁中，按一下 **編譯**或**偵錯** 索引標籤。  
  
3.  按一下**平台**然後從平台清單中選取 x86。  
  
     根據預設，Visual Basic 和 C# 編譯器會產生可在任何 CPU 上執行的程式碼。 在 64 位元電腦上，這些二進位檔會當做 64 位元處理序執行。 若要在 32 位元處理序上執行，您必須選擇**Win32**，而非**AnyCPU**。  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>若要將平台變更為 32 位元 (C/C++)  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下您的專案，然後按一下 [**屬性**快顯功能表中。  
  
2.  在 屬性頁中，按一下 **平台**然後從平台，清單中選取 Win32  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 64 位元應用程式](../debugger/debug-64-bit-applications.md)