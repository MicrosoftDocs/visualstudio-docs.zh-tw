---
title: 偵錯原生程式碼 |Microsoft Docs
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
ms.openlocfilehash: 5a7cf0b150c45037941010bf7e611f4bc21252c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851902"
---
# <a name="debugging-native-code"></a>偵錯機器碼
本章節內容涵蓋原生應用程式一些常見的偵錯問題和技術。 本章節所涵蓋的技術屬高階技術。 使用 Visual Studio 偵錯工具的機制，請參閱 <<c0> [ 第一次查看偵錯工具](../debugger/debugger-feature-tour.md))。

## <a name="in-this-section"></a>本節內容
 [如何：偵錯最佳化程式碼](../debugger/how-to-debug-optimized-code.md)提供提示，偵錯最佳化程式碼，明確地說，為什麼您應該進行偵錯您的程式，偵錯和發行組態的預設最佳化設定非最佳化的版本而且秘訣的尋找僅限 bug，會出現在最佳化程式碼 （開啟偵錯組建組態中最佳化）。

 [DebugBreak 和 __debugbreak](../debugger/debugbreak-and-debugbreak.md)描述 Win32`DebugBreak`函式，並提供其平台 SDK 中的參考主題的連結。 同時也說明 `__debugbreak` 內建函式。

 [C /C++判斷提示](../debugger/c-cpp-assertions.md)討論判斷提示陳述式、 其運作方式、 使用 （攔截邏輯錯誤，檢查作業的結果和測試錯誤條件），它們的優點與他們互動`_DEBUG`，以及的類型支援的判斷提示[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

 [如何：偵錯內嵌組譯碼](../debugger/how-to-debug-inline-assembly-code.md)提供簡短指示使用反組譯碼視窗來檢視組譯碼指令和暫存器視窗來檢視暫存器內容，並提供關於這些視窗的主題連結。

 [MFC 偵錯技術](../debugger/mfc-debugging-techniques.md)連結至偵錯技術的 MFC 程式，包括： afxDebugBreak、 TRACE 巨集，偵測記憶體流失的問題在 MFC 中，MFC 判斷提示，並減少 MFC 偵錯的大小建立。

 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)連結至偵錯技術的 C 執行階段程式庫，包括使用 CRT 偵錯程式庫、 報告巨集、 malloc 和 _malloc_dbg、 撰寫偵錯攔截函式和 CRT 偵錯堆積之間的差異。

 [偵錯原生程式碼的常見問題集](../debugger/debugging-native-code-faqs.md)提供有關偵錯視覺效果的常見問題集解答C++程式

 [COM 和 ActiveX 進行偵錯](../debugger/com-and-activex-debugging.md)提供偵錯 COM 和 ActiveX 應用程式，包括您可以使用的工具來 COM 和 ActiveX 進行偵錯資訊。

 [如何：偵錯插入程式碼](../debugger/how-to-debug-injected-code.md)提供偵錯會使用屬性的程式碼的指引。 包含如何開啟來源附註、如何檢視插入程式碼，以及如何在目前的執行點上檢視反組譯碼程式碼的指示。

 [逐步解說：偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)描述如何使用**平行工作**並**平行堆疊**工具視窗來偵錯平行應用程式。

## <a name="related-sections"></a>相關章節
 [視覺化C++專案類型](../debugger/debugging-preparation-visual-cpp-project-types.md)提供的主題會說明如何建立視覺效果的原生專案類型進行偵錯的連結C++專案範本。

 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)提供有關如何偵錯原生和 managed Dll 的資訊。

 [第一次查看偵錯工具](../debugger/debugger-feature-tour.md)提供較大的區段的 偵錯文件的連結。 這些資訊包括：偵錯工具的新功能、設定和準備、中斷點、例外狀況處理、編輯後繼續、偵錯 Managed 程式碼、偵錯機器碼、偵錯 SQL，以及使用者介面的參考。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [Visual Studio 偵錯](../debugger/index.md)