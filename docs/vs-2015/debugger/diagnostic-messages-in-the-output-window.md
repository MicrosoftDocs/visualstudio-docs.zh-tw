---
title: '[輸出] 視窗中的診斷訊息 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72d9da2ea3ab6cb9807fc7e0a668155d37110c3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246779"
---
# <a name="diagnostic-messages-in-the-output-window"></a>輸出視窗中的診斷訊息
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可使用 Debug 類別或 Trace 類別編寫輸出至輸出視窗的執行階段訊息，這兩個類別是 <xref:System.Diagnostics> 類別庫的一部分。 如果您只希望在程式的偵錯版本中輸出，請使用 Debug 類別。 如果要同時在偵錯和發行版本 (Release Version) 中輸出，則使用 Trace 類別。  
  
## <a name="output-methods"></a>輸出方法  
 <xref:System.Diagnostics.Trace> 和 <xref:System.Diagnostics.Debug> 類別會提供下列輸出方法：  
  
-   各種 `Write` 方法可在不中斷執行的情況下輸出資訊。 這些方法將取代前幾版 Visual Basic 所使用的 `Debug.Print` 方法。  
  
-   <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 方法會在指定的條件失敗時中斷執行並輸出資訊。 根據預設，`Assert` 方法會在對話方塊中顯示此資訊。 如需詳細資訊，請參閱 < [Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)。  
  
-   <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> 方法一定會中斷執行並輸出資訊。 根據預設，`Fail` 方法會在對話方塊中顯示資訊。  
  
 程式所輸出的應用程式中，除了**輸出**視窗可以顯示下列資訊：  
  
-   偵錯工具已載入或卸載的模組。  
  
-   已擲回的例外狀況。  
  
-   已結束的處理序。  
  
-   已結束的執行序。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [輸出視窗](../ide/reference/output-window.md)   
 [追蹤和檢測應用程式](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [檢測和追蹤的簡介](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)



