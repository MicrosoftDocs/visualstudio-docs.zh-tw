---
title: 將訊息傳送至 [輸出] 視窗 |Microsoft Docs
description: 使用 Debug 類別或 Trace 類別（屬於 System.object 類別庫的一部分），將執行時間訊息寫入 Visual Studio 中的輸出視窗。
ms.custom: SEO-VS-2020
ms.date: 11/08/2018
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b61d0c6bc89f8be2680930411e0b9109fdeec473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872051"
---
# <a name="send-messages-to-the-output-window"></a>傳送訊息至 [輸出] 視窗

您可以使用類別 <xref:System.Diagnostics.Debug> 或 <xref:System.Diagnostics.Trace> 類別（屬於類別庫的一部分），將執行時間訊息寫入至輸出視窗 <xref:System.Diagnostics> 。 <xref:System.Diagnostics.Debug>如果您只想要在程式的 *Debug* 版本中輸出，請使用類別。 <xref:System.Diagnostics.Trace>如果您想要在 *Debug* 和 *Release* 版本中都有輸出，請使用類別。

## <a name="output-methods"></a>輸出方法
 <xref:System.Diagnostics.Trace> 和 <xref:System.Diagnostics.Debug> 類別會提供下列輸出方法：

- 各種 `Write` 方法可在不中斷執行的情況下輸出資訊。 這些方法將取代前幾版 Visual Basic 所使用的 `Debug.Print` 方法。

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 方法，如果指定的條件失敗，則會中斷執行和輸出資訊。 根據預設，`Assert` 方法會在對話方塊中顯示此資訊。 如需詳細資訊，請參閱 [managed 程式碼中的判斷](../debugger/assertions-in-managed-code.md)提示。

- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> 方法，一律會中斷執行和輸出資訊。 根據預設，`Fail` 方法會在對話方塊中顯示資訊。

[ **輸出** ] 視窗也可以顯示下列資訊：

- 偵錯工具已載入或卸載的模組。

- 已擲回的例外狀況。

- 已結束的處理序。

- 已結束的執行序。

## <a name="see-also"></a>另請參閱
- [偵錯工具安全性](../debugger/debugger-security.md)
- [輸出視窗](../ide/reference/output-window.md)
- [追蹤和檢測應用程式](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) (機器翻譯)
- [C #、F # 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)
