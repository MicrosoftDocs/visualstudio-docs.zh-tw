---
title: 偵錯 Managed 程式碼 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 81a0e4b872732fa0b776c163bafa4cc162d91da2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938103"
---
# <a name="debugging-managed-code"></a>偵錯 Managed 程式碼

本節針對 Managed 應用程式或是以 Common Language Runtime 為目標的程式語言 (例如 Visual Basic、C# 和 C++) 所撰寫的應用程式，說明常見的偵錯問題和技術。 本文所說明的技術屬於高階技術。 [偵錯工具簡介](../debugger/debugger-feature-tour.md)。

## <a name="in-this-section"></a>本節內容

[輸出視窗中的診斷訊息](../debugger/diagnostic-messages-in-the-output-window.md)  
描述 <xref:System.Diagnostics.Debug> 和 <xref:System.Diagnostics.Trace> 類別，您可以使用它們將執行階段訊息寫入 [輸出] 視窗。 這兩個類別包括能夠讓資訊輸出的方法，有些資訊輸出不會中斷執行，有些則會在指定條件失敗時中斷執行。

[Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)  
描述 Managed 程式碼中的判斷提示，此段程式碼會測試指定為 `Assert` 方法引數的條件。 此外，本主題也會提供範例程式碼、<xref:System.Diagnostics.Debug> 和 <xref:System.Diagnostics.Trace> 類別方法的使用資訊、偵錯版本和發行版本程式碼的種種考量、副作用、判斷提示引數、自訂判斷提示行為以及組態檔。

[Visual Basic 中的 Stop 陳述式](../debugger/stop-statements-in-visual-basic.md)  
描述提供另一種設定中斷點方式的 `Stop` 陳述式。 同時也提供一段範例程式碼，比較 `Stop` 陳述式和 `End` 陳述式，以及 `Stop` 和 `Assert` 陳述式。

[逐步解說：對 Windows Form 進行偵錯](../debugger/walkthrough-debugging-a-windows-form.md)  
提供建立 Windows Form 和偵錯這個表單的逐步指示說明。 Windows Form 是 Managed Windows 應用程式的標準元件，也是最常用的 Managed 應用程式。 此逐步解說會使用 Visual C# 和 Visual Basic 語言，不過，利用 C++ 建立 Windows Form 的技術大致與這兩種語言相似。

[對 OnStart 方法進行偵錯](../debugger/how-to-debug-the-onstart-method.md)  
提供程式碼範例，讓您可以偵錯 Managed Windows 服務的 `OnStart` 方法。 若要偵錯 Windows 服務的 `OnStart` 方法，您必須加入幾行程式碼模擬該服務。

[Mixed-Mode Debugging](../debugger/debugging-mixed-mode-applications.md)  
說明偵錯混合模式應用程式的方法。 也就是結合機器碼和 Managed 程式碼的任何應用程式。

[錯誤：無法進行偵錯，因為系統中已啟動核心偵錯工具](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
描述如果您嘗試在以偵錯模式啟動且執行 [!INCLUDE[win7](../debugger/includes/win7_md.md)]、[!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]、[!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]、[!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] 或 Windows NT 的系統上，對 Managed 程式碼進行偵錯時會產生的錯誤訊息。

[JIT 最佳化和偵錯](../debugger/jit-optimization-and-debugging.md)  
描述 JIT 最佳化對偵錯的影響。

[對 LINQ 和 DLINQ 進行偵錯](../debugger/debugging-linq.md)  
討論對 LINQ 查詢進行偵錯的技術。

[逐步解說：對平行處理應用程式進行偵錯](../debugger/walkthrough-debugging-a-parallel-application.md)  
描述如何使用 [平行工作] 和 [平行堆疊] 工具視窗來偵錯平行應用程式。

## <a name="related-sections"></a>相關章節

[IntelliTrace](../debugger/intellitrace.md)錄製您的應用程式執行記錄，使用 IntelliTrace 尋找更快速且輕鬆的 bug。 向後和向前逐步執行記錄的事件和呼叫，以檢查關鍵時間點的應用程式狀態。 進行程式碼偵錯，而不需要設定許多中斷點或經常重新啟動應用程式。 您必須安裝 Visual Studio Enterprise。

[追蹤和檢測應用程式](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
說明可以讓您在執行應用程式時監視其執行情形的追蹤方法，以及在程式碼的策略性位置上放置和使用追蹤陳述式。 本主題也提供包含介紹檢測和追蹤、追蹤參數、追蹤接聽程式、應用程式中的追蹤程式碼、在應用程式程式碼中加入追蹤陳述式，以及使用 <xref:System.Diagnostics.Debug> 和 <xref:System.Diagnostics.Trace> 進行條件式編譯的連結。

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)  
描述將 <xref:System.Diagnostics.DebuggableAttribute> 加入至以 C++ 撰寫之程式碼的連結器選項。 當使用像是掛上 C++ 的偵錯功能時就會需要這個屬性。

[對 Windows 服務應用程式進行偵錯](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)  
提供偵錯 Windows 服務應用程式所需考量的因素，包括設定、附加到處理序、偵錯服務的 `OnStart` 方法程式碼和 Main 方法中的程式碼、設定中斷點，以及使用服務控制管理員啟動、停止、暫停和繼續服務。

[偵錯和分析](/dotnet/framework/debug-trace-profile/index)  
討論偵錯 .NET Framework 應用程式，及其組態需求。

[對指令碼和 Web 應用程式進行偵錯](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
描述您在偵錯指令碼和 Web 應用程式時會遇到的一般偵錯問題和技術。

[Visual Studio 2015 中偵錯工具的新功能](../debugger/what-s-new-for-the-debugger-in-visual-studio.md)  
說明這個版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中所加入的新偵錯功能。

[偵錯首頁](../debugger/debugger-feature-tour.md)  
提供偵錯相關文件的主要連結。 這些資訊包括偵錯工具的新功能、設定和準備、中斷點、例外狀況處理、編輯後繼續、Managed 程式碼的偵錯、Visual C++ 專案的偵錯、COM 和 ActiveX 的偵錯、DLL 偵錯、SQL 偵錯，以及使用者介面的參考。

## <a name="see-also"></a>另請參閱

[逐步解說：在設計階段針對自訂 Windows Forms 控制項進行偵錯](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)  
[偵錯工具安全性](../debugger/debugger-security.md)  
[Visual Studio 偵錯](../debugger/index.md)  
[偵錯工具簡介](../debugger/debugger-feature-tour.md)