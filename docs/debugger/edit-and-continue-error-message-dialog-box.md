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
ms.openlocfilehash: 47693c6fbb25fb0a7c2468abbad515f8aaf63159
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694981"
---
# <a name="edit-and-continue-error-message"></a>編輯後繼續錯誤訊息

**編輯後繼續**會出現錯誤訊息方塊，當您偵錯程式碼語言支援 編輯後繼續，但編輯後繼續不適用於您所做的程式碼變更。 錯誤訊息會提供更詳細的說明。 若要回應的對話方塊中，選取**確定**以關閉對話方塊，並取消編輯嘗試。

此錯誤訊息的可能原因包括：

-   嘗試編輯 SQL Server 程式碼。
-   嘗試編輯最佳化程式碼。 您可能需要從發行組建切換至偵錯組建。
-   嘗試編輯的程式碼，當它執行時，而不是偵錯工具中暫停時。 請嘗試[設定中斷點](../debugger/using-breakpoints.md)，和編輯程式碼時暫停。
-   嘗試啟用只有 unmanaged 偵錯時編輯 managed 程式碼。 編輯後繼續不適用於[混合模式偵錯](../debugger/how-to-debug-in-mixed-mode.md)。
-   讓程式碼變更，不支援編輯後繼續在您的程式語言。 如需詳細資訊，請參閱文件的相關[支援中的程式碼變更C# ](supported-code-changes-csharp.md)，[不支援的 Visual Basic 編輯後繼續 中的編輯](/visualstudio/debugger/supported-code-changes-csharp)，和[支援 c + + 程式碼變更](supported-code-changes-cpp.md).
-   您會附加到，比起從偵錯的應用程式中編輯程式碼嘗試**偵錯**功能表。
-   嘗試將偵錯 Dr 時編輯程式碼。Watson 傾印。
-   嘗試編輯的程式碼之後發生未處理的例外狀況, 和選項**回溯呼叫堆疊上未處理例外狀況**未選取。
-   嘗試將偵錯內嵌的執行階段應用程式時編輯程式碼。
-   嘗試編輯的.NET Framework 版本早於 4.5.1 使用 64 位元應用程式目標的 managed 程式碼。 若要使用 [編輯後繼續適用於.NET Framework 4.5.1 之前，請將目標設定為**x86**中**\<專案名稱 >** > **屬性** > **編譯**] 索引標籤**進階編譯器**設定。
-   嘗試編輯的偵錯期間已修改，且已重新載入的組件中的程式碼。
-   嘗試編輯尚未載入的組件中的程式碼。
-   開始偵錯舊版的應用程式，因為最新版本有建置錯誤。

如需詳細資訊，請參閱:
- [C + + 編輯後繼續的部落格文章](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [支援的程式碼變更 (C++)](../debugger/supported-code-changes-cpp.md)
- [編輯後繼續](../debugger/edit-and-continue.md)