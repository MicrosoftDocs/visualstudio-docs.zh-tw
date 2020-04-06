---
title: 指令設計 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709652"
---
# <a name="command-design"></a>指令設計
將命令添加到 VSPackage 時,必須指定該命令的顯示位置、何時可用以及如何處理。

## <a name="define-commands"></a>定義命令
 要定義新命令,請在 VSPackage 專案中包括 Visual Studio 命令表 *(.vsct*) 檔。 如果使用 Visual Studio 程式包範本建立了 VSPackage,則專案包括其中一個檔。 有關詳細資訊,請參閱[可視化工作室命令表 (.vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

 Visual Studio 合併它找到的所有 *.vsct*檔案,以便它可以顯示命令。 由於這些檔與 VSPackage 二進位檔案不同,因此 Visual Studio 不必載入包來查找命令。 有關詳細資訊,請參閱[VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

 Visual Studio<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>使用註冊屬性定義功能表資源和命令。 有關詳細資訊,請參閱[指令實現](../../extensibility/internals/command-implementation.md)。

 命令可以在運行時以許多不同的方式更改。 它們可以顯示或隱藏、啟用或禁用。 它們可以顯示不同的文本或圖示,或包含不同的值。 在 Visual Studio 載入您的 VSPackage 之前,可能會執行大量自定義。 有關詳細資訊,請參閱[VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

## <a name="command-handlers"></a>命令處理常式
 創建命令時,必須提供事件處理程式來執行該命令。 如果用戶選擇該命令,則必須對其進行適當路由。 路由命令意味著將其發送到正確的 VSPackage 以啟用或禁用它、隱藏或顯示它,並在使用者選擇這樣做時執行它。 有關詳細資訊,請參閱[命令路由演演算法](../../extensibility/internals/command-routing-algorithm.md)。

## <a name="visual-studio-command-environment"></a>視覺化工作室命令環境
 Visual Studio 可以承載任意數量的 VS 包,並且每個元件都可以貢獻自己的命令集。 環境僅顯示適合當前任務的命令。 關於詳細資訊,請參考[指令可用性](../../extensibility/internals/command-availability.md)與[選擇內容 。](../../extensibility/internals/selection-context-objects.md)

 定義新命令、功能表、工具列或快捷功能表的 VSPackage 通過引用本機或託管程式集中的資源的註冊表項,在安裝時向 Visual Studio 提供其命令資訊。 然後,每個資源引用二進位資料資源(*.cto*) 檔案,該檔是在編譯 Visual Studio 命令表 *(.vsct*) 檔時產生的。 這使 Visual Studio 能夠提供合併的命令集、功能表和工具列,而無需載入每個已安裝的 VSPackage。

### <a name="command-organization"></a>指揮組織
 環境按組、優先順序和功能表定位命令。

- 群組是相關命令的邏輯集合,例如「**剪切**」、「**複製**」 與 **「貼上」** 指令群組。 組是顯示在功能表上的命令。

- 優先順序確定組中單個命令在功能表上的顯示順序。

- 功能表充當組的容器。

  環境預定義一些命令、組和功能表。 有關詳細資訊,請參閱[預設指令、群組和工具列放置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)。

  命令可以分配給主組。 主組控制命令在主選單結構和 **「自訂」** 對話方塊中的位置。 命令可以出現在多個組中;但是,命令可以出現在多個組中。例如,命令可以位於主菜單、快捷功能表和工具列上。 有關詳細資訊,請參閱[VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

### <a name="command-routing"></a>命令路由
 VSPackages 的調用和路由命令的過程不同於在物件實例上調用方法的過程。

 環境按順序將命令從基於當前選擇的最內層(局部)命令上下文路由到最外層(全域)上下文。 能夠執行命令的第一個上下文是處理該命令的上下文。 有關詳細資訊,請參閱[命令路由演演算法](../../extensibility/internals/command-routing-algorithm.md)。

 在大多數情況下,環境使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面處理命令。 由於命令路由方案允許許多不同的物件處理命令,<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>因此可以由任意數量的物件實現;其中包括 Microsoft ActiveX 控制件、視窗檢視實現、文件物件、專案層次結構和 VSPackage 物件本身(用於全域命令)。 在某些特殊情況下,例如,層次結構中的路由命令,必須實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[命令執行](../../extensibility/internals/command-implementation.md)|描述如何在 VSPackage 中實現命令。|
|[命令可用性](../../extensibility/internals/command-availability.md)|描述可視化工作室上下文如何確定哪些命令可用。|
|[命令路由演演算法](../../extensibility/internals/command-routing-algorithm.md)|描述 Visual Studio 命令路由體系結構如何使命令能夠由不同的 VS 包處理。|
|[命令放置指南](../../extensibility/internals/command-placement-guidelines.md)|建議如何在可視化工作室環境中放置命令。|
|[VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|描述 VSPackages 如何最好地利用可視化工作室命令體系結構。|
|[預設命令、群組與工具列放置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|描述 VS 包如何最好地使用 Visual Studio 中包含的命令。|
|[管理 VSPackages](../../extensibility/managing-vspackages.md)|描述可視化工作室如何載入 VS 包。|
|[視覺化工作室指令表 (.vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|提供有關基於 XML*的 .vsct*檔案的資訊,這些檔用於描述 VS 包中命令的佈局和外觀。|
