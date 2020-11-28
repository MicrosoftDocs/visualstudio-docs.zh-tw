---
title: 命令路由演算法 |Microsoft Docs
description: 瞭解 Visual Studio 中的命令解析順序，因為命令是由不同的元件處理，並從最內層路由到最外層的內容。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1694e0835add6eac75986538a8abae99adf717b1
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305240"
---
# <a name="command-routing-algorithm"></a>命令路由演算法
在 Visual Studio 命令會由許多不同的元件處理。 命令會根據目前的選取範圍，從最內層的內容路由傳送至最外層的 (也稱為全域) 內容。 如需詳細資訊，請參閱 [命令可用性](../../extensibility/internals/command-availability.md)。

## <a name="order-of-command-resolution"></a>命令解析的順序
 命令會透過下列層級的命令內容來傳遞：

1. 增益集：環境會先提供命令給任何出現的增益集。

2. 優先權命令：這些命令是使用註冊的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> 。 它們是針對 Visual Studio 中的每個命令呼叫，並依其註冊的順序呼叫。

3. 內容功能表命令：位於內容功能表上的命令會先提供給內容功能表所提供的命令目標，然後再提供給一般路由。

4. 工具列設定命令目標：當您呼叫時，這些命令目標會註冊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> 。 `pCmdTarget`參數可以是 `null` 。 如果不是 `null` ，則會使用這個命令目標來更新您正在設定的工具列上的任何命令。 如果 shell 正在設定您的工具列，則會將視窗框架傳遞為， `pCmdTarget` 如此一來，工具列上命令的所有更新都會流經視窗框架，即使不是焦點也是如此。

5. 工具視窗：通常會實作為介面的工具視窗 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 也應該執行介面， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 讓 Visual Studio 可以在工具視窗是使用中視窗時取得命令目標。 不過，如果具有焦點的工具視窗是 [ **專案** ] 視窗，則會將命令路由傳送至所 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 選項目的通用父系介面。 如果此選項跨越多個專案，則會將命令路由傳送至階層 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面包含 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 方法，類似于介面上的對應命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。

6. 文件視窗：如果命令 `RouteToDocs` 在其 *.vsct* 檔案中設定了旗標，Visual Studio 會在檔視圖物件（也就是介面的實例或檔物件的實例）上尋找命令目標， <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> (通常是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 介面或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 介面) 。 如果 document view 物件不支援命令，Visual Studio 會將命令路由傳送至傳回的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。  (這是檔資料物件的選用介面。 ) 

7. 目前階層：目前的階層可以是擁有使用中文件視窗的專案，或是在 **方案總管** 中選取的階層。 Visual Studio 會尋找在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 目前或使用中的階層上所執行的介面。 階層應該支援每次使用時都有效的命令，即使專案專案的文件視窗具有焦點也一樣。 不過，只有在 **方案總管** 具有焦點時才適用的命令，必須使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 介面及其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和方法來支援 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 。

     **剪** 下、 **複製**、 **貼** 上、 **刪除**、 **重新命名**、 **輸入** 和 **DoubleClick** 命令都需要特殊處理。 如需如何處理階層中 **刪除** 和 **移除** 命令的詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> 介面。

8. 全域：如果先前提及的內容尚未處理某個命令，Visual Studio 會嘗試將它路由至擁有執行介面之命令的 VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。 如果尚未載入 VSPackage，當 Visual Studio 呼叫方法時，就不會載入它 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 。 只有在呼叫方法時，才會載入 VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 。

## <a name="see-also"></a>另請參閱
- [命令設計](../../extensibility/internals/command-design.md)
