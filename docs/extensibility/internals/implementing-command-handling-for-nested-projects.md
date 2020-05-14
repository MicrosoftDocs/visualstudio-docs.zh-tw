---
title: 為嵌套項目實施命令處理 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707601"
---
# <a name="implementing-command-handling-for-nested-projects"></a>實作巢狀專案的命令處理
IDE 可以將<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>通過<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>和介面傳遞到嵌套專案的命令,或者父專案可以篩選或重寫命令。

> [!NOTE]
> 只能篩選父專案通常處理的命令。 無法篩選 IDE 處理的**生成**和**部署**等命令。

 以下步驟描述了實現命令處理的過程。

## <a name="procedures"></a>程序

#### <a name="to-implement-command-handling"></a>執行指令處理

1. 當使用者選擇嵌入的嵌套項目或節點時:

   1. IDE 調<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>用 方法。

      — 或者—

   2. 如果命令源自層次結構視窗(如解決方案資源管理器中的快捷功能表命令),則IDE將在專案的父視窗中<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>調用該方法。

2. 父專案可以檢查要傳遞給`QueryStatus`的參數,`pguidCmdGroup`如`prgCmds`和,以確定父專案是否應篩選命令。 如果父項目實現以篩選命令,則應設置:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    然後父項目應傳`S_OK`回 。

    如果父項目不篩選命令,則應該被返回`S_OK`。 在這種情況下,IDE 會自動將命令路由到子專案。

    父專案不必將命令路由到子專案。 IDE 執行此任務。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)
- [巢狀專案](../../extensibility/internals/nesting-projects.md)
