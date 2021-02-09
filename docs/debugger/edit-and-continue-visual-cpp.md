---
title: " (c + +) 的 [編輯後繼續] |Microsoft Docs"
description: C + + 專案可使用 [編輯後繼續]。 瞭解哪些是支援的編輯，以及如何控制是否以及何時套用您的編輯。
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4fd6d5214211318e2271418425a117a73eb0ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871880"
---
# <a name="edit-and-continue-c"></a>編輯後繼續 (C++)
您可以在 c + + 專案中使用 [編輯後繼續]。 如需 [編輯後繼續] 限制的相關資訊，請參閱支援的程式 [代碼變更 (c + +) ](../debugger/supported-code-changes-cpp.md) 。

如需 Visual Studio 2015 Update 3 改善的詳細資訊，請參閱 [Visual Studio 2015 update 3 中的 c + + 編輯後繼續](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)。

 在 Visual Studio 2013 Update 3 中推出的 [/Zo (增強最佳化偵錯)](/cpp/build/reference/zo-enhance-optimized-debugging) 編譯器選項會將額外資訊新增至不使用 [/Od (停用 (偵錯))](/cpp/build/reference/od-disable-debug) 選項編譯之二進位碼檔案的 .pdb (符號) 檔案。

 **/Zo** 會停用 [編輯後繼續]。 請參閱[如何：對最佳化程式碼進行偵錯](../debugger/how-to-debug-optimized-code.md)。

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> 啟用或停用編輯後繼續
 如果您不希望在目前的偵錯工作階段中套用正在編輯的程式碼內容，您可能需要停用 [編輯後繼續] 的自動引動過程。 您也可以重新啟用自動的 [編輯後繼續]。

> [!IMPORTANT]
> 如需有關功能相容性的必要組建設定及其他資訊，請參閱 [Visual Studio 2015 Update 3 中的 c + + 編輯後繼續](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)。

1. 如果您是在偵測會話中，請停止調試 (**Shift + F5**) 。

2. 在 [工具] 功能表上，選擇 [選項]。

3. 在 [ **選項** ] 對話方塊中，選取 **[調試 > 一般**]。

4. 若要啟用，請選取 [ **啟用編輯後繼續**]。 若要停用，請清除該核取方塊。

5. 在 [編輯後繼續]  群組中，選取或清除 [啟用原生編輯後繼續]  核取方塊。

   修改這個設定會影響您處理的所有專案。 變更這個設定之後不需要重建應用程式。 如果您從命令列或 makefile 建立您的應用程式，但在 Visual Studio 環境中進行偵錯工具，您仍然可以在設定 **/zi** 選項時使用 [編輯後繼續]。

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> 如何明確套用程式碼變更
 在 c + + 中，[編輯後繼續] 可以用兩種方式套用程式碼變更。 當您選擇執行命令時，會隱含地套用程式碼變更，而您使用 [ **套用程式碼變更** ] 命令時，則會明確套用程式碼變更。

 當您明確套用程式碼變更時，程式會保持在中斷模式中，即完全不會執行。

- 若要明確套用程式碼變更，請在 [偵錯]  功能表上，選擇 [套用程式碼變更] 。

## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> 如何停止程式碼變更
 當 [編輯後繼續] 正在套用程式碼變更時，您可以停止該作業。

 若要停止套用程式碼變更：

- 在 [偵錯]  功能表上，選擇 [停止套用程式碼變更] 。

  只有套用程式碼變更時，才能看見這個功能表項目。

  如果您選擇此選項，就無法認可任何的程式碼變更。

## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> 如何重設執行點
 某些程式碼變更會在 [編輯後繼續] 套用該變更時，造成執行點移至新位置。 [編輯後繼續] 會盡量精確地放置執行點，但有時結果未必完全正確。

 在 c + + 中，對話方塊會在執行點變更時通知您。 您應該先確認位置是否正確，再繼續偵錯。 如果位置不正確，請使用 [ **設定下一個陳述式** ] 命令。 如需詳細資訊，請參閱 [設定下一個要執行的陳述式](./navigating-through-code-with-the-debugger.md#BKMK_Set_the_next_statement_to_execute)。

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> 如何使用過時程式碼
 在某些情況下，[編輯後繼續] 不能立即將程式碼變更套用至執行檔，但是如果您繼續偵錯或許能在稍後套用程式碼變更。 如果您編輯呼叫目前函式的函式，或將 64 位元組以上的新變數加入至呼叫堆疊上的某個函式時，就會發生這種情況。

 在上述情形中，偵錯工具會繼續執行原始的程式碼直到套用變更為止。 過時程式碼會在不同的來源視窗中顯示為暫時原始程式檔視窗，並使用像是 `enc25.tmp`的標題。 已編輯的來源會繼續出現在原始來源視窗中。 如果您嘗試編輯過時程式碼，就會出現警告訊息。

## <a name="see-also"></a>另請參閱
- [支援的程式碼變更 (C++)](../debugger/supported-code-changes-cpp.md)