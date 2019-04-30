---
title: 命令設計 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c176a558d7d5956c1d41593f5d0cc71184a9a820
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861689"
---
# <a name="command-design"></a>命令設計
當您將命令加入 VSPackage 時，您必須指定所要出現，時，它的方式處理。

## <a name="define-commands"></a>定義命令
 若要定義新的命令，包括 Visual Studio 命令資料表 (*.vsct*) VSPackage 專案中的檔案。 如果您已經使用 Visual Studio package 範本建立 VSPackage，專案會包含其中一個檔案。 如需詳細資訊，請參閱 < [Visual Studio 命令表檔案 (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

 Visual Studio 合併所有 *.vsct*檔案，會發現，讓它可以顯示的命令。 因為這些檔案是二進位 VSPackage 有所區別，所以 Visual Studio 並沒有載入的封裝，若要尋找的命令。 如需詳細資訊，請參閱 <<c0> [ 如何 Vspackage 加入使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

 Visual Studio 會使用<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>註冊屬性來定義功能表資源和命令。 如需詳細資訊，請參閱 <<c0> [ 命令的實作](../../extensibility/internals/command-implementation.md)。

 命令可以在執行階段變更，在幾個不同的方式。 它們可以顯示或隱藏、 啟用或停用。 它們可以顯示不同的文字或圖示，或包含不同的值。 可能會執行大量自訂，Visual Studio 會載入 VSPackage。 如需詳細資訊，請參閱 <<c0> [ 如何 Vspackage 加入使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

## <a name="command-handlers"></a>命令處理常式
 當您建立命令時，您必須提供事件處理常式執行命令。 如果使用者選取命令時，它必須適當地路由傳送。 路由命令，表示傳送至正確的 VSPackage，以啟用或停用、 隱藏或顯示，並執行它，如果使用者選擇要執行這項操作。 如需詳細資訊，請參閱 <<c0> [ 命令的路由演算法](../../extensibility/internals/command-routing-algorithm.md)。

## <a name="visual-studio-command-environment"></a>Visual Studio 命令的環境
 Visual Studio 可以裝載任何數目的 Vspackage，以及每個可以參與它自己的命令集。 環境會顯示適用於目前工作的命令。 如需詳細資訊，請參閱 <<c0> [ 命令可用性](../../extensibility/internals/command-availability.md)並[選取內容物件](../../extensibility/internals/selection-context-objects.md)。

 定義新的命令、 功能表、 工具列或捷徑功能表的 VSPackage 提供其命令資訊給 Visual Studio 在安裝期間，透過參考原生或 managed 組件中的資源的登錄項目。 然後每個資源參考的二進位資料資源 (*.cto*) 檔案，當您編譯的 Visual Studio 命令資料表則會產生 (*.vsct*) 檔案。 這可讓 Visual Studio，而不必載入每個已安裝的 VSPackage 提供合併的命令集、 功能表和工具列。

### <a name="command-organization"></a>命令的組織
 環境將依照群組、 優先權和功能表命令。

- 群組是邏輯集合的相關命令，例如，**剪下**，**複製**，並**貼上**命令群組。 群組會出現在功能表的命令。

- 優先順序會決定在群組中的個別命令功能表出現的順序。

- 功能表做為容器的群組。

  某些命令、 群組和功能表會預先定義的環境。 如需詳細資訊，請參閱 <<c0> [ 預設命令、 群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)。

  命令可以指派給主要群組。 主要群組控制項的命令，在主功能表結構和位置**自訂** 對話方塊。 命令可以出現在多個群組;例如，命令可以是主功能表上、 快顯功能表和工具列。 如需詳細資訊，請參閱 <<c0> [ 如何 Vspackage 加入使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

### <a name="command-routing"></a>命令路由
 叫用和路由命令的 Vspackage 的程序與不同的物件執行個體上呼叫方法的程序。

 環境將路由傳送到最外層的 （全域） 內容從 (local) 的最內層命令內容，此作業取決於目前的選取項目，依序命令。 無法執行命令的第一個內容是處理它。 如需詳細資訊，請參閱 <<c0> [ 命令的路由演算法](../../extensibility/internals/command-routing-algorithm.md)。

 在大部分情況下，環境會處理命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 命令路由配置可讓許多不同的物件來處理命令，因為<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>可以實作任意數目的物件，這些包括 Microsoft ActiveX 控制項、 視窗檢視實作、 文件物件、 專案階層並 （適用於全域命令） VSPackage 物件本身。 在某些特殊的情況下，例如，路由命令 」 在階層中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>必須實作介面。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[命令實作](../../extensibility/internals/command-implementation.md)|描述如何在 VSPackage 中實作命令。|
|[命令可用性](../../extensibility/internals/command-availability.md)|描述 Visual Studio 內容如何決定哪些命令。|
|[命令路由演算法](../../extensibility/internals/command-routing-algorithm.md)|描述 Visual Studio 命令路由架構如何讓由不同的 Vspackage 的命令。|
|[命令放置指導方針](../../extensibility/internals/command-placement-guidelines.md)|會建議如何放置在 Visual Studio 環境中的命令。|
|[Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|描述 Vspackage 如何最佳利用 Visual Studio 命令架構。|
|[預設命令、 群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|描述 Vspackage 如何最佳使用隨附於 Visual Studio 的命令。|
|[管理 Vspackage](../../extensibility/managing-vspackages.md)|描述 Visual Studio 載入 Vspackage 的方式。|
|[Visual Studio 命令表檔案 (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|提供資訊以 XML 為基礎 *.vsct*用來描述的配置和外觀的命令，在 Vspackage 中的檔案。|