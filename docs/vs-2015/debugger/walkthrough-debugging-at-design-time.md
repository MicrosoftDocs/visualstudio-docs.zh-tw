---
title: 逐步解說：在設計階段進行調試 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149422"
---
# <a name="walkthrough-debugging-at-design-time"></a>逐步解說：在設計階段進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您的應用程式未執行時，您可以 **使用 Visual Studio 即時** 運算視窗來執行函式或副程式。 如果函式或副程式包含中斷點，Visual Studio 將會在適當的時間點中斷執行。 然後，您就可以使用偵錯工具視窗來檢查程式狀態。 這項功能在設計階段稱為「偵錯工具」。  
  
 下列程式說明如何使用這項功能。  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>從即時運算視窗點擊中斷點  
  
1. 將下列程式碼貼入 Visual Basic 主控台應用程式中：  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. 在讀取的行上設定中斷點 `s="Add BreakPoint Here"` 。  
  
3. **在 [即時**運算] 視窗中輸入下列內容：`?MyFunction<enter>`  
  
4. 請確認已叫用中斷點，而且呼叫堆疊是正確的。  
  
5. 在 [ **調試** 程式] 功能表上，按一下 [ **繼續**]，並確認您仍處於設計模式。  
  
6. **在 [即時**運算] 視窗中輸入下列內容：`?MyFunction<enter>`  
  
7. **在 [即時**運算] 視窗中輸入下列內容：`?MySub<enter>`  
  
8. 確認您點擊中斷點，並檢查 `i` [ **區域變數** ] 視窗中的 [靜態變數] 的值。 其值應為3。  
  
9. 確認呼叫堆疊正確無誤。  
  
10. 在 [ **調試** 程式] 功能表上，按一下 [ **繼續**]，並確認您仍處於設計模式。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)
