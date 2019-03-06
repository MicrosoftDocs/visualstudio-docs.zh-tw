---
title: 實作的命令處理巢狀專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a75c6edcc084c8ec7c6942e011af9978a961c83
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606528"
---
# <a name="implementing-command-handling-for-nested-projects"></a>實作巢狀專案的命令處理
IDE 可以傳遞命令，會傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>而<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>巢狀的專案，或父專案的介面可以篩選或覆寫命令。

> [!NOTE]
>  您可以篩選通常由父專案的命令。 命令，例如**建置**並**部署**，都由 IDE 無法進行篩選。

 下列步驟描述實作命令處理的程序。

## <a name="procedures"></a>程序

#### <a name="to-implement-command-handling"></a>若要實作命令處理

1. 當使用者選取巢狀的專案或節點中的巢狀專案：

   1. IDE 呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。

      — 或 —

   2. 如果此命令，在 階層 視窗中，例如在 方案總管的捷徑功能表命令產生 IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>專案的父代上的方法。

2. 父專案可以檢查傳遞給參數`QueryStatus`，這類`pguidCmdGroup`和`prgCmds`，以決定父專案是否應該篩選命令。 如果父專案來篩選命令來實作，它應該設定：

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    則應傳回父專案`S_OK`。

    如果父專案不會篩選命令，它應該只傳回`S_OK`。 在此情況下，IDE 會自動將命令路由至子專案。

    若要將命令路由傳送至子專案沒有父專案。 IDE 會執行此工作...

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)
- [巢狀專案](../../extensibility/internals/nesting-projects.md)