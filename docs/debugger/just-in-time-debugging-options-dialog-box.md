---
title: '[選項] 對話方塊、即時調試 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c27ec66c8165995c6877b9a9e65802813140c7f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731615"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>選項對話方塊、偵錯、Just-In-Time
若要存取 [Just-In-Time] 頁面，請前往 [工具] 功能表並按一下 [選項]。 在 [選項] 對話方塊中，展開 [偵錯] 節點並選取 [Just-In-Time]。 這個頁面可讓您啟用 Managed 程式碼、機器碼和指令碼的 Just-In-Time 偵錯。 如需詳細資訊，請參閱 [Just-In-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)。

 您可以為這些程式類型啟用 Just-In-Time 偵錯：

- Managed

- 原生

- 指令碼

  Just-In-Time 偵錯一項技術，可讓您對 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外部啟動的程式進行偵錯。 您可以執行在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境外的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中所建立的程式。 如果您已啟用 Just-In-Time 偵錯，發生損毀時將會顯示對話方塊，詢問您是否要進行偵錯。

## <a name="associated-warnings"></a>相關聯的警告
 當您前往 [選項] 對話方塊的這個頁面時，可能會看見像這樣的警告訊息：

 **另一個偵錯工具已經將本身註冊為即時偵錯工具。若要修復，請啟用即時調試，或執行 Visual Studio 修復。**

 如果您將另一個偵錯工具設為 Just-In-Time 偵錯工具 (可能是舊版的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具)，就會出現這則訊息。

 以下是您可能會看到的另一則訊息：

 **偵測到即時偵測到的註冊錯誤。若要修復，請啟用即時調試，或執行 Visual Studio 修復。**

 如果您看到這些警告的任何一項，那麼在修正問題之前，使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 的 Just-In-Time 偵錯都需要系統管理員權限。 如果您嘗試在這些狀況下以非系統管理員身分啟用，將會看見下列錯誤訊息：

 **拒絕存取。讓系統管理員能夠進行即時的偵錯工具，或修復您的 Visual Studio 安裝。**

## <a name="see-also"></a>請參閱
- [選項對話方塊、偵錯](../debugger/debugging-options-dialog-box.md)
- [如何：指定偵錯工具設定](../debugger/how-to-specify-debugger-settings.md)