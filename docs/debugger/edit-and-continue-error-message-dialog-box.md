---
title: 編輯後繼續錯誤訊息對話方塊 |Microsoft Docs
description: '[編輯後繼續] 可能會報告您的程式碼變更無法使用它。 本文提供可能的原因。'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8ef34889b838e2f7eaa92420eec90db9def57e65
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862839"
---
# <a name="edit-and-continue-error-message"></a>編輯後繼續錯誤訊息

當您要以支援 [編輯後繼續] 的程式碼語言進行偵錯工具時，會出現 [ **編輯後繼續** ] 錯誤訊息框，但是您所做的程式碼變更無法使用 [編輯後繼續]。 錯誤訊息會提供更詳細的說明。 若要回應對話方塊，請選取 **[確定** ] 關閉對話方塊，並取消編輯嘗試。

此錯誤訊息的可能原因包括：

- 嘗試編輯 SQL Server 程式碼。
- 嘗試編輯優化的程式碼。 您可能需要從發行組建切換至 debug build。
- 嘗試在執行時編輯程式碼，而不是在偵錯工具中暫停。 嘗試 [設定中斷點](../debugger/using-breakpoints.md)，並在暫停時編輯程式碼。
- 當僅啟用非受控的偵錯工具時，嘗試編輯 managed 程式碼。 [編輯後繼續] 不適用於 [混合模式的調試](../debugger/how-to-debug-in-mixed-mode.md)。
- 在程式設計語言中進行 [編輯後繼續] 不支援的程式碼變更。 如需詳細資訊，請參閱 [c # 中支援的程式碼變更](supported-code-changes-csharp.md)檔、 [Visual Basic 編輯後繼續中不支援的](supported-code-changes-csharp.md)編輯，以及 [支援的 c + + 程式碼變更](supported-code-changes-cpp.md)。
- 嘗試在您所連接的應用程式中編輯程式碼，而不是從 [ **調試** 程式] 功能表開始偵錯工具。
- 嘗試在偵測 Dr. Watson 傾印時編輯程式碼。
- 在未處理的例外狀況發生後嘗試編輯程式碼，但未選取 [未處理的例外狀況] 的 **[回溯呼叫堆疊** ] 選項。
- 嘗試在對內嵌執行時間應用程式進行偵錯工具時編輯程式碼。
- 嘗試使用64位應用程式目標的4.5.1 之前的 .NET Framework 版本來編輯 managed 程式碼。 若要針對4.5.1 之前的 .NET Framework 使用 [編輯後繼續]，請 **x86** 在 [ **\<ProjectName>**  >  **屬性**  >  **編譯**] **Advanced Compiler** 索引標籤中，將 [目標] 設定為 [x86]
- 嘗試編輯元件中的程式碼在偵錯工具期間已修改，且已重載。
- 嘗試編輯尚未載入之元件中的程式碼。
- 開始對繼承應用程式進行偵錯工具，因為最新版本的組建錯誤。

如需詳細資訊，請參閱：
- [C + + 編輯後繼續的 blog 文章](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [ (c + +) 支援的程式碼變更 ](../debugger/supported-code-changes-cpp.md)
- [編輯後繼續](../debugger/edit-and-continue.md)