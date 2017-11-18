---
title: "逐步解說： 在設計階段偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d497535f8511c3f9e6c55e80157507ed36184b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-at-design-time"></a>逐步解說：在設計階段進行偵錯
您可以使用 Visual Studio**即時運算**視窗執行函式或副程式時不執行您的應用程式。 如果函式或副程式包含中斷點，Visual Studio 會在適當處中斷執行。 您接著可以使用偵錯工具視窗檢查程式狀態。 這項功能稱為設計階段偵錯。  
  
 下列程序示範如何使用這項功能。  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>若要叫用中斷點，從即時運算視窗  
  
1.  將下列程式碼貼到 Visual Basic 主控台應用程式：  
  
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
  
2.  讀取的行上設定中斷點`s="Add BreakPoint Here"`。  
  
3.  輸入中的下列**即時運算**視窗：`?MyFunction<enter>`  
  
4.  請確認，叫用中斷點，和呼叫堆疊正確無誤。  
  
5.  在**偵錯**功能表上，按一下 **繼續**，並確認您是否仍在設計模式。  
  
6.  輸入中的下列**即時運算**視窗：`?MyFunction<enter>`  
  
7.  輸入中的下列**即時運算**視窗：`?MySub<enter>`  
  
8.  請確定您叫用中斷點，然後檢查靜態變數的值`i`中**區域變數**視窗。 它應該有值為 3。  
  
9. 驗證正確的呼叫堆疊。  
  
10. 在**偵錯**功能表上，按一下 **繼續**，並確認您是否仍在設計模式。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)