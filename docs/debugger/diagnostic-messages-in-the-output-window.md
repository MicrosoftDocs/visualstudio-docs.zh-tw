---
title: "診斷訊息傳送至輸出視窗 |Microsoft 文件"
ms.custom: 
ms.date: 04/25/2017
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
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2b898921b022dde9a666a42725bf63c0bb9e6ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>診斷訊息傳送至輸出視窗
您可以撰寫執行階段訊息**輸出**視窗使用`Debug`類別或`Trace`類別，也就是組件的<xref:System.Diagnostics>類別庫。 如果您只希望在程式的偵錯版本中輸出，請使用 Debug 類別。 如果要同時在偵錯和發行版本 (Release Version) 中輸出，則使用 Trace 類別。  
  
## <a name="output-methods"></a>輸出方法  
 <xref:System.Diagnostics.Trace> 和 <xref:System.Diagnostics.Debug> 類別會提供下列輸出方法：  
  
-   各種 `Write` 方法可在不中斷執行的情況下輸出資訊。 這些方法將取代前幾版 Visual Basic 所使用的 `Debug.Print` 方法。  
  
-   <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 方法會在指定的條件失敗時中斷執行並輸出資訊。 根據預設，`Assert` 方法會在對話方塊中顯示此資訊。 如需詳細資訊，請參閱[Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)。  
  
-   <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> 方法一定會中斷執行並輸出資訊。 根據預設，`Fail` 方法會在對話方塊中顯示資訊。  
  
 程式所輸出的應用程式時，除了**輸出**視窗可以顯示下列資訊：  
  
-   偵錯工具已載入或卸載的模組。  
  
-   已擲回的例外狀況。  
  
-   已結束的處理序。  
  
-   已結束的執行序。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [輸出視窗](../ide/reference/output-window.md)   
 [追蹤和檢測應用程式](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)