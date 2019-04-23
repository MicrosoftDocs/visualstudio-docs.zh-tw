---
title: HOW TO：回到呼叫 MFC，如果暫止的函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a86efc2e181a7f692e84244eecb2355783b188bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039367"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>HOW TO：於暫止時回到呼叫 MFC 的函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
 如果您使用 [偵錯] 功能表上的 [中斷] 命令來暫止程式並於 MFC 中結束，而且您確定問題位於程式碼時，可以使用 [呼叫堆疊] 視窗巡覽回該函式。 如需詳細資訊，請參閱[如何：使用 [呼叫堆疊] 視窗](../debugger/how-to-use-the-call-stack-window.md)。  
  
 有時候，您的程式碼可能會在訊息幫浦內中斷。 如果發生這種情形，呼叫堆疊上不會有任何使用者程式碼。 若要避免發生此問題，您可以改用中斷點 (可能含條件與叫用次數) 來取代 [中斷] 命令。 如需詳細資訊，請參閱 <<c0> [ 中斷點和追蹤點](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583))。  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>若要巡覽至呼叫 MFC 的函式  
  
- 使用 [呼叫堆疊] 視窗。  
  
## <a name="see-also"></a>另請參閱  
 [對機器碼進行偵錯的常見問題集](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)
