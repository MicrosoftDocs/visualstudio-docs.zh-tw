---
title: 原生執行階段會檢查自訂 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 66591308c2b0c59cf310d3957131f80191cc51c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905482"
---
# <a name="native-run-time-checks-customization"></a>自訂原生執行階段檢查
當您編譯 **/RTC** （執行階段檢查），或使用`runtime_checks`pragma，C 執行階段程式庫提供原生執行階段檢查。 有時候，您可能想要自訂執行階段檢查：

- 若要將執行階段檢查訊息傳送至非預設的檔案或目的端。

- 若要指定使用協力廠商偵錯工具所出現的執行階段訊息之輸出目的端。

- 若要報告由 C 語言執行階段程式庫發行版本編譯的程式之執行階段檢查訊息 程式庫的發行版本在報告執行階段錯誤時並不使用 `_CrtDbgReportW`。 而是為每一個執行階段錯誤顯示一個 [判斷提示] 對話方塊。

  若要自訂執行階段錯誤檢查，您可以：

- 撰寫執行階段錯誤報告函式。 如需詳細資訊，請參閱[如何：撰寫執行階段錯誤報告函式](../debugger/how-to-write-a-run-time-error-reporting-function.md)。

- 自訂錯誤訊息目的端

- 查詢執行階段錯誤的相關資訊

## <a name="customize-the-error-message-destination"></a>自訂錯誤訊息目的端
 如果使用 `_CrtDbgReportW` 報告錯誤，您便可以使用 `_CrtSetReportMode` 來指定錯誤訊息目的端。

 如果使用自訂報告函式，您便可以使用 `_RTC_SetErrorType` 為一種錯誤結合一個報告類型。

## <a name="query-for-information-about-run-time-checks"></a>查詢執行階段檢查的相關資訊
 `_RTC_NumErrors` 會傳回由執行階段錯誤檢查偵測到的錯誤類型數目。 若要取得每個錯誤的簡短說明，您可以從 0 迴圈至 `_RTC_NumErrors` 傳回值，並將重複值傳給每一個迴圈上的 `_RTC_GetErrDesc`。 如需詳細資訊，請參閱 < [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors)並[_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc)。

## <a name="see-also"></a>另請參閱
- [如何：使用原生執行階段檢查](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport、_CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)