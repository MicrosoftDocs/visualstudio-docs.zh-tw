---
title: 偵錯工具機器碼 |Microsoft Docs
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
ms.openlocfilehash: f98b99a31d9215d661879aa7fa52d4b671024496
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738159"
---
# <a name="debugging-native-code"></a>偵錯機器碼
本章節內容涵蓋原生應用程式一些常見的偵錯問題和技術。 本章節所涵蓋的技術屬高階技術。 如需使用 Visual Studio 偵錯工具的機制，請參閱[偵錯工具的第一次](../debugger/debugger-feature-tour.md)查看）。

## <a name="in-this-section"></a>本章節內容
 [如何：偵錯工具優化程式碼](../debugger/how-to-debug-optimized-code.md)提供偵錯工具優化程式碼的秘訣，具體來說，就是為什麼您應該要為程式的未優化版本、Debug 和 Release 設定的預設優化設定，以及尋找僅出現在優化程式碼中之 bug 的秘訣（開啟Debug 組建設定中的優化）。

 [DebugBreak 和 __debugbreak](../debugger/debugbreak-and-debugbreak.md)描述 Win32 `DebugBreak` 函式，並提供其在 Platform SDK 中參考主題的連結。 同時也說明 `__debugbreak` 內建函式。

 [C/C++判斷](../debugger/c-cpp-assertions.md)提示討論判斷提示語句、其運作方式、使用它們的優點（攔截邏輯錯誤、檢查作業的結果，以及測試錯誤狀況）、它們與 `_DEBUG` 的互動，以及 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中支援的判斷提示類型。

 [如何： Debug 內嵌組解碼程式碼](../debugger/how-to-debug-inline-assembly-code.md)提供有關使用 [反組解碼] 視窗來查看元件指示和 [暫存器] 視窗以查看暫存器內容的簡短指示，並提供有關這些視窗的主題連結。

 [MFC 調試技術](../debugger/mfc-debugging-techniques.md)連結至 MFC 程式的調試技術，包括： afxDebugBreak、追蹤宏、偵測 MFC 中的記憶體流失、MFC 判斷提示，以及減少 MFC Debug 組建的大小。

 [CRT 調試技術](../debugger/crt-debugging-techniques.md)連結至 C 執行時間程式庫的偵錯工具技術，包括使用 CRT Debug 程式庫、用於報告的宏、malloc 和 _malloc_dbg 之間的差異、撰寫 Debug 攔截函式，以及 CRT Debug 堆積。

 [原生程式碼常見問題的調試](../debugger/debugging-native-code-faqs.md)程式提供有關調試C++程式常見問題的解答

 [COM 和 ActiveX 調試](../debugger/com-and-activex-debugging.md)提供有關偵測 COM 和 ActiveX 應用程式的資訊，包括您可以用於 COM 和 ActiveX 偵錯工具的工具。

 [如何：偵錯工具插入程式碼](../debugger/how-to-debug-injected-code.md)提供有關使用屬性的偵錯工具代碼的指引。 包含如何開啟來源附註、如何檢視插入程式碼，以及如何在目前的執行點上檢視反組譯碼程式碼的指示。

 [逐步解說：調試平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)描述如何使用 [**平行**工作] 和 [**平行堆疊**] 工具視窗來偵測平行應用程式。

## <a name="related-sections"></a>相關章節
 [準備調試C++ ](../debugger/debugging-preparation-visual-cpp-project-types.md)程式會提供主題連結，說明如何將C++專案範本所建立的原生專案類型進行調試。

 [調試 DLL 專案](../debugger/debugging-dll-projects.md)提供如何對原生和 managed Dll 進行調試的相關資訊。

 [第一次查看偵錯工具](../debugger/debugger-feature-tour.md)提供調試檔之較大區段的連結。 這些資訊包括：偵錯工具的新功能、設定和準備、中斷點、例外狀況處理、編輯後繼續、偵錯 Managed 程式碼、偵錯機器碼、偵錯 SQL，以及使用者介面的參考。

## <a name="see-also"></a>請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [Visual Studio 偵錯](../debugger/index.yml)