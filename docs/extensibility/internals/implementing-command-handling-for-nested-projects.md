---
title: 執行嵌套專案的命令處理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 628fde153441104e4bb504253d96235270b4b8fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727087"
---
# <a name="implementing-command-handling-for-nested-projects"></a>實作巢狀專案的命令處理
IDE 可以傳遞透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面傳遞至嵌套專案的命令，或父專案可以篩選或覆寫命令。

> [!NOTE]
> 只有一般由父專案處理的命令才可以進行篩選。 無法篩選由 IDE 處理的命令，例如**組建**和**部署**。

 下列步驟描述執行命令處理的程式。

## <a name="procedures"></a>程序

#### <a name="to-implement-command-handling"></a>若要執行命令處理

1. 當使用者選取嵌套專案或嵌套專案中的節點時：

   1. IDE 會呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法。

      — 或 —

   2. 如果命令源自于階層視窗（例如方案總管中的快捷方式功能表命令），IDE 會在專案的父系上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 方法。

2. 父專案可以檢查要傳遞給 `QueryStatus`的參數（例如 `pguidCmdGroup` 和 `prgCmds`），以判斷父專案是否應該篩選命令。 如果將父專案實作為篩選命令，應該設定：

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    然後，父專案應該會傳回 `S_OK`。

    如果父專案未篩選命令，則應該只傳回 `S_OK`。 在此情況下，IDE 會自動將命令路由傳送至子專案。

    父專案不需要將命令路由至子專案。 IDE 會執行這項工作。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)
- [巢狀專案](../../extensibility/internals/nesting-projects.md)