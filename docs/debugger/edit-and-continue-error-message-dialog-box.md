---
title: 編輯後繼續錯誤訊息對話方塊 |Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df95eae689f7c3abbb0d75a7557ce749bdceee5
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188230"
---
# <a name="edit-and-continue-error-message"></a>編輯後繼續錯誤訊息

當您使用支援 [編輯後繼續] 的程式碼語言進行偵測，但 [編輯後繼續] 無法用於您所做的程式碼變更時，就會出現 [**編輯後繼續**] 錯誤訊息框。 錯誤訊息會提供更詳細的說明。 若要回應對話方塊，請選取 **[確定**] 以關閉對話方塊，並取消編輯嘗試。

此錯誤訊息的可能原因包括：

- 正在嘗試編輯 SQL Server 程式碼。
- 正在嘗試編輯優化的程式碼。 您可能需要從發行組建切換到 debug 組建。
- 嘗試在程式碼正在執行時進行編輯，而不是在偵錯工具中暫停。 嘗試[設定中斷點](../debugger/using-breakpoints.md)，並在暫停時編輯程式碼。
- 只有在啟用非受控的偵錯工具時，嘗試編輯 managed 程式碼。 [編輯後繼續] 不會使用[混合模式的調試](../debugger/how-to-debug-in-mixed-mode.md)。
- 在程式設計語言中進行 [編輯後繼續] 不支援的程式碼變更。 如需詳細資訊，請參閱[中C#有關支援的程式碼變更](supported-code-changes-csharp.md)的文章、 [Visual Basic 編輯後繼續中不支援的編輯](supported-code-changes-csharp.md)，以及支援[ C++的程式碼變更](supported-code-changes-cpp.md)。
- 嘗試編輯您所連接之應用程式中的程式碼，而不是從 [**調試**程式] 功能表開始進行偵錯工具。
- 在偵測 Dr. Watson 傾印時嘗試編輯程式碼。
- 在未處理的例外狀況發生後嘗試編輯程式碼，而且未選取 [未**處理的例外狀況回溯呼叫堆疊**] 選項。
- 嘗試在進行內嵌的執行時間應用程式時編輯程式碼。
- 嘗試使用64位應用程式目標的4.5.1 之前的 .NET Framework 版本來編輯 managed 程式碼。 若要針對4.5.1 之前的 .NET Framework 使用 編輯後繼續，請在 **\<專案集 >**  > **屬性** > **編譯** 索引標籤、 **Advanced 編譯器** 設定中，將目標設定為**x86**
- 正在嘗試編輯元件中的程式碼，該元件已在偵測期間修改，並已重載。
- 正在嘗試編輯尚未載入之元件中的程式碼。
- 因為最新版本的組建錯誤，所以開始對應用程式的舊版進行 debug。

如需詳細資訊，請參閱:
- [C++編輯後繼續的 blog 文章](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [支援的程式碼變更 (C++)](../debugger/supported-code-changes-cpp.md)
- [編輯後繼續](../debugger/edit-and-continue.md)