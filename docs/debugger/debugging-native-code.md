---
title: 原生程式碼的偵錯工具 |Microsoft Docs
description: 瞭解 Visual Studio 中原生應用程式的常見偵錯工具問題和高階技術。
ms.custom: SEO-VS-2020
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4fee3044e4eaa1e7dd3549923082f9b843951b28
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728313"
---
# <a name="debugging-native-code"></a>偵錯機器碼
本章節內容涵蓋原生應用程式一些常見的偵錯問題和技術。 本章節所涵蓋的技術屬高階技術。 如需使用 Visual Studio 偵錯工具的機制，請參閱 [偵錯工具) 的第一次查看](../debugger/debugger-feature-tour.md) 。

## <a name="in-this-section"></a>本節內容
 [如何：偵錯工具優化程式碼](../debugger/how-to-debug-optimized-code.md) 提供偵錯工具優化程式碼的秘訣，具體而言，就是為什麼您應該針對程式的未優化版本、Debug 和 Release 設定的預設優化設定，以及尋找只出現在優化程式碼中的 bug 的秘訣， (在偵錯工具) 中開啟優化。

 [DebugBreak 和 __debugbreak](../debugger/debugbreak-and-debugbreak.md) 描述 Win32 `DebugBreak` 函數，並提供其在 PLATFORM SDK 中參考主題的連結。 同時也說明 `__debugbreak` 內建函式。

 [C/c + + 判斷](../debugger/c-cpp-assertions.md) 提示討論判斷提示語句、其運作方式、使用這些語句的優點 (攔截邏輯錯誤、檢查作業的結果，以及測試錯誤狀況) 、其與其互動， `_DEBUG` 以及中支援的判斷提示類型 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

 [如何：偵錯工具內嵌組解碼程式碼](../debugger/how-to-debug-inline-assembly-code.md) 提供使用 [反組解碼] 視窗來查看元件指示和 [暫存器] 視窗以查看暫存器內容，以及提供這些視窗相關主題連結的簡短指示。

 [MFC 調試技術](../debugger/mfc-debugging-techniques.md) 連結至 MFC 程式的調試技術，包括： afxDebugBreak、追蹤宏、偵測 MFC 中的記憶體流失、MFC 判斷提示，以及減少 MFC 偵錯工具的大小。

 [CRT 調試技術](../debugger/crt-debugging-techniques.md) 連結到 C Run-Time 程式庫的調試技術，包括使用 CRT Debug 程式庫、用於報告的宏、malloc 和 _malloc_dbg 之間的差異、寫入偵錯工具攔截函式，以及 CRT Debug 堆積。

 [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md) 提供有關偵錯工具 c + + 程式之常見問題的解答

 [COM 和 ActiveX 調試](../debugger/com-and-activex-debugging.md) 提供有關偵錯工具和 ActiveX 應用程式的詳細資訊，包括您可以用於 COM 和 ActiveX 偵錯工具的工具。

 [如何：將插入的程式碼進行調試](../debugger/how-to-debug-injected-code.md) 程式提供有關使用屬性的程式碼偵錯工具的指引。 包含如何開啟來源附註、如何檢視插入程式碼，以及如何在目前的執行點上檢視反組譯碼程式碼的指示。

 [逐步解說：進行平行應用程式的偵錯工具](../debugger/walkthrough-debugging-a-parallel-application.md) 描述如何使用 [ **平行** 工作] 和 [ **平行堆疊** ] 工具視窗來對平行應用程式進行偵錯工具。

## <a name="related-sections"></a>相關章節
 [準備 Debug c + + 專案](../debugger/debugging-preparation-visual-cpp-project-types.md) 提供主題的連結，這些主題描述如何將 c + + 專案範本所建立的原生專案類型進行調試。

 [調試 DLL 專案](../debugger/debugging-dll-projects.md) 提供有關如何調試原生和 managed Dll 的資訊。

 [開始查看偵錯工具](../debugger/debugger-feature-tour.md) 提供偵錯工具檔較大區段的連結。 這些資訊包括：偵錯工具的新功能、設定和準備、中斷點、例外狀況處理、編輯後繼續、偵錯 Managed 程式碼、偵錯機器碼、偵錯 SQL，以及使用者介面的參考。

## <a name="see-also"></a>請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [Visual Studio 偵錯](../debugger/index.yml)