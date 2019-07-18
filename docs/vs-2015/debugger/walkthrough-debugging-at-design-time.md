---
title: 逐步解說：在設計階段偵錯 |Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149422"
---
# <a name="walkthrough-debugging-at-design-time"></a>逐步解說：在設計階段進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio **Immediate**視窗，以在您的應用程式未在執行時執行函式或副程式。 如果函式或副程式含有中斷點，Visual Studio 會中斷執行的適當位置。 然後，您就可以使用偵錯工具視窗來檢查程式狀態。 這項功能稱為設計階段偵錯。  
  
 下列程序示範如何使用這項功能。  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>從即時運算視窗中叫用  
  
1. 將下列程式碼貼到 Visual Basic 主控台應用程式：  
  
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
  
2. 讀取的行上設定中斷點`s="Add BreakPoint Here"`。  
  
3. 輸入中的下列**Immediate**視窗： `?MyFunction<enter>`  
  
4. 請確認，叫用中斷點，和呼叫堆疊正確無誤。  
  
5. 在 [**偵錯**] 功能表中，按一下**繼續**，並確認您是否仍處於設計模式。  
  
6. 輸入中的下列**Immediate**視窗： `?MyFunction<enter>`  
  
7. 輸入中的下列**Immediate**視窗： `?MySub<enter>`  
  
8. 確認您叫用中斷點，並檢查靜態變數的值`i`中**區域變數**視窗。 它應該有值為 3。  
  
9. 驗證正確的呼叫堆疊。  
  
10. 在 [**偵錯**] 功能表中，按一下**繼續**，並確認您是否仍處於設計模式。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)
