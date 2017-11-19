---
title: "命令路由演算法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e85ad4c4027a27b33f2f96284df80f852ffe3b85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="command-routing-algorithm"></a>命令路由演算法
在 Visual Studio 中多個不同的元件會處理命令。 命令會從最內部的內容中，根據目前的選取範圍，路由傳送到最外層 （也稱為通用） 的內容。 如需詳細資訊，請參閱[可用性](../../extensibility/internals/command-availability.md)。  
  
## <a name="order-of-command-resolution"></a>命令解析順序  
 命令傳遞的命令內容的下列層級：  
  
1.  增益集： 環境第一次提供的任何增益集出現的命令。  
  
2.  優先順序命令： 使用這些命令會註冊<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>。 它們會呼叫在 Visual Studio 中的每個命令，且其已註冊的順序呼叫。  
  
3.  內容功能表命令: 內容功能表上的命令第一次提供給一般路由提供給內容功能表中，在命令目標。  
  
4.  工具列設定命令目標： 當您呼叫註冊這些命令目標<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>。 `pCmdTarget`參數可以是`null`。 如果不是`null`，則此命令的目標用來更新您要設定在工具列上找到的任何命令。 如果介面設定您的工具列，則它會傳遞做為視窗框架`pCmdTarget`，讓所有更新的命令視窗框架中，您工具列流經都即使當它不是處於焦點。  
  
5.  工具視窗： 工具視窗，通常會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面，也應該實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，讓 Visual Studio 工具視窗是作用中視窗時，可取得命令目標。 不過，如果工具視窗有焦點是**專案**視窗中，則此命令會路由傳送至<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>共同的選取項目的父系的介面。 此選取項目跨越多個專案，如果要將命令路由至<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>階層。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面包含<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>上對應的命令類似的方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  
  
6.  文件視窗： 如果命令已在其.vsct 檔案中設定了 RouteToDocs 旗標，Visual Studio 會尋找文件檢視物件，可能是在命令目標的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面或文件物件的執行個體 (通常<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>介面或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面)。 如果文件檢視物件不支援命令，Visual Studio 會將路由至命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>傳回的介面。 （這是文件資料物件的選用介面）。  
  
7.  目前的階層： 目前的階層可擁有使用中的文件視窗或階層中所選取的專案**方案總管 中**。 Visual Studio 會尋找<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>最新的或使用中的階層實作的介面。 階層應支援階層為作用中，即使專案項目的文件視窗具有焦點時是有效的命令。 不過，命令時，才套用**方案總管 中**具有焦點必須支援使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面及其<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>方法。  
  
     **剪下**，**複製**，**貼上**，**刪除**，**重新命名**，**輸入**，和**DoubleClick**命令需要特殊處理。 如需有關如何處理資訊**刪除**和**移除**命令在階層中，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>介面。  
  
8.  全域： 如果命令尚未處理的先前所述的內容中，Visual Studio 會嘗試傳送至擁有命令實作 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 如果 VSPackage 尚未已經載入，它時不會載入 Visual Studio 會呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 只有當載入 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [命令設計](../../extensibility/internals/command-design.md)