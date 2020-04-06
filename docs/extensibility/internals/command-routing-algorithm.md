---
title: 命令路由演演演算法 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709542"
---
# <a name="command-routing-algorithm"></a>命令路由演演算法
在 Visual Studio 中,命令由許多不同的元件處理。 命令從最裡面的上下文(基於當前選擇)路由到最外層(也稱為全域)上下文。 有關詳細資訊,請參閱[命令可用性](../../extensibility/internals/command-availability.md)。

## <a name="order-of-command-resolution"></a>指令解析順序
 命令通過以下等級的指令上下文傳遞:

1. 載入項:環境首先向存在的任何載入項提供命令。

2. 優先順序命令:這些命令使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>註冊。 它們被調用在 Visual Studio 中的每個命令,並且按註冊順序調用。

3. 上下文菜單命令:首先向提供給上下文菜單的命令目標提供位於上下文菜單上的命令,然後提供給典型的路由。

4. 工具列設定指令目標:呼叫 時將註冊這些命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>目標 。 參數`pCmdTarget`可以`null`是 。 如果不是`null`,則此命令目標用於更新所設置工具列上的任何命令。 如果 shell 正在設定工具列,則它會將視窗框架`pCmdTarget`作為 傳遞 ,以便工具列上的命令的所有更新都流過視窗框架,即使它不在焦點中也是如此。

5. 工具視窗:工具視窗通常實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面,它也應該<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實現介面,以便 Visual Studio 可以在工具視窗處於活動狀態視窗時獲取命令目標。 但是,如果具有焦點的工具視窗是**Project**視窗,則該命令將路由到<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>所選項 的常見父級介面。 如果此選擇跨越多個專案,則命令將路由到<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>層次結構。 介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>包含<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>與介面上的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>相應 命令類似的 和 方法。

6. 文件視窗:如果命令在其 *.vsct*檔中`RouteToDocs`設置了 標誌,Visual Studio 會查找文檔檢視物件上的命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>目標,該物件是介面的實例或文件物件的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>實例<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>(通常是介面或介面)。 如果文件檢視物件不支援該命令,Visual Studio 會將命令路由到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>返回的介面。 (這是文件數據物件的可選介面。

7. 當前層次結構:當前層次結構可以是擁有活動文檔視窗的專案或**解決方案資源管理器**中選擇的層次結構。 Visual Studio<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>查找 在當前層次結構或活動層次結構上實現的介面。 層次結構應支援每當層次結構處於活動狀態時有效的命令,即使專案項的文檔視窗具有焦點也是如此。 但是,必須使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面及其<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>及其及其方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>支援僅在**解決方案資源管理器**具有焦點時應用的命令。

     **剪下**、**複製**、**貼上**、**刪除**,**重新命名**,**請輸入**與**按下 命令**需要特殊處理。 有關如何在層次結構中處理**刪除**和**刪除**命令的<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>資訊, 請參閱介面。

8. 全域:如果命令未由前面提到的上下文處理,Visual Studio 會嘗試將其路由到擁有實現介面的命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>的 VSPackage。 如果 VSPackage 尚未載入,則 Visual Studio 調用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>該方法時不會載入它。 僅當調用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法時,才會載入 VSPackage。

## <a name="see-also"></a>另請參閱
- [指令設計](../../extensibility/internals/command-design.md)
