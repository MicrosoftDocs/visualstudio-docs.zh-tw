---
title: 如何： 回到呼叫 MFC，如果暫止的函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da15793027eb643078771d33464258fea73fec9d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283388"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>如何：如果暫止，回到呼叫 MFC 的函式
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 如果您使用**中斷**命令**偵錯**暫止程式的功能表和已結束，以在 MFC 中，而且您確定問題是出在您的程式碼中，您可以使用 [呼叫堆疊] 視窗，瀏覽回您的函式。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 [呼叫堆疊] 視窗](../debugger/how-to-use-the-call-stack-window.md)。  
  
 有時候，您的程式碼可能會在訊息幫浦內中斷。 如果發生這種情形，呼叫堆疊上不會有任何使用者程式碼。 若要避免這個問題，您可以使用中斷點 （可能含條件與叫用的次數），而不是**中斷**命令。 如需詳細資訊，請參閱 <<c0> [ 中斷點和追蹤點](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>若要巡覽至呼叫 MFC 的函式  
  
-   使用**呼叫堆疊**視窗。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯機器碼常見問題集](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)