---
title: 不支援 IA64 處理序的混合模式偵錯。 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3cf7308b3302c682f32a2db9837f86cd0173260
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203295"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>不支援 IA64 處理序的混合模式偵錯。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 不支援對 IA64 處理序中的 Managed 程式碼和機器碼進行混合模式偵錯。 這表示在偵錯時，您無法從 Managed 程式碼逐步執行到機器碼，或從機器碼逐步執行到 Managed 程式碼。  
  
### <a name="workarounds"></a>因應措施  
  
- 在不同的偵錯工作階段中分別偵錯 Managed 程式碼和機器碼。  
  
     –或–  
  
     將混合程式碼當做 32 位元處理序來偵錯，如下列程序所述。  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>若要將平台變更為 32 位元 (Visual Basic 或 C#)  
  
1. 在**方案總管** 中，以滑鼠右鍵按一下您的專案，然後按一下捷徑功能表中的 [屬性]****。  
  
2. 在屬性頁中，按一下 [編譯]**** 或 [偵錯]**** 索引標籤。  
  
3. 按一下 [平台]****，並從平台清單中選取 [x86]。  
  
     根據預設，Visual Basic 和 C# 編譯器會產生可在任何 CPU 上執行的程式碼。 在 64 位元電腦上，這些二進位檔會當做 64 位元處理序執行。 若要在 32 位元處理序上執行，您必須選擇 [Win32]****，而非 [AnyCPU]****。  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>若要將平台變更為 32 位元 (C/C++)  
  
1. 在**方案總管** 中，以滑鼠右鍵按一下您的專案，然後按一下捷徑功能表中的 [屬性]****。  
  
2. 在屬性頁中，按一下 [平台]****，並從平台清單中選取 [Win32]。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 64 位元應用程式](../debugger/debug-64-bit-applications.md)
